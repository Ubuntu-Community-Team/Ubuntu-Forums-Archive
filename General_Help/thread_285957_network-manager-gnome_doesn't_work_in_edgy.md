---
title: "network-manager-gnome doesn't work in edgy"
date: 2006-10-27
forum: General Help
---

### Post by dr_d on 2006-10-27
hi.. when i boot up edgy after installing network-manager-gnome i get the error

The NetworkManagerApplet cannot find some required resources. It cannot continue.


it worked under dapper so it's not to do with my hardware... must be something to do with edgy...

any help would be greatly appreciated.
cheers!

---

### Post by Architeuthis on 2006-10-27
[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

According to this page, wireless network cards are not properly detected, this may be the issue you are having.

---

### Post by dr_d on 2006-10-27
hey thanks for replying..

it sure doesn't seem like it... i have the intel pro/set wireless card which is reported to work fine... furthermore if i set the SSID or whatever manually it works.

any ideas?

---

### Post by dr_d on 2006-10-28
I just noticed this in the known issues page:

> Applications (Main)

    *

      network-admin (System->Networking)
          o

            Problem: Does not scan for wireless networks. [WWW] Bug #59159
          o

            Description: The drop-down list with available wireless ESSIDs is empty
          o

            Workaround: Enter ESSID manually, search with "iwlist scan"





I'm thinking that this might be causing my problem.. Hopefully it will be fixed soon.

---

### Post by rene32 on 2006-10-28
Hi,

I have similar problems here. I am using a Prism2 wifi card (PCI) and after update, Edgy loaded some evil modules which did not work. So I had to blacklist the modules orinoco, prism2, hermes to make hostap first choice module and get the wifi card running again. After a restart, Edgy froze, the next start went fine. The same behaviour could be seen on other systems as well: Add modules to blacklist, restart and the system freezes once then starts up fine again.

Right now, I can connect to open and WEP networks using command line tools like iwconfig and dhclient3.

No about the Network Manager: Network Manager is not able to connect to anything. Be it an open network, be it a WEP or WPA encrypted network. It sees the network, detects the encryption method properly but horribly fails to connect. In most cases it hangs and kills the desktop by blocking the keyboard and preventing other applications from starting. A friend of mine told me he got it working (by doing nothing special) but I am experiencing those reproducible freezes again and again. Wifi in Edgy (using a Prism2) is a real mess at the moment. I do not understand why this isn't improving.

I have already looked for a newer version of Network Manager. Ubuntu is shipped with version 0.6.3. There has been an important freeze bugfix in 0.6.4, current version is 0.6.5. Unfortunately, I did not find an updated version for Ubuntu :-(

If anyone can help, please do. This is really annoying me.

René

---

### Post by dr_d on 2006-10-29
problem fixed. #1 diagnostic tool ever: search google for error message.

now i can enjoy edgy problem free.. btw isn't the new version of firefox nice

cheers

---

