---
title: "Cryptkeeper makes duplicate folders/ does not require password for access"
date: 2014-06-15
forum: General Help
---

### Post by ozark_hillbilly on 2014-06-15
After installing latest version (0.9.5-5) of Cryptkeeper onto Ubuntu 12.04 I was able to invoke the program and create a folder(s). It did ask for a password assignment during the folder creation. What is odd is the fact that Cryptkeeper generated two folders instead of just one (see screenshot attachment). And it does not ask for a password to access the newly created folder. I am able to click on the folder and go straight to the contents. Huh?

Attempts to delete these folders are unsuccessful; something about not being assigned to fstab. Would it be OK or even work  to use Nautilus, under Terminal mode, to delete these folders?

I was hoping Cryptkeeper was the most straightforward way to make confidential data less accessible. Maybe not.

Thanks in advance for any help,

Ed

---

### Post by bapoumba on 2014-06-18
Is this lubuntu ?
In any case, looking on the forums I saw several users recommend Gnome Encfs Manager. 
[http://ubuntuforums.org/showthread.php?t=2224218](http://ubuntuforums.org/showthread.php?t=2224218)
[http://ubuntuforums.org/showthread.php?t=2189483](http://ubuntuforums.org/showthread.php?t=2189483)

---

### Post by ozark_hillbilly on 2014-06-20
Is this lubuntu ?

Nope.... Ubuntu 12.04

From the lack of response I guess Cryptkeeper is not popular....

---

### Post by kurt18947 on 2014-06-21
I've been on a similar pursuit, being able to encrypt data on a notebook such that if the notebook were stolen, the thief would have to expend some effort to get at the data.  I too came across recommendations for Gnome Encfs Manager.  A simple but I'm not sure how secure option is to create a folder, right-click it and select 'compress'.  Certain compression schemes such as .rar and 7z support encryption.  If the file names are encrypted as well it should keep casual prying eyes away but this option seems pretty easy to crack from what I've read.

A somewhat more robust option seems to be to install 'cryptsetup' from the repositories.  This adds an 'encrypt' option to the 'Disks' app using LUKS to encrypt partitions and removable devices.  This seems more robust but seems to only work on block devices, not folders.  When I was using Windows I had a separate data partition such that if (when) Windows crapped the bed the data partition was unaffected.  It was also  simple to backup the entire (small) partition on a regular basis. Perhaps such a scheme  would work with linux as well?

Edit: Or a separate encrypted /home?  I was looking more at being able to encrypt removeable drives e.g. flash and SDHC storage.

---

### Post by bapoumba on 2014-06-21
> **ozark_hillbilly said:**
> Is this lubuntu ?

Nope.... Ubuntu 12.04



Will change your thread prefix from lubuntu to ubuntu.

---

