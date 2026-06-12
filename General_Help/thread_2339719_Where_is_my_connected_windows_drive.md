---
title: "Where is my connected windows drive?"
date: 2016-10-12
forum: General Help
---

### Post by ben1828 on 2016-10-12
[COLOR=#1D2129][FONT=helvetica]Hello,

I have a machine with a fresh installation of Ubuntu 16 desktop, I have connected to media on a Windows server (using the desktop 'connect to server' assistant), I have installed Plex and now need to navigate to the connection to the windows server to complete the Plex configuration.

I can't figure out where it (the share) is (navigating the folders). Plex does it as if navigating through the directories on a command line basis.[/FONT][/COLOR]


[COLOR=#1D2129][FONT=helvetica]Have followed a dozen guides which involved installing cifs but still haven't had success in finding where the drive is (so I can simply tell Plex where my media is)

Any help would be gratefully received

Thanks



[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-10-12
You need to mount the share via /etc/fstab: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

As for where it is, you need to use either the IP address of the Windows server, or create a hostname in /etc/hosts that points to that address.  Once you mount it as described above, it will have a fixed location in the Linux directory tree.

Oh, and make sure the Windows machine has a static IP address.  You may need to edit the router's configuration to do this, or give the machine an address outside the range automatically assigned via DHCP.

---

### Post by ben1828 on 2016-10-12
So basically I need to set it up as a permanent map / mount for it to then appear under /media (as per the example in that link) ?

Thanks. I should be able to follow that - will give it a go tonight

---

### Post by ben1828 on 2016-10-13
Thanks - worked perfectly and just what I wanted

---

