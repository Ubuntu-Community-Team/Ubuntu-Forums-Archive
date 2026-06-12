---
title: "Help to mount encrypted home with liveusb?"
date: 2019-03-05
forum: General Help
---

### Post by usernamoi on 2019-03-05
I have my login user and pw, but from a bizarre problem im unable to start as usual, or even launch an alternate kernel, or the -recovery mode-.

I want to mount my /user/home folder, to backup some files, but ignore how to do so.

Is it possible using chroot?

---

### Post by oldfred on 2019-03-05
Encrypted /home phased out in 18.04
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase)
remove encryption on /home
[http://www.howtogeek.com/116179/how-to-disable-home-folder-encryption-after-installing-ubuntu/](http://www.howtogeek.com/116179/how-to-disable-home-folder-encryption-after-installing-ubuntu/)

Ubuntu does have full drive encryption which uses LVM.
If LVM:
       
 Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

---

### Post by usernamoi on 2019-04-09
im back (i was unable to access this forums).

i found out i was unable to mount my home partition from a misunderstanding about some words (i found that the word "passphrase" is used to describe the "login password" in relation to using "sudo ecryptfs-recover-private"; i thought this passprase was something different which i needed to recover using my login password).

So, i managed to backup my home partition, but would also like to find which programs i have installed to make a list, and also which ppas i used. i found this answer 
[https://askubuntu.com/questions/148932/how-can-i-get-a-list-of-all-repositories-and-ppas-from-the-command-line-into-an](https://askubuntu.com/questions/148932/how-can-i-get-a-list-of-all-repositories-and-ppas-from-the-command-line-into-an)

that addresses different ways to do something similar to what i want to do, but since im in a liveudb i dont know how could i apply that answer to my problem (making a list of programs and their ppas from the liveusb, and if i would need to use chroot, how i should use it properly, and which would be the right way to use it with encryptfs). 

Another thing i would like to learn but have been unable to find information about is if its possible to install older software in recent versions of ubuntu, and how if its possible (ie software that only has xenial versions to run in bionic or more recent ubuntu versions). If you could guide me, or offer me documentation about this, it would be great.

After solving the previous problem, i would like to try to recover access to the system, and to do that i want to try this but im unsure how to do it: to manually change the default kernel from the liveusb, in the desktop rather than grub (grub cant offer me the option to switch to other kernels as usual, from a problem i still ignore how i started exactly, but which i know was result of uninstalling and trying to reinstall a kernel improperly)

Thanks for any additional information you can help me with.

---

### Post by oldfred on 2019-04-09
If you can chroot into your install, you then can run a list of installed apps.
But better to boot system to avoid chroot.

If you have have encryption, be sure that you mount those as Boot-Repair may not ask.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by usernamoi on 2019-04-10
thanks olfred.

The thing is i dont know how to use chroot, and i  was unable to understand a few very old (maybe also outdated since they  were for ubuntu 10 or 12) guides which offered examples for using it  with a liveusb.

what i understood is that what i want to do  (changing manually which kernel loads as default without grub) should be  possible through chroot, but apart from that i ignore the exact way i  should follow to avoid doing damage or changing something i shouldnt.

i also dont understand ok what or how chroot works: 
from  what i read, is that it allows to mount and use a different root  directory to manipulate a different intallation, but different guides  offered different list of partitions that should be mounted along it so  it would work properly (which in my case i will also need to point since  i placed at least two system partitions in a different disk). also if using chroot would ask me my user name and login password to install and use sudo to make changes, since encryptfs didnt asked me my username when i finally understood that the passphrase it asks is my login password, and i didnt have to use my username anywhere with it.

I  also ignore if i could changed the default kernel through chroot  without mounting other partitions, and how it works or should be used  with encryptfs: should i first mount my encrypted home directory using  that encryptfs recover private, and later use chroot? and if thats the  case, what else should i need to do: do i need to mount another  partition or folder, and how? and then, how i can actually change the  order of kernels, and uninstall one to reinstall it properly.

> **oldfred said:**
> 
If you have have encryption, be sure that you mount those as Boot-Repair may not ask.


Those? 

My problem isnt with grub (it used to work properly), but with something i did when trying to remove and reinstall a kernel, and that somehow made me unable to select alternative kernels in grub, and which also prevents me from reaching login screen, or attempt do anything else without a liveusb.

so, in short, 
- do you know someone that could guide me with chroot so i could manually change which kernel is the first one, and maybe also how to remove a kernel and reinstall it from a live usb?
- do you know if its possible and how to use old debs and programs in more recent systems (xenial apps in bionic os, for example)

---

### Post by oldfred on 2019-04-10
Have you tried Boot-Repair. It walks you thru a minimum chroot to reinstall grub & add the newest kernel.
Use advanced mode & check those options. If you had custom settings in grub, a new install  will reset to defaults. But you can restore from your backups.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you have an UEFI install, you have to also mount that. Boot-Repair will mount /, ESP, & /boot if you have those partitions. But it needs you to mount encrypted partitions. It does not work for users who have server type installs with many of the folders in / as separate partitions. 

       
  chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)
Kernel panic at boot: not syncing. No init found - chroot to resolve
[http://ubuntuforums.org/showthread.php?t=2228437](http://ubuntuforums.org/showthread.php?t=2228437)

---

### Post by usernamoi on 2019-04-15
thanks for the links. 

i think you missed my last paragraph.

-----------

> **oldfred said:**
> 
If you have have encryption, be sure that you mount those as Boot-Repair may not ask.


Those? 

My problem isnt with grub (it used to work properly), but with something  i did when trying to remove and reinstall a kernel, and that somehow  made me unable to select alternative kernels in grub, and which also  prevents me from reaching login screen, or attempt do anything else  without a liveusb.

so, in short, 
- do you know someone that could guide me with chroot so i could  manually change which kernel is the first one, and maybe also how to  remove a kernel and reinstall it from a live usb?

- do you know if its possible and how to use old debs and programs in  more recent systems (xenial apps in bionic os, for example)

----------

---

### Post by usernamoi on 2019-04-15
im not an IT expert, but i have been learning bit of useful stuff from toying with linux distros for some time.

"why i want to chroot"

I have been checking a few videos about chroot, and i know its possible to create a "jail" to copy there the proper folders and files to safely work with them, or to do changes before going "live". i still dont know how im supposed to move or enable changes made in chroot in the original partition(s), or how and which folders i have to link, or how i must mount them only for doing two things:

- A change the order of kernels (to try to start my system with another one); B remove anything related to the files that i didnt installed properly; c install a new kernel via synaptic to try to use that one.

- check my firefox to recover browser settings, addon settings, and other tweaks and files (unless i have already have recovered them when i created the backup of /home, even if some icons and theme data exist outside it under "/"). 

- start cairo-dock to copy manually links and the list of some programs and tools i cant remember.

from what ive seen, it shouldnt be very complicated: what matters is knowing which folders are need a copy, and which folders or partitions dont and how to link and mount them properly; and later how to make the changes permanent to load them after boot.

---

### Post by oldfred on 2019-04-15
Boot-Repair's advanced mode is the easiest way to install new default kernel. Best to also reinstall grub unless you made major reconfiguration of grub as that will reset to all the defaults. Its just that Boot-Repair normally mounts /, and essential partitions if you have them like ESP, /boot, but not other system folders that some servers may have as partitions nor automount encrypted partitions.
So use Boot-Repair but mount your encrypted partition so Boot-Repair can see / inside the encrypted partition.
Then advanced mode check reinstall grub & new kernel.

---

### Post by usernamoi on 2019-04-15
I didnt knew. how i do that with boot-repair?

i will like to try using chroot to recover bookmarks in firefox and settings in cairo dock.

also heres a pastebin
**[http://paste.ubuntu.com/p/cnzkV9w8TY/](http://paste.ubuntu.com/p/cnzkV9w8TY/)**

---

### Post by oldfred on 2019-04-15
I think once you run Boot-Repair you just click on advanced options after you have mounted your encrypted partition with your passphrase:
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Is just /home the only encrypted partition. I do not think Boot-Repair needs /home mounted to update grub & kernel.
You also show a lot of old kernels & should houseclean once system is working again.

With encryption, you must have really good backup procedures as sometimes the encryption breaks and the only way to recover is restore from backup.

Did you try this & some of the other links to /home issues.
[https://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](https://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)
and:
       [http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865) 
    [URL="https://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/"]
[/URL]

---

### Post by usernamoi on 2019-04-15
I checked advanced options, and it offers just one option in relation to   kernels under the "grub options" tab: "purge kernels then reinstall   last kernel". i would prefer to install the original kernel that comes   with ubuntu-studio (the distro i installed, and then changed a bit, and   also the one i have in the liveusb im using).

the kernel that is part of the ubuntu-studio version is Kernel: x86_64 Linux 4.13.0-36-lowlatency. 

the  last kernel i tried to install, and didnt worked, was one of the  deb  files i manually downloaded (dont remember if it was a  4.16.0.041600 kernel and also a 4.15+etc), and which were the beginning  of this  problems, so im not sure that asking boot-repair to try to  reinstall the  last kernel would be the best option, or if could work  rather than  making the problem bigger if its missing files or something  like that  (since i didnt installed it properly). The 4.15.0-43 worked  before i had a problem trying to upgrade the nvidia drivers, so i think i  could try to use that one as first option (via chroot) before deleting  the kernels.

Do you know how it works, and should i try that option? 
if so, which other advanced options i must turn on or off in boot-repair to improve chance of success and also a new problem?

---

### Post by oldfred on 2019-04-15
You could just try the total reinstall of grub.
Not sure a downloaded kernel from a .deb, would be correctly configured for Ubuntu. Best to use repository or ppa.
And if you have nVidia drivers, that has to be incorporated into the kernel with is automatic with Ubuntu's kernel and nVidia files from Ubuntu repository.
If you install any other way you have to manually reconfigure yourself, which is not recommended. 
For kernel not with nVidia, you would probably need nomodeset boot parameter to boot.

---

### Post by usernamoi on 2019-04-16
Could you guide me a bit with chroot so i can mount firefox to recover bookmarks, and maybe also cairo-dock settings, and maybe after that to also try to change the order of kernels?

After recovering the bookmarks and make a copy of some settings, im ok with trying boot-repair as last option. 

Another thing i would like to know if possible, is if i can copy and run the partitions into a virtual machine just to check which things i can backup before resetting the system.

As long as i can check my old files and make a list of the things i must or can reinstall, i wouldnt mind much reinstalling the system from zero.

---

### Post by usernamoi on 2019-04-16
update.

[https://www.youtube.com/watch?v=XTyY3in5r6Q](https://www.youtube.com/watch?v=XTyY3in5r6Q)
[https://www.youtube.com/watch?v=VfyvF1cnYdE](https://www.youtube.com/watch?v=VfyvF1cnYdE)

this tutorials explain how to use chroot to mount firefox from another os, but im not sure if i can follow the same process to recover cairo-dock settings, and also if i could change the order of kernels following that guide how could i later move the changes into the original system.

---

### Post by oldfred on 2019-04-16
It would be similar to this, but you have to include the ESP - efi system partition.
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)

       UEFI chroot:
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

