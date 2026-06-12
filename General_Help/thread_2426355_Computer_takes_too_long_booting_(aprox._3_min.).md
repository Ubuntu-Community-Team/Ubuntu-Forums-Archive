---
title: "Computer takes too long booting (aprox. 3 min.)"
date: 2019-09-07
forum: General Help
---

### Post by zetomes on 2019-09-07
[COLOR=#203243][FONT=Helvetica]Greetings all and many thanks for your attention:

[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]I installed **Lubuntu 18.04 LTS** on a** inspiron 1525**. I also partitioned the hard disk. The battery isn’t working so I took it from the computer. Initially there was a problem with the wireless but now (thanks to the great Ubuntu community) it’s perfectly working.

[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]The computer works very fine with video streaming, Libre Office, Internet, everythings seems to work very fluidly. The only problems are:[/FONT][/COLOR]

[LIST]
[*]it takes about **3 minutos to boot**. There’s also a huge listing at the booting;
[*]when hibernating it takes a minute or so waking up;
[*]when shutting down also shows a scroll of information, but it’s quite fast turning off.
[/LIST]

[COLOR=#203243][FONT=Helvetica]I would like to know **how to create a file with that information** (booting and shutting down) so that if possible I could correct any errors by your guidance and also if I can **generate a file with the schematics of my partitioning** so that any mistake could be amended in the same way.

[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]PS:[/FONT][/COLOR]

[LIST]
[*]I analysed everything, memory, disk, and the results were all fine.
[*]the previous operating system was Windows Vista
[*]I didn’t update the BIOS
[/LIST]

[COLOR=#203243][FONT=Helvetica]Thanks in advance[/FONT][/COLOR]
[COLOR=#203243][FONT=Helvetica]José[/FONT][/COLOR]

---

### Post by zetomes on 2019-09-07
I tried to generate a **boot.txt **file as **[this post]("https://discourse.lubuntu.me/t/is-this-normal-startup/384/4")** suggests, but either I can't find its location (used **Catfish** to try to find it) or I didn't type properly the commands...

[FONT=arial]**[COLOR=#333333]systemd-analyze blame; systemd-analyze critical-chain > boot.txt[/COLOR]**[/FONT]

---

### Post by cruzer001 on 2019-09-07
Try this
```
systemd-analyze blame > boot.txt
```
```
systemd-analyze critical-chain > boot2.txt
```

---

### Post by zetomes on 2019-09-07
Thank you, 

and here it goes:

* [**boot.txt**]("https://pastebin.ubuntu.com/p/N7rhm8m7tM/")
* [**boot2.txt**]("https://pastebin.ubuntu.com/p/7nGpskfyyv/")

also using the command "**dmesg >blah**" for listing the boot messages:

* [**blah**]("https://pastebin.ubuntu.com/p/RYsx4gfgcc/")

---

### Post by cruzer001 on 2019-09-07
Just for comparison here's my top 4 processes.
> 1.339s dev-sda1.device
1.321s gpu-manager.service
1.222s systemd-journal-flush.service
697ms systemd-resolved.service
But thats i7 + SSD.  What are you running?  Please post:
```
inxi -b
```
You may have to install it.

But you say three minutes.  Wonder if you have other things going on.  please post:
```
df -h && snap list
```

---

### Post by cruzer001 on 2019-09-07
And in blah you have a repeat error.  Going to have to search that.

---

### Post by guiverc on 2019-09-08
I'm not a fan of people posting 'help me' in multiple places ([https://discourse.lubuntu.me/t/computer-takes-3-min-booting/394](https://discourse.lubuntu.me/t/computer-takes-3-min-booting/394)) , so I've not put much effort into this.  Walter (wxl) over on Lubuntu suggested ([https://forums.linuxmint.com/viewtopic.php?t=273797](https://forums.linuxmint.com/viewtopic.php?t=273797)) maybe helpful in chasing down issues in your `dmesg`, I just compared it to the boot messages of my thinkpad t43 running the same Lubuntu 18.04(.3) LTS x86. The biggest difference is more [drm] messages in yours, which maybe related to your i915 and my amd radeon, but I didn't boot a box another box using an i915 for comparison.

Your systemd-analyze have two huge items
[I]1min 30.779s gpu-manager.service
    1min 26.859s plymouth-quit-wait.service[/I]which relate to the i915 and maybe relate to drm I saw.

---

### Post by zetomes on 2019-09-08
Greetings and many thanks again for your help!

Here they go:
* [COLOR=#000000][FONT=&quot]**[inxi -b]("https://pastebin.ubuntu.com/p/RqYgnkTrgZ/")**
[/FONT][/COLOR]* [B][[COLOR=#000000][FONT=&quot]df -h && snap list[/FONT][/COLOR]]("https://pastebin.ubuntu.com/p/xTZftCtkrm/")
[/B]

---

### Post by zetomes on 2019-09-08
> **guiverc said:**
> I'm not a fan of people posting 'help me' in multiple places ([https://discourse.lubuntu.me/t/computer-takes-3-min-booting/394](https://discourse.lubuntu.me/t/computer-takes-3-min-booting/394)) , so I've not put much effort into this.

Well, this guy that posted in two different places doesn't have enough time because he's a father in full-time + working, so he has to find the best and quickest place for answers. And because he's a nullity in Linux but he has the best intentions to install it for free on his friends computers (because they don't have money to buy new ones to support new Windows versions) and he never posted at these forums he's also unsure if he's asking the right questions at the right places... he tried two shots. So, I appreciated very much your help [**here**]("https://discourse.lubuntu.me/t/computer-takes-3-min-booting/394"), and I respect and applaud profoundly the cooperative essence of these forums and their members, and please don't take me wrong, but don't waste more of your precious time with me. 
Thank you.

---

### Post by GhX6GZMB on 2019-09-08
You have the (in)famous Intel 965 chipset problem.

You'll need to edit /etc/default/grub (sudo is needed)

Change the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=SVIDEO-1:d"

Save and update grub (sudo update-grub).

Reboot. Then you'll be fine.

---

### Post by zetomes on 2019-09-08
> **ml9104 said:**
> You have the (in)famous Intel 965 chipset problem.

You'll need to edit /etc/default/grub (sudo is needed)

Change the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=SVIDEO-1:d"

Save and update grub (sudo update-grub).

Reboot. Then you'll be fine.

I would kiss you on your forehead if you were here!
It's perfect, 30 seconds booting, 3 seconds shutting down.
The computer is anew!

Major thanks [COLOR=#DD4814][COLOR=#000000][cruzer001]("https://ubuntuforums.org/member.php?u=2084993"), [/COLOR][/COLOR][[COLOR=#000000]ml9104[/COLOR]]("https://ubuntuforums.org/member.php?u=2127041")[COLOR=#000000] , you made my day[/COLOR]!

---

### Post by GhX6GZMB on 2019-09-08
You're welcome.
With my old HP laptop I diddled around for two days before someone had the solution.
Enjoy your new installation :)

BTW, your boot/shutdown times are equal to mine.

---

### Post by zetomes on 2019-09-08
Thanks, I really appreciate this! :D
My next quest is with its battery.

---

### Post by mörgæs on 2019-09-08
Good that you got the problem solved. Please mark the thread so.

---

### Post by zetomes on 2019-09-08
Done!

---

### Post by Skaperen on 2019-09-08
next: how to make the installer detect this and adjust accordingly?

---

### Post by GhX6GZMB on 2019-09-09
> **Skaperen said:**
> next: how to make the installer detect this and adjust accordingly?

Since the problem persists since at least 12.04 LTS, there must be another issue with changing the installer. I've no idea which.

---

