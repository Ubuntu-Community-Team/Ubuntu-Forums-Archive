---
title: "Ubuntu 14.04 crashed"
date: 2016-06-18
forum: General Help
---

### Post by 978753351 on 2016-06-18
Am I the only one who met this problem? I used Ubuntu for about a week and it worked fine. But when I startup my laptop this morning. And I found the network options are grey and I can't choose any of it. I first think of restart however it doesn't work. I open the terminal it says my username @ubuntu. However when i go into the settings-> user account. It says "failed to cotact the account service. Make sure that the account service is installed and enabled." I try to copy my files into usn device. But the laptop could not even find the device. And also some settings are missed and I can't used them properly. What Happened? How to fix these.. Please help

---

### Post by grahammechanical on 2016-06-18
When we install Ubuntu we set a user name and a name for the machine to identify it to a network. The name that you choose for the machine is ubuntu. True? There should be a user name in front of the @. To illustrate, this is what I see when I open a terminal: graham@Ub1604:~$ 

It is possible to switch off the network adapter. Especially if the machine is a laptop. It reduces battery drain. Are you sure that the network adapter is not switched off? Please run this command

```
rfkill list
```

This is what I see

> graham@Ub1604:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


If you see "Soft blocked: yes" it means the WiFi adapter is not enabled by the operating system. If you see "Hard blocked= yes" then it means that the WiFi adapter is physically switched off. Perhaps by the pressing of a keyboard combination.

Do you have Windows installed on this machine? If you do and you switch off the WiFI adapter in Windows to save battery power, then it will not be switched on when you load Ubuntu.

Oh, one more thing. It is bad manners to be impatient. We are all volunteers. We live in different parts of the world. We have our own lives to live. Allow at least 24 hours before repeating a request for help.

Regards.

---

### Post by QDR06VV9 on 2016-06-18
Please do not bump your thread before 12 hrs after posting.
We are all volunteers here and come from different timezones and as such sometime the person that has a solution for your problem is not on-line ATM.
One more piece of advise is to state your problem with clear Details && Specs, and Version of the current OS.
Thanks and Good Luck

---

### Post by 978753351 on 2016-06-18
Oh sorry about being impatient. I installed only Ubuntu and I can still access those files I have .I type the command and it says "software block no. Hardware block no." And besides wifi, there are other serious problems with my laptop. I m not sure it is software or hardware problem. Thanks for your help!

Fine I m new and I dont know the rules here sorry and I won't anymore

---

### Post by QDR06VV9 on 2016-06-18
> **978753351 said:**
> Fine I m new and I dont know the rules here sorry and I won't anymore
No Worries just being informative:) We thought you might be new to the Forums and Welcome:)

---

