---
title: "Viewing Windows Files in Ubuntu"
date: 2016-05-02
forum: General Help
---

### Post by RobGoss on 2016-05-02
Hello everyone, I'm using one of my machines as a dual running Ubuntu 16.04 and Windows 10, the problem I'm having is I can see my Windows 10 files when I'm using Ubuntu

When I click on **files **I see a **Windows Files **along with a Recovery file as well for Windows

Is there any way for me to unmount my Windows partition so I won't see these Windows files.

Thanks so much

---

### Post by oldfred on 2016-05-02
If you never want to see them, you actually mount it hidden.
Or you can mount read only in /mnt/Windows and not normally see them in Nautilus.

Mount in fstab:
       [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) 
            [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 
    
       # Hide mount template examples with noauto,  you have to make the mount points yourself first
sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all, UUID is better than this example with device mount
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
#hide windows 7 second hard drive
sudo mkdir /mnt/reserved
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
sudo mkdir /mnt/win7
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0

---

### Post by RobGoss on 2016-05-02
> **oldfred said:**
> If you never want to see them, you actually mount it hidden.
Or you can mount read only in /mnt/Windows and not normally see them in Nautilus.

Mount in fstab:
       [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) 
            [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 
    
       # Hide mount template examples with noauto,  you have to make the mount points yourself first
sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all, UUID is better than this example with device mount
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
#hide windows 7 second hard drive
sudo mkdir /mnt/reserved
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
sudo mkdir /mnt/win7
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0


Hello Fred it looks kinda of complicated I don't want to see them from my Linux desktop

---

### Post by oldfred on 2016-05-02
Auto mount with /media shows in Nautilus.

But manually mounting or using fstab to mount into /mnt will not show in Nautilus.

It really is copy & paste but using your UUID and your mount point.

---

### Post by HermanAB on 2016-05-02
Edit /mnt/fstab and put a # in front of the line that mounts the Windows partition.

---

### Post by Impavidus on 2016-05-02
If the windows partitions are not mentioned in /etc/fstab, nautilus will list them and will mount them somewhere in /media when you click on them. To avoid this, list them in /etc/fstab with the option noauto. Then, nautilus will not list them and they won't be mounted automatically. You can still mount then manually as root.

Using different options in /etc/fstab you can mount the windows partitions automatically, but read-only, which should also be safe.

---

### Post by izznogooood on 2016-05-02
You could open the Program Called "disks" and edit the mount options from there. Im not on Ubuntu now but Im sure you´l find it ;). Just turn of Auto-mount.

---

### Post by RobGoss on 2016-05-02
> **izznogooood said:**
> You could open the Program Called "disks" and edit the mount options from there. Im not on Ubuntu now but Im sure you´l find it ;). Just turn of Auto-mount.

Yes this seem to work as far as the Windows files not showing thanks so much for the tip..

---

### Post by RobGoss on 2016-05-02
Thanks so much guys for the helping hand as always you guys are what makes Ubuntu so much fun and enjoyable to learn....

Big thanks to you all

---

### Post by RobGoss on 2016-05-03
> **izznogooood said:**
> You could open the Program Called "disks" and edit the mount options from there. Im not on Ubuntu now but Im sure you´l find it ;). Just turn of Auto-mount.

This method work great for hiding my Windows files but I still see another file with numbers that have a Windows recovery folders in it, and suggestions how to hide this also

---

### Post by mc4man on 2016-05-03
Did you do a fresh install or an upgrade?
At least here in a dual boot with win 10 (same hdd), only windows is shown in the nautilus sidebar & is not part of the default automount of media (org.gnome.desktop.media-handling
screen shows

---

### Post by RobGoss on 2016-05-03
> **mc4man said:**
> Did you do a fresh install or an upgrade?
At least here in a dual boot with win 10 (same hdd), only windows is shown in the nautilus sidebar & is not part of the default automount of media (org.gnome.desktop.media-handling
screen shows

Thanks for the reply, This is a fresh installation of 16.04 I managed to hide the Windows files but there is still one one more with Recovery files in it...but it's numbered like so,** 0c84857b8,** when i click on it there are two files in this folder one is **Recovery**, and **System  volume.**

---

### Post by izznogooood on 2016-05-03
Is this a partition? (if so you can do the same as you did for your windows files, in the same program, you just have to find the right partition...)
Or is it a folder somewhere? Do you have a screenshot.

---

### Post by aanyadsouza on 2016-05-03
I agree with izznogooood. [COLOR=#000000]Just turn of Auto-mount.[/COLOR]

---

### Post by mc4man on 2016-05-03
I would use gparted & set a hidden flag on the recovery partition(s). It really should have been done automatically during your install. (was here
Ex. of  /dev/sda5 here in screens, dev/sda4 is another recovery related partition & also was flagged the same during the install

---

### Post by RobGoss on 2016-05-03
> **izznogooood said:**
> Is this a partition? (if so you can do the same as you did for your windows files, in the same program, you just have to find the right partition...)
Or is it a folder somewhere? Do you have a screenshot.


Yep and it worked just as you said, I did not want these Windows files accessible from my Linux desktop maybe something could have happened to them you know.  Thanks so much for the help everyone

---

