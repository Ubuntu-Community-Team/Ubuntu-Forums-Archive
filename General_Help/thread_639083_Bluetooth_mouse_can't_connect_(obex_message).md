---
title: "Bluetooth mouse can't connect (obex message)"
date: 2007-12-12
forum: General Help
---

### Post by aum11 on 2007-12-12
I am trying to connect a bluetooth mouse..
I have right clicked on the bluetooth icon on right corner and clicked on "browse device".

It finds the mouse.
 
Then highlight the mouse device, and then click connect.

Then get this message:    Couldn't display "obex://[00:07:61:94:36:e6]".

                                          Check if the service is available.

I have checked all the posts and cannot find a solution...see others have the same problem and they get no responses.

Have also tried Blueman also with no success.

Is it a system bug, or has anyone got their bluetooth mouse working?

Have tried it another laptop with same results.

Thanks for Your help.

---

### Post by NilsE on 2007-12-12
Yup, they work just fine but need a little coaxing. The error you are getting is simply because OBEX if not for a mouse but for file transfer.

First make sure gnome-bluetooth and bluez-gnome are installed in Synaptic. Also see if the mouse shows up in bluetooth preferences and mark it trusted. It may not show up until after you do the following.

Then in a terminal:

To get address of mouse: 

sudo hidd --search

To connect:   

sudo hidd --connect 00:07:61:89:32:b9 (change that to your address)

Change this line in /et/default/bluetooth

HIDD_OPTIONS="--connect 00:07:61:89:32:b9 --server" (change that to your address)

may also need to change HIDD_ENABLED=0 line to 1

---

### Post by linuxwizard on 2007-12-12
Look at the bottom of this page in Troubleshooting

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by aum11 on 2007-12-12
Thanks linuxwizard,

as I followed that pathway you suggested I found the following instuction which resolved all of the troubles:

Right-click on the bluetooth applet and select "Preferences", go to the "Services" tab, left-click on "Input service", click the "Add" button, select your input device & connect.

---

### Post by linuxwizard on 2007-12-12
You're Welcome That's great that link helped you and now have it all setup and working.

---

### Post by lenticular on 2007-12-12
I have a Logitech diNovo keyboard which was already listed as a service in the bluetooth applet.  After a period of inactivity it drops.  And will not reconnect.  When this happens it either does not show up as a device in the bluetooth applet "Browse Device" screen, or, if it does, trying to connect to it gives the obex error message mentioned earlier.  Trying to connect to it via "sudo hidd --connect 00:07:61:3C:3D:A2" yields a connection refused error.

I can stop and start the bluetooth daemon and the keyboard works again.

This only started when I went from Feisty to Gutsy.

-John

---

### Post by NilsE on 2007-12-14
> **lenticular said:**
> I have a Logitech diNovo keyboard which was already listed as a service in the bluetooth applet.  After a period of inactivity it drops.  And will not reconnect.  When this happens it either does not show up as a device in the bluetooth applet "Browse Device" screen, or, if it does, trying to connect to it gives the obex error message mentioned earlier.  Trying to connect to it via "sudo hidd --connect 00:07:61:3C:3D:A2" yields a connection refused error.

I can stop and start the bluetooth daemon and the keyboard works again.

This only started when I went from Feisty to Gutsy.

-John
Make sure that in preferences the device is set as trusted and it should work.

Also, see if there is a firmware update for your systems  bluetooth module.  I had the same problem with a Logitech mouse and found a firmware update on the manufacturers (Toshiba) web site and it solved the problem.

---

### Post by lenticular on 2007-12-16
Whether I have the keyboard and mouse set as trusted or not, they both time out after some period of inactivity.  When this happens, BT Manager shows them as still being connected.  When they are not trusted, I can disconnect them, wiggle the mouse or hit a key, and BT Manager  asks if I want to conect them.  When they are trusted, I'm never asked about them one way or another.

It is odd the BT mgr sees them as connected when they don't work.

I'm using a Logitech DiNovo keyboard and mouse combo with a Logitech BT dongle.  The hardware is crap, for sure ( browse the Logitech BT forum [http://forums.logitech.com/logitech/board?board.id=bluetooth_mice](http://forums.logitech.com/logitech/board?board.id=bluetooth_mice) ) but I had them working fine under Feisty.

-John

---

### Post by thecure on 2008-02-26
> **aum11 said:**
> Thanks linuxwizard,

as I followed that pathway you suggested I found the following instuction which resolved all of the troubles:

Right-click on the bluetooth applet and select "Preferences", go to the "Services" tab, left-click on "Input service", click the "Add" button, select your input device & connect.

Thank you. That was so simple and here I was upset that hidd was dropped from Hardy.

---

