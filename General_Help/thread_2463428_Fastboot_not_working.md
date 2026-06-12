---
title: "Fastboot not working"
date: 2021-06-10
forum: General Help
---

### Post by misternemo on 2021-06-10
Hello folks

I have a problem with wanting to flash a custom rom on my phone while connecting my phone i can use the adb devices command and adb reboot bootloader command but the fastboot command does nothing i have searched the far reaches of the web can someone please help i wil post details below.



trying this on a sony xz1 compact and a hp elitebook 6930p

used the following commands

Open your terminal and use these commands:
 
[LIST=1]
[*]sudo apt update 
[*]sudo apt upgrade 
[*]sudo apt install android-tools-adb 
[*]sudo apt install android-tools-fastboot 
[/LIST]

then checked if it worked with adb version


then downloaded the flashboot folder from  [https://developer.android.com/studio/releases/platform-tools](https://developer.android.com/studio/releases/platform-tools)

Then i unzip and open the folder and while in the folder i open a terminal and then start with 

sudo adb devices (works)
sudo adb reboot bootloader(works)
sudo fastboot  (does nothing)

it has been six weeks it has been driving me crazy any help wil be greatly epricated.

Kind regards

n

---

### Post by alcealcibiade on 2022-01-10
Have you tride fastboot -h?

---

