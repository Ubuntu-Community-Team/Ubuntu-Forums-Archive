---
title: "Can I disable automatic monitor adjustment?"
date: 2013-01-03
forum: General Help
---

### Post by Digitaltomj on 2013-01-03
Hello, I am running Ubuntu 12.10-64 bit on my HTPC with an AMD Anthlon II X4 640 Processor x4 and using VESA RS880 graphics. Since it is an HTPC I have connected it into my Yamaha Natural Sound AV Receiver RX-V367 via HDMI and then from my Yamaha into my Samsung TV also via HDMI.

So far everything works perfectly except that at times (normally when I switch inputs and turn the TV and Reciver off while leaving the HTPC on) Ubuntu will no longer detect my 50 inch Samsung and will instead detect a 32 inch Yamaha (whicjh I guess is my reciver) It is a simple fix, once i open the display menu it auto corrects, but if im in a full screen application such as XBMC it is a bit of a pain.

So my question is, if there is anyway to disable this auto detection and resolution adjustment of new monitors?

---

### Post by slickymaster on 2013-01-03
I don't think that there's a good solution to your case, but you can take a look at this [post]("http://ubuntuforums.org/showpost.php?p=10410332&postcount=4") and this [one]("http://ubuntuforums.org/showpost.php?p=10432877&postcount=5"). Try to see if it works for you.

---

### Post by tgalati4 on 2013-01-03
Understand that when you use an HDMI connector you are also using HDCP--high definition copy protection.  This means that both devices need to be powered on and connected with an HDMI cable for the HDCP handshake to occur.  When you switch off either device, the handshake is broken and no communication will occur.

Use analog or fiber optic connections and then it should work the way you want it do.  HDMI is a convience and a curse.

---

### Post by efflandt on 2013-01-03
I have seen something similar mentioned on a Raspberry Pi forum ($35 arm computer on credit card size board that runs Debian wheezy called Raspbian), which I think had an HDMI receiver in the line between the computer and Samsung TV.  It may have something to do with CEC [http://en.wikipedia.org/wiki/Consumer_Electronics_Control#CEC](http://en.wikipedia.org/wiki/Consumer_Electronics_Control#CEC) which can send control signals over HDMI for on/off, TV or other device remote buttons, etc.

When he would switch to a different input, the screen was blanked out when he would try to switch back. He got around that when not running XBMC by disabling CEC in Raspbian's /boot/config.txt, but not sure how CEC is implemented Ubuntu or if the receiver is not passing on that info when your TV comes back on or that input is selected.

I don't have that issue with my several year old LG HDTV, switching inputs with 64-bit Ubuntu 12.04 and 1 or 2 Raspberry Pi connected directly to different inputs.  Even if I boot with the TV off each OS recognizes that it is connected to a 1080p display.  But all the TV's remote can do through Simplink CEC in XBMC is scroll and select, play, pause, stop, etc. (no Back or Home buttons, so I still need a mouse).

---

### Post by Digitaltomj on 2013-01-04
Thank you for your replies, I do know that hdmi cables can communicate devices power states, but that is hardly my problem.

 I am looking for a way within Ubuntu to just set the monitor and resolution and keep it that way no matter what other monitor is plugged into it afterwards...

It seems to me like this should be either a setting in the main UI itself or just a simple command in terminal...I mean there has to be a command that sets the display and monitor...and there has to be a way to set that as the default display permanently too. 

Im still pretty new to Ubuntu and finding commands for me is a little hard.

---

### Post by Digitaltomj on 2013-01-04
> **slickymaster said:**
> I don't think that there's a good solution to your case, but you can take a look at this [post]("http://ubuntuforums.org/showpost.php?p=10410332&postcount=4") and this [one]("http://ubuntuforums.org/showpost.php?p=10432877&postcount=5"). Try to see if it works for you.

These may be what I am looking for, i will have to try them out and see, thank you.

---

### Post by slickymaster on 2013-01-04
Did you ever get to see some of the posts I mentioned in my previous post?

I'll post them again, anyway:
[http://ubuntuforums.org/showpost.php?p=10410332&postcount=4](http://ubuntuforums.org/showpost.php?p=10410332&postcount=4)
[http://ubuntuforums.org/showpost.php?p=10432877&postcount=5](http://ubuntuforums.org/showpost.php?p=10432877&postcount=5)

---

### Post by slickymaster on 2013-01-04
> **Digitaltomj said:**
> These may be what I am looking for, i will have to try them out and see, thank you.

Ups. My bad. Didn´t notice you already mentioned them.

---

### Post by Digitaltomj on 2013-01-12
> **slickymaster said:**
> Did you ever get to see some of the posts I mentioned in my previous post?

I'll post them again, anyway:
[http://ubuntuforums.org/showpost.php?p=10410332&postcount=4](http://ubuntuforums.org/showpost.php?p=10410332&postcount=4)
[http://ubuntuforums.org/showpost.php?p=10432877&postcount=5](http://ubuntuforums.org/showpost.php?p=10432877&postcount=5)

So I tried theses and upon reboot my comp asked me without a UI (terminal style) for my username and password. I have my computer setup to not require a password on login so I thought this was odd, I then entered in the username and password correctly and it said it was incorrect, I even tried to leave them blank and just press enter but no it wouldnt log me on...so I took out my live cd and removed the xorg.conf file that way but yeah I'm now back to square 1. :(

---

