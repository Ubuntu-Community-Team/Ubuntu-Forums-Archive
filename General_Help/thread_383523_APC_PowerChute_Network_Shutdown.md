---
title: "APC PowerChute Network Shutdown"
date: 2007-03-13
forum: General Help
---

### Post by mbert on 2007-03-13
I've been trying to get APC's PowerChute Network Shutdown to run on Edgy Eft (couldn't get it to run on dapper either) and am having no luck.

I have Sun Java 1.5.08 installed and have successfully installed pcns221lnx.bin.  It registers with the UPS and completes without any errors.

When I manually start the program it executes with no errors, however when i look to see if the process is running it is not there.  In fact from reading the script it should be leaving a pcns.pid in the install directory but it does not.  

I have scanned through the log files but I haven't been able to find anything.

---

### Post by mbert on 2007-03-19
Bump...anyone using this out there?

---

### Post by mbert on 2007-05-02
Well, i've tried again with 7.04 and sun java 1.6 and have gotten the same results so far.  Install appears to be successful, daemon seems to start fine, but in the end there is no process running.  I have emailed APC to see if they can figure this out...

---

### Post by mbert on 2007-05-02
Well, APC's response was that ubuntu is not supported and that was it....back to the drawing board...

---

### Post by dcstar on 2007-05-02
> **mbert said:**
> Well, APC's response was that ubuntu is not supported and that was it....back to the drawing board...

One side issue on using any "Network" UPS software (where the commands to & from the UPS transverse over a LAN) is that the LAN itself must also be on a UPS.

Last year I set up 3 new servers on a single UPS using LAN communications between them, all the tests worked fine (unplug UPS, shutdown sequence worked on server directly connected to UPS and also on the other servers communicating via LAN) so it all seemed good.

A couple of months later a real power failure occurred, and only the direct connect server shut down correctly - the LAN equipment wasn't on a UPS (as we had assumed) so those other servers never received the shutdown command when the power died!

---

### Post by mbert on 2007-05-02
Yeah, my production environment has the switches running off the same ups's as the windows servers we currently have running.  Though, i think i am going to double check just to make sure it is all set up properly.

Right now, I am testing with ubuntu in hopes to start moving away from windows. I would like to be able to use the same setup for the UPSs so that i don't need to purchase any more hardware.  Then again, maybe i should just save my time and buy a serial expansion, that way i can also avoid any problems with the switches...

---

### Post by mbert on 2007-05-02
I think i have found a solution to my problem.  The latest version of APCUPSD now support APC's Network Shutdown protocol (PCNET).

I installed apcupsd from source following the instructions [[COLOR="Red"]here[/COLOR].]("http://www.apcupsd.org/manual/Building_Installing_apcupsd.html#SECTION000112000000000000000")

Setting up my configuration following the instructions [[COLOR="Red"]here[/COLOR].]("http://www.apcupsd.org/manual/Configuration_Examples.html#SECTION000135000000000000000")

Everything appears to be running as it should so far, now for some testing:

First note:  The documentation at apcupsd.org and the apcupsd.conf file indicate you need the passphrase for connecting to the ups.  I first tried the "password", but in fact it wants the "authentication phrase". 

Now I am connected and receiving signal from the UPS.

---

### Post by elcasey on 2007-05-10
***EDIT: I built apcupsd from source, changed my cable and ups types to "usb" and, after an intial issue which gave me a very helpful error message ("you should probably run configure with --enable-usb"), I reconfigured it, remade and reinstalled it and it worked fine using "sudo apctest". This is a great daemon with a great manual, and I even got a popup notification telling me my "system is running on backup power!" when I initiated the self-test in the apctest utility. **Good job**, apcupsd team! :D

---

