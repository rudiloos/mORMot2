# Synopse *mORMot 2* Framework

*An Open Source Client-Server ORM/SOA/MVC framework in modern Object Pascal*

![Happy mORMot](doc/happymormot.png)

(c) 2008-2023 Synopse Informatique - Arnaud Bouchez

https://synopse.info  - http://mORMot.net

Thanks to all [Contributors](CONTRIBUTORS.md)!

**NOTICE: This version 2 replaces [*mORMot 1.18*](https://github.com/synopse/mORMot) which is now in maintainance-only mode. Consider using *mORMot 2* for any new or maintainable project.**

## Resources

You can find more about *mORMot 2* in:
- its [Official Documentation](https://synopse.info/files/doc/mORMot2.html) (work in progress);
- the [Synopse Forum](https://synopse.info/forum/viewforum.php?id=24);
- the [Source Code `src` sub-folder](src);
- the [Synopse Blog](https://blog.synopse.info);
- the [Old mORMot 1 Documentation](https://synopse.info/files/html/Synopse%20mORMot%20Framework%20SAD%201.18.html) which still mostly apply to the new version - especially the design/conceptual parts.

If you find it worth using, please consider [sponsoring mORMot 2 dev](https://github.com/sponsors/synopse) if you can - and even better through [sharing your own commits](https://github.com/synopse/mORMot2/pulls). :-)

## Presentation

### mORMot What?

Synopse *mORMot 2* is an Open Source Client-Server ORM SOA MVC framework for Delphi 7 up to Delphi 11 Alexandria and FPC 3.2/trunk, targeting Windows/Linux/BSD/MacOS for servers, and any platform for clients (including mobile or AJAX).

![mORMot map](doc/IamLost.png)

The main features of *mORMot* are therefore:

 - An optimized cross-compiler and cross-platform JSON/UTF-8 and RTTI kernel;
 - Direct SQL and NoSQL database access (e.g. SQLite3, PostgreSQL, Oracle, MSSQL, OleDB, ODBC, MongoDB);
 - ORM/ODM: objects persistence on almost any database (SQL or NoSQL);
 - SOA: organize your business logic into REST services defined as `interface`;
 - Convention-over-configuration REST/JSON router, locally or over HTTP/HTTPS/WebSockets;
 - Clients: consume your data or services from any platform, via ORM/SOA APIs;
 - Web MVC: publish your ORM/SOA process as responsive Web Applications;
 - A lot of other reusable bricks (e.g. Unicode, cryptography, network, threads, dictionaries, logging, binary serialization, variants, generics, cross-platform...).

Emphasizing speed and versatility, *mORMot* leverages the advantages of modern object pascal native code and easy-to-deploy solutions, reducing deployment cost and increasing ROI. It can be used:

 - to add basic ORM or Client-Server features to simple applications for hobbyists,
 - or let experienced users develop scalable service-based (DDD) projects for their customers, 
 - or leverage FPC cross-platform abilities with an existing Delphi codebase, to embrace the next decades,
 - have fun and see modern object pascal challenge the latest languages or frameworks.

### Sub-Folders

The *mORMOt 2* repository content is organized into the following sub-folders:

- [`src`](src) is the main source code folder, where you should find the actual framework;
- [`packages`](packages) contains IDE packages and tools to setup your dev environment;
- [`static`](static) contains raw library `.o`/`.obj` files needed for FPC and Delphi static linking;
- [`test`](test) defines the regression tests of all framework features;
- [`res`](res) to compile some resources used within `src` - e.g. the `static` third-party binaries;
- [`doc`](doc) holds the documentation of the framework;
- [`ex`](ex) contains various samples.

Feel free to explore the source, and the inlined documentation.

### MPL/GPL/LGPL Three-License

The framework is licensed under a disjunctive three-license giving you the choice of one of the three following sets of free software/open source licensing terms:
- Mozilla Public License, version 1.1 or later;
- GNU General Public License, version 2.0 or later;
- GNU Lesser General Public License, version 2.1 or later.

This allows the use of our code in as wide a variety of software projects as possible, while still maintaining copy-left on code we wrote.
See [the full licensing terms](LICENCE.md).

## Quick Start

### Compiler targets

The framework source code:
- Tries to stay compatible with FPC stable and Delphi 7 and up;
- Is currently validated against FPC 3.2.3 (fixes-3_2) and Lazarus 2.2.5 (fixes_2_2), Delphi 7, 2007, 2009, 2010, XE4, XE7, XE8, 10.4 and 11.1.

Please submit pull requests for non-validated versions.

### Installation

1. Get the source, Luke!

1.1. Clone the https://github.com/synopse/mORMot2 repository to get the source code, and download latest https://synopse.info/files/mormot2static.7z 

or

1.2. Download a release from https://github.com/synopse/mORMot2/releases with its associated `mormot2static.7z` file.

2. Extract the `mormot2static.7z` content to the `/static` sub-folder of your mORMot 2 repository.

3. Setup your favorite IDE: 

3.1. On Lazarus, just open and compile the [`/packages/lazarus/mormot2.lpk`](packages/lazarus/mormot2.lpk) package - and [`mormot2ui.lpk`](packages/lazarus/mormot2ui.lpk) if needed.

3.2. On Delphi: 

3.2.1. Create a new environment variable `mormot2` with full path to the *mORMot 2* `src` sub-folder (*Tools - Options - IDE - Environment Variables*), e.g. `c:\github\mORMot2\src` or `d:\mormot2\src`; 

3.2.2. Add the following string to your IDE library paths (for all target platforms, i.e. Win32 and Win64):
   `$(mormot2);$(mormot2)\core;$(mormot2)\lib;$(mormot2)\crypt;$(mormot2)\net;$(mormot2)\db;$(mormot2)\rest;$(mormot2)\orm;$(mormot2)\soa;$(mormot2)\app;$(mormot2)\script;$(mormot2)\ui`

4. Discover and enjoy:

4.1. Open and compile [`test/mormot2tests.dpr`](test/mormot2tests.dpr) in the IDE, and run the regression tests on your machine.

4.2. Browse the [examples folder](/ex) (work in progress).

4.3. Start from an example, and follow the [documentation](https://synopse.info/files/doc/mORMot2.html).


### Contribute

Feel free to contribute by posting enhancements and patches to this quickly evolving project.
  
Enjoy!

## Coming From Version 2

### Why Rewrite a Working Solution?

The *mORMot* framework stayed in revision 1.18 for years, and is was time for a full refactoring.

The main refactoring points tried to better follow SOLID principles:
 - Switch to a more rigorous versioning policy, with regular releases;
 - Split main big units (`SynCommons.pas`, `mORMot.pas`) into smaller scope-refined units;
 - OS- or compiler- specific code separated to ease evolution;
 - Rename confusing types, e.g. `TSQLRecord` into `TOrm`, `TSQLRest` into `TRest`...;
 - Favor composition over inheritance, e.g. `TRest` class split into proper REST/ORM/SOA classes - and folders;
 - Circumvent compiler internal errors on Delphi, e.g. changed untyped const/var changed into pointers, or reduced the units size;
 - Full rewrite of the whole RTTI, JSON and REST cores, for better efficiency and maintainability;
 - Optimization of the framework `asm` kernel, using AVX2 if available;
 - New features like *OpenSSL*, *libdeflate* or *QuickJS* support;
 - New asynchronous HTTP and WebSockets servers, with optional HTTPS/TLS support via Let's Encrypt;
 - Introduce modern syntax like generics or enumerators - but optional for compatibility.

We therefore created a whole new project and repository, since switching to version 2 induced some backward uncompatible changes. New unit names were used, to avoid unexpected collision issues during migration, or if 1.18 is to remain installed for a compatibility project.

### Upgrade In Practice

Quick Steps when upgrading from a previous 1.18 revision:

1) Note all units where split and renamed, and some breaking changes introduced for enhanced features, therefore a direct update is not possible - nor wanted

2) Switch to a new folder, e.g. #\lib2 instead of #\lib

3) Download latest 2.# revision files as stated just above
  
4) Change your references to *mORMot* units:
 - All unit names changed, to avoid collision between versions;
 - Look [at the samples](ex) to see the main useful units.
 
5) Consult the documentation about breaking changes from 1.18, mainly:
 - Units refactoring (see point 4 above);
 - Types renamed in `PUREMORMOT2` mode;
 - Delphi 5-6 and Kylix compatibility removed;
 - BigTable, LVCL, RTTI-UI deprecated.
 