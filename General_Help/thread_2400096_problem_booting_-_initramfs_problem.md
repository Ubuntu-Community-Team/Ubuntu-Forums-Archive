---
title: "problem booting - initramfs problem"
date: 2018-09-02
forum: General Help
---

### Post by jgw on 2018-09-02
Last night by machine froze and I had to reboot.  When it rebooted it got stuck on [initramfs].  I then spent hours researching initramfs and actually tried some of the 'answers'.  Everything failed.  I then entered 'exit'.  The computer then told me I had a problem with the filesystem and to run fsck.  Looked that one up and was told to run fsck /dev/stb1.  Then it started fixing thing (pressed 'y' on every query to fix).   After that I rebooted.  This time I was taken to the boot menu and I chose the top option and it booted right up.  Somehow, however, I lost my radeon video driver.  I am running a 4k tv with this machine and my resolution was 1024x780.  It was BIG!  So I went to symantic and reinstalled all radeon drivers and also fixed any packages.  It then did a search on installing the radeon driver and found a suggesting that I add a ppa, for the driver, and then update.  I did that and I rebooted.  This is where I am right now.  Oh, I also ran fsck again and it found no problems.

So, now I am back up and running but I have no idea if I should do anything else and would appreciate any thoughts on this.

Oh, when I rebooted the last time it also asked me for a password to unlock a key ring before the network would start.  When the network came up it wouldn't connect.  So, even though it thought it wasn't.  At that point I stopped the network and then restarted it.  Now, obviously, the network is working, still...........

Somehow this machine REALLY got screwed up.  Once I figured it out it was pretty simple to get running but I remain concerned that I might have more problems waiting to rear up and bite me in the a** 

Thank you...................

I thought I had changed my signature but it didn't take.  This is my real signature:
Computer
	Processor			AMD A8-7650K Radeon R7, 10 Compute Cores 4C+6G
	Memory			15338MB (2617MB used)
	Operating System	Ubuntu 18.04.1 LTS    
Display
	Resolution		         3840x2160 pixels
	OpenGL Renderer	 AMD KAVERI (DRM 2.50.0 / 4.15.0-33-generic, LLVM 6.0.0)
	X11 Vendor		 The X.Org Foundation

---

### Post by oldfred on 2018-09-02
Abnormal shutdown often causes file corruption.
If possible better to use REISUB.

       Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[https://askubuntu.com/questions/926461/whats-the-difference-between-the-magic-reisub-reset-and-holding-down-the-power](https://askubuntu.com/questions/926461/whats-the-difference-between-the-magic-reisub-reset-and-holding-down-the-power)

And you can automate the y answer.
       
 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by jgw on 2018-09-02
Thanks for the reply!

I fixed my signature to show what I am using.

Your suggestion for reboot and not turning computer on and off was interesting.  My problem is that I don't reboot, with the on/off switch, unless the computer is truly frozen.  This means that there is no mouse, no keyboard, nothing - I just have a frozen screen (and assuming its the computer too as there is no disk activity light flashing).  I have a system monitor that shows my cpu, memory and disk activity displayed all the time (top bar).  I can tell when I am frozen as the display is frozen too.  I am also not unconvinced that the freezing has something to do with my browser (firefox) but can't nail it down although, rarely, it might just freeze when firefox is down (I turn it off when I don't need it).  I should probably switch browsers.  There are a lot out there I just gotta find the time.  I did try google browser but don't like it.  I suspect that is a comfort zone thing.

Anyway, thanks again!

---

### Post by jgw on 2018-09-03
I guess there are no more replies so I will mark this one as solved.  I also want to thank oldfred again for his help.

I should mention that my solution of simply entering 'exit' at the [ initramfs] allowed me to fix the problem.  

There was a lot of stuff on this one, including "ask ubuntu", all of which were a bit complicated.  On reflection I wonder why but I guess there must not be an answer.

---

### Post by oldfred on 2018-09-03
Random shutdown can be one of the most difficult to debug.
Is system overheating?

---

