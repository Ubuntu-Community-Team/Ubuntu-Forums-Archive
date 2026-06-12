---
title: "Receiving files via bluetooth"
date: 2008-04-27
forum: General Help
---

### Post by LonelyTraveler on 2008-04-27
After installing Hardy, I can't receive file via bluetooth from my phone. It just keeps saying sending failed on my phone. My phone is set as trusted on my computer and so is my computer on my phone. Any suggestions?

---

### Post by robertchahine on 2008-04-27
i had something like that.make sure you have installed "gnome-blutooth" from the synaptic package manager

---

### Post by LonelyTraveler on 2008-04-27
Thanks Robert. I did not have it installed, so I installed it. but it still won't work. I just tried my other phone (Samsung Z400) and it worked. Then I send a file from the phone that I'm trying to send to my computer from, to my Samsung Z400 and it worked. So it is only between my computer and my Nokia that it doesn't want to work in Hardy.

---

### Post by andy80 on 2008-04-27
I confirm the problem. After upgrading from Ubuntu 7.10 to Ubuntu 8.04 I cannot send files from my Nokia N73 to my PC anymore.

---

### Post by LonelyTraveler on 2008-04-27
I'm glad I'm not the only one having this problem then. I can browse my phone by click on browse device via the bluetooth icon in the system tray though.

Hopefully this is something that will get resolved soon.

The main thing I'm actually trying to do is to sync files on my phone with files on my computer. Meaning that is a file changes it will merge the two files. I was told that rsync (I'm using grsync = GUI for rsync) can do that, but at this stage it only sends it one way, and when it sends it to the phone the phone doesn't recognize the files.

---

### Post by gds on 2008-04-27
I've been having exactly the same problem: the upgrade from 7.10 to 8.05 broke bluetooth file receiving.

Some research indicates this may be a bug in bluez-utils 3.26. Installing the debian sid version of 3.30 fixed this problem for me (but broke my rfcomm bindings for some reason. I guess I should build from source, and I'll do that when I get a chance).

---

### Post by LonelyTraveler on 2008-04-27
> **gds said:**
> Installing the debian sid version of 3.30 fixed this problem.

I installed 3.30 from [this]("http://packages.ccux-linux.de/index.php?pdetail=6242") website. Is this the right one? Because it is not making a difference.

---

### Post by gds on 2008-04-27
Hi LonelyTraveler,

That's the right version number, but that build is for ccux-linux, not Debian.

The version I used is downloadable from [here]("http://packages.debian.org/unstable/admin/bluez-utils"). I also installed the corresponding libbluetooth2 package (you'll find a link on that page, too, under "similar packages").

I removed it, since I need rfcomm working more than I need obex-push, but it seemed to work for file transfer. I'd be interested to hear if it does the trick for you.

---

### Post by LonelyTraveler on 2008-04-27
Thanks gds. I'll check this out tomorrow. My mind is busy going to sleep. Late here.

---

### Post by thomasf on 2008-04-28
I reported similar problem here: [http://ubuntuforums.org/showthread.php?t=771460](http://ubuntuforums.org/showthread.php?t=771460)

ohhh...I need to get rfcomm working.

---

### Post by thomasf on 2008-04-28
OK, bluez-utils 3.3 from [http://packages.debian.org/sid/i386/bluez-utils/download](http://packages.debian.org/sid/i386/bluez-utils/download) helped me! OBEX and data transmission using rfcomm are working OK. Thx gds!

---

### Post by gds on 2008-04-28
So rfcomm works too? Great! 

I see this bug was reported [reported]("https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/211252") a while ago.

---

### Post by LonelyTraveler on 2008-04-29
Hi gds,

I did what you said and installed both packages (or at least tried to). It worked after bluetooth-utils but I figured I'd install the lib too. Big mistake! I don't know how this could have happened, but I did something that cause nautilus and evolution to get uninstalled. I didn't feel like stumbling accross other things thats missing so as this was a new install I decided to just redo my machine and in doing that removing my Windows partition and installing windows in VirtualBox. So now after formatting I only installed bluetooth-utils and now its all working fine. But I still want to figure out why I can't write to my phone when it is mounted.

Thanks for the help.

---

### Post by gds on 2008-04-30
Hi LonelyTraveler,

Oops, that sounds pretty bad! I don't know what went wrong, but tonnes and tonnes of stuff depends on libbluetooth2, so if you somehow tried to remove it (prior to installing the debian one, for instance) then all hell would break loose.

Installing the package "ubuntu-desktop" should restore the missing packages if that's what happened (I know, you reinstalled, but in case anyone else reading had this happen...)

I'm glad to hear it's working for you. After thomasf's posting I tried installing bluez-utils from sid again, and I got the same problem. Obex works, but serial services are broken (it's marked stopped in bluetooth preferences, and clicking on the checkbox to activate it has no effect). Trying to configure it manually in /etc/bluetooth/rfcomm got me the device but it wouldn't talk to my phone. Since I *need* this (that's how I'm online right now), I have reverted to the Hardy packages, and I'll have to live without obex until it's fixed.

It's annoying though, because I used to use [http://code.google.com/p/amora/](http://code.google.com/p/amora/) for presentations, and that fails in Hardy too (but not with the debian packages).

*sigh*. I had everything working so nicely in Gutsy. :-(

Perhaps someone with working rfcomm connections could post a configuration?

---

### Post by thomasf on 2008-04-30
I use rfcomm but in my own Java application which works as a Bluetooth server for cell phone. It was impossible with Ubuntu's bluez-utils. I'm sorry if I misled you, gds.

---

### Post by gds on 2008-04-30
No problem thomasf, actually I'm glad to hear that it's not something specific to my setup; I reckon that makes it more likely that a compatible build of 3.30 will fix the problems.

---

### Post by LonelyTraveler on 2008-05-01
Thanks for the tip gds. I will keep that it mind if something like that happens again.

---

### Post by comradekingu on 2008-07-07
I followed [this]("http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu") guide.

PC-> mobile works, but the other way around doesnt on nokias.

However if you leftclick the bluetooth-icon you can select browse devices. (You will even get access to the C: (aswell as E: )) From there you can transfer files from the mobile (and the other way around)

Its just a quick fix, but it works. Bluetooth isnt bug-free, but i expect this will be better in the future.

Also, it helps to authenticate from both the machine and the mobile end.

PC: Bluetooth-->Preferences--> entrust

Nokia: Bluetooth--> (left menu) "connected devices"--> authorize from the menu.


Hope this helps someone, it does the job for me.

---

