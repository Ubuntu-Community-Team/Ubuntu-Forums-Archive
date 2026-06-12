---
title: "Ubuntu PC not booting up (/dev/nvme0n1p2: clean error)"
date: 2022-05-11
forum: General Help
---

### Post by jefazo92 on 2022-05-11
Hi everyone, I'm having the issue of my Lenovo ThinkStation P350 Intel Core vPro i9, single partition with Ubuntu, not booting up. Whenever I turn on the computer I'm presented with a black screen with a message (see screenshot attached below) and won't do anything else. I have searched the error on Google but haven't found any solution for my desktop. Has anyone ever encountered this error and know how to boot it up? Thanks in advance.


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290426&stc=1[/IMG]

---

### Post by oldfred on 2022-05-11
Please do not post screenshots or photos in line. 
You can easily attach with Forum's Go Advanced Editor and the paperclip icon.

That is not an error, but just saying that partition is fine as it has passed the file checking on boot.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
```
sudo apt-get update
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair


```

Since system can be configured many different ways, you can also run this to document your configuration.
If you want lots of details on hardware you can run this new script. Do not copy data from the screen as it may include data you do not want to share. The upload to pastebin site removes that type of data. Spacebar thru the screens & q to exit screens.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info

```
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

---

