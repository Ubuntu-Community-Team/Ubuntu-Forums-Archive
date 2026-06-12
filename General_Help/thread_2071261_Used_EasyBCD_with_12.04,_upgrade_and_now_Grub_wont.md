---
title: "Used EasyBCD with 12.04, upgrade and now Grub wont let me in"
date: 2012-10-15
forum: General Help
---

### Post by Mitchcm on 2012-10-15
Ok so when I was using 12.04 I would hit the Windows bootloader which gave me Windows and Ubuntu through EasyBCD... then if I hit Ubuntu it would take me to a purple screen with many variations of Ubuntu like safe mode etc. And I just hit enter twice to get to the OS

So I start it up after the upgrade and the once-purple screen is now black like the windows bootloader but with ubuntu font. It says at the top **Grub4Dos 0.4.5b** and suggested I hit **tab** for my options... I tried "boot" and "help" and it gave me nothing but a request for devices etc. 

I am using my Windows 7 partition right now. I tried opening EasyBCD again and making other ubuntu options using the one that scans for the grub loader... thing. That found nothing... Legacy and grub2 got me nowhere... 

I am lost... I hate bootloaders... I only had it do the EasyBCD thing because I really hate bootloaders... 

I have not a clue what to do... Thanks

---

### Post by Tralce on 2012-10-15
You may be able to recover from this by obtaining an ubuntu livecd and folllowing the directions here: [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

Sorry, that's the only thing I can think of. I feel your pain; I went through a few years with faulty bootloaders. At one point LILO almost made me give up on Linux entirely.

---

### Post by Mark Phelps on 2012-10-15
GRUB is very different from GRUB4DOS -- and the latter is what, I believe, that EasyBCD implements.

Rather than installing GRUB, you might want to go over to the NeoSmart Technolgy forums and post your question there.  They are the developers and distributors of EasyBCD and may be able to help you fix the problem.

---

### Post by Mitchcm on 2012-10-15
Ah Well thanks for the suggestions. I decided to just burn a new 12.04 iso... Then when I got in I "try Ubuntu" then downloaded the boot-repair thing... Then it was a very simple just waiting... it restarted and GRUB came up first.. and ubuntu booted fantastically. 

It did however say that my ubuntu boot image... thing... was far away from the front of the disk and should be revised.

---

### Post by oldfred on 2012-10-15
If system is booting you are ok.

We are seeing a lot of systems where grub just will not boot from a large / (root) over some very large size or when well beyond the beginning of the drive. We are not sure if grub issue, BIOS or some combination. There used to be a known issue with very old IDE BIOS that could not boot beyond 137GB, but that is systems over 6 years old. But issue seems similar. 

I normally suggest 25GB / with separate /home and/or data partitions and those usually work.

---

