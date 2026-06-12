---
title: "HELP: Problem starting windows after attempting Ubuntu install"
date: 2007-03-01
forum: General Help
---

### Post by RUGUNIT on 2007-03-01
I started to install ubuntu on my second hard drive, but i messed up the partitioning on it, so i was going to go back to windows and use MMC to fix the second hard drive by deleteing the partition i had made.

When i attempt to boot to windows, it just brings me to a screen that says:

GRUB>

and wont let me boot windows even with the disc out of the drive.

I didnt touch anything on my windows hard drive, however, earlier i did try to install a program from ubuntu called WUBI (found here: [https://wiki.ubuntu.com/install.exe/Prototype)](https://wiki.ubuntu.com/install.exe/Prototype)).

I am thinking that may be the culprit but i cant be sure.

Anyone know why i cant access windows anymore?

Thanks
Rug

---

### Post by AlcoJaguar on 2007-03-01
Unfortunately you overwrote your Master Boot Record (MBR) and now it's Grub instead of the microsoft version that instantly calls ntloader. 

To rectify this situation you either need a windows emergency repair and run the command 'fixmbr' or you need to manually add a boot record to grub from that command line.

Now I haven't actually typed a record into Grub directly in a long time but if you type 'help' it should give you a list of commands and I think one of them will let you edit the grub config on the fly (I don't believe it'll save your changes but it'll at least let you boot to windows once, from there you can fix the MBR by right clicking on System, clicking Properties, clicking on the Advanced tab, and clicking on Settings under Startup and Recover).

In Grub you'll want to set up a boot record similar to this 
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
``` 

This should allow you to boot to a Windows XP install on the first partition of your first hard drive.

Let me know how things go, I can look up more information on grub if you're having trouble.

---

### Post by RUGUNIT on 2007-03-01
Any idea how i would have done such a thing? I would like to know so i dont make the same mistake again...

Also do you mean an operating system disc for xp by saying windows emergency repair?

Thanks for the quick response...

-Rug

---

### Post by confused57 on 2007-03-01
Here's how to repair your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Once you get your Windows mbr, you might consider setting your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You could always reinstall Ubuntu on your secondary drive, which would reinstall grub to your primary hard drive mbr.

---

### Post by AlcoJaguar on 2007-03-01
I meant to add the word 'disc' to windows emergency repair, sorry about that. Here's a link to the command I refered to -
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true")
Also here's another link to a tutorial on how to boot to the Recovery Console and execute 'fixmbr' -
[http://www.windowsnetworking.com/articles_tutorials/wxprcons.html]("http://www.windowsnetworking.com/articles_tutorials/wxprcons.html")
That route is preferable as it's the least complicated and it'll also restore how you're use to your system booting.

The reason Grub overwrote your MBR is you must have completed the install from that executable you linked while in Windows. but I take it you couldn't boot to Ubuntu for some reason?

---

### Post by RUGUNIT on 2007-03-01
Okay back in business on the windows side, now back to ubuntu.

Thanks for the links but that seems to make ubuntu need a whole drive. I used to have fedora core 4 installed as just a small section of my second drive. So i think ill do it that way since my second hd still has a bunch of my stuff on it with no where else to go.

Thanks again everyone.

---

### Post by AlcoJaguar on 2007-03-01
You don't need an entire dedicated drive to install Ubuntu, I have it dual booted on an 80gb drive with Windows XP. Partitioned with 40gb for Windows XP, 40gb for Ubuntu. I can't vouch for that windows executable method you were using but as long as you have an empty partition you can fire up your system with the install cd and have Ubuntu up and running in about 25 minutes.

---

