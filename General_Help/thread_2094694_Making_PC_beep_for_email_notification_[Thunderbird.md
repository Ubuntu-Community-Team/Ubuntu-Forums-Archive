---
title: "Making PC beep for email notification [Thunderbird]"
date: 2012-12-14
forum: General Help
---

### Post by resruta on 2012-12-14
Hi there,

do you know a way to use the internal speaker, which e.g. beeps while initializing the BIOS, as an email notification with Thunderbird?

I'm still on Kubuntu 10.04.

Thanks for your help,
resruta

---

### Post by Habitual on 2012-12-14
Tbird > Edit >  Preferences >

---

### Post by resruta on 2012-12-14
Hi and thank you for your answer.

Deactivating both ckeckboxes as shown on your screenshot does not give me any kind of sound when recieving an email. I indeed have to admit that I do not understand why it should. :D

By the way, ```
printf "\a"
``` does neither return an error nor a sound, so their might be a problem in my configuration in general. However the board beeps while booting, so it should not be a problem with the hardware.

resruta

---

### Post by SeijiSensei on 2012-12-14
You have to *check* the box to make Thunderbird play a sound.

---

### Post by resruta on 2012-12-15
I'm sorry, I misunderstood the picture.
Using "Default system sound for new email" I ain't get any sound at all.
With "Use the following sound file" I get the chosen file playd via my soundcard, but that's not what I want. I want the internal little speaker on the mainboard to beep so that I get notified even if there are headphones plugged in or if my HiFi (which is the only device connected to my soundcard) is in a different channel.

---

### Post by Gillingham on 2012-12-15
Can you get the internal speaker to beep at all?

Rather than using ```
printf "\a"
``` I use a program beep on the command line to access the internal speaker.

Also I forget when ubuntu started to do this but the internal speaker kernel module got blacklisted a while back because too many people were getting nasty beeps during boot up. To check either use lsmod to look for the speaker module
```
lsmod | grep pcspkr
``` 
or look at /etc/modprobe/blacklist.conf and look for a line like
```
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr
```
To get around this following some guide or another I edited rc.local file (which will be run at start up
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#enable pcspeaker kernel module late enough so it works
modprobe pcspkr || true
exit 0

```
 For a one off event you can run
```
sudo modprobe pcspkr || true
```

I can't help with getting thunderbird to beep though.

---

### Post by resruta on 2012-12-15
Hi,

thank you for your suggestion!
I tried to access the speaker with *beep* but that did not work, too.

pcspkr is not blacklisted.

```
$ lsmod | grep pcspkr
pcspkr                  1699  0 

``````
sudo modprobe pcspkr || true
```Of course does not return an error, the module is loaded.

resruta

---

