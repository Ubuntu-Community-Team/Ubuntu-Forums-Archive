---
title: "Logitech K400R keyboard w/Intergrated TouchPad is not recognised"
date: 2013-02-04
forum: General Help
---

### Post by RJLacroix on 2013-02-04
I've tried installing the synaptic TouchPad Manager, but it just crashes when I try to start it up. KBuntu 12.04 LTS refuses to recognize the the integrated keyboard TouchPad as anything other than a Mouse.
Is this a Logitech issue? Or am I just trying to use incorrect drivers?
Any suggestions would be appreciated.

Thanks,
RJLacroix
:-({|=

---

### Post by Mark Phelps on 2013-02-04
You could try the site listed below: 

[http://www.hidpoint.com/hidpoint/overview/overview.html]("http://www.hidpoint.com/hidpoint/overview/overview.html")

---

### Post by dave2001 on 2013-04-03
I've been looking for a solution to this, thanks Phelps, I'll give it a try.

---

### Post by dave2001 on 2013-04-03
took a look, but my keyboard (the logitech k400) is not listed as supported. Also the latest version of ubuntu supported is 10.10. I think it must be a dead project.

---

### Post by CaptainMark on 2013-04-03
I'm using the K400 now and it works fine with both my desktop (Ubuntu 12.10) and my laptop (Ubuntu 12.04) so there must be some other evil at work here,

---

### Post by dave2001 on 2013-04-11
Indeed Cap'n. Silly me, I tried the keyboard first with my old 11.04 system and neglected to try with my 12.04 system. My K400r keyboard works just fine outa the box with 12.04.

---

### Post by oooh on 2013-10-26
uname -a
Linux ----XS35 3.5.0-42-generic #65-Ubuntu SMP Tue Oct 1 21:38:59 UTC 2013 i686 i686 i686 GNU/Linux
k400 working perfect
all gestures working fine
did not have to do anything clever to make it work 

NOTE :
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
NAME="Ubuntu"
VERSION="12.10, Quantal Quetzal"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu quantal (12.10)"
VERSION_ID="12.10"

---

### Post by pbrentlinger on 2014-02-26
I was having issues with this on lubuntu.  The first thing that one can try is to power the k400r off and back on, this may force a repairing of the device with the logitech unifying receiver.  If that doesn't work you can check out [https://wiki.archlinux.org/index.php/Logitech_Unifying_Receiver](https://wiki.archlinux.org/index.php/Logitech_Unifying_Receiver) where they have a few links to various utilities you can use to unpair and repair the device to the reciever.  The nice thing about these apps is that they can also let you add additional logitech devices to the unified reciever if you have such a need.  I personally am using [http://pwr.github.io/Solaar/](http://pwr.github.io/Solaar/)

---

### Post by dan92 on 2014-05-05
Quick and easy solution if you have a Windows machine: Install the Logitech software, pair all of your devices with the receiver on your windows machine, then they will remember each other when you move them to Linux and everybody's happy :)

---

