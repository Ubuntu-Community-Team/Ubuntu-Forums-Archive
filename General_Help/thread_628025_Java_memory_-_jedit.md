---
title: "Java memory - jedit"
date: 2007-11-30
forum: General Help
---

### Post by OBI_Ron on 2007-11-30
Hello Everyone,

I am using Ubuntu 7.1 gutsy and jEdit 4.3pre11

I have installed jedit, normally, my favorite editor.  However, I recently tried to open a large file (90mb), and got an out of memory error.  From the help documentation, I found I need to increase the memory with the following:

-Xmx512x

Can anyone explain exactly (like your talking to a 2 year old) how to do this?  I searched the jedit forums, which are slower than molasses in January, and found reference to modifying the Info.plist file in the Contents directory.  That directory and /or file do not exist.

I tried adding the -Xmx512x to the command line when starting jedit - nothing.

I am really frustrated at this point.  Any help would be greatly appreciated.

Thanks in advance!!

---

### Post by kjkrum on 2007-12-01
jEdit is actually launched from a shell script.  Edit it and change the value of JAVA_HEAP_SIZE:

$ vi `which jedit`

---

### Post by OBI_Ron on 2007-12-01
kjkrum,

Got it - edited as root - all is fine.  Thanks for the help!!

---

### Post by SyL on 2007-12-01
the parameters xmx and xms are used for set the heap size of your JVM.

---

