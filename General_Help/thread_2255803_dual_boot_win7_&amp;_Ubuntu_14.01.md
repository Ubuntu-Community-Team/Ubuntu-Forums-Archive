---
title: "dual boot win7 &amp; Ubuntu 14.01"
date: 2014-12-07
forum: General Help
---

### Post by sam104 on 2014-12-07
Hi all weekend I have been trying to install Ubuntu 14.01 on my computer, I am able to boot off the disk But right after where there's the Ubuntu logo with the red/white loading dots, the system hangs and doesn't move further after 10 different installation disks both 64/32bit :( I'm so frustrated I am also new to this jus following YouTube videos, I was able to successfully install it on virtual box but for some reason I am getting limited features, such as if I go to system settings I can't see user accounts. So I guess this is 2 problems I have

---

### Post by oldfred on 2014-12-07
What brand/model computer and what video chip?

If nVidia or AMD, you probably need nomodeset.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
Have you used all 4 primary partitions? Most Windows 7 system have. 

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

Post this from live installer:
sudo parted -l

---

### Post by sam104 on 2014-12-07
Thanks for the reply fred,
I have a MSI motherboard, intel processor and Nvidia graphics. I reinstalled windows 7 and created one partition just for this exercise because i have to do a report for school. I am not to familiar with the boot options but i will look into the links. Any suggestions why i can not see user accounts under system settings in my virtualbox? I did this installation on my laptop.

---

### Post by oldfred on 2014-12-07
Do not know about virualbox. That may be better in a separate thread with that in the title rather than dual boot.

---

