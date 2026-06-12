---
title: "Picture, but no sound with Tv Time"
date: 2007-02-20
forum: General Help
---

### Post by SirPaPa on 2007-02-20
Hello, I'm having a problem with Tv Time and Gnomeradio. With Tv Time I get picture but no sound. I just install this tv tuner card( AverMedia Go 007 FM Plus ) yesterday but can't get sound to work from neither Tv Time nor Gnomeradio. Any ideas what could be the matter?

I get sound from everything else. I need someone's help please.
Thank,you.:confused:

---

### Post by Whoopie on 2007-02-20
Hi,

have a look at [http://www.linuxtv.org/v4lwiki/index.php/Avermedia_AVerTV_GO_007_FM](http://www.linuxtv.org/v4lwiki/index.php/Avermedia_AVerTV_GO_007_FM)

The interesting part is the sox command.

Best regards,
Whoopie

---

### Post by SirPaPa on 2007-02-20
> **Whoopie said:**
> Hi,

have a look at [http://www.linuxtv.org/v4lwiki/index.php/Avermedia_AVerTV_GO_007_FM](http://www.linuxtv.org/v4lwiki/index.php/Avermedia_AVerTV_GO_007_FM)

The interesting part is the sox command.

Best regards,
Whoopie

Yes , thank you Whoopie but I got this:

---

### Post by Whoopie on 2007-02-20
First, you need to install the sox package: "sudo apt-get install sox"

Perhaps, the module was already loaded. You could try the following: after a reboot, plug in the device. Then "lsmod|grep saa7134-oss". If you see an output, you don't need to modprobe it.

---

### Post by fragos on 2007-02-20
Before installing, right click the speaker icon in the upper right applet panel.  Select "Open Volume Control" and make sur Playbacks aren't muted.  By using the File menu drop down and Change Device you can check on other sound sources.  When you exit set device to 0, your sound card< so the speaker icon will be able to control volume.  This should be the first place to look whenever sound is missing.  Note that some TV cards require you to externaly cable sound to the PS's Line in jack.  I have no experience with your specific TV card.

---

### Post by SirPaPa on 2007-02-21
> **Whoopie said:**
> First, you need to install the sox package: "sudo apt-get install sox"

Perhaps, the module was already loaded. You could try the following: after a reboot, plug in the device. Then "lsmod|grep saa7134-oss". If you see an output, you don't need to modprobe it.

Hi Whoopie, I installed the "[COLOR="Red"]sox[/COLOR]" package but got no results from the command "[COLOR="Red"][COLOR="Black"]lsmod|grep saa7134-oss[/COLOR][/COLOR]. This is what I found :

---

### Post by Whoopie on 2007-02-21
I don't know how to help you. I don't own that device.
You could ask on irc.freenode.de at channel #v4l. But if saa7134-alsa is loaded, you perhaps don't need saa7134-oss. Just try the sox command.

---

