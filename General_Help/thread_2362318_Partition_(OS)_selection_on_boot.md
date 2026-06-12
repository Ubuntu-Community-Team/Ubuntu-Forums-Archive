---
title: "Partition (OS) selection on boot"
date: 2017-05-26
forum: General Help
---

### Post by old.jim on 2017-05-26
I'm using Ubuntu 16.04. Can someone give me the path to the file that is used for the selection of which operating system to boot on a multiple partition hard drive? I want to change the order of the selections, so it will automatically boot to the OS I use the most. Thank you much.

---

### Post by Bucky Ball on 2017-05-26
Try following this under the heading '[Set Default OS by Manually configuring Grub]("http://tipsonubuntu.com/2016/07/20/grub2-boot-order-ubuntu-16-04/")'.

When you boot your machine, count down the list of entries and take note of which number the OS you want to boot at is (third in the list? Number 3 then). You will need this later in the process.

It is easy if you follow those instructions carefully. Any issues, post back.

(PS: You can also use Grub Customiser for this, but really not worth installing a bit of software for it. Bloat. ;))

---

### Post by oldfred on 2017-05-26
If BIOS with MBR:
You can just boot into your main install and run this:
       sudo grub-install /dev/sda

But grub install remembers the location you installed into. And on a major update will reinstall, so your other install may take over again.
You can fix that with this:
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  


 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643) 

If you already have grub as a boot loader, you can do a second install without grub.

 This launches the installer program (Ubiquity) with an option (-b) to not install a boot loader from live installer in live mode:
In the Terminal window, type ubiquity -b.  

Then run this to  add second install to menu.
sudo update-grub.

More advanced ways to manage grub menu.
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

