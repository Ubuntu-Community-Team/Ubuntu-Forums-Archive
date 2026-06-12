---
title: "Perfomance problem 13.10"
date: 2013-11-25
forum: General Help
---

### Post by coffeespoon on 2013-11-25
hello guys,

please could you advise me how to setup the ubuntu in order to performance.
I have 13.10 distribution and it need to be once per two hours restarted (unfortunately more than my previous OS XP :))
Regular problem is with Nautillus which is useless and NetBeans. When I start it the ubuntu will freeze in a few minutes (OS doesn't swap anything).

Usually comp has about 30% usage of RAM and when it starts swapping OS is freezing.

Distro is 32bit and machine has 2GB.

Thank you in advance.

Lucas

---

### Post by fantab on 2013-11-26
Tell us more about your machine's other specs like Graphics, CPU etc...
If Processor is 64bit then you should install 64bit Ubuntu.

Sometimes, Reinstalling Ubuntu can be a good option.

---

### Post by coffeespoon on 2013-11-26
Hi,

I have been to 64bit but it was very slow and I decided to go on 32 bit Ubuntu Which I had been using for couple years without any problem. I have also already tried to reinstall it without effect.

I found this on Lenovo's specification (Lenovo IC C540)


[LIST]
[*][COLOR=#000000][FONT=Arial]Graphic - [/FONT][/COLOR][COLOR=#555555][FONT=Arial]Intel® HD Graphics 2500 [/FONT][/COLOR]
[*][COLOR=#555555][FONT=Arial][/FONT][/COLOR]Processor - [COLOR=#555555][FONT=Arial]Intel® Core™ i3[/FONT][/COLOR]
[/LIST]

[LIST]
[*][COLOR=#555555][FONT=Arial]Memory - 2GB 1600GH[/FONT][/COLOR]
[/LIST]
[LEFT][COLOR=#555555][FONT=Arial]
Is that enought? I can also run some command to get more details.

Thanx a lot.
L
[/FONT][/COLOR]
[/LEFT]

---

### Post by fantab on 2013-11-26
By using 32bit you are NOT utilizing that processor to its fullest.

Do you have a SWAP partition? If you are not sure post the output of:

```
sudo fdisk-l
sudo parted -l
```

Another thing... Ubuntu with Unity or Gnome-Shell and a few other DE's consumes more resources. If I were you, with a machine with 2Gb RAM, I would either get me more RAM or try a lighter flavor of Ubuntu, like Xubuntu. In fact on my netbook with 2Gb RAM I use Xfce and its runs quite fast than Unity or Gnome-shell.

---

### Post by philinux on 2013-11-26
Moved to General Help forum.

---

### Post by grahammechanical on 2013-11-26
If the system freezes when you load Netbeans, then the problem must be to do with Netbeans. It is logical. yes?

> [COLOR=#000000] NetBeans. When I start it the ubuntu will freeze in a few minutes[/COLOR]

what version have you installed. The software centre has Netbeans version 7.0.1. The latest version is 7.4 but when we install outside of what is in the software centre we may have problems with missing libraries (dependencies). In the case of Netbeans it may require a version of Java that not installed on your machine. I look at the reviews in the software Centre and many people mention Netbeans crashing.

Regards.

---

### Post by coffeespoon on 2013-11-27
Hi,

output is below
sudo fdisk -l
[I]
 Disk /dev/sda: 500.1 GB, 500107862016 bytes
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 60 801, celkem 976 773 168 sektor&#367;
Jednotky = sektory po 1 * 512 = 512 bajtech
Velikost sektoru (logického/fyzického): 512 bajt&#367; / 4096 bajt&#367;
Velikost I/O (minimální/optimální): 4096 bajt&#367; / 4096 bajt&#367;
Identifikátor disku:&#8239;0x000caf6e

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/sda1   *        2048   972777471   486387712   83  Linux
/dev/sda2       972779518   976771071     1995777    5  Roz&#353;í&#345;ený
Oddíl 2 neza&#269;íná na hranici fyzického sektoru.
/dev/sda5       972779520   976771071     1995776   82  Linux swap/Solaris

Disk /dev/mmcblk0: 31.9 GB, 31914983424 bytes
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 3 880, celkem 62 333 952 sektor&#367;
Jednotky = sektory po 1 * 512 = 512 bajtech
Velikost sektoru (logického/fyzického): 512 bajt&#367; / 512 bajt&#367;
Velikost I/O (minimální/optimální): 512 bajt&#367; / 512 bajt&#367;
Identifikátor disku:&#8239;0x00000000

   Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/mmcblk0p1            8192    62333951    31162880    c  W95 FAT32 (LBA)[/I]

and sudo parted -l
 
[I]Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Tabulka oddíl&#367;: msdos

&#268;íslo  Za&#269;átek  Konec  Velikost  Typ       Systém soubor&#367;  P&#345;epína&#269;e
 1     1049kB   498GB  498GB     primary   ext4            boot
 2     498GB    500GB  2044MB    extended
 5     498GB    500GB  2044MB    logical   linux-swap(v1)[/I]

Thats it.

As I see I do not have swap partion. Am I right? Please could you help me how to create it without impact into used sectors?

Many thanx,
L

---

### Post by fantab on 2013-11-27
Yes, you do have a Swap parittion.
> [I]&#268;íslo  Za&#269;átek  Konec  Velikost  Typ       Systém soubor&#367;  P&#345;epína&#269;e
 1     1049kB   498GB  498GB     primary   ext4            boot
 2     498GB    500GB  2044MB    extended
 **5     498GB    500GB  2044MB    logical [COLOR=#006400]  linux-swap(v1)[/COLOR]**[/I]

Please reply to 'grahammechanical's' post. 
If the problem is with 'netbeans' and if you have installed it from a source other than 'Software Center' then its possibly the cause of your woe. Uninstalling it and re-installing it from 'Sofware Center' may solve your issue.

---

### Post by coffeespoon on 2013-11-27
NetBeans is 7.3.1, Java 1.7.0_45

But the problem is also with Nautilus and e.g. Ubuntu SW center. f-spot neither starts. For instance I had to remove chromium because it was horrible to run on 13.10.

---

### Post by coffeespoon on 2013-11-27
Hmm. :))

Sorry. I've missed it.
> Yes, you do have a Swap parittion.

---

