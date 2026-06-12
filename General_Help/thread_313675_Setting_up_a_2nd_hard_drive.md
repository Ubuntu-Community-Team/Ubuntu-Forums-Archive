---
title: "Setting up a 2nd hard drive"
date: 2006-12-06
forum: General Help
---

### Post by disabled_20220313 on 2006-12-06
Hi there,

This should be an easy problem for someone who knows more about me than Linux systems.

I had a 120gb hard drive, containing my complete system.

I have installed another 40gb hard drive for the intended use that I have 40gb for system stuff, and 120gb purely for my home directory.

I have successfully installed the 40gb drive and a fresh copy of Edgy.

How do I edit the fstab to mount the 120gb drive so that only I can read/write to it, and have it set as my home directory?

Thanks,

Ciaran

---

### Post by drpaul on 2006-12-06
The first thing is to study man fstab a little. This will help you understand what to put in there.

If your 120G drive is clean, i.e., freshly formatted, I would copy the contents of your home folder to it. Then insert in fstab a line that starts with the hardware location of the 120G on your computer, e.g., /dev/hdb1 which would then be followed by /home/username and some directions like

ext3 defaults,.....

or

ext3 rw,user,.....

YOu can see examples of these in your fstab file and in the man fstab pages.

HTH

Paul

---

### Post by disabled_20220313 on 2006-12-06
Thanks,

Will remember to check the Man pages first next time.

Is there any need for me to worry about how its mounted? Ie If i mount it to my home directory, will other uses be able to read/write to that drive?

Or because its mounted to my home directory do my user permission come into effect?

Ciaran

---

### Post by drpaul on 2006-12-06
I'm not an expert, but I think that mounting it to /home/user limits write access to "user". My system, which is a default config, allows others to read or execute, but you could change that it you wanted.

Paul

---

### Post by disabled_20220313 on 2006-12-07
Thanks,

I found a guide online to do what I wanted.

But I've totalled my machine :D Ah the fun. Well I'll learn.

I agree with you, once the hard drive is mounted to /home then folders undernear /home like my own home directory become my property.

Ciaran

---

