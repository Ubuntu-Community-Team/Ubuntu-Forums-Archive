---
title: "Set brightness failure: empty /sys/class/backlight (no acpi_video0) &amp; boot problem"
date: 2014-04-22
forum: General Help
---

### Post by alireza-rafiee94 on 2014-04-22
I "tried" to set the default brightness for Ubuntu 14.04. Following [here]("http://askubuntu.com/questions/66751/how-do-i-set-default-display-brightness"), At first I did:

  ```
echo 5 > /sys/class/backlight/acpi_video0/brightness

```  then:
  ```
sudo apt-get install xbacklight

```  then copy-pasted below inside the terminal:
  ```
sudo bash -c '{
echo "#!/bin/bash"
echo "xbacklight =30"
} > /etc/lightdm/display-setup-script.sh '

```
then:
  ```
sudo chmod a+rx /etc/lightdm/display-setup-script.sh

```  then:
  ```
if 
  grep ^display-setup-script /etc/lightdm/lightdm.conf ; 
then 
  echo "Already a display-setup-script. It may already do what you need. Else please adjust manually" ; 
else 
  sudo bash -c "echo display-setup-script=/etc/lightdm/display-setup-script.sh >>/etc/lightdm/lightdm.conf" ; 
fi

```

 Then an error occured for the last one such that there's not  lightdm.conf (I don't understand why because I checked it later and it  was there!). So I removed "display-setup-script.sh" and even uninstalled  xbacklight. But now inside /sys/class/backlight is empty whereas it  should have a link "acpi_video0" and another folder. After restarting  the system, Ubuntu won't boot properly and says "the disk drive is not  ready yet or present" and gives the UUID (The disk is an encrypted SSD).
  I would be thankful if anyone could tell me how to fix the system  since I, idiotically, don't have a backup (and the backup for the  decryption key as well!)



  P.S. My system is a Lenovo Thinkpad X230, Intel graphics card.

---

