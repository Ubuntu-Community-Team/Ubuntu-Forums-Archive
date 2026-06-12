---
title: "opening/saving files -&gt; crash (any application)"
date: 2008-05-23
forum: General Help
---

### Post by d.avid on 2008-05-23
Hello!

I'm running Ubuntu for a couple of months now and I'm not too familiar with the material.
I installed Hardy Heron some weeks ago - with fatal consequences:

I cannot open or save files with any application. 

Exceptions: - starting an application by double clicking the file I want to work with (or via console (>gedit file))
- everything works perfectly fine when I start the application with "sudo"
- I can play music and attach files to emails etc

Whenever I try to open a file via the button in the menu (eg openoffice, gimp, evince, gedit), to extract files with the file-roller or to use "save as" the application crashes with a segmentation fault.
I checked the memory, no errors. 
I reinstalled ubuntu with no effect. 
The install cd works, I didn't have any problems installing hardy on another system with the same cd.
Further, the problem doesn't occur when I boot from cd.


Someone told me to try
```

sudo chown $USER:$USER $HOME -R
chmod -R u+rwX $HOME
chmod 600 $HOME/.dmrc
```

chown produces an error message: "Cannot access „/home/david/.gvfs“: Permission denied" (or something like that, it's German)
I was told to enter the line in rescue mode.

No success.

That's more or less everything I know. I didn't format my home partition yet, i think that would be my next step (which i'm trying to evade for quite a while)..
Maybe one of you guys has a better idea?

Best regards
david

---

### Post by cmnorton on 2008-05-23
Using the live CD or an OS like Knoppix, look through your log files (/var/log). Did you install 8.04 or upgrade to it? If  you upgraded, a complete install might be needed. I am waiting for the 3-month point release and will try again,after upgrading and then installing fresh. I am back on 7.10.

---

### Post by d.avid on 2008-05-23
I freshly installed 8.04, then.

Thanks for your advice, the log said:
```
May 23 19:25:25 DeepThought kernel: [   87.651453] gedit[5924]: segfault at 00000003 eip b73c3bc7 esp bf8e1b78 error 4
May 23 19:25:35 DeepThought kernel: [   97.750491] gedit[5949]: segfault at 00000003 eip b742bbc7 esp bfa904e8 error 4
```

Don't know what to do with this, though.


The file system check didn't report any errors, by the way.

---

### Post by lrasm274 on 2008-05-24
Thanks for the info, wish I would have looked into this BEFORE I updated :o)  I'm having the same issues w/ apps crashing now.  I've seen some people suggest using gdb to run gedit and see where the crash occurs.  I'm new to that, but I'll post back to this thread if I figure out what else might fix it (outside of a fresh install).

---

### Post by d.avid on 2008-05-25
Interesting.

> **lrasm274 said:**
> I'm new to that, but I'll post back to this thread if I figure out what else might fix it (outside of a fresh install).

Don't count on it. As I said, I didn't do the upgrade, I installed Hardy from the cd. Twice. The problems appeared after the first install and the second didn't change anything. 

Grüße ;)

---

### Post by d.avid on 2008-05-25
Ok, I ran gedit with gdb.
This happens when I try to open a file:

```

..
(no debugging symbols found)
[New Thread 0xb64e9b90 (LWP 9943)]
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb6c03720 (LWP 9938)]
0xb73ecbc7 in strchr () from /lib/tls/i686/cmov/libc.so.6

```

uhm. yeah. :/

(No problems saving or opening files with nano btw, it's the "open/save as" dialogue in the applications with GUI..)

---

### Post by omababy on 2008-05-25
If this is happening with all different types of applications I'm guessing its a dynamic library thats causing the problem, as per gdb output. Cause maybe version or pkg conflicts? I dunno.

---

### Post by d.avid on 2008-05-25
Seems unlikely, the problem occurred after I reinstalled version 8.04 without me having downloaded any packages. But what could be the cause if it's not the software? Hard drive and memory are fine according to the checks. 
Well, I think I'll reinstall Hardy again and format my home drive when I have some time. Random idea #13.


edit: Ok, it worked, don't ask me why. Thanks for the help.

---

