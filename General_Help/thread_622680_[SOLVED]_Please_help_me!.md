---
title: "[SOLVED] Please help me!"
date: 2007-11-25
forum: General Help
---

### Post by CodyGuitarist on 2007-11-25
So Im still sort of fresh to linux and have a major issue i can for the life of me figure out.
(Im using Ubuntu 7.10 Gutsy Gibbon)
This is actually a 2 part issue.

#1
When Im at the login screen the res is 1024x780 or 1280x1024 (I dont know the default)

But once i log in it becomes 800x600. I havent found any answers for this so any Insight would be appreciated.

#2 
Im not 100% but i have a very good feeling this is linked to the first one.

If i try to take a screenshot whilst still 800x600 it looks perfectly find. However, if i take it  after ive switched my res to 1280x1024(The one i use)  my screen shots look like this.......

[IMG]http://i127.photobucket.com/albums/p131/Wastebasketx/Ohnoes.png[/IMG]

Again i have ABSOLUTELY no idea how to fix this or why it is doing it.


But i did have an issue with my video card before hand. So that could be why.
Ati Mobility Radeon 9200

---

### Post by jcsteele on 2007-11-25
Do you have the closed source ATI drivers currently installed?

//jcs

---

### Post by CodyGuitarist on 2007-11-25
> **jcsteele said:**
> Do you have the closed source ATI drivers currently installed?

//jcs

As far as I know all I did was install the ATI binary and am using one of the ones already listed in the Graphics section.

However, I was reading a tutorial on how to install beryl  and was copying and pasting things it told me to change (in the xorg file).

Problem was(that i only noticed after) the fact that the card they had was the FireGL 9000 by Ati. So all my settings were configured to that. 

I thought i had fixed it because i nolonger got the  Low Graphics Mode  pop up  on start up.

But now those 2 problems are there.

---

### Post by jcsteele on 2007-11-25
When you installed the ATI binary, did you use the repositories method, or did you manually download the driver from ati.com ? ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI))

Also, beryl is no longer a project, and is has been merged with the Compiz project - both projects are now called "Compiz-Fusion" ([http://www.compiz-fusion.org/](http://www.compiz-fusion.org/)) which is included by default on recent version of ubuntu (turned on my default in Gutsy 7.10)

Can you post the output of a "lspci" below, this will help verify some things.

//jcs

---

### Post by CodyGuitarist on 2007-11-25
Well someone told me that Compiz-Fusion renders graphics differently. I installed the binary by Applications->Add/Remove

Here is my lspci.

> 00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)


---

### Post by jcsteele on 2007-11-25
I would start by removing the beryl that you installed....I do not think your going to notice much of a difference (if any) with it....use the included by default compiz-fusion (which can be customized very easily). See if things change from there.  If not, see below.

Remove your ATI Graphics driver you installed and use the opensource versions of the driver....have you edited your xorg.conf file?  If so, you will most likely need to revert back to a previous version, or obtain a new one (possibly using the live cd).  If things get back to normal, you can work on getting the ATI driver setup again once things are back to normal.

//jcs

---

### Post by CodyGuitarist on 2007-11-25
Youll have to excuse me i stil am a noob. Where  can i find this opensource driver? How do i remove my current? and how can i remove beryl if add/remove doesnt list it?

---

### Post by jcsteele on 2007-11-26
Lets focus on removing the beryl or whatever you installed...do you remember what you did when you installed it?  Did you follow a website or guide?

//jcs

---

### Post by CodyGuitarist on 2007-11-27
I followed a guide. Which, in turn, Im assuming also help corrupted my video. Cause I was copying and pasting everywhere.

---

### Post by jcsteele on 2007-11-28
Do you know where the guide was?  Do you have a copy of it?  Its hard to tell you anything without seeing what you did.

//jcs

---

### Post by CodyGuitarist on 2007-11-28
Ok I looked through my browsing history and heres the guide. 

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

Someone had told me that installing stuff on FF was the same as GG.

---

### Post by CodyGuitarist on 2007-11-29
Well thanks for your insight. I managed to fix it by messing with it a little (and a friend came to help :D). I think it had something to do with the setting i was going on.

---

### Post by jcsteele on 2007-11-29
Thats good...I haven't had any time to look through the guide you said you followed, so I was reluctant to respond without knowing exactly what to tell you (or at least a guess :) )

Glad things are working again...make sure to mark the thread as SOLVED in the "thread tools" section.

//jcs

---

