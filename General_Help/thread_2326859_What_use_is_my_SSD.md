---
title: "What use is my SSD?"
date: 2016-06-05
forum: General Help
---

### Post by makem2 on 2016-06-05
I have  Toshiba laptop which came without a DVD drive. I have replaced the blanking plastic piece with a caddy that contains a 120GB SSD which was free from a friend.

After a steep earning curve I have the drive mounting and with a nice 119GB ext4 partition.

I do not at this stage want to swap the HDD with the SSD as the machine is still in warranty and running perfectly. I don't play games or use anything regularly that needs speed, however it does seem a waste to just store data on the SSD. I already have complete regularly updated data backups across two remote HDDs.

I am not short of HDD space.

I appreciate I cannot have a 'Program Files' folder on there so can I make some other use of the SSD that uses the speed?

---

### Post by mcduck on 2016-06-05
I would just use the drive for your system partition, that way you'll get a nice speed benefit from it, and the drive has plenty of space for use as /. I'd even keep /home on the SSD, maybe keeping some of the larger directories from my home on the normal hard drive if there's need for more space.

Of course you can also go for the closest equivalent of "Program Files", and move your /usr directory there. Not quite as good as /, but you'd still see some benefit in program startup times.

---

### Post by makem2 on 2016-06-05
Thank you.

I am not sure if I can boot the SSD from the caddy (Toshiba even said an SSD could not work in a caddy) so don't want to mess with the current boot.

I am interested in your suggestion of moving /usr there but can that be done now, after I have a working install I don't want to mess up?

---

### Post by NadirPoint on 2016-06-05
> **makem2 said:**
> I do not at this stage want to swap the HDD with the SSD as the machine is still in warranty and running perfectly.
Replacing or upgrading a hard drive won't affect your warranty.  Just re-install the OEM drive if it needs to go back for other warranty repairs.

---

### Post by makem2 on 2016-06-05
Point taken, but I am quite new to linux and cannot risk messing up my current system until later in the year when I can devote more time. Maybe late November.

---

### Post by mcduck on 2016-06-06
I agree with NadirPoint, switching the drives around would be the best option. Also regardless of what Toshiba said, it would most liekly boot just fine from the caddy, it's just connecting to same SATA bus just like the internal hard drive.

Anyway, moving /usr is pretty straightforward as well, all you'd need to do is format the SSD as Ext4 (or any other native Linux filesystem), then copy all the contents of /usr to the new drive. After that you just edit the /etc/fstab file and add a line to mount the SSD partition at /usr.

At this point it's pretty much nondestructive change, at least until you install any updates or new software, you can just boot with USB drive and remove the change from/etc/fstab. However all the contents that currently exist in the /usr directory of your normal hard drive will still be there on the drive, taking space, but hidden from you since the SSD is mounted on top of them. So after you've confirmed you can get to desktop normally with /usr moved to SSD, you'll want to boot the system with live USB drive, mount your normal hard drive, and delete everything inside /usr directory. (leave the directory itself there as it's needed as the mount point for the SSD)

---

### Post by makem2 on 2016-06-06
Thank you for that detailed explanation, however, a problem has arisen with this SSD in the caddy.

After a shutdown the drive is not found any more. It is found every time by windows and always in xubuntu after a reboot following windows. However, after a reboot or shutdown from xubuntu it is not found.

Please see the question posted at:

[http://ubuntuforums.org/showthread.php?t=2326896](http://ubuntuforums.org/showthread.php?t=2326896)

This explains what is happening and if you can enlighten me I would be very grateful.

---

### Post by makem2 on 2016-06-06
Thanks mcduck: coming back to my what to do query, perhaps I can finish that for the future?

Having moved the contents of /usr to the SSD and now needed an update ( I assume I should have turned off auto update):

Do I comment out the fstab reference to the /usr, make the update, copy the contents of the updated /usr over the SSD /usr and uncomment the fstab reference?

---

### Post by uwe-bungto on 2016-06-06
Your Bois should allow for the boot order, HDD, USB or DVD(which is now the SSD drive) to be set.

---

### Post by makem2 on 2016-06-07
I am not using the SSD as a boot drive yet. The boot order is HDD, USB, DVD untilI can get the SSD the be detected every time.

The SSD is used purely as a data driveor would be.

---

### Post by uwe-bungto on 2016-06-07
> **makem2 said:**
> I am not using the SSD as a boot drive yet. The boot order is HDD, USB, DVD untilI can get the SSD the be detected every time.

The SSD is used purely as a data driveor would be.

Is this SSD in your fstab? 
If I am not mistaken, if the (SSD, HDD, partition) is not mentioned in fstab it will not be mounted at startup.

in /etc/fstab
eg:
# /data is on /dev/sdb1 during installation
UUID=3eeb2980-222b-48df-9026-03f89dd9e787   /ssd         ext4    defaults 0    2
Thus UUID id will be an unique descriptor for you SSD which can be found with 
sudo blkid

Make a dir in /home called data
mkdir data

then link /home/data to /ssd

ln -s  /ssd  data 

This should make a symbolic link from /home/data to /ssd.

No guarantee i keep getting target and link name mixed up. if it is there will be a warning.

---

### Post by Bucky Ball on 2016-06-07
I did exactly what you are doing with a Toshiba Satellite Pro L510. Replaced optical drive with caddy, put SSD in, but in my case, I cloned my Ubuntu install from the HDD to the SSD and was using that. Super speed improvement but you need to jump through hoops to get the SSD booting. My machine does not like to boot from anything that is not sda, so need to set boot device to caddy everytime (FDD for some strange reason).

Anyway, upshot is, just a few days ago I swapped them over and now have the SSD booting perfectly in sda rather than sdb in the caddy (didn't even have to do anything to grub, just slapped it in and away it went). The HDD is now in the caddy and I have wiped the four Ubuntu installs I had on there and expanded my data partition to use the whole drive (and leaving Win7 at the beginning of the drive which, incidentally, still boots fine booting from FDD).

Everything working perfectly. My suggestion would be to clone the OS from the HDD to the SSD for a start, try and figure how to boot to it (you'll still have your HDD install to fall back on while doing this), and swap them over when the warranty is out. I agree that using an SSD for data storage when you are running an OS from HDD is not such much a waste, but not ideal.

Don't know if any of that helps, just sharing my experience as I have done the exact same thing with a Toshiba. Slap an SSD in the drive bay caddy. Good luck.

---

### Post by makem2 on 2016-06-07
Thank you all for your input.

The SSD is not compatible with Intel chip set 8 or greater. My chipset is greater.

Reason why it works in Windows - windows does not need special drivers.

It 'may' work as a main drive.

This information comes from  OCZ the suppliers of the SSD. As a matter of interest that are part of Toshiba, have online chat and great quick support.

Having had the SSD as a gift I have lost nothing but have gained much knowledge and also got the bug for SSD

I am considering the OCZ-Vector-180-SSD-VTR180-25SAT3-240G-2-5-SATA-6Gb-240GB-SSD.

They supply free cloning software (one of the worries I had) and a 5 year guarantee.

I will dispose of the SSD somehow and have the new SSD as main drive and the current HDD in the caddy.

---

### Post by Bucky Ball on 2016-06-07
Give it to another computer enthusiast. They'll be real happy. 

I wouldn't worry too much about cloning software that comes with the SSD. Probably won't work with Ubuntu anyway and there are plenty of tools to do it in Ubuntu already (Clonezilla and fsarchiver to name a couple). Good luck with it and yes, SSDs are the way to go. I chucked an SSD and 4Gb of RAM in my previous desktop, an upgrade from an old HDD and 1Gb RAM, and it was like a new machine. ;)

---

### Post by Chion_Mika on 2016-06-10
Thank [you]("http://lizhenxian.com/refused-credit-guaranteed.html") [for]("http://misheda.com/small-boat-sales.html") [the]("http://0371city.com/72.html")[ inform]("http://jiapk.com/computer_86")[ations]("http://sanmao56.com/archives/28"). It's help me!

---

