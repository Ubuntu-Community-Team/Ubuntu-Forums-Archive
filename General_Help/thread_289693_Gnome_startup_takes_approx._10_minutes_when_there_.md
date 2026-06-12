---
title: "Gnome startup takes approx. 10 minutes when there is no network or not configured"
date: 2006-10-31
forum: General Help
---

### Post by NiksaVel on 2006-10-31
Hey all,

I have a new installation of edgy on my laptop and am very happy with it, just finished the last theme touches and all...  

I do have a slight problem ...   started the laptop for the first time at home today and it took like 10 minutes to start gnome after I entered my login/password. In the end I found out that it only has this latency when it is a) not connected to a network (internet?) or b) the network is not configured properly.

As soon as I configured the home network it was back to instant loading. Tried to unplug the cable and re-login and it was taking minutes again....


I was searching through the forums and found out that it might be related to loopback not being initialised after reboot, but I didn't fully understand what needed to be done or even if that was my problem...


thanks for the help!

---

### Post by pillypoon on 2006-10-31
do you have portmap installed?

---

### Post by NiksaVel on 2006-10-31
yes, synaptic shows it as installed

---

### Post by NiksaVel on 2006-11-02
can some1 please help me with this issue??  It's quite of a problem and I am at a loss at what to do... 

gnome loads perfectly if it's connected to a network but it takes up to 10 minutes if I am loading it with no network connection or connected to a different network that it is not configured for...

---

### Post by NiksaVel on 2006-11-02
I tried installed kde-core to see how that would work...  this is getting silly now...

everything works great when connected


when it's with no network connection, KDE actually loads normally, but trying to end current session takes some 3-5 minutes


](*,)

---

### Post by RikoW on 2006-11-02
can it be that you /etc/network/interfaces file is somehow created dynamically when you are connected to a network? how does it look when there is not internet connection available?

This slow start-up of gnome could be related to the loopback interface not set to auto. See my post here:

[http://ubuntuforums.org/showthread.php?t=282641]("http://ubuntuforums.org/showthread.php?t=282641")

Cheers,

             Riko

---

### Post by NiksaVel on 2006-11-02
I don't know... the file seems identical wether I login with network or without it

---

### Post by RikoW on 2006-11-02
The thing that caused a very slow start-up of gnome in my case was a missing *auto lo* for the loopback interface.

Good luck, 

           Riko

---

### Post by NiksaVel on 2006-11-02
yes... I saw several forums posts with such a problem - but that's the first line in my interfaces file!!  ](*,) ](*,) ](*,) ](*,)

---

### Post by pattymnaish on 2006-11-02
Try this: open up your /etc/dhcp3/dhclient.conf file, uncomment the line that specifies timeout and change it from ```
timeout 60;
``` to ```
timeout 5;
``` or similar.

---

### Post by NiksaVel on 2006-11-13
I have static IP configured so I don't think it's DHCP related, HOWEVER I believe I have traced the problem down to checkgmail program...

I have it autostart with every session, but when I'm not connected to the internet it seems to hang and take up 90% of CPU and I can't shut it down with any command....   I finally removed it from autostart and I start gnome normally now...


can anyone confirm this?

---

### Post by NiksaVel on 2006-11-13
well... I guess I can confirm it myself if it might be of any use to anyone:


Changes:
(Version 1.10.1 - 28/10/06)
- New feature: The number of messages can be sent to scripts run on mail arrival by using %m in the command
- Slight change in translation handling code: the version of the user translations is now checked against the program version, and if the user translations are up-to-date language keys can be modified even if they exist in the default preferences
**- BUGFIX: If version 1.10 was started when no network connection was present, checkgmail got caught in an infinite loop when trying to log in, with predictably disasterous consequences ... :(  This has been fixed by adding a 30 sec sleep period between trying to connect**
- BUGFIX: Messages with <> tags in the header weren't displayed correctly if the tag wasn't compatible with Pango
- BUGFIX: Mail order sort changed so that newest messages are displayed first
- BUGFIX: Really fixed proxy support this time!
- New Translation: Japanese (Satoshi Tanabe)
- New Translation: Romanian (Marius Mihai)
- Updated translations

---

