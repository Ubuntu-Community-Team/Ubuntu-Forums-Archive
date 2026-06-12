---
title: "My computer went dead after upgrading from Ubuntu 12.04 to 12.10 :("
date: 2013-09-16
forum: General Help
---

### Post by Tarun_Kumar_Singh on 2013-09-16
**History:**
My assembled computer is very old (bought in 2007) with the specs 2.2 GHz., Core2Duo, 1 GB RAM, 32 Bit and no USB boot support. Earlier I had Windows XP installed on it. However in 2012 I asked one of the local vendor to install Windows 7 on it. It was running fine until few months back it started showing that my Windows is not genuine. Since, I changed my location so I had no contacts with the older vendor so I just ignored the warning initially. However, the computer got slow and slow with the time and also started showing dead screens. I talked with MS guys and they asked me to buy their product as my Windows is found to be a pirated version. Obviously the price of Windows is too much and beyond my pocket and hence I thought to try something else and zeroed on Linux.

So, I installed Ubuntu 12.04 from Wubi installer. My C drive still had faulty windows so I dedicated whole D drive to Ubuntu. The dual boot was working very fine and I was very happy to work on 12.04.

**Problem:**
The problem started when one day I thought to upgrade my 12.04 to 12.10. Actually I wanted to have 13.04 as I have read that 12.10 is not so good. However, to get the 13.04 I needed to first upgrade the 12.04 to 12.10. I ran the update manager and started the upgrade. Everything worked fine and I was asked to restart my computer to finish the upgrade. After pressing the OK my system restarted and showed me the screen to choose Windows or Ubuntu. I choose Ubuntu which only showed me a purple screen and then went black with a underscore '_' character on it. After that nothing happened. When nothing happened for next 30 mins I again rebooted my computer and choose Ubuntu but the results were same.

For couple of days whenever I tried to run Ubuntu it simple showed me the black blank screen only. So finally I thought to search for an answer on Internet by booting with Windows, however now my computer is even not showing anything.

Whenever, I am switching my computer only my CPU shows the lights that it is working but my screen shows a blank and no other peripherals like keyboard or mouse works.

Please help and let me know what to do? As of now I am just cursing myself that why i thought of upgrading it.

Thank you in advance for your suggestions and also please forgive me for such a long story and bad English. Please treat me as newbie and request you to give your suggestions in a simple manner.

---

### Post by Kirboosy on 2013-09-16
Let me be the first to say, Welcome to the Forums! :D

Well, all hope is not lost. If push comes to shove you could reinstall Ubuntu from scratch. Your files can even be rescued by booting a new LiveCD of Ubuntu 13.04 and copying the files on the computer to a external hard drive.

First lets try this. 
[Boot Repair on Ubuntu]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu")

Let me know if that fixes it or changes anything.

Hope that helps!
~Caboose

---

### Post by Tarun_Kumar_Singh on 2013-09-16
> **Caboose885 said:**
> Let me be the first to say, Welcome to the Forums! :D

Well, all hope is not lost. If push comes to shove you could reinstall Ubuntu from scratch. Your files can even be rescued by booting a new LiveCD of Ubuntu 13.04 and copying the files on the computer to a external hard drive.

First lets try this. 
[Boot Repair on Ubuntu]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu")

Let me know if that fixes it or changes anything.

Hope that helps!
~Caboose

Thank you for the warm Welcome Caboose! Your reply relieved me that things will be fine. I will try to follow the instructions given in the link you provided and will give the feedback.

Thank you again!

---

### Post by Impavidus on 2013-09-16
Wubi depends on the Windows boot loader and the Windows file system, including the Windows file system repair tool (fchk if I'm right) to repair any file system damage. When you already have a damaged Windows installation this is dangerous.

Show us the summary made by bootrepair. The next step is, booted from a live disk, to try to mount your D partition (not guaranteed to work) and then your root.disk file with the Ubuntu file system to backup all your important files. Unless you already have good backups of course.

---

### Post by Tarun_Kumar_Singh on 2013-09-19
Update:
So I tried the boot repair as well as tried with Live CD but nothing worked. The computer refused to boot. Finally I asked one of the local vendors to check and run my system.

Today when I received my computer, the vendor had installed Windows 8 on C: drive however formatted my D Drive which had the Linux :(. Now I have another problem. Please help!

On starting my computer the system asks me to choose between Windows or Ubuntu. I can login into Windows 8 but I know if I choose Ubuntu then nothing will happen as the drive in which Ubuntu was installed is formatted now. What to do now? Should I again install the Ubuntu in my D Drive where it was earlier installed? Will this make me login to ubuntu normally?

---

