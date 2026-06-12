---
title: "Dual partition (Ubuntu 16.04/Windows 10): not enough space on /boot"
date: 2022-03-11
forum: General Help
---

### Post by AmadeusOK on 2022-03-11
Hi All,

I hope someone can help me with this. I need to update the system because a couple of programs are not working properly. I've been looking for a solution online for months to no avail. Is it possible at all to resize the /boot disk? If so, how can I do that? Thanks in advance.

---

### Post by Impavidus on 2022-03-11
/boot partitions can be resized, but you have to do so when booted from a live disk. In your case, you first have to move sda8 and sda7 a bit to the right to create room.

However, I'm a bit puzzled by your statement that you "need to update the system because a couple of programs are not working properly." Isn't installing updates standard procedure even if there are no obvious malfunctions? Ubuntu 16.04 reached end of life almost a year ago, except for extended security maintenance, for which you have to sign up and which only applies to some core packages. Maybe it would be a better idea to make a fresh start, jumping straight to Ubuntu 20.04. Or even to 22.04. You can keep your current /home partition. Either make the root partition a bit smaller to create room for a larger /boot partition (600MB should be fine) or stop using a /boot partition. It doesn't look like you really need it, as you don't use encryption.

---

### Post by oldfred on 2022-03-11
Your 16.04 is EoL, although extended support is available.
Better to backup and do a total new install of 20.04 or wait until 22.04 is released in April, 2022.
Most desktops do not even need a separate /boot partition. It just becomes one more partition that you have to manage size of, as you have found out.

You need good backup including /home, perhaps some settings in /etc, any server apps you may have installed that are in / and a list of installed apps to make it easy to reinstall all your existing programs.
And then you could erase /boot & / and combine into one partition. Do a total new install, selecting / & select existin /home but DO NOT check the format box.

---

### Post by AmadeusOK on 2022-03-11
Maybe I misunderstood it and it was long ago anyway. I remember trying to open a program and getting a message about needing to update the system. And of course I cannot do that since there's no enough space on the /boot disk.

---

### Post by AmadeusOK on 2022-03-11
Thank you guys for the quick responses. I've decided to wait to do a fresh install of the new Ubuntu 22.04 LTS when it becomes available.

---

### Post by TheFu on 2022-03-11
Running an unpatched 16.04 isn't safe. There are a number of remote attacks on the internet, in active use.
Have you cleaned up the old kernels in /boot already?  Use the package manager to remove all but 2 of them.

In 16.04, /boot/ was used if we installed with LVM and/or encrypted storage. I see the /boot is under 200MB in size. That's been small for the last 10 yrs.  If it were me, I'd use the 16G unallocated storage (after sda8), create a 600MB /boot partition there, then clone the old /boot/ into the new one. 
I'm sure that I've forgotten some critical detail.  Doesn't **gparted** have a way to copy/paste a partition into a new location?  I'd try that. It has to be 'unused' at the time, which means booting from alternate media.  It cannot be mounted.  
Then I'd fix the /etc/fstab to point to the new partition (new UUID), remove the old partition (even delete it from the fstab) and run a **sudo update-grub** command.  All of this needs to happen from a *Try Ubuntu* flash boot device, under a chroot environment.

The main goal is to get from a sub-200MB to a 600MB partition for all the boot stuff above.

If the system doesn't boot, go into the *Try Ubuntu* environment again from your flash device, setup a chroot environment and try to follow some instructions to reinstall grub and update it that match the current release, 16.04.  It might be necessary to update some settings so the **mkinitramfs** command does the right things.  I have to deal with this so seldom, that I don't know the exact commands or options or even the settings. **update-grub** calls mkinitramfs and should locate where boot is and update the kernels as needed.  

You are really lucky to have that 16G free.  BTW, I'd place the new 600MB partition next to the swap, not the /home area. Basically, the new partition wizard asks where you'd like to place the new partition with a MB from the start and MB from the end of the free area.  Say 15G from the start. That should be close enough and leave 15G of space that you can expand /home into later, if that becomes necessary.

---

### Post by AmadeusOK on 2022-03-12
Hey, thanks for the thorough response. I'll take everything you have said into account. Good suggestions!

---

