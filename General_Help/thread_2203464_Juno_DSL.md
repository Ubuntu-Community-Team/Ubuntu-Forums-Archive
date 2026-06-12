---
title: "Juno DSL"
date: 2014-02-03
forum: General Help
---

### Post by gfranney on 2014-02-03
Does anyone know how well UBUNTU 12.04 would work with JUNO DSL.  They say it will work but can not be supported.  Anyone have any experience with this? I am doing this for a friend that needs something better than Windows xp.  but has Juno DSL and their mail program that he does not want to change if possible.  Thanks

---

### Post by wildmanne39 on 2014-02-03
I suggest you create a livecd or usb disk of 12.04 LTS and try it out.

It is also likely that his wireless card if he uses one will need a driver or firmware to work, after you are running from the livecd please copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by gfranney on 2014-02-04
Thank you Wild Man.  Sounds like good advice.  It will be awhile before I can try this but I will let you know how it comes out!

---

