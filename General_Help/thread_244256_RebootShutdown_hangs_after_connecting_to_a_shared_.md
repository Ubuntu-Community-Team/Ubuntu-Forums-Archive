---
title: "Reboot/Shutdown hangs after connecting to a shared folder"
date: 2006-08-26
forum: General Help
---

### Post by ekerazha on 2006-08-26
Hi,
I've this issue:

1) I copy a file from a shared folder of my LAN (the shared folder is on a Windows machine).
2) I reboot/shutdown my machine
3) The system hangs on "deconfiguring network interfaces"
4) I've to hard reboot
5) Now... *everytime* I reboot/shutdown my machine it hangs on "deconfiguring network interfaces" and I've to hard reboot, also if I haven't accessed the network.

I use and need DHCP.

Please help me [-o< :p

---

### Post by ekerazha on 2006-08-26
Nobody?

---

### Post by ifokkema on 2006-08-26
What happens if you manually unmount the network drives first?

---

### Post by ekerazha on 2006-08-27
> **ifokkema said:**
> What happens if you manually unmount the network drives first?
It uses the smb:// path, how can I unmount them?

---

### Post by ifokkema on 2006-08-27
Hmm... not mounted then. Maybe using that configuration kinda messes something up. Have you every tried to mount the drive? You can put an entry in your /etc/fstab file for the network drive, and then use the mount command to mount the drive (or have it mounted automatically when you boot up). If you want to test just once, you can use smbmount to try first. Either way, possibly that will work.

How's your experience with /etc/fstab and the mount command?

---

### Post by ekerazha on 2006-08-27
> **ifokkema said:**
> Hmm... not mounted then. Maybe using that configuration kinda messes something up. Have you every tried to mount the drive? You can put an entry in your /etc/fstab file for the network drive, and then use the mount command to mount the drive (or have it mounted automatically when you boot up). If you want to test just once, you can use smbmount to try first. Either way, possibly that will work.

How's your experience with /etc/fstab and the mount command?
The shared folders aren't always the same... the "mount" way isn't acceptable... it seeems like a bad Dapper bug...

---

### Post by ifokkema on 2006-08-27
Ok... well, you could try and deconfigure your network interface by hand before you shutdown, and see if you're getting any errors of some kind. Use the ifdown program for that.

```
sudo ifdown eth0
```
You'll may have to replace *eth0* with whatever your interface is called.

---

