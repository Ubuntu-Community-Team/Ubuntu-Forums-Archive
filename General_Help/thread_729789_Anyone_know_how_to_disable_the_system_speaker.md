---
title: "Anyone know how to disable the system speaker?"
date: 2008-03-20
forum: General Help
---

### Post by Funky91 on 2008-03-20
Anyone know how to switch off the pc internal speaker that beeps. It is soooooo annoying!

---

### Post by oldb0y on 2008-03-20
Have you checked in the BIOS?

---

### Post by Funky91 on 2008-03-20
is it possible to just disable it under ubuntu. Because its a dual booted pc and the speaker is fine in xp. 

I will do it in the bios if its not possible to do it just in ubuntu.

---

### Post by y-lee on 2008-03-20
See [Turning Off The System (hardware) Beep]("http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/").

Hope that helps :)

---

### Post by ryanhaigh on 2008-03-20
in the terminal
```

sudo rmmod pcspkr

```

To do this on boot add the following line to the bottom of /etc/modprobe.d/blacklist
```

blacklist pcspkr

```

---

