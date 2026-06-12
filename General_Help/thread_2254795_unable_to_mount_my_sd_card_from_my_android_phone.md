---
title: "unable to mount my sd card from my android phone"
date: 2014-11-30
forum: General Help
---

### Post by prakprad on 2014-11-30
Hi i was using ubuntu 12.04 for the past one year. After upgrading to 12.10, my android phone is not being detected for file transfer (which used to happen by default when i connect my phone earlier in ubuntu 12.04). Some one please help me with this.

---

### Post by Bucky Ball on 2014-11-30
Welcome. 12.10 has not been supported for sometime, sorry. I would advise either going back to 12.04 LTS or 14.04 LTS, both supported for five years (2017 and 2019 respectively). 14.10 is also supported, but for nine months. 

Because 12.10 is so old it is unlikely you will get much help with it, unfortunately. 

Please see [here]("http://ubuntuforums.org/showthread.php?t=2229730") and [here]("https://help.ubuntu.com/community/EOLUpgrades") for more tips.

Good luck. ;)

---

### Post by Bucky Ball on 2014-11-30
12.10 has not been supported for sometime, sorry. I would advise either going back to 12.04 LTS or 14.04 LTS, both supported for five years (2017 and 2019 respectively). 14.10 is also supported, but for nine months. 

Because 12.10 is so old it is unlikely you will get much help with it, unfortunately. There are also no updates for 12.10, and that includes security updates.

Please see [here]("http://ubuntuforums.org/showthread.php?t=2229730") and [here]("https://help.ubuntu.com/community/EOLUpgrades") for more tips.

Good luck. ;)

---

### Post by prakprad on 2014-12-02
First of all thank you Bucky Ball. I am terribly sorry. It was ubuntu 14.10 that has the problem detecting my android phone for data transfer, and I mistyped 12.10 for 14.10. Please help.

---

### Post by gordintoronto on 2014-12-02
Install Airdroid on the phone.

---

### Post by Yougo on 2014-12-03
What android version is your phone? android 4 and up don't connect like normal USB drives.

according to [http://askubuntu.com/questions/376815/how-to-connect-mtp-android-device-to-ubuntu-13-10](http://askubuntu.com/questions/376815/how-to-connect-mtp-android-device-to-ubuntu-13-10)

you could try connecting your phone to a USB3 port (with a blue tab on the inside) or installing some packages:
```
sudo apt-get install mtp-tools mtpfs
```

---

