---
title: "Ubuntu 20.04 boot softlock"
date: 2021-01-10
forum: General Help
---

### Post by humanoidcomplaints on 2021-01-10
i'm not sure why I can't boot ubuntu, but a posibility is that I changed the identifier of my root partition from it's uuid to it's mountpoint('tis was a mistake, but alas, I shalt suffer the consequences) via the disk utility.

I can get a root shell in emergency mode but I can't resume the boot.
While booting there were only [OK]s to be found with an exeption of mounting /dev/sda2 - the root partition.
I have very little experiance with linux commands and no exoeriance with grub, tho I am doing my best to resolve this on my own.

Any help is much apreciated!

---

### Post by ajgreeny on 2021-01-10
You will, I think, have to boot to a live system such as the USB or DVD you used to install and edit the /etc/fstab file of your installed system.

Having booted to the live system run command ```
sudo blkid
``` to find the UUID of the partition.
Then in the file manager click on the root partition of the installed system which will show as one of the volumes in the left hand pane of the file manager; this partition should then be mounted in /media/ubuntu/partition (the partition may show as its UUID or any label it has) and you will be able to navigate to /etc/fstab in that partition.

Now you need  to edit that file as root and change the /dev/sda2 entry back to the UUID you will find in the output of the blkid command using the syntax
UUID=6cada31d-10df-46cf-a43b-15ed4d09cf93 /               ext4   errors=remount-ro 0       1
but with your own UUID of course.
Using a live system of 20.04 you can safely use ***sudo gedit*** with no need for a password in order to edit that fstab file.

---

