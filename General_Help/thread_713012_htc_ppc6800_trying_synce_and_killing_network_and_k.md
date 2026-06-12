---
title: "htc ppc6800 trying synce and killing network and keyboard"
date: 2008-03-02
forum: General Help
---

### Post by openback on 2008-03-02
I've been trying to install Synce for use with my Sprint Mogul (HTC PPC-6800) using [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) and successfully got a connection to the device, but I also end up getting a second eth device and my DNS server entry gets removed, so I lose internet access. I was able to disconnect the phone, ifdown, add my DNS and then ifup to restore my connection before, but now when I disconnect the phone, "events/0" takes all the CPU and it doesn't acknowledge keyboard input.

Does anyone know 1. How can I disable just the modem from my phone? Or is that needed for Synce? I tried Settings->USB to PC on the phone and unchecked "Enable advanced network functonality" and that disables the modem, but that also makes ```
pls
``` fail

2. I tried the next step on that Synce tutorial ([http://www.synce.org/moin/SynceSetup/SyncEngine](http://www.synce.org/moin/SynceSetup/SyncEngine)) which tells me to run ```
create_partnership.py "Linux desktop" "Contacts,Calendar"
``` but that doesn't exist. Where do I get that from?

---

### Post by ChinoxR on 2008-03-03
Try to modify your device on Start/settings/connections/Network Cards/Network adapters
On the tab "My network card connects to" Select "Work".
Or on Start/settings/connections/connections You can delete the modem connection of your device on "manage existing connection".
After any modification you have to do a soft reset.

I got the same problem as you runing the command on linux:

$ create_partnership.py "Linux desktop" "Contacts,Calendar"

it says: "bash: create_partnership.py: command not found"

If there is any help!?

---

