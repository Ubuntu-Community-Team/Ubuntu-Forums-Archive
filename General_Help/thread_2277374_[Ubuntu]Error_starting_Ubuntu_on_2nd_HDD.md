---
title: "[Ubuntu]Error starting Ubuntu on 2nd HDD"
date: 2015-05-08
forum: General Help
---

### Post by mnoker on 2015-05-08
I am trying to run Ubuntu alongside Win 7 but on a separate 1TB HDD and after installing Ubuntu have hit a error wall.
> "error: attempt to read or write outside of disk 'hd0'."
"error: unknown filesystem."
"error: file '/vmlinuz-3.19.0-15-generic' not found."
"error: you need to load the kernel first."

My partition scheme 
SWAP: 10gb
/Boot: 250mb
/: 30gb
/home: whatever space is left.

I have done the Boot-repair from Ubuntu Live but that did not fix anything. Here is the log [http://paste.ubuntu.com/11020473/ ]("http://paste.ubuntu.com/11020473/")

i appreciate any help you guys provide. Thanks!

Edit: Wanted to clarify that this is on first boot from grub.

---

### Post by mnoker on 2015-05-12
Anyone?

---

### Post by Bashing-om on 2015-05-12
mnoker; Hello:

Scary thought " error: attempt to read or write outside of disk 'hd0'.
Where hd0 is the 1st hard drive.
Digging deeper, I see ubuntu 15.04, but I do not understand what I am looking at in how it ( 15.04) boots.

However, I do note that grub is installed to most of the drives, might I suggest that Windows' boot loader be (RE-)installed to the 1st hard drive ?

Regrets, but presently I do not know enough to offer advise in installing grub to that 2nd hard drive. I do not know that there is a difference in how systemd (15.04) and upstart (14.04) integrate with grub. But the menu 'build' is not as I would expect and I do not know what is now "normal" with systemd .

Though it is considered bad form to respond "I do not know" at least you know we do care.

regards

---

### Post by QDR06VV9 on 2015-05-12
I have had this error: attempt to read or write outside of disk 'hd0'.
In my case I have a badly designed tower in regards to fitting extra drives and such, and point being that a connection came loose.
When that error code came up.
Maybe? Maybe Not.
Would not hurt to check.
Regards

---

### Post by mnoker on 2015-05-12
I will check my cables to make sure everything is connected today when I get home.

---

### Post by oldfred on 2015-05-15
Are you booting directly from sdb?

Boot-Repair's auto fix tries to install grub to every MBR. With multiple drives you usually do not want that as you usually want to keep the Windows boot loader on the Windows drive. Boot-Repair's advanced mode gives you the option to choose an install and which drive to install the boot loader into. It will install a Windows type boot loader to sda if you choose that.

Also you have one drive as gpt. Grub will not install correctly to that drive without another tiny partition 1 or 2MB unformatted with the bios_grub flag. You do not need that if not trying to install grub to a gpt drive.

---

