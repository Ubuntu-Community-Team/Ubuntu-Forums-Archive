---
title: "Does RemasterSys work with Ubuntu 14.04?"
date: 2014-04-14
forum: General Help
---

### Post by Vannyi on 2014-04-14
I know the original developer of RemasterSys no longer works on this program, but it was fantastic and it worked in Ubuntu 12.04 which I still use.

I was looking to upgrade to Ubuntu 14.04 and was wondering if anyone might have tried a beta version of this OS and could confirm if RemasterSys still works?  Long shot but just thought I would ask.

Thank you

---

### Post by sudodus on 2014-04-14
You find alternatives including forks if you browse the internet. Maybe it is too early to find something that works with 14.04.

How do you intend to use it? I mean what kind of re-spin are you intending to make?

-o-

Maybe you can co-operate with *phillw*. See
[URL="http://ubuntuforums.org/showthread.php?t=2216356"]
Please help us test Lubuntu with Phill's non-pae kernel[/URL]

---

### Post by Vannyi on 2014-04-14
Thanks sudodus.

I kind of figured it might be a bit to early but just through I would check.  I will probably just install 14.04 and remastersys this weekend and test it out.

In terms of how I use it, it was to make a liveCD of my build so that I could share it.

---

### Post by sudodus on 2014-04-14
A simpler alternative might be to use the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971")

You can make your system clean, or even better, make an [OEM installation]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview"), and create a tarball from it (a compressed tar archive file). This tarball can be used to install the system into other computers. It is possble to make single boot as well as dual- or multiboot final systems. But the system in the tarball should have only one root partition (and one swap partition).

The OBI is made to work from USB install drives, not CD or DVD. I don't know how important it is for you (and your friends or clients) to be able to boot from CD.

---

### Post by tea for one on 2014-04-27
> **Vannyi said:**
> I know the original developer of RemasterSys no longer works on this program, but it was fantastic and it worked in Ubuntu 12.04 which I still use.

I was looking to upgrade to Ubuntu 14.04 and was wondering if anyone might have tried a beta version of this OS and could confirm if RemasterSys still works?  Long shot but just thought I would ask.

Thank you

I have installed 14.04 and also added Gnome-shell.

I was also curious to see if Remastersys would function with 14.04.

I had a copy of the Remastersys deb file, installed it via the Software centre and ran Remastersys from the terminal.

The iso created itself successfully and I installed onto a USB stick with Start Up Disk Creator.

The USB device booted perfectly so I installed my Remastered Image on an external drive.

The external drive booted OK and Unity and Gnome-shell look pretty good so far.

I am answering your post from the remastered image.

It would take hours to check every little detail of this Remastered image, but so far so good.............

---

### Post by Ez_Sit on 2014-06-05
> **tea for one said:**
> I have installed 14.04 and also added Gnome-shell.

I was also curious to see if Remastersys would function with 14.04.

I had a copy of the Remastersys deb file, installed it via the Software centre and ran Remastersys from the terminal.

The iso created itself successfully and I installed onto a USB stick with Start Up Disk Creator.

The USB device booted perfectly so I installed my Remastered Image on an external drive.

The external drive booted OK and Unity and Gnome-shell look pretty good so far.

I am answering your post from the remastered image.

It would take hours to check every little detail of this Remastered image, but so far so good.............

  I have also used remastersys version 3.0.4-2 to successfully create a distro backup of my installed Ubuntu 14.04 64bit system. I installed all the programs I wanted, ran update, then bleachbit to clean up. Remastersys version 3.0.4-2 created the iso, I used Ubuntu's startup disk creator to make a bootable USB drive and I booted that iso and installed the system on another computer to test. Everything worked perfectly and I currently run the installed system day-to-day and have not experienced any problems. I guess Ubuntu 14.04 did not change enough to prevent remastersys 3.0.4-2 from working eventhough it was released for Ubuntu almost two years ago.

---

### Post by BlackatHacker on 2014-06-10
Verified By me.... [SIZE=5][FONT=arial black]**It Worked**[/FONT][/SIZE] With Remastersys... Not Matter How You Use it.... Here's the Proof

[h=1][[COLOR=#ff0000]***Ubuntu 14.04 ReMastered & Reloaded by Linear***[/COLOR]]("https://www.youtube.com/watch?v=UV0eCVUhUhM")[/h]

---

### Post by kansasnoob on 2014-06-10
> **BlackatHacker said:**
> Verified By me.... [SIZE=5][FONT=arial black]**It Worked**[/FONT][/SIZE] With Remastersys... Not Matter How You Use it.... Here's the Proof

[h=1][[COLOR=#ff0000]***Ubuntu 14.04 ReMastered & Reloaded by Linear***[/COLOR]]("https://www.youtube.com/watch?v=UV0eCVUhUhM")[/h]

Cool I've been planning on creating my own respin using Flashback w/Metacity combined with some basic system recovery tools :guitar:

---

### Post by phil4000n on 2014-08-14
"I have also used remastersys version 3.0.4-2 to successfully create a distro backup of my installed Ubuntu 14.04 64bit system."
Where and how did you install it? 
Running Lubuntu 14.04.1, not in Ubuntu Soft Center

Thanks

---

### Post by nugroho.redbuff on 2014-08-23
Here is my experience remastering Lubuntu 14.04 using remastersys.
1. I got remastersys package from [http://www.remastersys.com/downloads/remastersys_3.0.3-1_all.deb](http://www.remastersys.com/downloads/remastersys_3.0.3-1_all.deb)
2. To install it, here is the command
> dpkg -i remastersys_3.0.3-1_all.deb; sudo apt-get install -f
3. Edit file /etc/lightdm/lightdm.conf, and write down this code
> #session=lubuntu

And remasterys just work fine. I use it to customize Lubuntu for local goverment, Kabupaten Banjarnegara, Central Java, Indonesia.

---

### Post by Dr_Frost on 2014-09-17
Does not work for me, using Ubuntu 14.04 - Mate Desktop 1.8.1
Tried with both 3.0.3-1 and 3.0.4-2
Both gives me same error from LOG.
genisoimage: Volume ID string too long

Anybody else got this issue, is it related to Mate Desktop?

**EDIT: Fixed with changing the LIVECDLABEL= , apparently it did not like the (64Bit) at the end??**

---

### Post by rani2 on 2015-02-05
Can someone Help me?
I'm tried many source to use remastersys . . .

I success make .iso from 
```
remastersys backup mydist.iso
```
but when I run my iso:
1. Live run perfectly
2. Install not work


Please some one help me

---

### Post by XBMC old School on 2015-05-07
Does anyone have a link to where i can get a copy of remastersys now?

---

### Post by Portaro on 2015-05-07
I think this can help if you need the copy of last remastersys .deb files -> [https://francofait.wordpress.com/2014/04/23/remastersys-os4-2014/](https://francofait.wordpress.com/2014/04/23/remastersys-os4-2014/)

As you can try this fork -> [http://linuxdicasesuporte.blogspot.com.br/p/remaster-gtk-ubuntu-e-derivados.html](http://linuxdicasesuporte.blogspot.com.br/p/remaster-gtk-ubuntu-e-derivados.html)

For rani2 - if help have you do the process of ISO build with Internet enabled, I think that I have this problem on past and I think that remastersys need the internet on to configure the installer definitions (program I dont remember the name).

---

### Post by acid3 on 2015-07-29
> **XBMC old School said:**
> Does anyone have a link to where i can get a copy of remastersys now?


A group of us are forking the code to Respin, but we have the Remastersys debs up. 

Feel free to use them,or our try ours.

The site is temporary, but for now it is [here]("http://azxp.net:89/respin.html"):

If you do try ours please give us feedback. include what distro, version, etc.

---

### Post by halfnote52 on 2015-07-31
> **acid3 said:**
> A group of us are forking the code to Respin, but we have the Remastersys debs up. 

Feel free to use them,or our try ours.

The site is temporary, but for now it is [here]("http://azxp.net:89/respin.html"):

If you do try ours please give us feedback. include what distro, version, etc.

HUGE props to you guys! I can't wait to try this out.  As an alternative suggestion to the OP, and future reference to others in the thread, I've had bad luck with remastersys and good luck with systemback under 15.04.  Will report my results for respin once I've tried it.

---

### Post by gelfling6 on 2015-09-10
Re-animating this thread.. I've been using a custom spin of 12.04 (Ultimate Edition, from off SourceForge)  I know there is a version 4.4 of the release out now, but not ready to jump that far as 3.5 has been very stable, and I've been able to manage it up to LUBUNTU 14.10 with no problem, until a few days ago..  My main machine, a Toshiba A505, (Intel i3 Quad-core, 4GM memory, 640GB HD with 8GB reserved as swap) decided to stop cold in the middle of upgrading to 15.04.  (actually had a small power-outage, it lost the signal, and I couldn't get it to continue.) So, 3/4 changed, the machine stopped working..  So.. using a 2nd machine, I'm slowly rebuilding it.  I'll let everyone know if remastersys-3.0.4-2.deb works, in creating a bare-metal backup.(thankfully, recovered all of my saved data to a blank 1TB on the 2nd machine.)(WHEW!!)

---

### Post by Adler on 2015-09-22
[QUOTEI'll let everyone know if remastersys-3.0.4-2.deb works, in creating a bare-metal backup.][/QUOTE]

gelfling6,

I just wanted to jump in here, and ask how everything worked out? I'll be looking to make a completely bootable backup on a 1Tb peripheral drive.

Just to throw this out here I wiped the drive from my machine - running 14.04 Trusty 64-Bit - with this command:

>   adler@adler-HP-ENVY-Spectre-XT-Ultrabook-PC:~$ sudo dd if=/dev/zero of=/dev/sdb bs=1048576
953869+0 records in
953868+0 records out
1000204138496 bytes (1.0 TB) copied, 23283 s, 43.0 MB/s
adler@adler-HP-ENVY-Spectre-XT-Ultrabook-PC:~$ 

The wipe took about 8 hours! I then used [gparted]("http://gparted.org/") to create a 1Tb Primary Partition using Ext4. The size of my peripheral drive is massively large compared to my Notebook's 128Gb SSD drive. But, I have a bunch of drives around. LOL!

Please do get back to use with your success. TIA.

Adler[I]
Down On The Jersey Shore[/I]

---

