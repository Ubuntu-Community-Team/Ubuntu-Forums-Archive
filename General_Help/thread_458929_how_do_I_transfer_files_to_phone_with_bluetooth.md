---
title: "how do I transfer files to phone with bluetooth?"
date: 2007-05-30
forum: General Help
---

### Post by unabatedshagie on 2007-05-30
I have a nokia N73 and am having problems sending files between it and my computer with bluetooth.

When I search for devices with my phone I can see my computer but can't send files from my phone to the computer.

However I am unable to "see" my phone with the computer.

I have googled for lots of guides and tried to follow them but I just can't seem to get it to work.

Does anyone have a full proof way of getting my bluetooth to work?

---

### Post by Cresho on 2007-05-30
I currently use a bluetooth on my laptop.  It has windows xp with a targus bluetooth usb on my laptop.  I decided to pull the usb and use it on my pc with the ubuntu.  If you look at the add and remove program, there are a few programs available for your pc.  Type "bluetooth" in the search and allow to search all available software.

NOW  THIS IS IMPORTANT!

Verizon is known for modifying the phone to dissallow file trasnfers.  The protocol is obex  ( [http://en.wikipedia.org/wiki/OBEX](http://en.wikipedia.org/wiki/OBEX) ).  In my home, we use a different carrier which does not purposely disable the obex which allowes us to grab the pictures, midi, homemade mp3 audio, gif animations, personal data.  I'm putting this out because I read alot of people having issues with trying to get the data out of the phone when there is nothing absolutely wrong with the hardware.  It is the user to blame for this for purchasing a product who likes to royally screw them.

When configuring, you need to pair the phone first and then allow obex protocol or set it up.

---

### Post by Cresho on 2007-05-30
Here is an interesting post.  IT works for me.

[http://ubuntuforums.org/showthread.php?t=94713&highlight=Bluetooth+obex](http://ubuntuforums.org/showthread.php?t=94713&highlight=Bluetooth+obex)

here is a better one.  I recommend the part one section

[http://ubuntuforums.org/showthread.php?t=75978&highlight=Browse+folders+over+Bluetooth](http://ubuntuforums.org/showthread.php?t=75978&highlight=Browse+folders+over+Bluetooth)


this is what really worked for me.

in add/remove programs, i installed the "bluetooth obex client"
and also in synaptic, I installed konqueror

last but not least, then for pin problems and correction, install this and reboot.

sudo aptitude install bluez-passkey-gnome

Now in internet->konqueror when it starts up, choose "network" and bluetooth.  stay in this area as it is looking for your phone.  after if it finds it, you can access it.  If not, it will put your phone device address up with a white sheet which means it is not viewable because most likely your phone carrier disabled it so you can't have access to your files.  If it is viewable, you can just drag and drop anywhere.

---

### Post by unabatedshagie on 2007-05-31
I've tried following both those with no success.

I would rather not use konqueror if I could avoid it but even that's not working, my phone seems to appear (well I can see the MAC address) but when I click on it I'm asked what I want to do with the file.

---

### Post by Cresho on 2007-05-31
I get the same issue with the "What do you want to do with the file" but what you are looking for is a hardisk icon.  This lets you view it like a hardrive.  when you click on it, it will take a bit and after, it will ask for pairing.  you pair both and now you have access to the hardrive.  If not, then your phone does not support the obex ftp and this issue will be more related to the phone company not allowing the obex to work properly.

If no Hardisk Icon is available, your phone will not work.  If you see obex push, your phone allowes recieving of files.  If you see no obex ftp nor obex push, you have  cellphone problem related to cellphone company purpously disabling or it does not support obex push.  If you cannot send files from the cellphone, It is purpously disabled or it does not support obex send.

---

