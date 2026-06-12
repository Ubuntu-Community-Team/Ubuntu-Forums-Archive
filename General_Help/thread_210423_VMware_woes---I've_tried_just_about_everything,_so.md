---
title: "VMware woes---I've tried just about everything, someone help me!"
date: 2006-07-06
forum: General Help
---

### Post by MM23 on 2006-07-06
Normally I would make a very specific topic title as to what my problem is, but this really isn't anything I can pinpoint, hence my reluctant topic in this forum.

As a long time user of VMWare Workstation and Ubuntu Linux, I have never really had any problems with them, and personally I have always thought they got along quite flawlessly together. But I had also never really bothered to update my kernel OR upgrade from Breezy to 6.06 Dapper Drake. So, today, I decided I was so out of date that I might as well, and took the steps to update my kernel to 2.6.15-25-686 and update all of my libraries and everything else, including Breezy itself. Knowing full well that vmware tends to be cranky whenever the kernel is changed, I took particular care in downloading the header files as well. After all was said and done, everything seemed to be working until I tried to start up vmware. I was not suprised---it told me that I needed to rerun the config script. Okay, why not. I did so, it wanted to overwrite 10 billion things so I let it, and I also let it compile the new modules with GCC 4.0.3 (which was the same version I used to compile the kernel in the first place). I told it not to change any of my network settings, as there was no need to change what has not been modified. Anyway, the gist of it is that the (re)installation went fine. No problems.

Then I go to run vmware, and I get a library error:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

Hmm. Odd. No big deal, though. I, as root, copy libpng.12.so.0 from /usr/lib to /usr/lib/vmware/lib/libpng12.so.0/, overwriting the original.

Then disaster strikes. I go to start up vmware, and NOTHING (I do mean nothing) happens. NOTHING. This is all the terminal output I get. Nothing more, nothing less, every time.

mm23@ggnore:~$ vmware
mm23@ggnore:~$

Trying again as root:

mm23@ggnore:~$ sudo vmware
Password:
mm23@ggnore:~$

Okay, I said to myself. What the hell did I do? After scouring the web endlessly for solutions, I decided to reinstall vmware from scratch. I ran the uninstall script (/usr/bin/vmware-uninstall.pl) and downloaded the latest tarball (VMware-workstation-5.5.1-19175.tar.gz) from the vmware website. I proceeded to run the install script once more and do everything as normal, and once again, everything worked. I set up my bridged networking fine, all the modules compiled successfully, etc.

I go to run vmware again, and I get the SAME libpng error, but this time, it's three times in a row:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

This time I tried deleting the library in /lib/vmware/, as I have it in /usr/lib/ anyway and vmware SHOULD be smart enough to find my paths. Once again, once I do this, the error dissapears, but... vmware STILL won't run! What the heck?

mm23@ggnore:~$ vmware
mm23@ggnore:~$

At this point I said screw it, uninstalled vmware workstation AGAIN, and attempted something I have never tried before---installing vmplayer.

mm23@ggnore:~$ sudo apt-get install vmware-player vmware-player-kernel-modules-2.6.15-25

yatta yatta everything goes fine it installs in no time, and I go to run it---

mm23@ggnore:~$ vmplayer
mm23@ggnore:~$

Now trying to run a .vmx

mm23@ggnore:~$ vmplayer vmware/Windows\ XP/winxp.vmx
mm23@ggnore:~$

I don't get the libpng error this time, but it still won't run, and it isn't giving me any output. I am at a loss as to what I could possibly to do to fix this. I have the right kernel image and headers installed; it isn't a problem with gtk or anything like that as everything else is working fine, and I'm frustrated to no end over this. Somebody give me some kind of means to debug this problem. Is there any kind of verbose mode for vmware? I've checked the manpages and I can't find anything. I really don't want to have to completely reinstall Ubuntu just to get vmware to work...

---

### Post by mannheim on 2006-07-06
> **MM23 said:**
> 
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)



That message always appears for me with vmware workstation (run from terminal), but it seems harmless. It is (perhaps) related to the failure of vmware workstation on dapper to use the expected gtk theme.

Apart from giving this message, vmware **should** start okay. So ignore the libpng12 message. The problem is elsewhere.

---

### Post by Jose Catre-Vandis on 2006-07-18
Try here for some answers

[http://www.ubuntuforums.org/showthread.php?t=214913](http://www.ubuntuforums.org/showthread.php?t=214913)

When moving from one kernel to another vmware has problems and you usually need to update kernel headers and stuff to get everything lined up again

---

