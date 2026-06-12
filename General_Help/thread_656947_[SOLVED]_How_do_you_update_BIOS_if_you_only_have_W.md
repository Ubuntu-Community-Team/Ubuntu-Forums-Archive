---
title: "[SOLVED] How do you update BIOS if you only have Windows executables?"
date: 2008-01-03
forum: General Help
---

### Post by omglol741 on 2008-01-03
I don't know how or if there is a way to run the executables. If there is, that would help. Anyway, the BIOS update is downloaded from [here]("http://downloadcenter.intel.com/Filter_Results.aspx?strTypes=all&ProductID=952&OSFullname=OS+Independent&lang=eng&strOSs=38").

The instructions say to put the exe in a temporary folder and run it to extract the files. Then insert a floppy and run the .bat file.

Is there a way to do that in Ubuntu? Because I get an error when I double click the exe now. 
If not, could someone email me the floppy disk image at [email]prickly.pirate@yahoo.com[/email]? That would help me out a lot.

---

### Post by jinx099 on 2008-01-03
You need to format a flash drive a certain way, then you can boot it to a DOS shell, then you just run the executable.  This is what I do and it works well.

---

### Post by Rhubarb on 2008-01-03
This can be done using dosbox, freedos, and a blank cd.
I'll post soon exactly how to do it.

---

### Post by omglol741 on 2008-01-03
lol I just tried running it from the floppy. I booted with an ME boot disk and switched the floppies when I got to the command line. It extracted and stuff correctly, but then it tried to write an image from itself onto itself. It said it was full lol.:) 

This would be easy if I could run DOS from Ubuntu. Is that what those programs do?

---

### Post by kpkeerthi on 2008-01-03
> **Rhubarb said:**
> This can be done using dosbox, freedos, and a blank cd.
I'll post soon exactly how to do it.

That would be really helpful for those that are running only linux. I would watch this space for updates. Or may be you can post the intructions in **Tutorials & Tips** Section.

---

### Post by Rhubarb on 2008-01-03
Okay, this should work fine for you:-

Install dosbox and mkisofs from synaptic package manager.
```
sudo aptitude install dosbox mkisofs
```
Now extract all the files within BTAP06IB.EXE
```
dosbox BTAP06IB.EXE
```
This creates lots of files, copy these files into a new blank folder, then extract more files:
```
dosbox SW.EXE
```
The new files created are the important ones you need to put onto a freedos cd (made from a freedos floppy boot disk image)
Follow [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789) which tells you how to do this.

Then hey presto!  You've got a nice 1.8MB bootable freeDOS image you can boot from and will automatically upgrade your BIOS with.

Edit:  If this is not helpful or specific enough, let me know and I'll make up a much nicer step by step guide how to do this.

---

### Post by omglol741 on 2008-01-03
hmmmmmmm. I don't see dosbox in the package manager (live cd if that matters). That looks like a lot of reading and stuff (the forum link). lol Maybe I'll try that tomorrow if I can't get it working right now. But I googled freedos when you mentioned it first, and I think I have it installed. In the readme, I get as far as when it tells me to ```
After you get the install right, you can execute DOSEMU with

  $ cd ~mydos/dosemu             # (your CWD _must_ be here)
  $ ./dosemu
```
But I get
```
ubuntu@ubuntu:~$ cd mydos/dosemu
ubuntu@ubuntu:~/mydos/dosemu$ ./dosemu
ERROR: X support not compiled in or not found:
ERROR: /usr/local/lib/dosemu/libplugin_X.so: cannot open shared object file: No such file or directory
ERROR: term support not compiled in or not found:
ERROR: /usr/local/lib/dosemu/libplugin_term.so: cannot open shared object file: No such file or directory
ERROR: Terminal (S-Lang library) support not compiled in.
Install slang-devel and recompile, use xdosemu or console dosemu (needs root) instead.
```
If I got that working, I could just run the executable and it would write the bootable BIOS update to the floppy, right?

---

### Post by Rhubarb on 2008-01-03
omglol741:  check your email ;)

You don't need to run it off a live ubuntu cd to do this (it can still be done - but once you've made up your freedos live cd with the new BIOS firmware on it, you will have problems burning it to a CD unless you have two optical drives (one of which being capable of writing to CDs))

The method I described does not require dosemu at all.

All that you are doing, is modifying an existing freedos floppy disk image, adding in all the files required to update you BIOS, then converting the floppy disk image into a CD image (because the image will not fit on a floppy disk).
From there you can burn this image to a CD, boot from it, then it will automatically update your BIOS.

---

### Post by omglol741 on 2008-01-03
I don't see any new emails. Anyway, that link seems easy enough actually. I just need to extract the exe like it says then I think it will work. Wow I'm starting to feel weird from being tired. I don't know if I should do this when I'm tired lol.

edit: OK I'm pretty sure I have it ready now. Thanks a lot Rhubarb.

---

### Post by TechZilla on 2008-01-03
create boot cd with floppy emulation

---

### Post by Rhubarb on 2008-01-03
It's best not to do anything big when tired.
Remember you can really brick your system if you do it wrong.

Edit:  I've taken down the link I created for you, just in case someone tries to update their intel BIOS for a different motherboard.  (which could cause problems).

---

### Post by omglol741 on 2008-01-03
WOOOOOOO it worked. It either works or it doesn't, right? Because I got an error message on Ubuntu. I think it's just settings stuff though. Anyway, thanks again Rhubarb.

And it fit on the floppy, so all I really needed to do was load that premade bootable floppy, extract the update, and copy the .bio, the .bat, and Iflash.exe onto the floppy. I'm going to bed now. ):P

---

