---
title: "Samba does not share folders until I've log in (13.04 Raring)"
date: 2013-05-18
forum: General Help
---

### Post by juicyoner on 2013-05-18
Hey everyone - I am running 13.04 Raring on a desktop machine. I am sharing some folders on it via samba for my raspberry pi to read from in the living room. Occasionally I have to remotely reboot my 13.04 machine via ssh. In order for the machine to make the samba shares visible on the network I need to go back to the physical machine and log in. Is there any way to configure my set up so that I can avoid this? I'd like to be able to reboot remotely and have the samba folders available immediately.

Thanks!

---

### Post by JRV on 2013-05-18
Try using SFTP instead.
```

pcmanfm sftp://USER@HOSTNAME/home/USER

```

---

### Post by Cheesemill on 2013-05-18
Do the directories that you are sharing live in an encrypted home partition by any chance?

If so then you have to log in before they are available because the encryption on your home folder is only unlocked when you log in.

You can either set your user to automatically log on which would defeat the purpose of encryption in the first place, or move the shared folders to a location outside of your encrypted home.

---

