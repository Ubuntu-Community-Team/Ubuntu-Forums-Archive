---
title: "How to delete multiple partitions"
date: 2007-06-28
forum: General Help
---

### Post by drsmaw on 2007-06-28
Noob here, need help.
Dual-boot windows xp and ubuntu 7.04 has been running absolutely fine. Until I decided to install beryl, and of course, out of excitement didn't read into it enough, and really screwed something up. I can't even remember what I typed in the terminal, but when I rebooted I got a nice dreaded " x server" message. Not having many references by my side, i rebooted again, but this time selected "recovery" - not good. KILL - and then everything went black.
Ok, so I figure to reinstall ubuntu, then maybe get back into my previous partitions and delete them.
Problem - I think i have way too many partitions now, I have no idea how to remove them.
Should I just re-install everything or How can I get back to my previous time before I installed beryl?
This is installed on a backup laptop, so there is no vital info that I need to backup.
Any words of wisdom would help
Thanks

---

### Post by Keen101 on 2007-06-28
Not quite sure what you did, or what you are actually asking, but as for easy partition editing I recommend Gparted. (which is what comes with Ubuntu) But,  I am recommending the Live-CD version of gparted. The live-cd version is easier to use in my opinion.   

[http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-8.iso?modtime=1182962209&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-8.iso?modtime=1182962209&big_mirror=0)



just remember to hit the "enter" key when it asks if you want to skip extra boot features (unless you need them), because the first time i used it I literally stared at that screen for about 5 min, thinking it was giving me an error message.

-good luck
-Keen101

---

### Post by russo.mic on 2007-06-28
well, If you want to simply reinstall Ubuntu, you could just install over the current Ubuntu partition, and the installer could take care of all your partitioning needs as it uses GPartited anyway. Just make certain that you don't kill the XP partition!

---

### Post by drsmaw on 2007-06-28
OK, no problem with any of these suggestions, but for some reason, I cannot boot UBUNTU.  Grub allows me to boot windows xp, but i cannot boot ubuntu. The screen just goes blank and the computer shuts down. Also, trying to boot from the live cd isn't helping, I keep getting critical temperature errors and it shuts down again.
I know which partitions to remove, I just need to get to them.

---

### Post by Keen101 on 2007-06-28
We'll, if that is what you want to do, then I still recommend Gparted LiveCD. It should boot up fine and should not give you any critical temp warnings. (although you should look into that)



-Keen101

---

### Post by euler_fan on 2007-06-28
If you can't boot ubuntu and are planning to reinstall right over it (very easy with live CD) I would first boot to the live CD and move any and all files you want to keep off to a flash drive or other media where it can be safe.  Another option is to look into an ext2 or ext3 driver for Windows (they exist, but I don't know their names) and get the files off either too your Windows partition or burn them to a CD while you're at it.

Then just go ahead and use the LiveCD to reinstall right over it. When it comes time to pick a partion, go through manual partition, then keep all the current partitions as is, and then select to install to the current Ubuntu partition (should be number 2, but make sure you check on your own machine).

@everyone: can someone post the name of the ext drivers for Windows?

---

### Post by drsmaw on 2007-07-02
ok, I'm pretty sure I've done enough damage. I booted xp and got into disk management, deleted anything that didn't apply to windows. Restart, and Grub gives me "error 22". Now nothing boots.  Looking for a fix-all. No, I do not have the boot discs, just recovery discs.  If I install Ubuntu from the live cd, then I lose Windows, which is ok.  But will it become a problem?  Or should I fixmbr and go back to dual boot.  Safest recommendations are highly welcome.  

I want to be non-Microsoft, but it's just a little tough getting used to everything.

---

### Post by LaRoza on 2007-07-02
Easiest and safest:

Get the Super Grub Disk, from my sig.

---

### Post by LaRoza on 2007-07-02
> **drsmaw said:**
> ok, I'm pretty sure I've done enough damage. I booted xp and got into disk management, deleted anything that didn't apply to windows. Restart, and Grub gives me "error 22". Now nothing boots.  Looking for a fix-all. No, I do not have the boot discs, just recovery discs.  If I install Ubuntu from the live cd, then I lose Windows, which is ok.  But will it become a problem?  Or should I fixmbr and go back to dual boot.  Safest recommendations are highly welcome.  

I want to be non-Microsoft, but it's just a little tough getting used to everything.

Windows is still there, if you were to reinstall Ubuntu next to it, you would be able to boot windows. If you used the Super Grub Disk, only Windows would boot and you would be able to get rid of Ubuntu easily.

---

### Post by LaRoza on 2007-07-02
> **euler_fan said:**
> 
@everyone: can someone post the name of the ext drivers for Windows?


[http://sourceforge.net/project/showfiles.php?group_id=43775](http://sourceforge.net/project/showfiles.php?group_id=43775)

That?

---

### Post by euler_fan on 2007-07-02
> **LaRoza said:**
> [http://sourceforge.net/project/showfiles.php?group_id=43775](http://sourceforge.net/project/showfiles.php?group_id=43775)

That?

That's it. Thanks.

---

### Post by drsmaw on 2007-07-02
Thanks for all the help.  Super Grub Disk = "lifesaver".  Absolutely excellent.  I've decided to keep windows xp, but only for work applications, but I'll still dual boot with Ubuntu.  Thanks again, now I'm not too afraid to screw something up - Until next time...........

---

### Post by strydermed on 2008-07-19
If you are stuck in a dual boot with Ubuntu/Vista or triple boot with Ubuntu/Vista/XP and want to remove Linux without affecting XP and /or Vista , there are many options..
If u have a Vista DVD, just boot off it and use the recovery console. Type *bootrec /fixmbr*
That's it you are done. If you don't have Vista DVD, then there are a few options. 
If you have deleted your Ubuntu partition from Windows you might that your system refuses to boot. Download Super Grub Disk and burn it to a cdrom, you can restore Windows after booting from that. VistaBootPro does not work in this situation, but you can use it to do lots of other cool stuff.
If you can boot into Vista then, there is a easy way. Just follow the steps below:
1. Download MBRFIX.EXE from [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx) 
2. Put it in your C or D drive. It does not matter where. Now right click on it and select security tab. Make it "Run as Administrator"
3. Type cmd in vista search box in start menu and right click it and select run Run as Administrator. 
4. In the command prompt go the directory where u have MBRFIX and now type *MbrFix /drive [COLOR="DarkOrange"]0[/COLOR] fixmbr /vista /yes* . This wont work without administrator permissions. Replace 0 with the number of ur drive. Just leave it if u have only one hard disk
That's it reboot and Vista boot manager will be back in  place of Grub. Now you can go into Diskmanager and format Linux partitions and reclaim the space

---

