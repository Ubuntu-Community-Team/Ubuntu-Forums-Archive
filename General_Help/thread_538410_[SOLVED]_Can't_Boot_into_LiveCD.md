---
title: "[SOLVED] Can't Boot into LiveCD"
date: 2007-08-30
forum: General Help
---

### Post by Banny706 on 2007-08-30
Hi Folks,

Been using Ubuntu on older computer for almost a year.  I bought a new computer this summer and only now getting to install Ubuntu on it.  I decided to try the Tribe 5 release of Gutsy to check out the new features.  Figured why not since I still have my trusty Fiesty Install CD's to fall back on.  Well... ran into problem.

I load up as normal and get the boot menu for LiveCD and of course press start.  The Ubuntu splash screen comes up with the pretty little orange bar bouncing back and forth inside the progress bar and then the problem starts.

[COLOR="Red"](I think it is a computer problem, because this also happens with Kubuntu Gutsy Tribe 5 Live CD as well as my trusty Fiesty LiveCD)[/COLOR]

Where was I?  Oh yes.  Problem starts here when Ubuntu splash disappears without completion of the progress bar and black screen gets displayed with this:

[COLOR="Blue"]BusyBox v 1.1.3 (Debian 1:1.1.3-5ubuntu4) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off.
(initramfs) _  (blinking cursor)[/COLOR]

I have enough linux knowledge to know that 'initramfs' means initialize RAM file system but not enough knowledge to know what the heck to do from here.  Typing 'help' leaves me scratching my head too.

Somebody out there must have run into this problem and I hope for some help.  Never had this problem on my old computer.  Help please I'm stuck closed-source until I can get this fixed.  The similar posts on this subject are beyond my scope of knowledge.

---

### Post by kesman on 2007-08-30
There should be an option in the boot menu called alternate boot options or something like that. Trying that allows you to edit the boot parameters of the kernel. Remove the words quiet and splash from the line and you'll be able to follow the whole booting process and maybe locate a more accurate reason for your problem.
Hope this helps, I don't know anything about the errormessage itself :F

---

### Post by merlinus on 2007-08-30
Press F6 at the opening menu and then you can edit the boot line as suggested.

-merlin

---

### Post by Banny706 on 2007-08-30
Well I tried to boot into the LiveCD with the quiet and splash parameters gone and the error message was again displayed.  The scrolling messages never gave any indication as to any boot problems.  It just stopped then the error message was displayed.  I even tried to boot using 6.10 and 6.06.  These never gave me the error message I mentioned before, they while booting just froze up after about 90 seconds.  According to my BIOS, I have a SATA HD.  I saw that this may the problem.  I guess until the Ubuntu coders fix this problem, I am stuck with Windows as I have no intention of purchasing more hardware to conform to Linux kernel.  Its not Ubuntu itself as I even tried to use SimplyMepis and Freespire.

---

### Post by Banny706 on 2007-08-30
Oh and thanks for the help.

---

### Post by pxwpxw on 2007-08-30
> **Banny706 said:**
> Oh and thanks for the help.

There are many things that can result in that error message. if you do a forum search for titles with " access tty job control " that may find something more you can try. sata is not necessarily a problem, but other stuff may just need configuring in the install options.

---

### Post by kesman on 2007-08-31
My compaq evo n800c laptop with sata drive worked flawlessly with latest feisty liveCD :F

---

### Post by kesman on 2007-08-31
[http://ubuntuforums.org/showpost.php?p=3118704&postcount=8](http://ubuntuforums.org/showpost.php?p=3118704&postcount=8)

There's discussion about this with more replies.

---

### Post by Banny706 on 2007-08-31
Thanks kesman, I'll let you know how it turns out

---

### Post by Banny706 on 2007-08-31
Well I tried merlinus' tut and it didn't work.  In Gutsy Tribe 5, the modprobe piix was a failure so I tried Feisty.  modprobe piix seemed to load and when I exited to boot into cd, I got that familiar error message again.  Tried for all versions back as far as Dapper and they didn't work either.  I'll continue to wait until the kernel is compatible with SATA.  It was a shot in the dark.  Maybe better luck next time.

---

### Post by Banny706 on 2007-09-28
Was able to install Ubuntu Feisty using Wubi to Windows and then using LVPM to install the Loop Mounted partition to a permanent ext3 partition.  Used Partition Magic 8 in Windows to set up the ext3 and swap partition.  Wish I could use the LiveCD....it is so much faster and less running around.

---

### Post by Banny706 on 2007-11-20
My boot problems are now over with the release of 7.10.  I installed 7.10 Beta using the Alternate Install CD and upgraded a week later when Gutsy was released.  Figured I would give the LiveCD another go to see if it works.  Booted 'er up last night without any problems whatsoever.  :):):):):):):) I even did a fresh install to celebrate.  This thread can more than likely be closed.

---

