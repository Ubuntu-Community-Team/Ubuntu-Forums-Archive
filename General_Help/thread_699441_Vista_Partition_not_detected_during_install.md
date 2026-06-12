---
title: "Vista Partition not detected during install?"
date: 2008-02-17
forum: General Help
---

### Post by rollinroll on 2008-02-17
Ok, so i'm installing ubuntu 7.10.
I resized the C drive using ubuntu installer and when i am at the final step it shoudl have said "Vista/Longhorn" loader. But it does not... Is it safe to install?

---

### Post by seventhc on 2008-02-17
What option did you choose during the install on *step 4*?
You should choose *Use largest continuous free space*. If you didn't change anything it's going to format your entire drive and vista will be gone.

---

### Post by rollinroll on 2008-02-17
> **seventhc said:**
> What option did you choose during the install on *step 4*?
You should choose *Use largest continuous free space*. If you didn't change anything it's going to format your entire drive and vista will be gone.
No, i choosed resize drive. The vista drive is still visible through ubuntu.

---

### Post by sammydee on 2008-02-17
rollinroll:

I'm a little unclear on exactly what you've done here. Have you actually installed ubuntu already, or are you just using the livecd?

Can you please go through step by step exactly what you have done?

sam

---

### Post by rollinroll on 2008-02-17
> **sammydee said:**
> rollinroll:

I'm a little unclear on exactly what you've done here. Have you actually installed ubuntu already, or are you just using the livecd?

Can you please go through step by step exactly what you have done?

sam
Ok, first i booted up the live cd, then runned the install prgogram.
Choosed my languages etc... until i came to the partitioner.
There, i choosed resize sda2 to make place for ubuntu.
Then i typed in my names and stuff.
And now i am at the install screen. But under the line "Migration assistant:" it does not say "Vista/Longhorn (loader)". So does this mean that when i install and reboot, the grub bootloader will not list Windows Vista there?

---

### Post by uberlube on 2008-02-17
If you have installed Ubuntu already and you can see the Vista partition while in the desktop but not at boot, you will need to enter Vista manually into the Grub. If I am understanding you correctly.

---

### Post by uberlube on 2008-02-17
First off go into windows and Defragment hardrive to get all your info bunched together then resize.

---

### Post by rollinroll on 2008-02-17
> **uberlube said:**
> First off go into windows and Defragment hardrive to get all you info bunched together then resize.
Read my post above, i already resized using ubuntu's installer.

---

### Post by sammydee on 2008-02-17
Hold on rollinroll - have you already resized?

I don't think whether it is listed in the migration assistant or not will affect whether it boots into the old os or not. Ubuntu in my experience has got the other operating systems to boot ever single time automatically. The migration assistant is quite new and not really essential to the install process.

---

### Post by uberlube on 2008-02-17
Sorry I wanst sure if the changes took place yet or not. Like I said if it does not show in the Migration Assistant and does not give you the option during boot then add it maually.
To add it use the guidelines here:

[http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)

---

### Post by rollinroll on 2008-02-17
> **uberlube said:**
> Sorry I wanst sure if the changes took place yet or not. Like I said if it does not show in the Migration Assistant and does not give you the option during boot then add it maually.
Ok, thanks

---

