---
title: "Lost password"
date: 2007-03-03
forum: General Help
---

### Post by Spriteling on 2007-03-03
I've lost my password to my username for logging onto my computer.  Is there any way I can retrieve it?

---

### Post by taurus on 2007-03-03
Boot into recovery mode from the GRUB menu and at the prompt, create a new password for your log in name, assuming it's **spriteling**.

```
passwd **spriteling**
```
Then reboot and you should be able to log back in again.

```
shutdown -r now
```

---

### Post by Spriteling on 2007-03-03
Er....sorry.

How do I get to the GRUB menu?

---

### Post by taurus on 2007-03-03
Right after you turn on your machine, you will see a GRUB screen where you have to press Esc (within 3 seconds) to see the menu.  In there, there should be an option, second option, that says Recovery Mode.  Use the down arrow key to highlight it and hit Return.

---

### Post by Spriteling on 2007-03-03
....argh.

What if you don't know the username? 

(I know I sound like an idiot.  I was in the hospital for six months, and now have forgotten my username and password.)

---

### Post by taurus on 2007-03-03
While still in the recovery mode, look at the output of this command to see your username.

```
ls -la /home
```

---

### Post by Spriteling on 2007-03-03
My computer is not accepting that command.

---

### Post by Spriteling on 2007-03-03
Actually, it is.

Sorry.

---

### Post by Spriteling on 2007-03-03
It says 'Enter new UNIX password:' but it will not let me type anything.

---

### Post by taurus on 2007-03-03
> **Spriteling said:**
> It says 'Enter new UNIX password:' but it will not let me type anything.

Actually, it does.  It just doesn't echo (even as *) back when you type in your new password so make sure you're careful with it.

---

### Post by SanjoEel on 2007-05-08
Hey Taurus thank for the tip, I forgot my name & pw on an old linux laptop and you saved the day bro! Thx again, later.

---

