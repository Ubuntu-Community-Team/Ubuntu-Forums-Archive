---
title: "Running X on new laptop"
date: 2014-03-31
forum: General Help
---

### Post by Ertai87 on 2014-03-31
Hi guys!  I have a problem.  I just bought a new laptop, but I can't get X to run on it.  The laptop is a Toshiba Satellite C40D-A, purchased today brand new (March 31 2014).  I swapped in my old HD from an older computer that had Ubuntu on it, and everything worked there, except it gave me a graphics error and then booted to command line. I subsequently created a boot USB to try to reinstall, but after I get past the Ubuntu splash screen (with the 5 dots that turn white and orange), the screen just goes black and X never loads.  The power light is still on and the internals are humming, so something is happening, but the screen is not.

The Ubuntu version on my old HD is 13.10, and the USB is 12.04LTS.  I've tried the USB on another computer, and it worked fine, so I think it's a problem with my computer.  Can anyone help me out?  As I said, I just bought the computer today so I can return/exchange it if necessary, but I'd rather not if I don't have to, since this one has all the specs I want.  Thanks.

---

### Post by grahammechanical on 2014-03-31
A question. Before you removed the hard disk did you run Ubuntu and activate the Nouveau open source video driver? The two machines have two different graphic adapters and the video driver on the old hard disk may not be compatible with the graphic adapter in the new machine. Can you see the problem?

Do you get a Grub boot menu? If not hold down shift while the machine is booting. Then select Recovery Mode and at the Recovery menu select Resume. That should you Ubuntu without using a proprietary video driver. If you get to a desktop you can use Additional drivers to find a more appropriate driver for that machine.

As regards the problem with the USB stick it also is a graphic driver problem. In this case 

1) At the first purple screen press Enter
2) At the next screen select the language (English is default) and press Enter
3) At the Try Ubuntu - Install Ubuntu press F6
4) Look for a menu at the bottom right of the screen and select nomodest and press Enter
5) Press Esc to clear the menu and then select either Try Ubuntu or Install Ubuntu.

Regards.

---

### Post by Ertai87 on 2014-03-31
That appears to have worked.  The 12.04 install did not recognize my 13.10 installation, so I'm just doing a pure format, which is fine cause there was nothing important there anyway.  If this is not normal, let me know.  In any case, I'll post back if something goes awry, otherwise I'll just close the thread.

---

### Post by sudodus on 2014-04-01
I understand that you were successful using nomodeset :-)

The installer really *should* recognise previously installed systems, at least as a system. If it did not recognize 13.10, it is not normal.

But an older Ubuntu version cannot be expected to 'be informed' about newer versions, so it should be recognized as a system, but maybe not described as 13.10 in the grub menu.

---

### Post by Ertai87 on 2014-04-01
Sorry, maybe my question was unclear. I'll be a bit clearer.  When I went to reinstall Ubuntu, the 12.04 installer said it did not recognize any operating systems on the hard drive (which had 13.10 installed) and hence did not offer to migrate my home folder into the older version.  Is that normal?

---

### Post by sudodus on 2014-04-01
I'll try to be more clear too.

I think something is wrong. Ubuntu 12.04 should recognize that there is an installed linux system already, even if it is a newer system.

It would be interesting to check, what you see, when selecting 'Something else' at the partitioning window of the installer.

Could it be a problem of one system being in UEFI mode and the other system in old style BIOS mode (alias CSM)?

---

### Post by Ertai87 on 2014-04-01
Dunno.  I'm not that knowledgable about this.  Also I completed the reformat, so I can't check it :(

---

### Post by sudodus on 2014-04-01
Anyway, are you happy with your installed Ubuntu system now?

---

### Post by Ertai87 on 2014-04-01
Well, it's fine, I'm just worried that if one thing went wrong then other things might also be wrong...

---

### Post by sudodus on 2014-04-01
Well, I'm testing the new Trusty version, to become 14.04 LTS in a couple of weeks. Doing that I cannot be too afraid of things going wrong ;-)

Let us know if something seems wrong, otherwise we assume everything is fine :-)

And when you can relax with your system, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Ertai87 on 2014-04-01
Well what I'm most afraid of is that I created the install disc on an untrusted computer, and perhaps there was a virus or something on that computer which got into the install package and screwed up my installation.  Is this possible?

---

### Post by sudodus on 2014-04-02
I don't think so. I think you made a CD/DVD. It was 'cloned' or imaged directly, so I don't see where it would have been infected by the host system. And it is linux, and it is very unlikely that linux malware is lurking in a Windows computer to infect a linux install disk. Maybe it would be possible, but I would say very very unlikely.

---

### Post by Ertai87 on 2014-04-02
Alright.  Just for fun I plugged the USB (not CD; apparently the 12.04 installer is over 700MB and couldn't be burned to a 700MB CD so I used a USB key instead) into my computer again just to see if it could see a 12.04 install, and it could.  Might have been a compatibility problem between 12.04 and 13.10.  Just so you know, as a 14.04 developer, if you could make the installer under 700MB so it could be burned to CD, that would be super appreciated =D

---

### Post by Ertai87 on 2014-04-02
Incidentally, I've marked this thread as solved, but I'm having a couple other problems with my system if you wouldn't mind taking a look.  The threads are located here:

[http://ubuntuforums.org/showthread.php?t=2214524](http://ubuntuforums.org/showthread.php?t=2214524)
[http://ubuntuforums.org/showthread.php?t=2214391](http://ubuntuforums.org/showthread.php?t=2214391)

---

### Post by sudodus on 2014-04-02
> **Ertai87 said:**
> Alright.  Just for fun I plugged the USB (not CD; apparently the 12.04 installer is over 700MB and couldn't be burned to a 700MB CD so I used a USB key instead) into my computer again just to see if it could see a 12.04 install, and it could.  Might have been a compatibility problem between 12.04 and 13.10.  Just so you know, as a 14.04 developer, if you could make the installer under 700MB so it could be burned to CD, that would be super appreciated =D

I'm not an Ubuntu 14.04 developer, only a tester, and I cannot change the size of the iso files. Developers seldom read the Ubuntu Forums. You can find them at IRC and they might read and write comments about bug reports at Launchpad.

But there are alternatives:

1. The obvious alternative is to make a USB or DVD install drive of the 'oversized' iso file.

2. There are some official Ubuntu flavour iso files, that fit in CD in all versions including Trusty Tahr (to become 14.04 LTS).

- ***The Lubuntu desktop iso and alternate iso***

- ***The Ubuntu mini iso*** (mini.iso) - this one can be the starter for all flavours and can be installed into most computers except those with UEFI systems

3. There is the experimental 9w installer (a community re-spin) with versions that fit in a CD. This is made for really small systems.

---

