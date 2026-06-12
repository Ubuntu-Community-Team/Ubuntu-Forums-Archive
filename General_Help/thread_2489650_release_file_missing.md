---
title: "release file missing"
date: 2023-08-05
forum: General Help
---

### Post by mountainman70 on 2023-08-05
I have a Dell 7010 and a Dell 9020 both dual booting W10 and Ubuntu Mate 22.04.2.
Thursday I got a red dot with a slash in it saying there was a problem and I may have broken packages.
This is the error I got  (E: The repository 'https://ppa.launchpadcontent.net/ubuntu-mate-dev/trusty-mate/ubuntu jammy Release' does not have a Release file.)
Nothing I have tried has worked and I don't know how to fix this. These are some sudo commands I tried.

sudo apt update
sudo apt upgrade
audo apt autoclean
sudo apt --fix-broken install
sudo apt autoremove

---

### Post by grahammechanical on 2023-08-05
If I remember correctly, that error refers to the fact that the PPA has not been upgraded to 22.04 (jammy). Have you recently upgrade the OS from an earlier release? I wonder what 

> trust-mate

refers to? Ubuntu Trusty was 14.04. It cannot surely refer to that release!

Regards

---

### Post by mountainman70 on 2023-08-05
Yes I always upgrade to the newest release by using Ubuntu upgrade. Do I need to purge trusty  and how do i do that?

---

### Post by yancek on 2023-08-06
Have you tried commenting out the line below in your /etc/apt/sources.list file by placing a # at the beginning of the line?

>  [https://ppa.launchpadcontent.net/ubuntu-mate-dev/trusty-mate/ubuntu](https://ppa.launchpadcontent.net/ubuntu-mate-dev/trusty-mate/ubuntu) jammy Release

---

### Post by grahammechanical on 2023-08-06
There is another way to remove a Personal Package Archive (PPA). Open Software & Updates>Other Software tab. You should see the PPA listed there. Untick it.

Regards

---

### Post by mountainman70 on 2023-08-06
yancek
                     
  I don't have that line in sources.list.

---

### Post by mountainman70 on 2023-08-06
grahammechanical---Did that and did not make any difference.

---

### Post by mountainman70 on 2023-08-06
O K I have solved my problem. I had removed the offending ppa from software and updates,  but because of a sick family member, I thought I had updated software and updates. How ever I realized I had not. Once I updated the software everything is back to normal. 
Thanks for the replies.

---

