# Principles of Computer System Design: An Introduction

This is outline and notes of essential parts in this [book](https://www.amazon.com/Principles-Computer-System-Design-Introduction/dp/0123749573).

[Part 2(online)](https://ocw.mit.edu/resources/res-6-004-principles-of-computer-system-design-an-introduction-spring-2009/online-textbook/)

---

- [Principles of Computer System Design: An Introduction](#principles-of-computer-system-design--an-introduction)
- [1. Systems](#1-systems)
  * [1.1 Systems and Complexity](#11-systems-and-complexity)
    + [1.1.1 Common problems of systems in many fields](#111-common-problems-of-systems-in-many-fields)
    + [1.1.2 Systems, Components, Interfaces, and Environments](#112-systems--components--interfaces--and-environments)
    + [1.1.3 Complexity](#113-complexity)
  * [1.2 Sources of Complexity](#12-sources-of-complexity)
    + [1.2.1 Cascading and interacting requirements](#121-cascading-and-interacting-requirements)
    + [1.2.2 Maintaining High Utilization](#122-maintaining-high-utilization)
  * [1.3 Coping with Complexity I](#13-coping-with-complexity-i)
    + [1.3.1 Modularity](#131-modularity)
    + [1.3.2 Abstraction](#132-abstraction)
    + [1.3.3 Layering](#133-layering)
    + [1.3.4 Hierarchy](#134-hierarchy)
    + [1.3.5 Putting it back together: Names make connections](#135-putting-it-back-together--names-make-connections)
  * [1.4 Computer systems are the same but different](#14-computer-systems-are-the-same-but-different)
    + [1.4.1 Computer systems have no nearby bounds on composition](#141-computer-systems-have-no-nearby-bounds-on-composition)
    + [1.4.2 d(technology)/dt is unprecedented](#142-d-technology--dt-is-unprecedented)
  * [1.5 Coping with complexity II](#15-coping-with-complexity-ii)
    + [1.5.1 Why modularity, abstraction, layering, and hierarchy aren't enough](#151-why-modularity--abstraction--layering--and-hierarchy-aren-t-enough)
    + [1.5.2 Iteration](#152-iteration)
    + [1.5.3 Keep it simple](#153-keep-it-simple)
  * [Exercises 1](#exercises-1)
- [2. Elements of Computer System Organization](#2-elements-of-computer-system-organization)
  * [2.1 The three fundamental abstractions](#21-the-three-fundamental-abstractions)
    + [2.1.1 Memory](#211-memory)
      - [2.1.1.1 Read/Write coherence and atomicity](#2111-read-write-coherence-and-atomicity)
      - [2.1.1.2 memory latency](#2112-memory-latency)
      - [2.1.1.3 Memory names and addresses](#2113-memory-names-and-addresses)
      - [2.1.1.4 Exploiting the memory abstraction: RAID](#2114-exploiting-the-memory-abstraction--raid)
    + [2.1.2 Interpreters](#212-interpreters)
      - [2.1.2.1 Processors](#2121-processors)
      - [2.1.2.2 Interpreter layers](#2122-interpreter-layers)
    + [2.1.3 Communication links](#213-communication-links)
  * [2.2 Naming in computer systems](#22-naming-in-computer-systems)
    + [2.1.1 The naming model](#211-the-naming-model)
    + [2.2.2 Default and explicit content references](#222-default-and-explicit-content-references)
    + [2.2.3 Path names, naming networks, and recursive name resolution](#223-path-names--naming-networks--and-recursive-name-resolution)
    + [2.2.4 Multiple lookup: searching through layered contexts](#224-multiple-lookup--searching-through-layered-contexts)
    + [2.2.5 Comparing names](#225-comparing-names)
    + [2.2.6 Name discovery](#226-name-discovery)
  * [2.3 Organizing computer systems with names and layers](#23-organizing-computer-systems-with-names-and-layers)
    + [2.3.1 A hardware layer: The bus](#231-a-hardware-layer--the-bus)
    + [2.3.2 A software layer: The file abstraction](#232-a-software-layer--the-file-abstraction)
  * [2.5 Case study: UNIX file system layering and naming](#25-case-study--unix-file-system-layering-and-naming)
    + [2.5.1 Application programming interface for the UNIX file system](#251-application-programming-interface-for-the-unix-file-system)
    + [2.5.2 The block layer](#252-the-block-layer)
    + [2.5.3 The file layer](#253-the-file-layer)
    + [2.5.4 The inode number layer](#254-the-inode-number-layer)
  * [Exercise 2](#exercise-2)
- [3. The design of naming schemes](#3-the-design-of-naming-schemes)
  * [3.1 Considerations in the design of naming schemes](#31-considerations-in-the-design-of-naming-schemes)
    + [3.1.1 Modular sharing](#311-modular-sharing)
    + [3.1.2 Metadata and name overloading](#312-metadata-and-name-overloading)
    + [3.1.3 Addresses: Names that locate objects](#313-addresses--names-that-locate-objects)
    + [3.1.4 Generating unique names](#314-generating-unique-names)
    + [3.1.5 Intended audience and User-friendly names](#315-intended-audience-and-user-friendly-names)
    + [3.1.6 Relative lifetimes of names, values, and bindings](#316-relative-lifetimes-of-names--values--and-bindings)
    + [3.1.7 Looking back and ahead: Names are a basic system component](#317-looking-back-and-ahead--names-are-a-basic-system-component)
  * [3.2 Case study: The Uniform Resource Locator (URL)](#32-case-study--the-uniform-resource-locator--url-)
    + [3.2.1 Surfing as a referential experience; name discovery](#321-surfing-as-a-referential-experience--name-discovery)
    + [3.2.2 INterpretation of the URL](#322-interpretation-of-the-url)
    + [3.2.2 URL case sensitivity](#322-url-case-sensitivity)
    + [3.2.4 Wrong context references for a partial URL](#324-wrong-context-references-for-a-partial-url)
  * [3.3 War stories: pathologies in the use of names](#33-war-stories--pathologies-in-the-use-of-names)
    + [3.3.1 A name collision eliminates smiling faces](#331-a-name-collision-eliminates-smiling-faces)
    + [3.3.2 Fragile names from overloading, and a market solution](#332-fragile-names-from-overloading--and-a-market-solution)
    + [3.3.3 More fragile names from overloading, with market disruption](#333-more-fragile-names-from-overloading--with-market-disruption)
    + [3.3.4 Case-sensitivity in user-friendly names](#334-case-sensitivity-in-user-friendly-names)
    + [3.3.5 Running out of telephone numbers](#335-running-out-of-telephone-numbers)
  * [Exercise 3](#exercise-3)
- [4. Enforcing modularity with clients and services](#4-enforcing-modularity-with-clients-and-services)
  * [4.1 Client/service organization](#41-client-service-organization)
    + [4.1.1 From soft modularity to enforced modularity](#411-from-soft-modularity-to-enforced-modularity)
    + [4.1.2 Client/service organization](#412-client-service-organization)

---

# 1. Systems

## 1.1 Systems and Complexity

### 1.1.1 Common problems of systems in many fields

- Emergent properties
- Propagation of effects
- Incommensurate scaling
- Trade-offs

### 1.1.2 Systems, Components, Interfaces, and Environments

- A system is a set on interconnected components that has an expected behavior observed at the interface with its environment.

### 1.1.3 Complexity

- Large number of components
- Large number of interconnections
- Many irregularities
- A long description
- A team of designers, implementers, or maintainers

## 1.2 Sources of Complexity

### 1.2.1 Cascading and interacting requirements

- **Principle of escalating complexity**

*Adding a requirement increases complexity out of proportion*

- **Avoid excessive generality**

*If it is good for everything, it is good for nothing.*

### 1.2.2 Maintaining High Utilization

- **The law of diminishing returns**

*The more one improves some measure of goodness, the more effort the next improvement will require.*

## 1.3 Coping with Complexity I

### 1.3.1 Modularity

- **The unyielding foundations rule**

*It is easier to change a module than to change the modularity.*

### 1.3.2 Abstraction

- **The robustness principle**

*Be tolerant of inputs and strict on outputs.*

- **The safety margin principle**

*Keep track of the distance to the cliff, or you may fall iver the edge.*

### 1.3.3 Layering

### 1.3.4 Hierarchy

### 1.3.5 Putting it back together: Names make connections

- **Decouple modules with indirection**

*Indirection supports replaceability.*

## 1.4 Computer systems are the same but different

### 1.4.1 Computer systems have no nearby bounds on composition

### 1.4.2 d(technology)/dt is unprecedented

- **The incommensurate scaling rule**

*Changing any system parameter by a factor of 10 usually requires a new design.

## 1.5 Coping with complexity II

### 1.5.1 Why modularity, abstraction, layering, and hierarchy aren't enough

### 1.5.2 Iteration

- **Design for iteration**

4. And another item.

*You won't get it right the first time, so make it easy to change.*

   Take small steps  
   Don't rush  
   Plan for feedback  
   Study failures

- **Keep digging**

*Complex systems fail for complex reasons.*

   Continue looking for other contributing or more basic causes.  
   Don't ignore unexplained behavior.

### 1.5.3 Keep it simple

- **Adopt sweeping simplifications**

*So you can see what you are doing.*

## Exercises 1

 1. B
 2. E
 3. False
 4. C
 5. 1,600 lines, 16 x 15 / 2 = 120, 2,000 lines, 4 x 3 / 2 x 5 = 30, Good - because interconnections are reduced.


# 2. Elements of Computer System Organization

Three well-defined classes: the memory, the interpreter, and the communication link.

A primary method by which the abstract components of a computer system interact is *reference*, the usual way for one component to connect to another by *name*.

## 2.1 The three fundamental abstractions

### 2.1.1 Memory

- Memory (storage) is the system component that remembers data values for use in computation,

- `WRITE(name, value)`, `value <- READ(name)`

- A *volatile* memory is one whose mechanism of retaining information consumes energy. By connecting a volatile memory to a battery or an uninterruptible power supply, it can be made *durable*, which means that it is designed to remember for at least some specified period, known as *durability*.

- A *non-volatile* memory retains its content without power supply. Non-volatile memory devices are subject to eventualdeterioration, known as *decay*.

- Hardware layer memory devices READ and WRITE contiguous arrays of *bits*, usually fixed in length, known by various terms such as *bytes* (usually 8 bits), *words* (a small integer number of bytes, typically 2, 4, or 8), *lines* (several words), and *blocks* (a number of bytes, in the thousands). Whatever size, they are called *cell*.

#### 2.1.1.1 Read/Write coherence and atomicity

- *read/write coherence*: the result of the READ of a named cell is always the same as the most recent WRITE to that cell.

   Performance enhancements  
   Replicated storage

- *before-or-after atomicity*: the result of every READ or WRITE is as if that READ or WRITE occurred either completely before or completely after any other READ or WRITE.

   Concurrency  
   Remote storage  
   Cell size incommensurate with value size  
   Replicated storage

#### 2.1.1.2 memory latency

- It takes time for a READ or WRITE to complete, known as *latency* or *access time*.

- *Random access memory* is one for which the latency for memory cells chosen at random is approximately the same as the latency for cells chosen in the pattern best suited for that memory device.

- Large-block READ and WRITE operations are sometimes relabeled GET and PUT.

#### 2.1.1.3 Memory names and addresses

- Conseutive integers for mapping geometric coordinates as names are called *addresses*, amd they form the *address space* of the memory device.

- A memory system that accepts unconstrained names is called an *associative memory*. Assiciativity layer is abstraction of *location-addressed memory* (physical layer).

- *cache* is sometimes implemented as an associative memory, either in software or hardware.

#### 2.1.1.4 Exploiting the memory abstraction: RAID

- RAID is an acronym for Redundant Array of Independent (Inexpensive) Disks.

- A RAID system consists of a set of disk drives and a controller configured with an electrical and programming interface that is identical to the interface of a single disk drive.

   Improved performance, by reading or writing disks concurrently  
   Improved durability, by writing information on more than one disk

### 2.1.2 Interpreters

- Interpreters are the active elements of a computer system; they perform the actions that constitute computations.

 1. An *instruction reference*, which tells the interpreter where to find its next instruction

 2. A *repertoire*, which defines the set of actions the interpreter is prepared to perform when it retrieves an instruction from the location named by the instruction reference.

 3. An *environment reference*, which tells the interpreter where to find its environment, the current state on which the interpreter should perform the action of the current instruction.

- Using the environment reference to find the current environment, the interpreter retrieves from that environment the program instruction indicated in the instruction reference. Again using the environment reference, the interpreter performs the action directed by the program instruction.

- Certain events, called *interrupts*, may catch the attention of the interpreter, causing it, rather than the program, to supply the next instruction.

- Multiple interpreters are usually *asynchronous*, running on separate, uncoordinated clocks.

#### 2.1.2.1 Processors

- The processor's instruction reference is a *program counter*, stored in a fast memory register inside the processor.

- The repertoire of our general-purpose processor includes instructions for expressing computations such as adding two numbers `ADD`, subtracting one number from another `SUB`, comparing two numbers `CMP`, and changing the program counter to the address of another instruction `JMP`.

- `LOAD` = `READ` a value from a named memory cell into a register into a register of the processor.

- `STORE` = `WRITE` the value from a register into a named memory cell. These get two arguments, the name of a memory cell and the name of a processor register.

#### 2.1.2.2 Interpreter layers

- Interpreters are nearly always ofganized in layers.

- The lowest layer is usually a hardware engine that has a fairly primitive repertoire of instructionsm and successive layers provide an increasingly rich or specialized repertoire.

- A full- brown application system may involve four or five distinct layers of interpretation.

### 2.1.3 Communication links

- A communication link provides a way for information to move between physically separated components.

- `SEND(link_name, outgoing_message_buffer)`, `RECEIVE(link_name, incoming_message_buffer)`

- The lawest layer of a system has received a message, higher layers may acquire the message by calling a `RECEIVE` interface of the lower layer, or the lower layer may "upcall" to the higher layer, in which case the interface might be b etter characterized as `DELIVER(incoming_message)`.

- The *link_name* arguments of `SEND` and `RECEIVE` identify one of possibly several available communication links attached to the system.

- Communication links involve more than simple copying an array of bits from one memory to another memory over a wire using `READ` and `WRITE`.

- Many complications, such as unpredictable time to complete, threatening integrity of the data transfer, asynchronous operation, message not delivered.

- Three-layer model that organizes communication links into systems called *networks*.

## 2.2 Naming in computer systems

- Computer systems use names in many ways in their construction, configuration, and operation.

- The computer system manipulates *objects*.

- There are two ways to arrange for one object to use another as a component:

   create a copy of the component object and include the copy in the using object (use by *value*)  
   choose a name for the component object and include just that name in the using object (use by *reference*). The component object is said to *export* the name.

- When passing arguments to proceduresm use by value enhances modularity. But it does not easily permit two or more objects to share a component object whose value changes.

- One purpose of names is to allow use by reference and thus simplify the sharing of changeable objects.

- A second purpose is to allow a system designer to defer to a later time an important decision: to which object should this name refer.

- Decoupling one object from another by using a name as an intermediary is know as *indirection*.

- Deciding on the correspondence between a name and an object is an example of *binding*.

### 2.1.1 The naming model

- *Naming scheme* has three components: *name space* comprises an alphabet of symbols together with syntax rules that specify which names are acceptable. *name-mapping algorithm* associates some names of the name space with some values in a *universe of values*.

- A name-to-value mapping is an example of *binding*.

- The name-mapping algorithm *resolves* the name, discovering and returning the associated value.

- The name-mapping algorithm is usually controlled by an additional parameter, known as a *context*.

- value <- `RESOLVE(name, context)`

- status <- `BIND(name, value, context)`

- status <- `UNBIND(name, context)`

- list <- `ENUMERATE(context)`

- result <- `COMPARE(name1, name2)`

- In practice, one encounters three frequently used name-mapping algorithms:

   Table lookup  
   Recursive lookup  
   Multiple lookup

### 2.2.2 Default and explicit content references

- There are two ways to come up with a context with which to resolve the names found in an object: *default context reference*, supplied by the resolver, and *explicit context reference*, supplied by the object.

### 2.2.3 Path names, naming networks, and recursive name resolution

- In *recursive name resolution*, a path name can be thought of as a name that explicitly includes a reference to the context in which it should be resolved.

- Path names can also be thought of as identifying objects that are organized in what is called a *naming network*. In a naming network, contexts are treated as objects, and any context may contain a name-to-object binding for any other object, including another context.

- Multiple names for the same object are known as *synonyms* or *aliases*.

- The file system of a computer operating system is usually organized as a naming network, with directories acting as contexts.

- Many systems have many different cross-hierarchy links, called *symbolic link*, *soft link*, *alias*, and *shortcut*.

### 2.2.4 Multiple lookup: searching through layered contexts

- *The idea of *multiple lookup* is to abandon the notion of a single, default context and instead resolve the name by systematically trying several different contexts.

- Since a name may be bound in more than one context, multiple lookup can produce multiple resolutions, so some scheme is needed to decide which resolution to use. A common such scheme is called the *search path*, which is a specific list of contexts to be tried, in order. (like `$PATH`) Provides *user-dependent binding*.

- In a set of layered contexts, the *scope* of a name is the range og layers in which the name is bound to the same object.

- A name that is bound only in the outermost layer is known as a *global name*.

- A *path name* is a name that carries its own explicit context, and a *search path* is a context that consists of a list of contexts.

### 2.2.5 Comparing names

- result <- `COMPARE(name1, name2)` is for:

   Are the two names the same?  
   Are the two names bound to the same value?  
   If the value(s) are actually the indentifiers of storage containers, such as memory cells or disk sectors, are the contents of the storage containers the same?

- The second includes recursive search to the lower layer. The third is about understanding what it means to be the "same".

- In practice, systems and programming languages typically provide several `COMPARE` operations with different semantics.

### 2.2.6 Name discovery

- The *name discovery protocol* informs an object's prospective user of the name that the object exports: the exporter *advertises* the existence of the name, while the user *searches* for an appropriate advertisement.

- Any methods of name discovery may require first discovering some other name by any methods, but the recursion must terminate somewhere.

## 2.3 Organizing computer systems with names and layers

- The typical organization of a computer system has three layers. The bottom layer consists of hardware components, such as processors, memories, and communication links. The middle layer consists of a collection of software modules, called the *operating system*, that abstract these hardware resources into a convenient *application programing interface* (API). The top layer consists of software that implements application-specific functikons, such as a word processor or Web browser.

- The exact division of labor between the hardware layer and the software layers is an engineering trade-off and debate between hardware and software designers. In principle, every software module can be implemented in hardware.

- The operating system layer usually exhibits a phenomenon that we might call *layer bypass*, some features of the hardware layer pass through the OS layer.

### 2.3.1 A hardware layer: The bus

- In the hardware layer, the processor module interpret programs, the random access memory modules store both programs and data, and the input/output modules implement communication links to the world outside the computer.

- The various modules plug into the shared *bus*, which is a highly specialized communication link used to `SEND` messages to other modules.

- Bus design has common features:

   A set of wires comprising address, data, and control lines that connect to a *bus interface* on each module.  
   A set of rules, called the *bus abstractionn protocol*, for deciding which module may sen d or receive a message at any particular time.    
   A *broadcast link*, which means that every module attached to the bus hears every message. A field of message called the *bus address* identifies the intended recipient.

- A common bus design is known as *split-transaction*. When one module wants to communicate with another, the first module uses the bus arbitration protocol on the control wires to request exclusive use of the bus for a message.

- *Direct access memory*: when a processor `SEND`s a request to a disk controller to `READ`a block of data from the disk, it includesthe address of a buffer in memory as a field of the request message. Then, as data streams in from the disk, the disk controller `SEND`s it directly to the memory module, incrementing the memory address appropriately between `SEND`s.

- **The principle of least astonishment**

*People are part of the system. The design should match the user's experience, expectations, and mental models.*

### 2.3.2 A software layer: The file abstraction

- A file holds an array of bits or bytes, the number of which the application chooses. A file

   Is durable.  
   Has a name.

- A typical API for the file abstraction contains call to `OPEN` a file, to `READ` and `WRITE` parts of the file, and to `CLOSE` the file.

- The reason why the file API suports `OPEN` and `CLOSE` in addition to `READ` and `WRITE` is that the`OPEN` and `CLOSE` procedures mark the beginning and the end of a sequence of related `READ` and `WRITE` operations so that the file system knows which reads and writes belong together as a group.

- Most recent file systems use `OPEN` and `CLOSE` to mark the beginning and end of an *atomic* action.

   *before-or-after atomicity*: if one program has a file open and another program tries to open the same file, the file system can make the second program wait until the first one has closed the file.  
   *all-or-nothing atomicity*: if the file system crashes before the application closes the file, none of the writes will be in the file when the system comes back up.

## 2.5 Case study: UNIX file system layering and naming

- `UNIX` operating system was developed by Bell Telephone Laboratories for the Digial Equipment Corporation PDP line of minicomputers in the late 1960s and early 1970s. Today there are many flavors of `UNIX` family:

   GNU/Linux (Red Hat, Ubuntu)  
   Darwin (Mac OS X)

### 2.5.1 Application programming interface for the UNIX file system


| layer                    | purpose                                             |                        |
|--------------------------|-----------------------------------------------------|------------------------|
| Symbolic link layer      | Integrate multiple file systems with symbolic links | user-oriented          |
| Absolute path name layer | Provide a root for the naming hierarchies           | user-oriented          |
| Path name layer          | Organize files into naming hierarchies              | user-oriented          |
| File name layer          | Provide human-oriented names for files              | machine-user interface |
| Inode number layer       | Provide machine-oriented names for files            | machine-oriented       |
| File layer               | Organize blocks into files                          | machine-oriented       |
| Block layer              | Identify disk blocks                                | machine-oriented       |

### 2.5.2 The block layer

- At the bottom layer the UNIX file system names some physical device such as a magnetic disk, flash disk, or magnetic tape that can store data durably.

```
procedure BLOCK_NUMBER_TO_BLOCK(integer b) returns block
    return device[b]
```


- A *block* is the smallest allocation unit of disk space, and its size is a trade-off between several goals.

- *Name discovery*: The names of blocks are integers from a compact set, but the block layer must keep track of which blocks are in use and which are available for assignment.

| 0          | 1           | ...                    |             |            |     | n - 1      |
|------------|-------------|------------------------|-------------|------------|-----|------------|
| Boot block | Super block | Bitmap for free blocks | Inode table | File block | ... | File block |

### 2.5.3 The file layer

- To record which blocks belong to each file (a linear array of bytes of arbitrary length), the UNIX file system creates an index node, or *inode* for short, as a container for metadata about the file.

```
structure inode
    integer block_numbers[N]    // number of blocks that constitute the file
    integer size                // file size in bytes
```

- A simplified name-mapping algorithm for resolving the name of a block in a file is:

```
procedure INDEX_TO_BLOCK_NUMBER(inode instance i, integer index) returns integer
    return i.block_numbers[index]
```

### 2.5.4 The inode number layer

- Instead of passing inodes themselves around, it would be more convenient to name them and pass their names around.

Cont from pp.96 - pp.112

## Exercise 2

# 3. The design of naming schemes

## 3.1 Considerations in the design of naming schemes

### 3.1.1 Modular sharing

- *Modular sharing* means that one can use a shared module by name without knowing the names of the modules it uses.

- Keep track of contexts and using indirect references (by using file system directories as contexts) is commonplace, but it is a bit ad hoc.

- Some programming languages implement *closure*, which connects each procedure definition with the naming context in which it was defined.

### 3.1.2 Metadata and name overloading

- *Metadata*, information that is useful to know about an object but that cannit be found inside the object itself.

- It is common to discover that file names are *overloaded* with metadata that has little or nothing to do with the use of the name as a reference.

- A *fragile name* appears when it is necessary to change the name of a file that moves to a new physical location, even though the identity and content of the file have not changed.

- A name is said to be *opaque* to a module if the name has no overloading that the module knows how to interpret.

### 3.1.3 Addresses: Names that locate objects

- An *address is the name of a physical location or of a virtual location that maps to a physical location: register numbers, physical and virtual memory addresses, processor numbers, disk sector numbers, removable media volume numbers, ...

- Addresses can be used as 1. an identifier and 2. a locator (if you read the address you can assume its location directly)

- *decouple modules with indirection* to hide address.

### 3.1.4 Generating unique names

- Name *collision*: accidentally use the same name twice

- Hash, *Secure Hash Algorithm (SHA)*: generates for any size of input, an output that is 160 bits length.

- Ethernet, 48-bit *Media Access Control (MAC)* address, set inti the hardware by the manufacturer.

- MAC address is properly viewed only as the unique name of a specific hardware component, not of the system in which it is embedded.

### 3.1.5 Intended audience and User-friendly names

- Tension between user-friendly name and unique name.

- Case-sensitive vs case-preserving

### 3.1.6 Relative lifetimes of names, values, and bindings

- A naming scheme, a name, the binding of that name to a value, and the value to which the name is bound can all have different lifetimes.

- When a name outlives its binding, any user of that name that still tries to resolve it will encounter a *dangling reference*, which is a use of a previously bound name that resolves either to a not-found result or to an irrelevant value.

- When an object outlives every binding of a name to it, that object becomes *orphan* or a *lost object*.

-  A system that regularly loses track of objects is said to have a *storage leak*.

### 3.1.7 Looking back and ahead: Names are a basic system component


## 3.2 Case study: The Uniform Resource Locator (URL)

- The World Wide Web is a naming network with no unique root, many different mames for the same object, and complex comtext references.

### 3.2.1 Surfing as a referential experience; name discovery

- The Web has two layers of naming: an upper layer that is user-friendly, and a lower layer, which is also based on character strings but mechanical.

- At the upper layers, users find web page as *hyperlinks*. The former is browser's view and the latter is user's view (HyperText Markup Language):

```
<a href="http://web.pedantic.edu/Alice/www/home.html">Alice's page</a>
```

- Between the quotation is *Uniform Resource Locator, URL*, an exampla of lower naming layer.

### 3.2.2 INterpretation of the URL

- The name-mapping algorithm for a URL works in several steps, as follows.

 1. The browser extracts the part before the colon, considers it to be the name of a network protocol to use, and resolves that name to a protocol handler using a table-lookup context stored in the browser. In the case of `http`:

 2. The browser takes the part between the // and the following / (web.pedantic.edu) and asks the Internet Domain Name System (DNS) to resolve it. The value that DNS returns is an Internet address.

 3. The browser opens a connection to the server at that address, and sends the remaining part of the URL (/Alice/www/home.html) to the server.

 4. The server looks for a file in its file system that has that path name.

 5. If the name resolution of step 4 is successful, the server sends the file with that path name to the client. The client transforms the file into a pahe suitable for display.

### 3.2.2 URL case sensitivity

- Some part of a URL is case sensitive and other parts are not. The host name part, interpreted by the Internet Domain Name Service, is case-insensitive. The protocol depends on the browser. After the host name, case-sensitivity depends on the file system of the server.

### 3.2.4 Wrong context references for a partial URL

- When the local file system name space allows synonyms for directory names, the mapping of local file system name space to the URL name space is not unique. Thus, several different URLs can have different path names for the same object.

- Trouble can arise when the object that has multiple URLs is a directory whose name is used as a context reference (relative path).

## 3.3 War stories: pathologies in the use of names

### 3.3.1 A name collision eliminates smiling faces

- smiley.jpg of smile faces collides Smiley

### 3.3.2 Fragile names from overloading, and a market solution

### 3.3.3 More fragile names from overloading, with market disruption

### 3.3.4 Case-sensitivity in user-friendly names

### 3.3.5 Running out of telephone numbers

## Exercise 3

- 3.1a separately

- 3.1b who created, who owns

- 3.1c 

- 3.2 C

- 3.3a /home/bob

- 3.3b 

- 3.4

- 3.5

# 4. Enforcing modularity with clients and services

- *enforced modularity* helps limit the propagation of errors from one module to another.

- One example: client <- (message) -> service

## 4.1 Client/service organization

- Implementation errors can propagate from caller to callee and vice versa.

- *Soft* modularity limits interactions of correctly implemented modules to their specified interfaces, but implementation errors can cause interactions that go outside the specified interfaces.


### 4.1.1 From soft modularity to enforced modularity

- Below is soft modularity:

```
procedure MEASURE(func)
  start <- GET_TIME(SECONDS)
  func()
  end <- GET_TIME(SECONDS)
  return end - start

procedure GET_TIME(units)
  time <- CLOCK
  time <- CONVERT_TO_UNITS(time, units)
  return time
```

??? >> pp152

- Need for *enforced modularity*

### 4.1.2 Client/service organization

- One good way to enforce modularity is to limit the interactions among modules to explicit messages.



pp155


