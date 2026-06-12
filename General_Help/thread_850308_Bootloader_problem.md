---
title: "Bootloader problem"
date: 2008-07-05
forum: General Help
---

### Post by Rishabhsood on 2008-07-05
I was installing uBuntu on portable HDD and by mistake installed bootloader files on it only

Now when I start PC I cant go to boot options without connecting  portable HDD, How can fix it?

---

### Post by caljohnsmith on 2008-07-05
> **Rishabhsood said:**
> I was installing uBuntu on portable HDD and by mistake installed bootloader files on it only

Now when I start PC I cant go to boot options without connecting  portable HDD, How can fix it?
It sounds like what you did was overwrote the MBR (Master Boot Record) of your internal HDD with Grub, while Grub's files were installed onto your portable HDD. That's why you have to have your portable HDD connected to get Grub to load properly on start-up.

You could repartition your internal HDD to have a really small partition where you could install Grub, that way Grub would load fine regardless of whether your portable HDD was connected.

And of course there are other options too, but what are you after? What is your setup, i.e. what OS(s) are on your internal HDD, and what's on your portable?

---

### Post by Rishabhsood on 2008-07-07
How to do so?

My Internal HDD have Vista, uBuntu 7.10

I was installing uBuntu 8.06 on my external HDD.

---

### Post by VMC on 2008-07-07
> **Rishabhsood said:**
> How to do so?

My Internal HDD have Vista, uBuntu 7.10

I was installing uBuntu 8.06 on my external HDD.

When you unplug your external drive and reboot, what errors messages do you get?

---

### Post by Rishabhsood on 2008-07-08
Some GRUB Configration error
Error 21

---

### Post by jw5801 on 2008-07-08
Ok, boot into your Gutsy install, and run:
```
sudo grub # this will give you a grub> prompt
find /boot/grub/stage1
```
This will return two values (hd0,X) and (hd1,Y). We want to reinstall grub using the grub files on your internal drive, so we want (hd0,X).
```
root (hd0,X) #remember to replace the 'X' with what we found above
setup (hd0)
quit
```

Then you should be all happy again. You will need to add a stanza in your /boot/grub/menu.lst to allow you to boot to the external Hardy install, however. Just copy the stanza from the Hardy install.

If you're unsure about anything ask. If you need help setting up you menu.lst, post the /boot/grub/menu.lst from both your Hardy and Gutsy installs and we'll help.

---

