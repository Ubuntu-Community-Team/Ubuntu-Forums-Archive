---
title: "I cannot boot into windows xp with grub2"
date: 2014-08-13
forum: General Help
---

### Post by MagicPotion on 2014-08-13
I have no idea what I'm doing

That said, I am trying to get a dual boot setup to work with ubuntu 14.04 64bit and windows xp 32bit (seperate hard drives), I tried boot repair (always deletes grub customizer btw) which lets me boot up once into windows xp after asking me to confirm a "Boot sector Write!!" warning me of a Virus... which is probably just that bios virus detection. I installed a new hard drive shortly after installing ubuntu 14.04 so I could eventually get windows 7 on there and had to swap some sata cables around to fit it in.

I'm in the middle of trying to revert back to grub legacy, but I feel that shouldn't be necessary and I'd like to get things working.

I've been on and off on all kinds of forums and most of the solutions for similiar problems make barely any sense to me or plainly don't work. Either than that I really like 14.04 it's really fresh and intuitive, especially compared to what I had.

Could someone find it in their heart to help me go through the correct configuration step by step?

---

### Post by bradwilliams923 on 2014-08-13
When you say "separate drives," do you mean separate hard drives or separate partitions on the same hard drive? I assume you mean separate hard drives, but it makes a difference.

---

### Post by MagicPotion on 2014-08-13
yeah seperate hard drives, not partitions.

---

### Post by yancek on 2014-08-13
Are you able to boot Ubuntu 14.04?
What happens when you run:  sudo update-grub with the xp drive attached?

---

### Post by oldfred on 2014-08-13
Do not convert to grub legacy, no one remembers how to use it. (back when grub2 first came out I hated it and did stay with legacy for awhile). 

Post link to just the info report from Boot-Repair. With mulitple drives do not run auto fix as that will just install grub everywhere. You want Windows boot loader on Windows drive and grub2 on Ubuntu drive. You can do that with Advanced options.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

