---
title: "Ubuntu Server: Unmount drive from Web"
date: 2012-10-23
forum: General Help
---

### Post by Inn33d4h3lp on 2012-10-23
Hi, I'd like to start off by saying I'm very new to both Ubuntu and web-programming in general. I use the Ubuntu Server and LAMP for my website, which is located on an external hard drive.

Basically, what I want to achieve is to be able to take my website up and down from the web, really just by mounting and unmounting the HDD and taking advantage of the fact that the contents of the mounted folder override the contents of the folder mounted to. Thereby effectively having two www-directories. 

I'm having some problems with the unmounting of the drive (I haven't tried the mounting part yet). I simply use a index.php file with a command like <?php system('umount -l /dev/sdb1'); ?>

Also tried putting the command above command in a .sh file and doing <?php exec('file.sh'); ?> Running the file.sh from terminal works flawlessly, but not when starting the index.php from the web.

I have been unable to display any error message, tried doing
$var = system('umount -l /dev/sdb1');      (and all other variants I could think of)
echo "$var"
However, I get no output. I wasn't successful in locating the php-log file either..

Could it be because the script run is on the HDD I'm trying to umount, or because www-data doesn't have permission?

I'm sorry if I'm posting this in the wrong place. That being said, I would really appreciate if someone could help me out! :)
Thanks in advanced.

---

