---
title: "Install Authy app after Twilio removed it from snap store"
date: 2024-04-19
forum: General Help
---

### Post by arisden on 2024-04-19
[FONT=Ubuntu]Hello all.[/FONT]
[FONT=Ubuntu]I have authy-desktop application installed in my current old system. This app was deprecated by Twilio and removed from snap store. Now if I try to install from store, the application is not found.[/FONT]
[FONT=Ubuntu]Having it already installed in other system, the only option is to migrate old installation from old PC to new one.

[/FONT]
[FONT=Ubuntu]I have no idea how to do. There is a method to export/backup a snap application and restore it in new system?

[/FONT]
[FONT=Ubuntu]Can it be done using cache of old system and take the file from there? I tried this mode, but all files names are encrypted, and not possible to see which one is authy among them.[/FONT]
[FONT=Ubuntu]Any help is appreciated. Many thanks.[/FONT]

---

### Post by Holger_Gehrke on 2024-04-19
The actual snap packages are stored in /var/lib/snapd/snaps/. There should be one file with the extension 'snap' in that directory on the old system that is the application you want to transfer and it should be quite easy to tell which one it is by the file name. Transfer that file to your new system and install it with 'snap install path/to/the/file --dangerous'. The option '--dangerous' just tells the snap program not to check signatures, which will probably be necessary since the file isn't available from the store anymore.

Holger

---

### Post by arisgerk on 2024-04-20
Hey Arisden.I ran into the same problem, but I don't have the authy snap package installed on another machine. If you could please, upload the snap file via any cloud provider and send a link, I would like to download it. As replied by Holger, you would find the snap file in /var/lib/snapd/snaps/.

---

