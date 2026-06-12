---
title: "Sync a Nokia 6300 with Google Calendar"
date: 2007-12-12
forum: General Help
---

### Post by Aybara on 2007-12-12
I'm looking for a solution to sync my Nokia 6300 calendar and my Google Calendar. I don't need to sync contacts and stuff, just the calendar. What apps should I look at for this task?

---

### Post by roman007 on 2008-01-21
Did you find a sollution? Or does anyone else know a sollution?
I am locking for the same under Kubuntu and could not get it working :(
I tried it with opensync (multisync-gui) with the gnokii-sync module and the syncml-obex-client.
I get the connection to the phone but it does not sync the calendar. For me it seems that it uses the wrong data format or something like this, but I do not get a real error message.

---

### Post by Aybara on 2008-01-21
Never found a solution :-(

---

### Post by CosminGC on 2008-01-22
I would be interesteed too

---

### Post by b20963a2 on 2008-01-22
Did either of yo check out opensync?

[http://www.opensync.org/wiki/6300](http://www.opensync.org/wiki/6300)
[http://wiki.ubuntuusers.de/OpenSync](http://wiki.ubuntuusers.de/OpenSync) (German!)
[http://wiki.ubuntuusers.de/OpenSync/Plugin-GoogleCalendar](http://wiki.ubuntuusers.de/OpenSync/Plugin-GoogleCalendar) (German!)
[http://eikke.com/cellphone-bluetooth-and-reddit-rant/](http://eikke.com/cellphone-bluetooth-and-reddit-rant/)

---

### Post by zordon on 2008-03-12
don't know if it works, but I found [this]("http://www.skybert.nu/cgi-bin/viewpage.py.cgi?computers+linux+syncing_nokia_6300_with_google_calendar") and it looks promising; I am going to check it out as I have 6300 too...

---

### Post by CosminGC on 2008-03-12
it works, I go my nokia 6300 syncing with evolution / google calendar and it's working great

PS: I am on gentoo using verion 0.22 of libopensync libopensync-plugin-gnokii libopensync-plugin-evolution2 libopensync-plugin-google-calendar

:)

---

### Post by steigers on 2008-04-20
**[SIZE="4"]Synchronizing the Nokia 6300 in 64-bit (K)ubuntu 7.10[/SIZE]**

Hello everybody

I've spent ages looking for libopensync-plugin-gnokii in my standard kubuntu distribution and eventually concluded it's not there in the standard repositories for 64-bit.

However, in [http://ubuntuforums.org/showthread.php?t=708769](http://ubuntuforums.org/showthread.php?t=708769) a guy built the library for 64 bit and it works fine for me. Just add 

deb [http://synerger.com/opensync-amd64](http://synerger.com/opensync-amd64) gutsy main

to the repositories (by Adept) and then get the gnokii plugin.

To **synchronize with e.g. google calendar** follow this:

1. get libopensync-plugin-gnokii, libopensync-plugin-google-calendar, multisync0.90, libsyncml0, maybe others

2. Pair ubuntu and the cell phone:
2a. Make sure both sides are visible to eachother: in kbluetooth go to Configuration->Adapters and set the mode to "discoverable", on your cell phone check Settings->Connectivity->Bluetooth->My phone's visibility and that Bluetooth is switched on at all
2b. get the phone address via "hcitool scan"
I'm not sure about the order of the next couple of commands
2c. sudo hcitool cc <address>
2d. hidd --connect <address>
2e. sudo hcitool auth <address> 
I think it was during that process that one has to enter the same number on both sides. When the two sides are paired, the phone will not ask for a passphrase afterwards (where I didn't figure out what to put)

3a. open Multisync-qad
3b. new group (e.g. "google-nokia")
3c. add google-calendar:
<config>
<username>user@gmail.com</username>
<password>blablabla</password>
<url>http://www.google.com/calendar/feeds/***/private/full</url>
</config>
The placeholder *** is a lengthy and cryptic e-mail address named Calendar ID which found in the calendar settings
3d. add gnokii-sync:
<config>
<connection>bluetooth</connection>
<port>the hcitool scan address</port>
<model>6510</model></config>
Yes, 6510 and not 6300!

4. from the terminal type "msynctool --sync <groupname, e.g. google-nokia>"

Please note also that KDE's KitchenSync seems to confuse and also overwrite the bluetooth address of the phone. Didn't work for me.

Hope this short desciption facilitates the synchronization for fellows who have the same setting as I do (kubuntu gutsy 64-bit, google calendar with more than one calendar)

Greetings Sebastian

---

