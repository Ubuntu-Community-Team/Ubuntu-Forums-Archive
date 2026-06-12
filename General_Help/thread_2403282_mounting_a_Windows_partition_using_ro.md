---
title: "mounting a Windows partition using ro"
date: 2018-10-09
forum: General Help
---

### Post by naomibrown on 2018-10-09
Hi,

My brother's Fujitsu Lifebook A series laptop isn't booting into Windows so I've just inserted a liveCD to try to copy the data off his hard drive as it isn't backed up. When I try to click on the Windows disc using Files it gives me the following error message:

Unable to access "Windows"
Error mounting /dev/sda4 at /media/ubuntu/Windows:Command-line 'mount -t "ntfs" -o
"uhelper=udisks2,nodev,nosuid,uidd=999,gid=999" "/dev/sda4" "/media/ubuntu/Windows" exited with non-zero status 14: The disk contains an unclean file system (0,0). 
Metadata kept in Windows cache, refused to mount. 
Failed to mount '/dev/sda4':Operation not permitted 
The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount hte volume read-only with the 'ro' mount option.

I've tried to follow the instructions at [https://askubuntu.com/questions/204166/how-do-i-mount-a-hibernated-ntfs-partition#204173]("https://askubuntu.com/questions/204166/how-do-i-mount-a-hibernated-ntfs-partition#204173") where user98085 suggests using something like "sudo mount -r /dev/sda4". However, I get the error "mount: can't find dev/sda4 in /etc/fstab" I've tried moving to /etc/fstab and get the same error. 

Any ideas? 
Thanks,
Naomi

---

### Post by oldfred on 2018-10-09
Try this:
sudo parted -l
       Force mount, read only (ro), change example with sda3 to your correct NTFS partition:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows

---

### Post by naomibrown on 2018-10-09
When I use "sudo parted -l" it says "Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0 has been opened read-only. Error: Can't have a partition outside the disk! Ignore/Cancel".

I typed Ignore and then used the other two commands. This seemed to complete correctly. When I changed directory to /media/windows/Documents\ and\ Settings and typed ls it said "ls: reading directory '.': Input/output error". 

I then tried opening this folder using Files, and I received the error message "This location could not be displayed. Sorry, could not display all the contents of "windows": Error when getting information for file '/media/windows/Fujitsu': Input/ouput error. 

Thanks,
Naomi

---

### Post by oldfred on 2018-10-09
sr0 is your DVD or CD drive. It is read only.

It looks like your NTFS partition needs major Windows repairs. You cannot do that from Linux, but need to use your Windows repair flash drive or DVD and its repair console. You often have to run chkdsk multiple times or until it shows no errors.

---

### Post by naomibrown on 2018-10-09
Thanks. I wasn't 100% sure about the CD drive! 

I'll see if I can find a Windows disc then.

Thanks for all your help :)

---

