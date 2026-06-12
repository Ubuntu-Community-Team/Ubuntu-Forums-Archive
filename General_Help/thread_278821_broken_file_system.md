---
title: "broken file system?"
date: 2006-10-16
forum: General Help
---

### Post by boca raton on 2006-10-16
I was trying to get a wifi card to run in network systems, something did not go well, the pc locked up solid.  Had to power down and then power up.  As it starts to load 6.06 one message reads "...was not cleanly unmounted, check forced.  .2% noncontiguous fail"  Then a few lines down it reads "*configuring network interfaces...."  and it hangs there.  

Did I bread the file system by powering down?

Is it stuck trying to configure a bad network interface?  

Any recovery suggestions?

Thanks

---

### Post by hw-tph on 2006-10-17
No, I don't think so. What you're seeing is the result of your meddling with - I wager - the /etc/networking/interfaces file or other networking configuration files. It's not lethal in any way. You are usually able to abort network configuration by pressing Ctrl+C. Boot up as usual and go on where you left off.

Also, make sure that the files you were editing (?) when the computer froze aren't left in a bad shape.


Håkan

---

