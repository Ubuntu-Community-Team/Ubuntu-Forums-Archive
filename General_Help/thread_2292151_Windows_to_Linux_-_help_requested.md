---
title: "Windows to Linux - help requested"
date: 2015-08-25
forum: General Help
---

### Post by Paul_Vesse on 2015-08-25
I have an Asus G46V. One the Asus I have two harddrives. It originally came with Win 8 on a 500GB disk. I upgraded it with an Intel SSD 210 GB mSATA.

I managed to install Linux Ubuntu 15.4 on the SSD after struggelig with boot options and what not. After that I have been able to make everything work, including the dual graphics cards.

So what do I need help with? Well, simply put, I want to terminate the Windows 8 on the 500 GB disk and get that as a storage disk for my Ubuntu. How do I go about doing that? :)

Thanks for any help!

Paul

---

### Post by yancek on 2015-08-25
> I want to terminate the Windows 8 on the 500 GB disk and get that as a  storage disk for my Ubuntu. How do I go about doing that? :smile:


If you still have the Ubuntu install DVD/flash drive, boot it up and open a terminal and type:  gparted or sudo gparted.  This will open the partition manager which is on the install media.  You can post the output with drive/partition information.  Generally, one would simply format the windows partitions with a Linux filesystem but since you have windows 8, you are probably using UEFI to boot and may have an EFI partition on that drive which you won't want to delete.  Post the info here and someone familiar with EFI will suggest something.

---

### Post by ajgreeny on 2015-08-25
You really must get out of the habit, if you have developed it as a habit, of using sudo with gui applications such as gparted.

On a live system use the menu to start gparted and you will be able to use it as you wish.  Using sudo with some gui applications can lead to your user being locked out of the system due to incorrect ownership of files in your /home.  You should use **gksudo** or as a safer version, **sudo -H** with gui apps.

However, having got Win 8 on the machine why not shrink it as much as you can and leave it available, just using the space freed as your data partition?
It's your machine; do what you want or prefer.

---

### Post by monkeybrain20122 on 2015-08-25
You can start gparted by just clicking its launcher then it will prompt for password. Why complicated matter by commands and that got into all confused with sudo/gksudo/sudo =H and what not (shouldn't use sudo, I agree)?

---

