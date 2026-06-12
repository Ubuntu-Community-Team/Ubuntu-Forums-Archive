---
title: "Ubuntu not booting - already tried some solutions"
date: 2015-11-29
forum: General Help
---

### Post by hector28 on 2015-11-29
Greetings! I come to you with a big problem. While I was away on a trip I was forced to leave my laptop with my sister, who doesn't really care much for technology. I was away for 1 month and found my laptop in a horrid state... Battery is now corrupted, my hard drive has a clicking noise and my keyboard doesn't even work (she said "a little water" was spilled over the laptop). How can someone do so much damage to a computer in so little time? I have no idea. I'm on the process of replacing the damaged components, but I'd like to know if I can rescue my hard drive, since it is 1TB and a 1TB HD comes really expensive where I live. For this I've heard I can test it from the Ubuntu disk utility, but there's only one problem... Ubuntu won't boot anymore! I was running on 14.04 LTS. It booted once or twice when I arrived, but had lost configuration and before starting, during the check-up, said it had found errors in /tmp, then in /, and I didn't even had time to solve this: now, it won't boot at all. Whenever I try to, it shows a black screen with the following messages:

Target filesystem doesn't have required /sbin/init
run-init: /bin/sh no such file or directory
Kernel panic - not syncing: attempted to kill init! exitcode=0x00000100

And some trace calls I didn't have the time to write down. Do I try booting and take a picture of said screen? Anyway, I've been exploring solutions to similar problems, on the forums.. I've already run a fsck on mi /dev/sda1 and even a e2fsck -f -y -v. Nothing seems to work. 

Also, I've tried installing Ubuntu 15.04 to correct any software problems without losing my information, but halfway through the installation it gives me an [errorno 5], I've tried the different burning speed solution that it suggests and had a powerful fan pointing at my computer to discard th reheating issue that it also suggests. Still same error.

Can you give me some help? I've also downloaded the boot info script and run it, results are as shown. Thanks in advance.

Oh, and I'm running from a 15.04 live CD

---

### Post by brian-mccumber on 2015-11-29
The clicking noise could be that the drive is not getting enough power since you said that the battery was messed up and water was spilled in it. If you have a way to power the drive without the data cable being connected, if it spins up without clicking it's a problem with not enough power from the laptop, if it is still clicking then the hdd is probably failing. It could be partial motherboard failure from a short because of the water that lowered the voltage from the mb to the drive.

If you have a desktop computer you can always use the hdd power cable from it to see if it will spin up without clicking.

---

### Post by hector28 on 2015-11-30
Thanks a lot! Unfortunately, I don't have a desktop, but I can go to a friend's place tomorrow and he'll let me use his desktop to try this. Will let you know how it goes. Do you think that's what is causing the errors it found on /tmp and / ?

---

### Post by brian-mccumber on 2015-12-05
Well it's hard to tell without knowing if the drive is still good. Bad sectors on the drive over the OS files will cause all kinds of problems and since you cannot get an installation to complete something is still going on with the computer like a shorted MB or bad drive. If the drive spins up the MB is probably partially shorted and that's why the install fails if the drive is bad then that's why or it could be a combination of both.

---

