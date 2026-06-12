---
title: "Stuck on boot"
date: 2017-10-01
forum: General Help
---

### Post by sonsoflinus on 2017-10-01
Hello fellas, first post here so I'm terribly sorry if I'm in the incorrect subforum. :) 

So I got a pretty old **Lenovo Ideapad S10E** which I want to use for my Uni work, so I decided to go with **Ubuntu 17.04**. I created a bootable USB drive as this notebook doesn't have CD/DVD drive and I'm able to go as far as the Installer boot menu, where the whole thing just freezes. No errors present, nothing, just stuck. I've tried resetting multiple times, the BIOS correctly boots the USB as I am able to see the boot menu Ubuntu has, however, nothing from there...

Any idea how should I proceed? Is it the laptop that's too poor for Ubuntu or am I doing something incorrectly? 

Thank you very much in advance! :)

---

### Post by yancek on 2017-10-01
You should post more details on your hardware such as processer speed, RAM and graphics card to get advice.  Depending upon the hardware, you may need to use a lighter Linux or Ubuntu derivative such as Xubuntu or Lubuntu.

---

### Post by ian-weisser on 2017-10-01
The stock S10e had 1GB RAM, insufficient to run the current default Unity flavor of Ubuntu.
1) Try again with Xubuntu or Lubuntu, which require fewer resources.

For troubleshooting:
2) It's possible for the download .iso to be corrupted during download. Use MD5SUM to check before copying to a USB.
3) An interrupted USB copy will corrupt the installer. Make sure you are using the recommended method.
4) An old USB stick may have corrupted memory on board.

---

### Post by sonsoflinus on 2017-10-01
After a bit more troubleshooting on my end, it indeed seems like it's just the notebook that's way below Ubuntu's specific. I guess I'll just make-do with Lubuntu in the meantime. 

Thank you, Ian! :)

---

