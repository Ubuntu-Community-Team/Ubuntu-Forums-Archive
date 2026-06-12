---
title: "APCUPSD not gracefully shutting down. no powerkill file?!"
date: 2008-01-28
forum: General Help
---

### Post by DJmart on 2008-01-28
I have been running around, like a mad man looking through old posts, and trying to find the solution to my problem as follows:

System Specs:
2 3.20ghz Xeon processors, 3GB RAM, Gusty 7.10 (up to date)

Issue:

I installed APCUPSD from apt-get install

I edited the conf file properly to detect the UPS. 

if i type ```
sudo apcaccess status
```

I do receive the information regarding the UPS's condition, so I know that its communicating.

if i check ```
sudo ps ax | grep apcupsd 
```

it is running! from /sbin

Now, with terminal open, I pull the plug on the UPS. 

I get the message from the APCUPSD service saying power has failed, and is running on batteries.

When the APC ups is about to go out of battery.

The APCUPSD terminates the session, it runs the rc.local scripts and shows the ubuntu "loading" screen, then SITS saying "attempting to kill the UPS power" "apcupsd has successfully killed the power" 

NOTE: The hard disks are not unmounted or shut off.

That last part isn't 100%, but its similar.

After that, it just SITS there. And the battery power is exhausted and the PC shuts down ungracefully.


One thing I noticed, I ran a simulated power fail, by typing the commands onbattery, and one thing I noticed was one error, a big error.

/etc/apcupsd/powerfail was not created. And I cant imagine why!

The folder has full rights to everyone i even set it 777.

PLEASE help me, I can't imagine why it does not work.

Other unrelated settings:
BIOS is set to power-on on replacement of AC power.
Gnome power manager is set to not act on power failure.

---

### Post by DJmart on 2008-01-30
Bump...

Sorry fellas this issue is still not resolved.

---

### Post by DJmart on 2008-02-14
Still unresolved.


Can someone send me the contents (code) of the powerkill file if they use APCUPSD

---

