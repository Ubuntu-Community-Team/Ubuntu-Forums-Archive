---
title: "[SOLVED] how to shutdown via command line"
date: 2008-04-03
forum: General Help
---

### Post by HappyFeet on 2008-04-03
shutting down from menu doesnt work and ive tried sudo shutdown -h now, sudo poweroff, and sudo halt. x shutsdown and i see all the processes shutting down in text and then im left with a blinking cursor. but the computer will not completely power off. any ideas? is there another command i can try?

btw, this was a command line install with the xfce desktop (not xubuntu-desktop). maybe i need another package for power management?

---

### Post by nathansoz on 2008-04-03
Is the computer pretty old? I know that I had an old computer that would NEVER shut down all the way when shut down with linux. I would have to manually press the power button. Also is power management enabled in your motherboard?

---

### Post by lemonlaw95 on 2008-04-03
you could try
```
sudo shutdown -t now
```
that works for me. but like nathansoz says, old hardware might be the problem.

---

### Post by HappyFeet on 2008-04-04
> **lemonlaw95 said:**
> you could try
```
sudo shutdown -t now
```
that works for me. but like nathansoz says, old hardware might be the problem.

yeah, it is an old compaq from 1999. every distro ive tried complains about being pre-2000 then says it needs to force acpi at startup. i even installed acpid from from synaptic and still no go. ive tried every command i could find but still have to hold the power button to power off. i guessing a bios update would do the trick?

---

### Post by Whiffle on 2008-04-04
Try getting rid of ACPI and installing APM.  It is usually better supported on older hardware.

[http://packages.ubuntu.com/gutsy/apmd](http://packages.ubuntu.com/gutsy/apmd)

You may have to add apm=on to your kernel boot line, I'm not sure.

---

### Post by HappyFeet on 2008-04-04
thanks alot for the responses. i found a bios update that im going to try first.

---

