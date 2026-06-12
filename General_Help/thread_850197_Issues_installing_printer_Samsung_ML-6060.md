---
title: "Issues installing printer Samsung ML-6060"
date: 2008-07-05
forum: General Help
---

### Post by arepaking on 2008-07-05
Hello,

I am having issues when it comes to install my Samsung ML-6060 printer.I followed step-by-step what it is being told in this post: [http://ubuntuforums.org/showthread.php?t=341621&highlight=ml-6060]("http://ubuntuforums.org/showthread.php?t=341621&highlight=ml-6060") but unfortunately it does not work for me.

I downloaded the latest linux drivers from [www.samsung.com](www.samsung.com). This website has onle one type of driver for linux, which is the ML-6060 Unified Linux Driver (ver.2.00.97).

I was able to successfully install this Unified Driver Configurator, I had followed each steps, and when it comes to assign the connection I selected "Parallel /dev/lp0". My printer is connected to my computer via LPT1 port.

I've also tried the following ports without any luck:
Parallel /dev/lp1
Parallel /dev/lp2
Parallel /dev/lp3

The following information is shown by the Unified Driver Configurator when I select my printer:
[B]
Local printer (Idle)
Model: Samsung ML-6060 Series (PS)
URI: Parallel /dev/lp0[/B]

And one more thing, This samsung software has a Test option for your printer. The following will show my results:

[B]Checking port....Failed!
Can't find any devices on parallel:/dev/lp0[/B]

What could I possibly miss? Do I have to make an additional configuration for my port?

Thanks guys, any help would be highly appreciate it.

Kind Regards,
-AK


Updates: 
1) After writing this post I tried to install the HPLIP driver. The funny thing is that it seems that my LPT1 port it is not being recognized by my Ubuntu. I'm saying this because I saw the Parallel Port option disable during the installation. The system proposed me instead the USB connection and Network connection.

2) When running the following command this is what I get: 

[B]nobody@nobody-desktop:~$ sudo cat > /dev/lp0
bash: /dev/lp0: Permission denied[/B]

Why is my permission denied?

---

### Post by arepaking on 2008-07-27
I solved this problem on my own by using an USB connection instead of the Parallel Port.Then I went to linuxprinting.org and I downloaded the driver assigned to the Samsumg ML-6060 which is the HPIJS driver.

BW laser printer, max. 600x600 dpi, works Perfectly!

I hope my post can help anyone out there!

Regards,
-AK

---

