---
title: "Noexec is driving me nuts"
date: 2012-12-10
forum: General Help
---

### Post by Emris Echo on 2012-12-10
Please keep in mind that i am  noob to scripting in general when replying, i just today installed ubuntu and started screwing around with very basic code, compiled into a 
executable file fine using chmod +X but when i try to actually execute it i am denied permission :x (which is always infuriating as my computer is now telling ME what i can and cannot do......)someone please tell me how to change my mount so that it is not nonexec please again keep in mind i am as green as it gets
thnx in advance

---

### Post by drmrgd on 2012-12-10
A few things:

1.  Where is this file located on your system?  The noexec bit usually set on devices other than your primary device.  If it was set on your OS or /home partitions (for example), I think you'd be having a lot more problems.  This is likely also something you would have set yourself when setting up the mount point, in which case, just removing that option from your fstab entry would suffice.  I don't think this is it, though.

2.  To make a file executable, the command option you need is lower-case 'x', not upper-case:

```
chmod +x <file>
```

Take note that everything is case-sensitive in Linux, and 'X' is not at all the same as 'x'.

3.  What kind of program or script is it, and how exactly are you trying to execute it?  If it is a bash script, then make sure you have a shebang line at the start of the script:

```
#!/bin/bash
```

Then after making the file executable, you can run it by typing:

```
./<script_name>
```

Alternatively, you can explicitly tell the script to run with the correct interpretter:

```
bash <script_name>
```

---

