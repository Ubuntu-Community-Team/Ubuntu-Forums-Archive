---
title: "Primary user missing in 'User settings'"
date: 2007-10-19
forum: General Help
---

### Post by maheshasolkar on 2007-10-19
Greetings,

I did a fresh Gutsy install dual boot with Windows XP - which went great.

In an effort to be able to use some XP applications - that I hardly log in to, I decided to give VirtualBox a shot. After installing VirtualBox, I opened *System -> Administration ->  Users and Groups -> Users settings* to add my primary user 'mahesh' to the group 'vboxusers'. I found that user 'mahesh' was missing from the user list, 'root' was the only listed user.

The primary user exists in the /etc/passwd file. Output of the 'id' command seems ok too.

```

$ id mahesh
uid=501(mahesh) gid=1000(mahesh) groups=1000(mahesh),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev)

```

Any idea why the primary user suddenly disappeared from the list? How do I fix this?

Thanks,
Mahesh.

---

