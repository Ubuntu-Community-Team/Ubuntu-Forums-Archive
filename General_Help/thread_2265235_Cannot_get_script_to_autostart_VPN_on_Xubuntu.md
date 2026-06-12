---
title: "Cannot get script to autostart VPN on Xubuntu"
date: 2015-02-13
forum: General Help
---

### Post by Mahewa on 2015-02-13
Hello all,

I'm fairly new to Xubuntu (and pretty much all of Linux).  I'm trying to make my VPN start automatically on login, and simply can't make it work.

I created a script, "open_vpn.sh" which reads as follows.

[TABLE="width: 500"]
[TR]
[TD]#!/bin/bash
nmcli con up uuid 89e6adb2-46ba-43cf-ab1d-587f135207b9[/TD]
[/TR]
[/TABLE]

I marked it executable, and it works fine.  When I double click it, I'm connected to the VPN.  But I cannot, for the life of me, get the script to run on startup.

I have tried adding each of the following commands to the Sessions and Startup Application Autostart tab:

sh /home/matthew/open_vpn.sh
bash /home/matthew/open_vpn.sh
/home/matthew/open_vpn.sh

No result.

I also tried adding those same commands  to /etc/rc.local. When that didn't work, I tried adding the second line of the script directly.  Still nothing.

What am I missing here?

ETA: I should probably mention that I'm running Xubuntu 14.10 in a Virtualbox VM, in case that matters.

---

### Post by Mahewa on 2015-02-14
I actually managed to finally figure this out.  I thought that this might be happening because it was executing before services it needed had started, so I added a sleep command.

So if anyone finds this and wants to start a VPN connection automatically on login, do the following:

In a terminal, execute the following:

nmcli con list | grep -i vpn

This will list your VPNs.  After the name of your VPN, it will give you a long alpha-numeric code which is the uuid for for your VPN (I believe it's just randomly generated).

Then in file manager go somewhere you want to put the script that will run on startup.  Mine is in my home directory.  When you're in the directory you want, right click on the blank space and click Create Document -> Empty File.  Name it whatever you want, but I recommend not having any spaces.  Mine is named Open_VPN.sh.  I don't believe the extension is required.  Open the file and insert the following:

[TABLE="width: 500"]
[TR]
[TD]#!/bin/bash
sleep 5
nmcli con up uuid *your-uuid-here*[/TD]
[/TR]
[/TABLE]
 
Replace *your-uuid-here* with the long alph-numeric code you got by running the nmcli con list | grep -i vpn command above.  Save the file.  Then right click on the file and go to permissions and check the box "Allow this file to run as a program" and click okay.  

Then go into Settings -> Session and Startup. Go into the Autostart Applications tab and click Add.  Name it whatever you want.  Click the folder button next to command to browse to and select the script you created.  Click OK, then close out of the sessions and startup program.  Your VPN should now connect when you login.

---

