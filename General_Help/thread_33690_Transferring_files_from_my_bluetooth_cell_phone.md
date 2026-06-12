---
title: "Transferring files from my bluetooth cell phone"
date: 2005-05-11
forum: General Help
---

### Post by derrick1985 on 2005-05-11
Hey all

I finally got my computer to recognize my Motorola CEllphone that has bluetooth in Gnome-bluetooth-manager, but now I can't figure out how to get the files off the cell phone.

It's a camera phone, and I want to be able to download the pictures/videos off the phone, but i'm stuck on how to in linux.

Any help greatly appreciated.

---

### Post by derrick1985 on 2005-05-12
anyone?

---

### Post by ltmon on 2005-05-12
You will have to install the gnome-bluetooth package, which will install as a dependency bluez-utils.  If you are on kde you will want to use kde-bluetooth instead, which is not in the repository, but do a search in these forums and you'll find  a wiki page which has ubuntu packages for it.

Bluez is the backend stuff, wheras gnome-bluetooth should supply a pretty frontend.

A good quick example of setting up bluez is in the kde-bluetooth docs (just ignore the kde specific parts if you are using gnome).

<a href="http://docs.kde.org/en/HEAD/kdeextragear-3/kdebluetooth/installation.setup.html">here</a>

The document they are talking about is /etc/bluetooth/hcid.conf

The pin helper is the key part for you:

pin_helper /usr/local/lib/kdebluetooth/kbluepin;

To not use the kbluepin you will need to replace this with something else.  Any program which simply echos a pin number is fine.

> nano /home/mylogin/bluepin.sh

and type

#!/bin/bash
echo 1234 <---- this is your pin

Save this and

> chmod +x bluepin.sh

then back to hcid.conf

pin_helper = /home/mylogin/bluepin.sh


Then try discovering your computer from your phone.  Your phone should prompt you for a pin.  Use the one matching the pin in the file you created.

Then try running one of the gnome-bluetooth programs (sorry I'm not familiar with these, I use kde-bluetooth).  Something along the lines of "OBEX file transfer" is what you are looking for.  You might try simply sending a file from your phone to your computer and seeing what pops up.  Can any gnome-bluetooth users chime in here???


Sorry for the rushed (incoherent) reply, but I haven't got any time.  I'll try to write a proper howto later on.

Cheers,

L.

---

### Post by derrick1985 on 2005-05-12
[QUOTE=ltmon]You will have to install the gnome-bluetooth package, which will install as a dependency bluez-utils.  If you are on kde you will want to use kde-bluetooth instead, which is not in the repository, but do a search in these forums and you'll find  a wiki page which has ubuntu packages for it.

Bluez is the backend stuff, wheras gnome-bluetooth should supply a pretty frontend.

A good quick example of setting up bluez is in the kde-bluetooth docs (just ignore the kde specific parts if you are using gnome).

<a href="http://docs.kde.org/en/HEAD/kdeextragear-3/kdebluetooth/installation.setup.html">here</a>

The document they are talking about is /etc/bluetooth/hcid.conf

The pin helper is the key part for you:

pin_helper /usr/local/lib/kdebluetooth/kbluepin;

To not use the kbluepin you will need to replace this with something else.  Any program which simply echos a pin number is fine.

> nano /home/mylogin/bluepin.sh

and type

#!/bin/bash
echo 1234 <---- this is your pin

Save this and

> chmod +x bluepin.sh

then back to hcid.conf

pin_helper = /home/mylogin/bluepin.sh


Then try discovering your computer from your phone.  Your phone should prompt you for a pin.  Use the one matching the pin in the file you created.

Then try running one of the gnome-bluetooth programs (sorry I'm not familiar with these, I use kde-bluetooth).  Something along the lines of "OBEX file transfer" is what you are looking for.  You might try simply sending a file from your phone to your computer and seeing what pops up.  Can any gnome-bluetooth users chime in here???


Sorry for the rushed (incoherent) reply, but I haven't got any time.  I'll try to write a proper howto later on.

Cheers,

L.[/QUOTE]


No, this is a help.

I might install the KDE utils and give it a try. The gnome one i'm using so far only detects the phone, i can't get obex file transfers at all.

And I don't think there is a way for me to send it from the phone, I only know of going through Windows explorer and doing it that way.

Cheers.

---

### Post by Suicide on 2005-08-09
I've had the same trouble, Gnome Bluetooth Manager detects the phone but my phone wont detect the computer. No resolution so far.

---

### Post by AndrewB on 2005-08-09
Go here do this:

[http://www.ubuntuforums.org/showthread.php?t=34740&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=34740&page=1&pp=10)

more info

[http://ubuntuforums.org/showthread.php?t=43843](http://ubuntuforums.org/showthread.php?t=43843)

My V3 and a usb BT dongle can send files all day long...

ymmv,
Andrew

---

