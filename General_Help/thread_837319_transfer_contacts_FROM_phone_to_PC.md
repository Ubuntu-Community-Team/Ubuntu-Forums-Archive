---
title: "transfer contacts FROM phone to PC"
date: 2008-06-22
forum: General Help
---

### Post by jbb on 2008-06-22
I have read and followed the info from the Guide of 26/04/08 on synching using Evolution.  I tried it and yes it does allow one to synch your cell phone to Evolution.  BUT!  a big but is that I still CANNOT transfer my contact data FROM the cell phone to my PC.  I am due to upgrade my phone and desire to be able to transfer the contact info to my pc  too many to re enter

Yes i have the Nokia disk but just as I've seen on other queries, half my contacts for some unknown reason do not get copied over. This is a pain that gets bigger when u have to boot windows just to get a partial result.

Are there any boffs out there that can advise us all on what other software( if necessary) to download/install  and how to get data tranferred from phone to pc..  I can download pics from phone to pc just using cell pairing and Bluetooth File Sharing but not my contacts


Help anybody please

---

### Post by jbb on 2008-06-24
It would seem that many users have the same problem viz reliable transfer of data from a cell phone to the pc and back.  I have a Nokia 6230I and due to a pending phone upgrade I needed to be able to copy my contacts from my phone to my pc.   I tried the advice given to sync using Evolution.  I could get access only to pictures and related data.   I tried downloading and trying every program that "worked for some one else" till eventually I tried Wammu.
After battling with the configuration I eventually made contact with my cell phone and was able to transfer the required contact and sms data to my pc.
I also found that I needed to use a different program to transfer pictures.
So all I can say to those like me searching for help is to try all the various programs  like Multi-sync ,  Evolution,   Wammu,  bluetooth tools for KDE / Nome  

Thanks to all those who replied to the various posts that I read on this subject.  

I close this post as resolved
:guitar:



:guitar:

---

### Post by clement forums on 2008-07-28
Hi jbb

I've been trying to sync my 6230i phone with Evolution for a long time without success so I'm very interessted on how you did it. Could you provide additional information?

I also tried it with wammu. As I understand it, I also need to use rfcomm. I tried that also but it seams I just can't connect to my phone using either rfcomm or wammu. However, I can very well connect using the gnome bluetooth manager.

So my questions:
1. What are your settings in wammu? (~/.gammurc)
2. Do you use the gnome bluetooth manager / applet to pair your phone?
3. Do you use rfcomm? How to you use it? (command)
4. Any thing else needed to know so I can sync my phone?

Any help is appreciated.
Thank you
clement

---

### Post by jbb on 2008-07-30
please refer to attached screenshots for setting data
Note Unless you delete a pairing  then that pairing remains valid even over many reconnections without needing to re-pair

Hope this helps

---

### Post by jbb on 2008-08-12
Using Ubuntu 8.04 on Aspire 3620 Laptop with Huawei E220 modem and Cellink Bluetooth dongle
Problem is that where Wammu worked A1 on Ubuntu 7.1 linking to my Nokia 6230i cellphone I can't get same to work on Ubuntu 8.04
I've attached screenshots showing my setups   Can anyone offer assistence?

Thanks  John

---

### Post by clement forums on 2008-08-12
Hi jbb

I've managed to sync my Nokia 6230i using wammu. I put the steps into a wiki: [https://help.ubuntu.com/community/syncnokia6230iwammu](https://help.ubuntu.com/community/syncnokia6230iwammu).

I also found this link interessting for syncing the Nokia with Evolution:
[https://help.ubuntu.com/community/NokiaEvolutionBluetoothSyncing](https://help.ubuntu.com/community/NokiaEvolutionBluetoothSyncing)

Unfortunatly neither solution seam to work very well for me. I guess I'll have to wait to buy a new phone and maybe try different approach (e.g. sync using imap / ical).

---

### Post by jbb on 2008-08-13
Hi   Thanks for info   I tried but get error show attached screen shot
ps  I found I needed to include the device no. in the connect statement
Can you advise what went wrong here?

Thanks John

---

### Post by clement forums on 2008-08-13
Hi, don't forget to uncomment your rfcomm.conf file by removing the '#' sign at the begining a line. Your file should look like this:
```
rfcomm0 {
bind yes;
device 00:13:FD:89:EC:61;  # <- change this to match the bluetooth address of your phone
}
```
Hope this help. See also the man page for rfcomm:
```
$ man rfcomm
```

---

### Post by jbb on 2008-08-15
I am still struggling to get Wammu to work onUbuntu 8.04  but here is how to get it to work on Ubuntu 7.1.


Getting Wammu to work on Ubuntu 7.10
1st check you have following files  if not then download/install them
 sudo apt-get install  filename

/gammu_1.13.0-1_i386.deb
/libbluetooth2_3.19-0ubuntu1_i386.deb
/libgammu2_1.13.0-1_i386.deb
/libgammu-common_1.13.0-1_all.deb
/1/libmysqlclient15off_5.0.45-1ubuntu3.3_i386.deb
/libpq5_8.2.6-0ubuntu0.7.10.1_i386.deb
/libwxbase2.6-0_2.6.3.2.1.5ubuntu12_i386.deb
/libwxgtk2.6-0_2.6.3.2.1.5ubuntu12_i386.deb
/mysql-common_5.0.45-1ubuntu3.3_all.deb
/python-gammu_0.22-3_i386.deb
/python-wxgtk2.6_2.6.3.2.1.5ubuntu12_i386.deb
/python-wxversion_2.8.4.0-0ubuntu3_all.deb
/wammu_0.22-1_all.deb

Now go to
	Applications
	Wammu
	Cancel "setup " message that comes up
	Select **"Phone Wizard"**
	Select "**Guided Config**"
	Select "**Bluetoot**h"
	Select "**Nokia Phone"**
	Select "**Nokia FBUS**"
	Select **"Phonet over Bluetooth**"
	Enter **00:12:D1:D4:D3:50**   Your phones Bluetooth address
get this by entering    **hcitool scan**  in a terminal
	Connection test now displays with   Wammu is now testing phon connection
	If youre lucky your phone should now show a "OK to connect" message
	Finish configuring Wammu

You can now retrieve  your Contacts, Calendar info, Messages, Phone Calls and Todos

This works 100% connecting my Nokia 6230I to my Laptop using a USB Bluetooth dongle on Ubuntu 7.10

---

