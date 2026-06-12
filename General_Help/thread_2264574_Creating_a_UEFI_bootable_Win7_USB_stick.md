---
title: "Creating a UEFI bootable Win7 USB stick"
date: 2015-02-08
forum: General Help
---

### Post by obaid2 on 2015-02-08
I'm using winsb to create a bootable usb stick. In terminal I enter this command:  winusb --install'/home/obaid/Downloads/Windows 7 Home Premium SP1 (64 Bit)/Windows.iso' /dev/sdb

It returns an error:
mkdir: cannot create directory ‘/media/winusb_iso_1423415599_8150’: Permission denied
Error occured !
Syncing...
Cleaning...
Umounting and removing '/media/winusb_iso_1423415599_8150'...
umount: /media/winusb_iso_1423415599_8150 is not mounted (according to mtab)
Umounting and removing '/media/winusb_target_1423415599_8150'...
umount: /media/winusb_target_1423415599_8150 is not mounted (according to mtab)

I'm new to ubuntu and have no idea how to fix this, help please.

---

### Post by yancek on 2015-02-08
You will probably have better luck creating a windows bootable flash drive from windows.
I read a post here that the winusb software has not been updated recently.  I've never used it so I don't know.
The problem with your command is that apparently it is trying to create a 'winusb.iso' in the /media directory.  I expect you are running that as a normal user.  A normal user does not usually have permission to write outside the /home/user directory in a default installation.  Prefix the command with sudo and enter your user password when prompted.  Also, you do need this part in quotes:  /home/obaid/Downloads/Windows 7 Home Premium SP1 (64 Bit)/Windows.iso because of the spaces in the name.  You probably need a space after 'install' also, can't tell if you do.

---

### Post by obaid2 on 2015-02-09
Solved it by using 'sudo' at the start of the command.

---

