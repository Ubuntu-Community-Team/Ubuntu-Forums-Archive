---
title: "Wireless not working Toshiba L50-B-1WP"
date: 2015-05-03
forum: General Help
---

### Post by Canaryguy on 2015-05-03
Hello,

My wired connection works fine but when I try to use wifi I can see the available wifi connections but the connection is never established although I give the right password.

Do I have to update or install a driver?

I don't know if that has something to do with the problem above but I have installed samba in both my netbook and laptop. Both have Ubuntu 15.04 x64 and in both I have installed samba. When I share a folder in the Toshiba computer I have access to this folder in my netbook but when I share a folder in my netbook I can't access it in the Toshiba computer.

Does anybody find a solution?

---

### Post by kc1di on 2015-05-03
First thing we need to know is what wireless card is in that machine. 

Go to a terminal and type the following

```
lspci
```

Also runs this script in a terminal and copy and past the resulting txt file which will be saved in your home folder. 
it give valuable information about your wireless connections. 

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

(Just copy and past it into a terminal and hit enter , it will ask you for your password)

good Luck :)

---

### Post by Canaryguy on 2015-05-03
**lspci shows the following:**

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
07:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
09:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265]

**The script shows:**

[https://cloud.openmailbox.org/public.php?service=files&t=76cb4163a7d9d77bb0f351ffbae91b22]("https://cloud.openmailbox.org/public.php?service=files&t=76cb4163a7d9d77bb0f351ffbae91b22")

---

### Post by kc1di on 2015-05-03
Ok take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2264792") and try Chilli555's fix.  see it that will work for you.

---

### Post by Canaryguy on 2015-05-03
> **kc1di said:**
> Ok take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2264792") and try Chilli555's fix.  see it that will work for you.

I followed all the steps but unfortunately it didn't work here. Thanks anyway.

---

### Post by kc1di on 2015-05-03
one other thing you might want to try is going to network manager and edit connections click on your wireless network and under IPv6 tab switch to ignore. 
give that a try.

---

### Post by Canaryguy on 2015-05-03
> **kc1di said:**
> one other thing you might want to try is going to network manager and edit connections click on your wireless network and under IPv6 tab switch to ignore. 
give that a try.

Yes, in the thread that you suggested is that mentioned that but it had no effect.
I guess I have to wait until a new driver/update is released. Meanwhile I'll try a live session with other distributions and I'll see if the same problem is still there.

---

### Post by pd65 on 2015-05-26
I've the same problem. The wired connection is Ok. The IP6 is on Ignore. I belive is a driver problem.

---

