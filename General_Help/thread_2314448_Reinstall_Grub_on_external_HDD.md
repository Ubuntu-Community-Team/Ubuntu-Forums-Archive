---
title: "Reinstall Grub on external HDD"
date: 2016-02-21
forum: General Help
---

### Post by marco1725 on 2016-02-21
Hello
I have installed Debian on external HDD but when I boot from USB it doesn't work (opens a black screen). In my pc I use already Ubuntu and Windows and have read that I can repair Grub on external HDD with boot repair (have installed it on Ubuntu). Can someone help me with a guide to make no mistake? 

Thank you

---

### Post by oldfred on 2016-02-21
UEFI or BIOS?
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

BIOS is straight forward.
from working  install you want grub in a MBR.
      
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

But grub has saved an entry based on orginal full install. You may need to update that or on major update to grub it will use old default.

 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)


 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 

If UEFI post back.

---

### Post by marco1725 on 2016-02-21
This is the result with Boot-Repair:
[URL="http://paste.ubuntu.com/15160165/"]http://paste.ubuntu.com/15160165/
[/URL]Do I follow your guide written above?

Regards

---

### Post by yancek on 2016-02-21
You have windows and Ubuntu on the first drive (sda) while Debian appears to be on the second drive (sdb1).  The reason you can't boot Debian when you select the external drive to boot is because you have nothing in the master boot record of that drive.  This is shown at the top of the output page.  If you want to be able to boot from that drive you need Grub code in the MBR.  If you can boot Ubuntu, do that and run:  sudo update-grub and watch the output for a Debian entry.  If you get a Debian entry, reboot to it and instal Grub to the MBR of that drive, make sure you get the correct drive.

---

### Post by oldfred on 2016-02-21
To get Ubuntu's grub to recognize an encrypted install you need lvm2 and encrypted drivers. And mount encrypted partition so is asks for encryption passphase. Then it will be seen, either to manually install grub, or use Boot-Repair.

I do not use encryption but others have posted commands like this, not sure if exactly what you need or not.

 sudo apt-get install lvm2
sudo vgchange -ay /dev/mapper/ubuntu--vg-root
mount /dev/mapper/ubuntu--vg-root /mnt
mount /dev/sdb1 /mnt/boot

and this, but do not know what is more correct:

 To get Ubuntu to see different encrypted install:
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sdb2 my-crypt
sudo os-prober
sudo update-grub

---

### Post by marco1725 on 2016-02-21
The first time that I installed OS and encrypt with only passphrase without wait the whole process it started perfectly, instead with full encryption process (for twice) it doesn't start. I don't know if it's the problem

---

### Post by oldfred on 2016-02-21
Basically yes, you have BIOS installs.
But I do not know all the details with LVM & full disk encryption.

It does not look like the report shows any of the encrypted partition data. You have to manually mount and unencrypt for Boot-Repair or install of grub to work.

Also many threads with issues on too many kernels in /boot with LVM installs. Besure to manually delete old kernels. Best to only keep two, new one and one older that you know works.

---

### Post by marco1725 on 2016-02-22
> **oldfred said:**
> To get Ubuntu's grub to recognize an encrypted install you need lvm2 and encrypted drivers. And mount encrypted partition so is asks for encryption passphase. Then it will be seen, either to manually install grub, or use Boot-Repair.I do not use encryption but others have posted commands like this, not sure if exactly what you need or not. sudo apt-get install lvm2sudo vgchange -ay /dev/mapper/ubuntu--vg-rootmount /dev/mapper/ubuntu--vg-root /mntmount /dev/sdb1 /mnt/bootand this, but do not know what is more correct: To get Ubuntu to see different encrypted install:sudo apt-get update && sudo apt-get install lvm2 cryptsetupsudo modprobe dm-cryptsudo cryptsetup luksOpen /dev/sdb2 my-cryptsudo os-probersudo update-grub
I've run this commands:
''sudo vgchange -ay /dev/mapper/ubuntu--vg-root'' ----> ''Invalid volume group name: ubuntu--vg-root''
''sudo cryptsetup luksOpen /dev/sdb2 my-crypt'' -----> ''Device /dev/subd2 is not a valid LUKS device''

I'm thinking to re-install with only passphrase and after encrypt all with third part software

---

### Post by oldfred on 2016-02-22
Examples I posted were for Ubuntu's LVM.

Should have noticed that yours was Debian.

root=/dev/mapper/Debian-root

---

### Post by marco1725 on 2016-02-22
The result is the same
During the installation I choose 'no' when asks me to allow login as root or not. Doesn't it find the volume for this?

---

### Post by oldfred on 2016-02-22
May be better to ask in a Debian Forum as it is specific to mounting Debian, and un-encrypting Debian's LVM. It should be like Ubuntu but every command needs to use your Debian based install and sdb drive.
Ubuntu threads all are with Ubuntu and usually sda drive. So you have to change commands.
Ubuntu does not use root for login, only sudo when you need it for administrative commands.

---

