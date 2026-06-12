---
title: "file sharing"
date: 2008-01-25
forum: General Help
---

### Post by 565Customz on 2008-01-25
hey guys,

im wondering how i would take files from my windows...more specifically dll's and place them on the /shared partition that i made, so that i can get wine to access them from there.  also how do i get the files to download and save in my /home partition? every time i install it goes right to my /root drive. any software  i can use on linux to view my drives and drive space?

and off topic but is there any way i can set ubuntu to use more ram to speed it up a bit. its kinda lagging, even as im typing right now its about 5 letters behind and im no fast typer....thanks..

---

### Post by Zizzech on 2008-01-25
[http://ubuntuforums.org/showthread.php?t=678220]("http://ubuntuforums.org/showthread.php?t=678220")

You just posted this >.>

---

### Post by PinkFloyd102489 on 2008-01-25
For the RAM bit:

```

sudo nano /etc/sysctl.conf

```

and add this to the end:

```

#Swappiness
vm.swappiness=0

```

Reboot and you're good.

---

