---
title: "HELP! won't boot properly"
date: 2007-11-20
forum: General Help
---

### Post by davbren on 2007-11-20
Ok i jsut installed some updates on Gutsy, it seemed like pretty standard stuff and now I can't get graphics. I'm stuck in command line and I can't do anything...

please help..!

cheers,
Dave.

---

### Post by bingoUV on 2007-11-20
> **davbren said:**
> Ok i jsut installed some updates on Gutsy, it seemed like pretty standard stuff and now I can't get graphics. I'm stuck in command line and I can't do anything...

please help..!

cheers,
Dave.

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by davbren on 2007-11-20
sorry I should have said that I've tried that... well i tried it with the -phigh in there

---

### Post by bingoUV on 2007-11-20
> **davbren said:**
> sorry I should have said that I've tried that... well i tried it with the -phigh in there

Did it complete successfully? Any error messages? Post your xorg.conf, and tell about your graphics hardware as much as you can.

---

### Post by davbren on 2007-11-20
how do i get the xorg.conf?? also how do i get the xorg.conf if i can't see anything except command line?

the graphics were working fine, everything was. Everything completed i just went for a reboot and then nothing...

I'm using an ATI X1850XT im using fglrx and xgl (haven't updated yet).

---

### Post by Grafster on 2007-11-20
> **davbren said:**
> how do i get the xorg.conf?? also how do i get the xorg.conf if i can't see anything except command line?

the graphics were working fine, everything was. Everything completed i just went for a reboot and then nothing...

I'm using an ATI X1850XT im using fglrx and xgl (haven't updated yet).

Yeah. The same thing happened to me. It's apparently global (i.e. it:s not just ubuntu but xbuntu and fluxbuntu too).

Having said that the command line isn't terrible.

You can edit xorg with
sudo nano etc/interrfaces/xorg.conf

it'll bring up xorg.conf in the simple and easy to understand nano
(control-x is save, they call it write-out for some reason)

then, find the lines of the file with you screen resolution and try to put something you're sure will work.

run startx

The error messages you get -may- help. (they haven:t helped me but I'm running a really old laptop)

---

