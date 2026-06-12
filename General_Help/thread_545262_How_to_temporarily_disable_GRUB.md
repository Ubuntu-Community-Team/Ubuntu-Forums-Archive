---
title: "How to temporarily disable GRUB?"
date: 2007-09-07
forum: General Help
---

### Post by Zdravko on 2007-09-07
Hi there, as you can see from my profile, I do dual-boot. In the next 2 months I am going to give my notebook to my mother, who is a Windows user. Currently GRUB waits 5 seconds and then starts Windows. I don't want to confuse my mother. Tell me how to disable GRUB for this period of time, or just set the time-out to 0? I remember only, that I used an application in Feisty Fawn called AutoStart or something like that to change the boot sequences and the time-out.
Thanks in advance!

---

### Post by CC_machine on 2007-09-07
tell her what GRUB does and that she should just wait or hit enter to start Windows. No problem really :)

---

### Post by Zdravko on 2007-09-07
I am afraid she might accidentally switch to Ubuntu :)
Joking, of course :) My mother is used to work with Windows (as I am) and I don't want to introduce her new things.
Just tell me how to surpass GRUB and start immediately Windows.

---

### Post by p_quarles on 2007-09-07
You can edit the "timeout" line in /boot/grub/menu.lst 

Set it to 0, and you won't see the grub menu.

---

### Post by Zdravko on 2007-09-07
I will do it :)

---

### Post by Zdravko on 2007-09-07
How do I login back to Ubuntu then?

---

### Post by p_quarles on 2007-09-07
You'll have to boot from the live CD and re-edit the menu.lst file. 

I think I misunderstood what you're trying to do here. If you just want to make GRUB invisible, you can change the timeout back to 5 or whatever you want, and the uncomment the "hiddenmenu" line. This will hide the menu, but you'll be able to access it by pressing escape.

---

### Post by Zdravko on 2007-09-07
Okay, let's summarize:
1. Set time-out to 1 second.
2. Set hiddenmenu

Later, if I want to restore GRUB I might be able to do so by pressing ESC during the boot-up?

---

### Post by p_quarles on 2007-09-07
Yes. You'll have to press esc during that timeout, though, so you might want to make it a little more forgiving than 1 second. Whatever you're comfortable with, though.

By the way, this doesn't actually "disable" GRUB (it's still the system's primary bootloader), it just hide the menu from view. If you really want to disable it completely, you would need to restore the Windows MBR.

---

