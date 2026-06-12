---
title: "Multi Boot Quandry"
date: 2007-02-06
forum: General Help
---

### Post by Red Knuckles on 2007-02-06
I have 4 partitions [+swap] with Linus OS's. My current boot loader is GRUB installed by PCLinuxOS on mbr. I'm currently upgrading Edgy to Feisty [by changeing allmost all repo entries from Edgy to Feisty]. IF this works I'm wondering:

A: How to set up '/boot/grub/menu.lst' in PCLinuxOS to boot to latest kernel in updated Ubuntu?
Can this be done by setting line '# groot=(hd0,0)' in '/boot/grub/menu.lst' to the partition where 
PCLinuxOS is? And the running 'sudo update-grub'? 

B:Or can I update '/boot/grub/menu.lst' in Kubuntu with 'sudo update-grub' and install Kubuntu boot loader to mbr? How do I do this?

I got this from wiki but am not understanding it as well as I'd like???:confused: 

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by tocleora on 2007-02-06
When I upgraded to edgy from dapper it automatically updated grub for me.  I would assume if you follow the proper procedure to upgrade to feisty it will as well.  If you are already using Edgy, I believe this will give you the option to upgrade to Feisty:

```
sudo update-manager -c -d
```

But since your grub isn't maintained by Ubuntu... I don't know, it might go ahead and upgrade the menu.lst file so you'd have the code, or you could install it, reboot using a previous kernel, then once inside look in your boot folder for the latest vmlinuz* and initrd* files, then take an existing entry for Ubuntu in the pclinuxos grub file and update it to the right files. This is what I have for my current kernel:

```

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=ed6c2040-5639-4525-b97f-13b9e4b81a7e ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

```

I would think you could just change those 2.6.17-10's to whatever the newest entries are.  This is a 1000% guess though so keep that in mind before trying this.  I know my menu.lst has like 4 entries that look exactly the same with the exeption of those version numbers, so it makes sense at least. ;)  Use at your own risk.

---

### Post by Red Knuckles on 2007-02-06
> **tocleora said:**
> When I upgraded to edgy from dapper it automatically updated grub for me.  I would assume if you follow the proper procedure to upgrade to feisty it will as well.  If you are already using Edgy, I believe this will give you the option to upgrade to Feisty:

```
sudo update-manager -c -d
```

But since your grub isn't maintained by Ubuntu... I don't know, it might go ahead and upgrade the menu.lst file so you'd have the code, or you could install it, reboot using a previous kernel, then once inside look in your boot folder for the latest vmlinuz* and initrd* files, then take an existing entry for Ubuntu in the pclinuxos grub file and update it to the right files. This is what I have for my current kernel:

```

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=ed6c2040-5639-4525-b97f-13b9e4b81a7e ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

```

I would think you could just change those 2.6.17-10's to whatever the newest entries are.  This is a 1000% guess though so keep that in mind before trying this.  I know my menu.lst has like 4 entries that look exactly the same with the exeption of those version numbers, so it makes sense at least. ;)  Use at your own risk.

I upgraded to Feisty by changing all 'Edgy' entries in '/etc/apt/sources.list' to 'feisty'. It did automatically upgrade '/boot/grub/menu.lst' so I copied and pasted and mailed it to myself then went to PCLinuxOS and copied and pasted the new entry into '/boot/grub/menu.lst' there. So that worked.

---

### Post by Red Knuckles on 2007-02-06
> **Red Knuckles said:**
> I upgraded to Feisty by changing all 'Edgy' entries in '/etc/apt/sources.list' to 'feisty'. It did automatically upgrade '/boot/grub/menu.lst' so I copied and pasted and mailed it to myself then went to PCLinuxOS and copied and pasted the new entry into '/boot/grub/menu.lst' there. So that worked.

I've changed my mind about updating. Some things about changing '/etc/apt/sources.list' to feisty look kinda shaky to me. I'm burning the Feisty Fawn Herd 3 Desktop ISO and will do an upgrade or fresh install with that. That will install the Ubuntu boot loader which in the past has been excellent at recognizing other Linux operating systems [in my case Debian Etch, PSLinuxOS 2007, MEPIS 6.0-4 beta 4, as well as Feisty Herd 3]. If it doesn't recognize anything I have copies of all 'menu.lst' files so I can edit 'menu.lst'.
:lolflag: ):P

---

### Post by tocleora on 2007-02-07
Yeah, the methods I've read about upgrading, none said that as an option so I was curious if that would work, but I'm by no means an expert so I figured you must have read it somewhere and felt comfortable about doing that. :)  Dapper to Edgy was extremely easy, and I'm saying that with errors.  I had an error that rendered XWindows unusuable for half a day and it still seemed easier than upgrading to XP from 98.  I read an article that told me how to do it that was somewhat misinformation, then I found the one on here and it had the simple one line command that fixed it.  I opted not to use the ISO because I wasn't sure if it had an upgrade option.  But that's me, so... :)

---

