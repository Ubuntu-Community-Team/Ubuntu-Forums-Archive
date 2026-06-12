---
title: "bluetooth problems"
date: 2007-11-24
forum: General Help
---

### Post by Kymus on 2007-11-24
I'm looking to use my Motorola HT820 Stereo Headset, but when I try pairing it with my Motorola PC850 bluetooth adapter, I get a wonderful error

> **"obex://[00:07:a4:f2:99:55]" is not a valid location.**
Please check the spelling and try again.

I did some looking on the forums to see if anyone else has tried using this headset and I was linked to [this]("http://bluetooth-alsa.sourceforge.net/build.html") site. I followed the directions:

> cvs -d:pserver:anonymous@sbc.cvs.sourceforge.net:/cvsroot/sbc login 
cvs -d:pserver:anonymous@sbc.cvs.sourceforge.net:/cvsroot/sbc co sbc
cd sbc
./bootstrap

at this point, I get errors:

> ./bootstrap: 7: aclocal: not found
./bootstrap: 7: glibtoolize: not found


This of course throws a wrench into things, and I can not complete this task.

I'm just looking to use this with Skype, Amarok, and Rosetta Stone language software (in wine). 

suggestions?

---

### Post by Kymus on 2007-11-25
bump

---

### Post by socalsurf2k on 2007-11-26
Hi,

I had the same problem on 7.10, after installing these packages
libbtctl4
libopenobex1
gnome-vfs-obexftp
bluez-btsco

I can pair the headset (plantronics voyager 510) and see it as an audio device in the bluetooth manager.

Next up is getting Ekiga recognize it as an audio device.
In Gentoo it was with btsco...

Cheers,
Marco

---

### Post by ukripper on 2007-11-26
it doesn't pair I have tried sevral devices all same. 
this may help : [http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/](http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/)

---

### Post by Lord C on 2007-11-26
> **Kymus said:**
> "obex://[00:07:a4:f2:99:55]" is not a valid location.
Please check the spelling and try again.

Okay, if you **sudo apt-get install gnome-vfs-obexftp**

The bluetooth applet should work fine :)

Let me know otherwise.

---

### Post by Kymus on 2007-11-27
well, the installation went fine. I then turned the headset on and prepared it for pairing, told the BT device manager to pair with the headset and then I was prompted for a passkey of course. I put it in and it spits more errors at me (of course):

> **Couldn't display "obex://[00:07:a4:f2:99:55]"**
Check if the service is available.

---

### Post by ukripper on 2007-11-27
> **Lord C said:**
> Okay, if you **sudo apt-get install gnome-vfs-obexftp**

The bluetooth applet should work fine :)

Let me know otherwise.

Thanks mate. works great!

---

### Post by Kymus on 2007-12-04
bump.

---

### Post by ukripper on 2007-12-04
> **Kymus said:**
> bump.

Folow Lord C instructions works great with bluetooth applet

---

### Post by Kymus on 2007-12-04
> **ukripper said:**
> Folow Lord C instructions works great with bluetooth applet

tried that

> **Kymus said:**
> well, the installation went fine. I then turned the headset on and prepared it for pairing, told the BT device manager to pair with the headset and then I was prompted for a passkey of course. I put it in and it spits more errors at me (of course):
[B]
Couldn't display "obex://[00:07:a4:f2:99:55]"
Check if the service is available.[/B]



---

### Post by Zuppa on 2007-12-04
> **Kymus said:**
> tried that

Hi all! 
I have exactly the same problem of Kymus. I also tried to connect several different mobile phones, and always get the same obex:// message.

Of course I also tried the solution proposed by Lord C, but unfortunately it didn't work :(

Thank you if you can help me!

Zuppa

---

### Post by alexandersk on 2007-12-06
I have the exact same problem.

---

### Post by glendavee on 2007-12-07
I'm having same problems as Kymus, trying to pair with a Motorola V3i phone and a HP Pocket PC. Initially got the "obex is not a valid location" error, then I installed obex as per Lord C, and went to the "check if the service is available" error message.

---

### Post by glendavee on 2007-12-07
Think I've cracked it. Answer was to install obextool, which I got using Synaptic. Still got a couple of error messages, but I have been able to pair with Motorola V3i phone and browse the files.

---

### Post by Kymus on 2007-12-07
I'll try that out and see how it works for me, thanks!

---

### Post by Kymus on 2007-12-11
I am unfortunately still having the same issue, even after installing obextool

> **Couldn't display "obex://[00:07:a4:f2:99:55]".**
Check if the service is available.

---

### Post by Chemist69 on 2008-01-01
Hi,
I have exactly the same problem. I tried all of the above, but still get the obex message.
I am trying to pair with a Fujitsu Siemens Pocket Loox N560.

---

### Post by Chemist69 on 2008-01-01
Hi again,
after some more googling I now think that is has to do with the mobile device itself which does not support ftp transfer (the service which is reported to be missing in the obex error). It seems to have something to do with the available bluetooth stack on the device. My hopes are now down that this can be solved.

---

### Post by epitaph123 on 2008-01-02
Lord C 's sudjestion worked great, I can now pair with the heatset, but when you try to get audio service started there is a new error:

Couldn't display "obex://[00:07:a4:f2:99:55]"
Check if the service is available.

---

### Post by shug33 on 2008-01-02
I, too, have had the exact same problems.  Using Plantronics PLT 510.

Lord C solution got the pairing, but could not complete it until installed obextool.  Now the earpiece shows in Bluetooth preferences, and I think it is connected.  But, there is still no sound to the earpiece.

How can one determine if the soundcard is sending thru the bluetooth connection, or direct it there?

---

### Post by claus70 on 2008-01-12
Hello.
I had the same problem when I tried to browse my Sony Ericsson K800i files. The phone was paired but the "couldn't display obex..." error appeared all of a sudden and I couldn't get into the phone. It worked before, like some of you said.
I've managed to make it work again disconnecting the device in "Preferences", under "Bonded devices" and connecting it again. I guess you must disconnect the device like that every time, instead of simply pulling out the bluetooth adapter from the USB slot like I did before.
Not sure if this is the sollution to your problems but it solved mine.
Cheers :)

---

### Post by pkg1313 on 2008-01-16
installing obextool from the synaptic solved my problem (I was getting the same obex invalid location...)

---

### Post by alex_mayorga on 2008-01-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/148712](https://bugs.launchpad.net/ubuntu/+bug/148712) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You might like to check whether this bug [https://bugs.launchpad.net/ubuntu/+bug/148712](https://bugs.launchpad.net/ubuntu/+bug/148712) is what is causing us trouble.

---

### Post by Kymus on 2008-01-20
thanks for the link! I think it probably is a bug. :(

---

### Post by rio-paco on 2008-01-24
I had, or actually I am still having, the same problems with my Sony Ericsson W800i. However rebooting the phone helps! I am very much a newbie when it comes to bluetooth but in my case it seems the bluetooth software in the phone is causing the problem.

---

### Post by TRANQU111TY on 2008-02-18
> **Lord C said:**
> Okay, if you **sudo apt-get install gnome-vfs-obexftp**

The bluetooth applet should work fine :)

Let me know otherwise.

How do I thank you :)

---

### Post by MES5464 on 2008-05-09
Installing gnome-vfs-obexftp does not work.

Lenovo X60
Ubuntu 8.04
Motorola HT820

---

### Post by RubberCrutch on 2008-05-12
Hi all, 

The BT device manager recognizes my headset but always fails to connect. I get the following error: [b]Couldn't display "obex://[00:11:B1:B0:DC:6B]/". Error: Host down
Please select another viewer and try again[/b]. I've installed all of the packages that were suggested previous to this post and nothing seems to solve the problem. Any further ideas?

-RC

---

### Post by illbashu on 2008-05-21
^ i have the same prob! :(

---

### Post by Son of Silas on 2008-06-19
> The BT device manager recognizes my headset but always fails to connect. I get the following error: Couldn't display "obex://[00:11:B1:B0C:6B]/". Error: Host down
Please select another viewer and try again. I've installed all of the packages that were suggested previous to this post and nothing seems to solve the problem. Any further ideas?


Same problem here with a Dell BH200 headset and a dell inspiron 1525 running Hardy.

---

