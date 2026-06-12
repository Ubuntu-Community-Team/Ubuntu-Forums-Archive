---
title: "Removing SuSE, fixing GRUB"
date: 2007-02-28
forum: General Help
---

### Post by Tsen on 2007-02-28
Alright, so I'm running Ubuntu 6.10, but I decided that it was time I give a few other distros a try, so I installed openSuSE 10.2.  It didn't turn out so well...I had a lot of usability issues, installing codecs and the like was a pain, it booted slower and generally wasn't what I wanted.  Part of the problem (perhaps even most) was just that I'd already got my Ubuntu install to be exactly what I wanted it to be, and starting over was hard, especially since I didn't know my way around SuSE, so I didn't have a predetermined pathway for getting it to where I wanted.

Well, now that the intros behind us, here's my problem:
I want to uninstall SuSE to make way for another OS--perhaps Feisty Fawn.  But since I installed SuSE after Ubuntu, it overrode Ubuntu's GRUB settings and created new ones.  If I just format the partition SuSE is on, will GRUB still be able to boot, or do I have to reconfigure it to use the old boot settings from Ubuntu (which are still intact, just not being used).

---

### Post by Tsen on 2007-02-28
Well, it's been two hours and threads get buried fast here.
This is partially a bump to get this back up where hopefully somebody will find it, but mostly I wanted to add more information:
On the SuSE wiki it said that you should do this:

   5.  To remove LILO or GRUB (if it is installed in the MBR), the original boot code that was in the MBR prior to the installation of SUSE LINUX can be restored. To do this, change to the following YaST module:
          * Boot Loader Setup ->
          * Reset (bottom right) ->
          * Restore MBR of Hard Disk 

After a security query, the boot code in the MBR is rewritten. The partition table remains unmodified. If another operating system is installed on your machine, it should boot automatically the next time the machine is powered on. 

But I think it's assuming that SuSE is the only Linux distro on your PC.  By deleting SuSE's GRUB, will it restore Ubuntu's version?

---

### Post by confused57 on 2007-02-28
> **Tsen said:**
> Well, it's been two hours and threads get buried fast here.
This is partially a bump to get this back up where hopefully somebody will find it, but mostly I wanted to add more information:
On the SuSE wiki it said that you should do this:

   5.  To remove LILO or GRUB (if it is installed in the MBR), the original boot code that was in the MBR prior to the installation of SUSE LINUX can be restored. To do this, change to the following YaST module:
          * Boot Loader Setup ->
          * Reset (bottom right) ->
          * Restore MBR of Hard Disk 

After a security query, the boot code in the MBR is rewritten. The partition table remains unmodified. If another operating system is installed on your machine, it should boot automatically the next time the machine is powered on. 

But I think it's assuming that SuSE is the only Linux distro on your PC.  By deleting SuSE's GRUB, will it restore Ubuntu's version?

You can install Ubuntu's grub to the mbr, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Here's a guide for booting multiple linux distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)
personally, I use chainloading...I haven't tried any of the other methods.

---

### Post by Tsen on 2007-02-28
Alright, thanks!  That helped a ton.

---

### Post by sloopveedub on 2007-02-28
Too funny!  I'm on the opposite side of this coin!  I've been using SUSE for the past few months (my first foray into Linux) and thought I'd try other distros to see what's out there!  Alas, I installed Ubuntu and am now a bit lost!  I find it much easier to get around in SUSE but I think it's simply because that's what I'm used to and being more comfortable with the KDE interface than GNOME hasn't helped.  Luckily I've reacquainted myself a little with the command line and also downloaded the KDE base packages for Ubuntu!

Is there an equivalent to SUSE's Yast in Ubuntu (v 6.10) or Debian?

---

### Post by g8m on 2007-03-01
I have used suse in the past. And it's one of the best distributions around. But I dropped it after the Novell take-over. I never looked for alternative for yast. Just searched for the "ubuntu/debian" way of  doing things. Synaptic/adept for software management. Although I also use apt-get a lot now. 
And just search for the preferences/administration options in the menu's. It was enough to get and keep it running. Missing sax though, that was a great app to configure the display.
I know there is something like dpkg --reconfigure xserver or something, but it asked questions, I didnt know the answer to.

My first experience with Ubuntu was Kubuntu 5.10 (KDE). I made the switch to ubuntu 6.10 (Gnome), because it;s the main distribution. I didnt like gedit though, installed Kate, didnt like rhytmbox, installed Amarok, didnt like gnomebaker, installed k3b. So my gnome desktop is infested with KDE.

Never got compiz working on suse, but with a howto on this forum i had it working in an hour.

---

