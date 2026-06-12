---
title: "Can't copy or move files from desktop"
date: 2019-01-24
forum: General Help
---

### Post by Autodave on 2019-01-24
Trying to either copy or move 2 files from my desktop to another drive. But, for some reason I cannot do this.  This is a dualboot machine.  Win10 is on a 1TB HD, Xubuntu on an SSD.  A made (a long time ago) a partition on the one TB to use as storage for pics, music, etc.  There is plenty of space remaining on the partition. But, I cannot move 2 small files onto it.  I checked permissions and they are good.  Any ideas?

---

### Post by Impavidus on 2019-01-24
What error message do you get when you try to copy those files using the terminal?

---

### Post by Autodave on 2019-01-24
Have not tried in the terminal: not even sure that I know the correct command.....

---

### Post by Autodave on 2019-01-24
OK: this is interesting.  I tried moving these 2 files yesterday and today.  Since the first unsuccessful try, this machine has been restarted several times in order to boot into Win10 and then back to Xubuntu.  After rebooting several times, the files would not move.  I just read your message above after rebooting into Xubuntu from Win10 and tried once again.  They both moved this time.  Any idea why?  No updates were done that I am aware of and nothing else was changed.

---

### Post by dragonfly41 on 2019-01-24
I have a similar dual boot configuration with Win 10 in one partition and Ubuntu in another partition. 
I created a small partition (NTFS) to allow files to be shared between these two worlds. 
My thoughts .. is your shared partition formatted EXT4 or NTFS?  Is the intermediary partition mounted?

---

### Post by cmcanulty on 2019-01-24
If you are trying to move items from Ubuntu to the windows desktop I have never been able to make that work and if I copied there it totally screwed up the windows desktop and made it inaccessible until I deleted the files using ubuntu. I couldn't even open the windows desktop from windows. Windows has some real weird parameters for the desktop folder.

---

### Post by Autodave on 2019-01-24
To dragonfly41: the shared space (used for storage) is fornatted NTFS.
To cmcanulty: moving from Linux desktop to storage area on HD that houses Win10.  Always worked before, quit working for 2 days, and now working again.  

Weird.

---

### Post by HermanAB on 2019-01-24
You have to shut Windows down completely. Usually it will suspend and keep the disk file system 'locked'.

---

### Post by Autodave on 2019-01-24
I realize that: have been dual booting for over 8 years now.  I have no idea what was going on: as quickly as it quit working, it started to work normally again.

---

### Post by ajgreeny on 2019-01-24
Has Windows received a large update recently as doing so often enables Fast-start again even if you previously disabled it, meaning that an NTFS partition will again be unmountable in Linux.

Check again that Windows does not have Fast-start enabled, and if it is, disable it once more.

---

### Post by Autodave on 2019-01-24
Nope: everything normal: fast boot is off.  Like I said, nothing was changed at all: just quit working for 2 days and then started to work again after many reboots from and to Win10.

---

