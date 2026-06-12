---
title: "Ubuntu Lies about supporting palm os"
date: 2007-06-30
forum: General Help
---

### Post by jrattner on 2007-06-30
Note: The title of this post may not be exactly true, but maybe it will get some knowledgeable person's attention.

Currently I have a Treo 700 smartphone which uses the Palm OS software.  Ever since I've had Ubuntu I've NEVER been able to get it to sync with any reliability with the system.  By Sync I mean synchronization of calendar, contacts, to-do and things like that whether it be via bluetooth or the USB cable.  Every time I've ever asked for support in this forum, people just point round to old obsolete or irrelevant information which ultimately hinders my ability to syncronize even more.

Does anyone have any RELIABLE information on how to EFFICIENTLY synchronize a Palm Treo 700p with ubuntu whether it be via blueetooth or USB?

---

### Post by tgm4883 on 2007-06-30
Not the 700p, but my 650p syncs perfectly over bluetooth to evolution on feisty 64-bit

Here is the guide I followed.

:EDIT:

Forgot the guide [http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)

---

### Post by jrattner on 2007-06-30
What did you follow to get your it working?

---

### Post by tgm4883 on 2007-06-30
lol, I thought I linked to it.

Here it is, I'll update my other post too

[http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)

---

### Post by jrattner on 2007-06-30
Yep, no success utilizing that tutorial...I appreciate it anyway.

---

### Post by tgm4883 on 2007-06-30
What seems to be the problem with the syncing?

---

### Post by jrattner on 2007-06-30
The Howto works for me, and the Treo 700p will connect and claims that its synchronizing and will exit saying synchronization complete, but then in Evolution all i see is my MEMOs synchronized...and everything else remains blank.  How did you set up gnome-pilot to work with the settings from this howto? Is there anything im missing?

---

### Post by tgm4883 on 2007-06-30
I assume you went into jpilot and told it to sync more than just your memos right?

---

### Post by jrattner on 2007-06-30
Yep, but out of sheer luck, somehow I've fixed the problem and been able to get it to sync consistently.  I will be writing a guide in days to go regarding how to do this using bluetooth, and USB.

---

### Post by shaft350x on 2007-09-15
I'll have to check this out later, I've been wanting to sync via Bluetooth since I lose my USB cable.  I'll let you all know if it works for me as well.

---

### Post by expatal on 2007-09-16
> **jrattner said:**
> Yep, but out of sheer luck, somehow I've fixed the problem and been able to get it to sync consistently.  I will be writing a guide in days to go regarding how to do this using bluetooth, and USB.

I have been having similar problems with gnome-pilot (2.0.15) and Evolution (2.10.1) running under Feisty (7.04). Syncing on the EMemos conduit just doesn't work, both Evolution and the PDA (Palm Tungsten E2 running PalmOS 5.4.7) remain completely oblivious of changes made on the other side. Initial copy from PDA to Evolution worked OK on One-time action and that was it. I'd be *very* interested in your solution... I'm struggling to liberate myself from the well-known industry-"standard" OS, and this is virtually my last sticking-point.

Thanks in advance.

---

### Post by jrattner on 2007-12-27
This is a step-by-step howto intended to get the Treo 700p to sync with Ubuntu via bluetooth.  Before attempting to utilize this guy, please ensure that you have installed all proper bluetooth software.  If you are running Gutsy and have a bluetooth card, this is most likely already the case.

_**Step 1: Prepare your Ubuntu System**_

Open /etc/default/bluetooth in your text editor of choice
```
gksudo gedit /etc/default/bluetooth
```
Then add the following lines to the file and then save:
> 
DUND_ENABLED=1
DUND_OPTIONS="--listen --persist --msdun call treo

Note: If you are using Feisty or Gutsy you should disable the other services in /etc/bluetooth by setting Autostart = false

Next open /etc/ppp/peers/treo in our text editor of choice
```
gksudo gedit /etc/ppp/peers/treo
```
Then, add the following lines to the file and then save:
> 
115200
192.168.1.1:192.168.1.2
local
ms-dns 127.0.0.1
noauth
debug


Note: For some systems, this configuration of addresses may not work.  But for the majority of set-ups, this should work perfectly  Also note that 192.168.1.1 represents the computer, and that 192.168.1.2 represents your Palm Treo 700p in this case. 

After compelting the changes, we next restart the bluetooth daemon using the following command:
```
sudo /etc/init.d/bluetooth restart
```

_**Step 2: Prepare your Palm Treo 700p**_

Start by turning bluetooth on the Palm Treo 700p to "On".

From the main screen, hit the menu button (Found in the bottom right hand corner on Verizon atleast) and proceed to:

"System Preferences" and then to --> "Connections"

From the "Connections" menu, first click the "New" buttonand enter the following information:

> 
**Name:** Ubuntu
**Connect to: ** PC
**Via:** Bluetooth
**Device: ** Click the button that says "Tap to Find" 


Note: It is important to make sure that bluetooth is on for both the computer and the phone in which you intend to sync.  Your Palm Treo 700p should find your computer.

Next, click "Details" and make sure the following settings are correct:
> 
**Speed:** 115,200 bps
**Flow Control:** Automatic



Now, with that out of the way, we will create the new network:

Once again, from the main screen, hit the menu button (Found in the bottom right hand corner on Verizon atleast) and proceed to:

"System Preferences" and then to --> "Network"

Once the "Network" screen opens, click the menu button on the bottom right of the phone again, and click then click "New" and enter in the following information:

> 
**Service:** Ubuntu
**Connection:** Ubuntu


Note:  For the connection, select the connection you already created named ubuntu.  Also note it is ESSENTIAL that you leave the Username and Password blank or untouched.

Next, click "Details" and make sure the following settings are correct:
> 
**Timeout:** 3 Minutes


After you have completed this, click "OK" to save the changes, and then "Connect"

_**Step 3: Prepare the HotSync application on your Palm Treo 700**_

From "Home" choose the "HotSync" icon.  Once the screen loads, hit the menu button, and proceed first to "Modem Sync Prefs..."

[INDENT]Within the "Modem Sync Preferences" screen, assure that "Network", not "Direct to Modem" is selected and then hit "OK".[/INDENT]

Next hit the menu button again while on the "HotSync" screen, and proceed to "LANSync prefs..."

[INDENT]Within the "LANSync Prefs..." screen choose "LANSync" instead of "Local HotSync" and then hit "OK"[/INDENT]

Next hit the menu button again while on the "HotSync" screen, and proceed to "Primary PC Setup" and make the following changes and then hit "OK":
> 
**Primary PC Name:** *Leave this blank
**Primary PC Address:**192.168.1.1
**Subnet Mask:***Leave this blank


Now, once again hit the menu button while on the "HotSync" screen, and proceed to "Connection"
[INDENT]Select the connection we just created (Named Ubuntu)  and then hit "OK"[/INDENT]

Finally, from the "HotSync" Main screen, choose "Modem" instead of "Local" and they select "Ubuntu" from the list below the HotSync button.

At this point everything should be set up properly, and you should never have to do this part again.

_**Step 4:Testing the setup, and troubleshooting0**_

Now from your computer initiate the following command:
```
pilot-xfer -p net:any -l
```

Now hit the "HotSync" button on your phone, and you should see a bunch of Palm related information flood the open terminal.  If you see this, you were successfull, if you didn't then you may need to reread through this howto.

Now as far as syncing is concerned, if you want to use J-Pilot, or gnome-pilot, make sure you set the connection mode to serial or virtual serial and everything should work perfectly. Also if your using J-Pilot set the serial port to net:any




Troubleshooting:

**1.)  Make sure Bluetooth is on the computer AND Phone are both on.**

2.) Sometimes after syncing with my computer a few times, the "Primary PC Address" somehow changes from 192.168.1.1....If for some reason your bluetooth connection is not working make sure that this address is correct within your Palm Treo 700p.

3.) In Evolution, I had to create a new Calendar named Palm in order for my items to sync properly.  



**Refences:** This guide is fundamentally an oversimpliciation of the guide found at [http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html).

---

### Post by rob.webinator on 2008-01-01
In Step 2, my Treo 700p does not find my computer.  I don't see anything interesting in dmesg.  I followed your setup verbatim and when the palm didn't find the computer, I also set Autostart=false in each /etc/bluetooth/*.service as per a recommendation at [http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)

Any thoughts?

---

### Post by chudder on 2008-01-13
**How to sync a Treo 680 via USB**

I've got my Treo 680 working by going into System> Preferences> Palm Devices (which I believe is the same thing as GnomePilot)

Go to the "Devices" tab and click "Add" and a dialog box will come up.  Name it whatever and then change the device pulldown to "usb:", also change the "Type" to "USB" by clicking the USB radio button.  Then click OK

Then go to the "PDAs" tab and click "Add" and another dialog box will come up.  

If you already are using your Treo click "Get From PDA" and then a window will pop up telling you to press the hotsync button.  Follow this direction.  It will exchange the information the data will be displayed on the dialog box. 

If this is the first time using your Treo then fill in the desired "Owner", "PDA ID", "Name of PDA", and if you want you can change the local folder.  Then click "Send to PDA" and the PDA will have this information.  Click Ok after following the prompts.

Click on Conduits and enable/disable what you wish and how it handles it.  I've noticed the "Syncronize" setting will get you into trouble by duplicating entries in Evolution (which is where the data is stored).  What I find the best is not syncing often but when I do sync I erase all data in Evolution and then sync from the Treo to Evolution.  

There a few things that don't work as nicely as I would like.  If I have multiple entries of the same type, (ie: two mobile numbers or two home numbers for one contact) only one of them gets transfered to Evolution.  I have yet to figure out how to fix this.  Another flaw is the Address categorizing.  If I have a Home address for a contact it still gets filed as a Work address in Evolution.  

Good luck to anyone who tries this!

Chudder

---

### Post by plh on 2008-01-14
.. I would like to ask the same question for a palm Z22, knowing that my problem is actually an inconsistency between addresses (old format, handled by jpilot for instance) and contact DBs (new format, handled by ???)

---

### Post by chudder on 2008-01-14
> **plh said:**
> .. I would like to ask the same question for a palm Z22, knowing that my problem is actually an inconsistency between addresses (old format, handled by jpilot for instance) and contact DBs (new format, handled by ???)

Are you saying that you used to use JPilot and are wondering what program/format is used with the method I described?  If so when you configure the Palm Pilot using PalmOS devices the default program it syncs with is the Evolution mail client.  

Does this answer your question?

---

### Post by plh on 2008-01-14
Not really, since I tried to use evolution but the initial sync fails on a timeout, so the config aborts :-(

BTW, thanks for answering so fast !

---

### Post by chudder on 2008-01-14
> **plh said:**
> Not really, since I tried to use evolution but the initial sync fails on a timeout, so the config aborts :-(

BTW, thanks for answering so fast !

You're saying you have tried what I said and it timed out on you?  Did you make sure that USB was selected on both the radio button and under the Devices drop down menu?  All of which are under the devices tab, it shouldn't tty01 or something like that if you're using a USB cable.  
Have you tried increasing the timout from the default to something higher?  Another option is increasing or decreasing the speed.  I had to experiment a few times when I was in Dapper but in Feisty as long as both USB settings were selected it worked.  

Let me know the results.

Good luck!

---

### Post by plh on 2008-01-14
Yes, I checked this out. The default timeout is more than a minute, so I don't expect anything great from increasing it ! Base speed is 56K, it does not seem to be too much for a USB connection, but I can try to decrease it tomorrow...

Thanks again!

---

### Post by Kokanee-YYZ on 2008-03-07
The problem that I had when using Evolution 2.1.2.1 and Gnome-Pilot 2.0.15 was that sync'ing was inconsistent: it would work most of the times but time-out some times.

I fixed the time-outs by going to System|Preference|Palm OS Devices, selecting my PDA device in the PDAs tab, clicking Edit, and clicking the 'Get from PDA' button.  Once this is successful, I can then sync the device... strange but it works! :confused:

Hope this helps you.

>K<

---

### Post by smithbt5 on 2008-05-14
I am also having a lot of trouble using the Treo 700p with Ubuntu.  I need to sync the Treo with Evolution.  I have tried using the installed gnome-pilot.  I get sporadic usb connections.  Maybe 50 percent of the time I get a connection.  What's worse is it makes a mess of my data.  I get massive duplication or dropped calendar entries, my changes in Evolution don't sync back to the palm, etc.  I seem to be able to get Jpilot to work, but that isn't what I'm looking for.  I am using Hardy.  I have seen a few posts that suggest an entry needs to be added to the /usr/share/gnome-pilot/devices.xml file, but I haven't seen what needs to be added for the 700p.  Any help would be appreciated.

---

### Post by chudder on 2008-05-14
> **smithbt5 said:**
> I am also having a lot of trouble using the Treo 700p with Ubuntu.  I need to sync the Treo with Evolution.  I have tried using the installed gnome-pilot.  I get sporadic usb connections.  Maybe 50 percent of the time I get a connection.  What's worse is it makes a mess of my data.  I get massive duplication or dropped calendar entries, my changes in Evolution don't sync back to the palm, etc.  I seem to be able to get Jpilot to work, but that isn't what I'm looking for.  I am using Hardy.  I have seen a few posts that suggest an entry needs to be added to the /usr/share/gnome-pilot/devices.xml file, but I haven't seen what needs to be added for the 700p.  Any help would be appreciated.

Maybe you've tried this already but have you set the connection to USB?  The default is tty1 or something like that.  Good luck!

---

