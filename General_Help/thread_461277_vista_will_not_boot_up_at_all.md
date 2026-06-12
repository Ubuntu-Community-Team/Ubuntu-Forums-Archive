---
title: "vista will not boot up at all"
date: 2007-06-01
forum: General Help
---

### Post by MikeM709 on 2007-06-01
Hello, 

Well I installed wubi about 3 days ago when I saw it on [www.download.com](www.download.com) The only thing is that they did not say anywhere on there that it would break the Vista boot loader. So for right now I'm stuck in ubuntu (which don't get me wrong, linux is awesome) but I'm a gamer and so all my games for windows are installed on Vista. 

I looked in the Wubi guides and it shows in there how to manually uninstall wubi. But when I tried it in wubi it told me that everything in my C drive was read-only. So I cannot delete or edit any of the boot files in Ubuntu right now. I figured that it cannot make changes to any files that are in use at the time so what I'm wondering is whether or not I can use an Ubuntu live cd and boot from that and do the manual uninstall listed in the wiki, which just involves deleting a few files in the root directory.  

I heard somewhere else on these forums that if you use the windows disk and choose Startup repair, it would fix the MBR and allow Vista to boot once again. I tried this but Windows said that there were no problems with the startup. I have also tried ihtting escape right after the text about loading Ubuntu or something of the like comes up, but to no avail. I really don't want to reformat my hard drive but I guess I will if I have to.

I would be happy to try out any future versions of Wubi that may work on Vista to help out the community. I love linux and I love the ease of use that Wubi offers. But I feel that next time I'm going to just partition my hard drive :)

Any help is greatly appreciated. 

Also my specs are as follows:
1.5GB RAM
1 x 40GB Hard Drive (master (also has root of Vista on it))
1 x 200GB Hard (slave)
2.8GHz Intel Pentium 4 with hyper-threading capabilities
1 x (Samsung I think) CD-ROM drive
1 x Philips DVD+/-RW drive
Nvidia GeForce 7600GT (overclocked) 

Ubuntu and Wubi runs great on this hardware by the way. I even tried out Beryl (something I've always wanted to do) and it runs like a treat. No lag and my computer starts up and turns off fast.

---

### Post by minhmeoke on 2007-06-01
In my opinion, if you are going to dual-boot Ubuntu-Vista, then the best long-term solution would be using the grub4dos bootloader, rather than Vista's; see progress on that project at: [http://ubuntuforums.org/showthread.php?t=438858]("http://ubuntuforums.org/showthread.php?t=438858")

Edit: Computer Guru has found a solution for dual-booting Vista and Wubi using EasyBCD, go see this thread for details:[http://ubuntuforums.org/showthread.php?t=463849]("http://ubuntuforums.org/showthread.php?t=463849")

Normally, I would suggest that you install the NTFS Configuration Tool package in Synaptic to have read/write access to the C: drive if you were using XP, but I am not sure about how compatible it is with Vista; you should do some research if you want to try it. The Howto from Wubi Guide is here: [https://wiki.ubuntu.com/WubiGuide#head-97b446f468a115ba68ef1fa1283e29278c53b318]("https://wiki.ubuntu.com/WubiGuide#head-97b446f468a115ba68ef1fa1283e29278c53b318")

---

### Post by MikeM709 on 2007-06-01
Thank you for that info. I would like to dual boot Ubuntu and Vista but for now I would really like to get back to vista before my family gets too fed up with me and Linux. So far, Linux isn't making a very good first impression on them. Also, I took a look at that first link you posted and it appears that I would have had to edit the bootloader before I rebooted. Oops. I really suggest that for the time being, the Wubi installer should include a warning when you first start it up. Something alongs the lines of "WARNING! Wubi has been known to cause boot errors when used in conjunction with Windows Vista. If you are a Vista user, please procede with caution, and only if you know what you are doing." That would have saved me a bit.

So for now my question is, without being able to get into Windows at all, is there a way to manually uninstall Wubi from the computer without being able to access Vista?

---

### Post by Computer Guru on 2007-06-01
GRUB and Lilo corrupt the Vista MBR quite often, IMO the best way to dual-boot Vista and anything else is to use the Vista bootloader with a configuration tool like [EasyBCD]("http://neosmart.net/dl.php?id=1") to configure a multi-boot between Linux and Vista.

You can uninstall Wubi from the bootloader by booting from the Vista DVD and running startup repair.

---

### Post by minhmeoke on 2007-06-01
OK, so you need a LiveCD that can access NTFS on Vista; I'm not sure whether the standard Ubuntu LiveCD can do that, but I found this Howto online that says that a Knoppix LiveCD can, with CaptiveNTFS: [http://www.shockfamily.net/cedric/knoppix/]("http://www.shockfamily.net/cedric/knoppix/"). Using the Knoppix LiveCD, you can delete the C:\wubi, C:\grldr, C:\grub.exe, and C:\menu.lst, then edit C:\boot.ini as described in the manual uninstall section of the Wubi Guide: [https://wiki.ubuntu.com/WubiGuide#head-6b9eb58ace9884384e5e0d197bcf4159a25ed267]("https://wiki.ubuntu.com/WubiGuide#head-6b9eb58ace9884384e5e0d197bcf4159a25ed267")

Again, it was probably designed for WinXP, so I'm not sure if it works on Vista. Also, once you remove Ubuntu, you may have to replace the GRUB bootloader with Vista's bootloader, if you get an unbootable computer: [http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12]("http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12")

You can probably reinstall the Vista bootloader using your Vista CD once you have removed Wubi.

If that doesn't work, then I also found a Vista LiveCD, [http://usbtools.wordpress.com/2007/05/24/portable-windows-vista-live-cd/]("http://usbtools.wordpress.com/2007/05/24/portable-windows-vista-live-cd/") but I'm not sure if it's any good. It might have something like the Unix chroot command ([http://ubuntuforums.org/showthread.php?t=157250]("http://ubuntuforums.org/showthread.php?t=157250")) that would let you change/repair your actual installation from LiveCD.

Hope that helps. Sorry that I can't give definitive answers; I don't have Vista myself, so I can't test whether these solutions work or not. Good Luck!

---

### Post by MikeM709 on 2007-06-01
Thank you all for the helpful advice. I have already tried the Vista startup repair and it reported nothing wrong but I will give it one more try. The only thing on here that I think might work is that knoppix cd idea. thanks very much, I'll try it and I'll be back here to report whether it works or not.

Also, I have looked around a little bit and found out that Vista is probably the first operating system to not use a boot.ini file. Everywhere I looked said that boot.ini was ignored when Vista was started up.

---

### Post by MikeM709 on 2007-06-02
Well I would like to report that I have gotten back to Vista. I used that Windows Vista LiveCD (which is a bit lacking in features for a LiveCD btw) to delete some of the files that start up grub, allowing me to get to that message telling me to choose between Ubuntu and Vista. 

Well that CD worked well except for the fact that it does not have a file explorer or anything (what idiot builds a Live with no file explorer). So what I ended up doing was getting into notepad and clicking File -> Open -> then I navigated through the folders to my C: drive and right clicked on the files I didn't need and clicked delete. Thank you notepad, you once again saved me. 

So right now my only problem is that my CD drive will not stay closed, but I will search google for the answer to that. 

Thanks very much to everyone that contributed their ideas to get my vista back up and running again. I will continue to be a presence on these forums and I'm definitely willing to try out and Vista ready betas of Wubi. I love the idea of not having to format my hard drive, especially now that I know how to get back to Vista once its over. 

Btw, BERYL RULES! YAY FOR CUBES!

---

### Post by minhmeoke on 2007-06-02
Glad to hear that you fixed the problem. Also, if possible, please list the exact steps you took to successfully restore the Vista bootloader, for any other users who may be having the same problem. Thanks.

---

### Post by MikeM709 on 2007-06-03
Sure!

NOTE: These instructions will only work with Vista because it does not utalise the boot.ini file.

ALSO NOTE: The Windows Explorer in the LiveCD is written in a foreign language, Russian I think (only the OK and Cancel buttons). They are still in the same place as all Windows explorer buttons are though, so as long as you remember where the OK and Cancel buttons are in a default explorer window, you'll be fine.

1. I went to [http://usbtools.wordpress.com/2007/05/24/portable-windows-vista-live-cd/](http://usbtools.wordpress.com/2007/05/24/portable-windows-vista-live-cd/) and downloaded the Vista LiveCD. All you need is either the first or second link. They are both the same.

2. I burned the .iso to a cd.

3. I changed my BIOS settings to boot off the CD so that I would be able to load it.

4. With the CD in, the LiveCD started up. I looked around a little, there wasn't much in the way of functionality on the LiveCD. So I right clicked on a blank portion on the desktop and click the first option on there. This opened up a Notepad2 file with some stuff on it. the exact stuff can be ignored, you just need the file browser.

5. Click on the File tab, then click Open. You will be brought to one of those windows open screens that you can do things to files like copy, paste, and delete. 

6. Browse through your computer, clicking the up folder button, until you get to the hard drives. There should be around 4 or so, maybe more, but probably no less. Double click to open up your C: drive, then right click and select delete on the following items:

-grldr
-menu.lst
-boot.ini

7. With those files deleted, restart your computer by clicking on Start -> Shutdown -> Restart and eject LiceCD. 

Now all you need to do is uninstall Wubi to get rid of Ubuntu and then your free of all that Linux trouble! But don't bash Wubi because it is not yet functional with your normal operating system. In time, I'm sure it will work out great.

With those steps followed, your Windows Vista will work again, and boot into Vista by default. (not guaranteed. start a thread in this forum and I will try and help)

---

### Post by djchandler on 2007-06-03
**WARNING!**

I'm glad MikeM709 got everything fixed. He's way more adventurous than me.

According to the official Wubi FAQ web page, [http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/faq.html#requirements](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/faq.html#requirements)
Vista is NOT supported at this time, but they are working on it. Also, please note that this is Beta software, not a full-fledged working release. MikeM709, your adventurous spirit may have significantly enhanced this project. Please share your experience with the Wubi developers. You are right out there on the bleeding edge, pal!

---

### Post by MikeM709 on 2007-06-03
Well thank you. I went to that Vista testers wanted thread and asked how I can get involved with testing the new builds. 

I got and heard about Wubi from [www.download.com](www.download.com) where they only had test2. But they did not list and warnings about it not being compatible with Vista or anything. So I installed it but I couldn't get back to Vista, so the rest of my family was getting a little fed up with linux, mainly because they did not understand that they use FireFox to browse the internet in Vista and its the same thing in Ubuntu. I think the colors threw them off a little too :P

But I will definitely stick around and recommend this to anyone that has XP for now.

---

### Post by dweez on 2007-06-06
Below is the link I used for dual booting.  First I had XP on the machine, then I dual booted to Gentoo.  I then upgraded XP to Vista, breaking grub.  The link below walked me through reinstalling grub.  Then I got rid of Gentoo and came back to Ubuntu, breaking Vista's bootloader.  Again, the following link helped me reinstall it.

[http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp](http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp)

---

### Post by Atlae on 2007-06-10
Hey,
I've been unable to boot up Vista since I installed Ubuntu (via liveCD). I tried the Vista LiveCD from the link provided, and unfortunately my C: drive says it must be formatted before I can use it.  I tried their bmr manager, and it recognizes the partition (woo, it's a start), but I can't activate the partition (it says "activation successful" but stays inactive) and can't see any of my data. Any ideas, possibly?

---

