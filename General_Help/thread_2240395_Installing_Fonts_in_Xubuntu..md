---
title: "Installing Fonts in Xubuntu."
date: 2014-08-19
forum: General Help
---

### Post by gordon99 on 2014-08-19
I dual boot Windows 7 and Xubuntu 14.04 and have copied and pasted some fonts from Windows7 into a Fonts folder in my Xubuntu 14.04 /home/username/ directory. I have tried dragging and dropping the imported Fonts folder into the /usr/shared/fonts folder and that does not work. I can't seem to be able copy and paste the folder into the .../fonts folder. I have also tried using terminal commands seen on different web sites. When following a 'Readme' file in 'fonts' which said I should use the command  "apt-get install -reinstall ttf-mscorefonts-installer" a message was returned suggesting an 'r' was missing. My script was an exact copy of the 'Readme' instruction as far as I could tell so I can only assume I should have been using a different command. Could someone kindly post a step by step guide that explains how to get these fonts into use, particularly for Apache Open Office, or provide a link to an up-to date instruction. Thank you.

---

### Post by oldos2er on 2014-08-19
Your command should be ```
sudo apt-get install --reinstall ttf-mscorefonts-installer
``` Since /usr/share/fonts/ (not "shared") is outside your home folder, you'd need sudo privileges to write to it: ```
gksudo nautilus
```

---

### Post by gordon99 on 2014-08-20
oldos2er, Thank you very much for your help. The ttf fonts came rolling in. I am now reading the PDF download. 500 pages to get through so I have a lot to learn. Will mark as solved.
PS I thought the song went: Daddy, you've been on my mind.

---

