---
title: "IcedTea 2.6.2 configuration:  “llvm-config: error: components given, but unused”"
date: 2015-10-26
forum: General Help
---

### Post by Tab_Neib on 2015-10-26
Hi everyone 
I'm configuring IcedTea 2.6.2 to build OpenJDK with ZeroShark. In order  to make IcedTea I have installed the following dependency packages:

```
sudo apt-get install zip gawk xsltproc libjpeg8-dev libgif-dev libpng12-dev liblcms2-dev libgtk2.0-dev cups libcups2-dev libc6-dev libattr1-dev libalsa-ocaml-dev libsctp-dev libXtst-dev libffi-dev 
sudo apt-get install llvm-3.6-dev libllvm-3.5-ocaml-dev libllvm3.5-dbg llvm-3.5-tools liblldb-3.5-dev
```

Configuring IcedTea before making:

```
./configure --enable-zero --enable-shark --with-rhino=no 
```

But I'm stuck on this step. Below is (part of) the output of the configuration:

```
checking for llvm-config... /usr/local/bin/llvm-config
llvm-config: error: components given, but unused

usage: llvm-config <OPTION>... [<COMPONENT>...]

Get various configuration information needed to compile programs which use
LLVM.  Typically called from 'configure' scripts.  Examples:
  llvm-config --cxxflags
  llvm-config --ldflags
  llvm-config --libs engine bcreader scalaropts

Options:
  --version         Print LLVM version.
  --prefix          Print the installation prefix.
  --src-root        Print the source root LLVM was built from.
  --obj-root        Print the object root used to build LLVM.
  --bindir          Directory containing LLVM executables.
  --includedir      Directory containing LLVM headers.
  --libdir          Directory containing LLVM libraries.
  --cppflags        C preprocessor flags for files that include LLVM headers.
  --cflags          C compiler flags for files that include LLVM headers.
  --cxxflags        C++ compiler flags for files that include LLVM headers.
  --ldflags         Print Linker flags.
  --system-libs     System Libraries needed to link against LLVM components.
  --libs            Libraries needed to link against LLVM components.
  --libnames        Bare library names for in-tree builds.
  --libfiles        Fully qualified library filenames for makefile depends.
  --components      List of all possible components.
  --targets-built   List of all targets currently built.
  --host-target     Target triple used to configure LLVM.
  --build-mode      Print build mode of LLVM tree (e.g. Debug or Release).
  --assertion-mode  Print assertion mode of LLVM tree (ON or OFF).
Typical components:
  all               All LLVM libraries (default).
  engine            Either a native JIT or a bitcode interpreter.
llvm-config: error: components given, but unused

usage: llvm-config <OPTION>... [<COMPONENT>...]
```

Get various configuration information needed to compile programs which use
```
LLVM.  Typically called from 'configure' scripts.  Examples:
  llvm-config --cxxflags
  llvm-config --ldflags
  llvm-config --libs engine bcreader scalaropts

Options:
  --version         Print LLVM version.
  --prefix          Print the installation prefix.
  --src-root        Print the source root LLVM was built from.
  --obj-root        Print the object root used to build LLVM.
  --bindir          Directory containing LLVM executables.
  --includedir      Directory containing LLVM headers.
  --libdir          Directory containing LLVM libraries.
  --cppflags        C preprocessor flags for files that include LLVM headers.
  --cflags          C compiler flags for files that include LLVM headers.
  --cxxflags        C++ compiler flags for files that include LLVM headers.
  --ldflags         Print Linker flags.
  --system-libs     System Libraries needed to link against LLVM components.
  --libs            Libraries needed to link against LLVM components.
  --libnames        Bare library names for in-tree builds.
  --libfiles        Fully qualified library filenames for makefile depends.
  --components      List of all possible components.
  --targets-built   List of all targets currently built.
  --host-target     Target triple used to configure LLVM.
  --build-mode      Print build mode of LLVM tree (e.g. Debug or Release).
  --assertion-mode  Print assertion mode of LLVM tree (ON or OFF).
Typical components:
  all               All LLVM libraries (default).
  engine            Either a native JIT or a bitcode interpreter.
checking for LLVMGetNextInstruction in -lLLVM-3.5.0... yes
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating hotspot.map
config.status: creating fsg.sh
config.status: creating nss.cfg
config.status: creating javac
config.status: creating javap
config.status: creating javah
config.status: creating tz.properties
config.status: creating pax-mark-vm
config.status: creating remove-intree-libraries.sh
config.status: creating tapset/hotspot.stp
config.status: creating tapset/hotspot_jni.stp
config.status: creating tapset/jstack.stp
config.status: creating tapset/hotspot_gc.stp
config.status: executing depfiles commands
```

I'm using X86_64 ubuntu 14.04 LTS. I have tried different versions of LLVM but the same error still occurs :(
Any help would be greatly appreciated. Thank you!

---

### Post by Tab_Neib on 2015-10-26
I've just realized that this post is in misplaced. Could anyone move it to the right subforum? Many thanks :)

---

### Post by slickymaster on 2015-10-26
*Moved to the ***General Help*** sub-forum*

---

