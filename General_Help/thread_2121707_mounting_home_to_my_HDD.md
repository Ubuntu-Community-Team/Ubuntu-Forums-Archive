---
title: "mounting /home to my HDD"
date: 2013-03-02
forum: General Help
---

### Post by Sagar thakkar on 2013-03-02
Hey guys,
I recently installed Ubuntu 12.10 secure on my 24GB SSD.

1.So i want to mount /home to other exsting HDD(750GB) so that my all stuff gets saved there.
2.Previously my ASUS laptop had windows 8 installed.in windows 8 ,full charging battery used to run 3 and half hour 
but after installing ubuntu it runs less than 2 hours only and it heats up  so fast, so heat fan continously runs.

so want to solve this battery problem and mounting /home thind.

---

### Post by Mr. Shannon on 2013-03-02
To answer your first question there is an article about how to do this in the documentation at [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving).

As for the second question, there is no way we can help you without more information.  What is the hardware on the laptop.  In particular does it have hybrid/optimus graphics.

---

### Post by Sagar thakkar on 2013-03-03
> **Mr. Shannon said:**
> To answer your first question there is an article about how to do this in the documentation at [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving).

As for the second question, there is no way we can help you without more information.  What is the hardware on the laptop.  In particular does it have hybrid/optimus graphics.

thanx for the first answering the first question.
my laptop is 
Asus s46M ultrabook
core i5 
nvidia geforce 635M 2GB
750 HDD
24 SSD
optical drive 
3 USB ports (3.0)

I am too much annoyed by this battery thing b'coz it doesnt really last even for 2 hours....
and heat fan remains ON for all the time...It wasnt like that in windows:confused:....

---

### Post by Mr. Shannon on 2013-03-04
It is likely that a large portion of your battery problem is due to your graphics card (which is an optimus card).  This means that it is designed to be turned on and off as needed.  By default, in Linux I think it will run all the time and will not actually do anything for you.  There are three options to remedy this:

1. Go into the BIOS and turn the video card off and use the integrated graphics.

2. Go into the BIOS and set the computer to always use the NVIDIA card. Ubuntu might recognize the card after this and offer to install drivers. I have not tested this.  NOTE: This will not help the battery issue, but It might let you use the NVIDIA card.

3. Use [http://bumblebee-project.org](http://bumblebee-project.org). This will allow you to launch an application and tell it to use the NVIDIA card.  This way the video card will remain off until you specifically enable it for an individual application.  If you do this then please note that it may break your system, however, I just talked someone through how to fix the system after this happens so It can be undone (at least in his case).  There seems to be some confusions as to how to install bumblebee so I will include instructions below:
```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install linux-headers-generic
sudo apt-get install bumblebee bumblebee-nvidia

```

---

### Post by Sagar thakkar on 2013-03-04
Thanks a lot  Mr.Shannon
the problem you identify was correct....Graphics card was consuming most of the battery.
and It looks like bumblebee is working really good .
thanx alot again....

---

