---
title: "Grub error"
date: 2015-09-16
forum: General Help
---

### Post by james168 on 2015-09-16
Hi. Recently my Dell inspiring laptop, on which I run Ubuntu 14.04, experienced booting trouble. I attempted to install an update the day before this happened and ran out of space before the update could finish. After that I had to use the grub menu to select an older kernel. I recently attempted to fix this issue by using a grub repair tool, but this has only made things worse. My computer can no longer find the OS and is in grub rescue mode. The only info I have at the moment is here: paste.ubuntu.com/12318572. I would really like help with this, especially since I am not Linux savy and I have information on my computer I am using to write a book and two scholarly papers.
I will add more to this and answer everyone's questions in the morning, to the best of my abilities.
Until then thanks for reading this.

---

### Post by oldfred on 2015-09-16
Please post full link to make it easy for us to use.
[http://paste.ubuntu.com/12318572/](http://paste.ubuntu.com/12318572/)

You have LVM, with encryption. I know neither, but have a couple of links.
With encryption, any major corruption can prevent anyone including you from accessing your data. If pass phase is not accepted the data is gone. That is the entire purpose of encryption. If any data is valuable, you need good backup procedures, and with encryption you need the absolute best backup procedures and regularly use them.

There are many, many threads on full boot partitions with LVM. They create a nominal size /boot partition. But new installs now have many updates to kernels and you must regularly houseclean or /boot gets too full. Very difficult to houseclean once full. New users do not realize LVM is an advanced partitioning scheme and requires a lot more work to set up, maintain, and repair.

       Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

While discussing resize, it show full process for mounting from live installer. But instead of resizing you need to chroot & remove kernels, reinstall grub, and possibley make other repairs. If you can mount with pass phase & do have backups of important files, make copies of them first.
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

