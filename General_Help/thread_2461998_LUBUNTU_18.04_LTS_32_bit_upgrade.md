---
title: "LUBUNTU 18.04 LTS 32 bit upgrade"
date: 2021-05-11
forum: General Help
---

### Post by ubu112 on 2021-05-11
[FONT=arial]Support for this version is ended on April.

If I'm not wrong,it's better to upgrade/change version.

But Lubuntu 20.04 LTS is 64 bit.

Now,I'm searching for an other very lightweight distro with a good support for my old Acer Aspire One AOA150/zg5.

For example,I fund BionicPup32 8.0 but I can't find how long is supported.

Can,please,someone help me and give me some advices.

Thank you[/FONT]

---

### Post by tea for one on 2021-05-11
> antiX comes in four flavours for 32 and 64 bit boxes

The above text was copied from [http://download.tuxfamily.org/antix/docs-antiX-19/FAQ/index.html](http://download.tuxfamily.org/antix/docs-antiX-19/FAQ/index.html)

Worth a look?

---

### Post by Dennis N on 2021-05-11
MX Linux is another that releases a 32-bit OS. Right now, it is #1 on Distrowatch.
I tried it some time ago. It's a nice Independent distro, based on XFCE. I think it uses Debian repositories. The negative for me was that the installer did not support LVM.

---

### Post by ajgreeny on 2021-05-11
I am using Debian 10 on an old 32 bit Netbook with an Atom N270 CPU and just 1G ram.  I use openbox only instead of a full DE such as LXDE as it then uses fewer resources.  I am using the testing repos on this, having changed from the buster to bullseye repos in the sources.list file

It runs fairly well but is less useful for web-browsing as so may sites these days have high resource requirements; it is almost useless for Youtube and any online videos but I use it mainly for browsing this site and other web-forums, so therefore text based sites, and also for email.

It will not run Libreoffice properly so I use abiword and gnumeric instead.

---

### Post by mikewhatever on 2021-05-11
There is no upgrde path for that system. There are also very few usage cases I can think of, for something that obsolete. Rather that look for a "distro with a good support", look for a replacement.

---

### Post by guiverc on 2021-05-11
I have given my opinions here & on the Lubuntu discourse site (one link is [https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/4](https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/4) where I very early on point to a prior post I did with regards `ubuntu-support-status`), which happen to be what @ajgreeny has already stated

> I am using Debian 10 on an old 32 bit Netbook with an Atom N270 CPU and just 1G ram

I tested Debian 10 using the same hardware I tested Lubuntu (and Xubuntu) x86/i386 flavors and with the exception of one really old box; it ran about equal (*Lubuntu outperformed Debian on the most under-powered box I have*).

I would be wary of distros ***downstream*** of Ubuntu (eg. you mention *bionicpup *; where the Bionic likely means using a Ubuntu 18.04 or  Ubuntu's *bionic* base; meaning I'd for sure see if they pick up the ball given 'universe' packages in Ubuntu are now unsupported (*I'm betting they don't, and like Linux Mint use a lower-security model so don't care*). Maybe you won't either, it's up to you.

You can use `ubuntu-support-status` to see how good your Ubuntu support is, which I have mentioned in various posts before so I won't repeat (*I sort of wish I'd written up something more recent for 18.04's EOL but I covered it when Lubuntu/Xubuntu dropped i386 in the disco or 19.04 cycle so felt it was already covered*).  For clues though follow the link I already provided (which will lead you to a [prior link]("https://discourse.lubuntu.me/t/lubuntu-18-04-lts-is-nearing-its-eol-end-of-life/2442") on Lubuntu's discourse but sorry not to the prior more detailed posts)

I still use x86 devices, and currently still have Lubuntu 18.04 LTS on at least one...   If/when I switch, it'll be to Debian which is already running on others.

FYI:  LXQt runs well on i386; the 18.10 & 19.04 Lubuntu ISOs showed that if you ever tried them, so it maybe worth considering (*on Debian of course*), but as @ajgreeny pointed out, you'll get best performance by skipping a full desktop. I have multiple installed (desktops & WMs) on mine, and decide at login which I'll use (*considering what I'll do on the box that session as well*)

---

### Post by amanchesterman on 2021-05-13
The Linux Mint team offer a distro called 'Debbie' which is based on Debian rather than Ubuntu. It uses the Cinnamon desktop but I haven't found that too much of a learning curve. I've installed in on an old laptop, a Dell Vostro machine, and it runs happily: it updates in the usual way and includes Firefox, Thunderbird and LibreOffice, plus quite a few other apps that I don't use. It has Long Term Support. Might be worth a look?

---

### Post by him610 on 2021-05-15
Raspberry Pi Desktop for PC and Mac
[https://www.raspberrypi.org/software/raspberry-pi-desktop/]("https://www.raspberrypi.org/software/raspberry-pi-desktop/")
> If you have an old computer that is no longer powerful enough to run a modern commercial operating system, try Debian with Raspberry Pi Desktop: it can often make the computer usable once more.

I have this installed on an Acer Aspire One AOA110 ZG5. I can't bear to part with it so I just keep installing 32bit operating systems on it.

---

### Post by mikewhatever on 2021-05-15
> **him610 said:**
> Raspberry Pi Desktop for PC and Mac
... 

I have this installed on an Acer Aspire One AOA110 ZG5. I can't bear to part with it so I just keep installing 32bit operating systems on it.

My question is, what do you do after it boots? Sure, you can look at the wallpaper or admire menu icons, and wax nostalgic all day long. If that is what makes you happy, I understand. However, can you list a few practical usage cases a machine with N270 CPU, 1GB RAM doesn't struggle with.
...to put it another way, what would "Debian with Raspberry Pi Desktop" make it usable for?

---

### Post by him610 on 2021-05-15
> ...to put it another way, what would "Debian with Raspberry Pi Desktop" make it usable for?
Same usability as on any of my other computers.... 
Check my connectivity to the internet.
Check for updates.
Check the weather.
Check my email.
Open the browser, check news of my sports teams.
Read and comment on issues in UbuntuForums if I have something to contribute.
I can ssh into any one of my other computers.
If I want to write or modify some bash script files, I can do that.
If I want to upgrade my coding skills in python3, I can do that too.
It has the complete LibreOffice suite.
After all, it is a real computer (x86 CPU) with a real operating system (Debian.) 
It is also my only laptop.

I have upgraded this machine from 512KB Ram to 1.5MB, and the 8GB SSD to 32GB. It is a little slow compared to some of my newer machines, but it still works fine. It used to be my main travel machine, but I don't travel much anymore.

---

### Post by him610 on 2021-05-15
@mikewhatever
```

pi@raspberry:~ $ neofetch
       _,met$$$$$gg.          pi@raspberry 
    ,g$$$$$$$$$$$$$$$P.       ------------ 
  ,g$$P"     """Y$$.".        OS: Debian GNU/Linux 10 (buster) i686 
 ,$$P'              `$$$.     Host: AOA110 1 
',$$P       ,ggs.     `$$b:   Kernel: 4.19.0-14-686-pae 
`d$$'     ,$P"'   .    $$$    Uptime: 46 mins 
 $$P      d$'     ,    $$P    Packages: 1845 (dpkg) 
 $$:      $$.   -    ,d$$'    Shell: bash 5.0.3 
 $$;      Y$b._   _,d$P'      Resolution: 1024x600 
 Y$$.    `.`"Y$$$$P"'         DE: LXDE 
 `$$b      "-.__              WM: Openbox 
  `Y$$                        Theme: Adwaita [GTK3] 
   `Y$$.                      Icons: Adwaita [GTK3] 
     `$$b.                    Terminal: lxterminal 
       `Y$$b.                 Terminal Font: Monospace 10 
          `"Y$b._             CPU: Intel Atom N270 (2) @ 1.600GHz 
              `"""            GPU: Intel Mobile 945GM/GMS/GME, 943/940GML Expr 
                              Memory: 171MiB / 1497MiB 

                                                      


```

---

### Post by mikewhatever on 2021-05-16
> **him610 said:**
> Same usability as on any of my other computers.... 
Check my connectivity to the internet.
Check for updates.
Check the weather.
Check my email.
Open the browser, check news of my sports teams.
Read and comment on issues in UbuntuForums if I have something to contribute.
I can ssh into any one of my other computers.
If I want to write or modify some bash script files, I can do that.
If I want to upgrade my coding skills in python3, I can do that too.
It has the complete LibreOffice suite.
After all, it is a real computer (x86 CPU) with a real operating system (Debian.) 
It is also my only laptop.

I have upgraded this machine from 512KB Ram to 1.5MB, and the 8GB SSD to 32GB. It is a little slow compared to some of my newer machines, but it still works fine. It used to be my main travel machine, but I don't travel much anymore.

Thanks for that. 
It looks like the top half of the list is what you do, while the bottom half is what you can do, but don't. I can relate to that.
There is an 2009 core2duo notebook here, 64bit, at least twice as pwoerful as your Acer. I boot it on weekends to install updates, and occasionally to use an old printer/scanner that doesn't have a driver for W10. 
It does work, but struggles with most everything people here want to do, like social media, gmail, large office docs, or video streaming, so it is not used much. Debian wouldn't boot on it ( probably need non-free stuff), so it has Ubuntu Mate installed with a few things removed or disabled. 

PS: Debian 11 is expected this year with 32bit support, let's see what happens with "a real OS" next.

---

### Post by him610 on 2021-05-16
From Host: AOA110
I have actually donated much more capable machines from around same BIOS date. As I said before, it is my only laptop, and the only one I ever paid for. The two I donated had been inherited from folks who had gotten tired of waiting for Windows to boot up, and I had no personal attachment to them.
I have used the AOA110 to troubleshoot my network in the past. 
I have recently accessed some of my other systems with ssh.
The battery has been replaced three times: although, I don't think I am going to do it again.
One of these days, I probably will donate it. Who wants to see a perfectly good computer get cannibalized!
I do need to wear my glasses when reading from the screen of the AOA110 :)

Some folks only have a computer as old or limited as this, and I am sure they like to hear of someone still making use of one.

By the way, the Raspberry Pi OS for X86 has the easiest installation and setup I have ever done. The *buntus should be this easy.

---

### Post by mikewhatever on 2021-05-16
It is funny how you keep saying "perpectly good computer", "real computer", "real operating system", "usable once more".  A lot of  wishful thinking there. 
While I am glad you find it useful, the reality is, it's only practically effective for trivial or niche tasks like install updates, check the weather, some light coding, silly ascii graphics, a few command line applications, etc.

Good luck anyway.

---

### Post by ubu112 on 2021-05-18
@guiverc,I tried "ubuntu-support-status"and I have 81,3% files supported until April 2023.

I made a live USB with Debian 10.09 with LXQt,it's much slower than Lubuntu 18.04.

I can't make changes because I just  have a live USB.

@ajgreeny,if I change Libre Office with Abiword+Gnumeric,Thunderbird with Sylpheed,Firefox with a light weight browser,which one?

Can I improve? I mean reach almost the Lubuntu speed.

Need I to use "openbox" too?I mainly use it for web browsing.

@guiverc,can you,please,explain to me what are WMs and how to install and change multiple desktop.

Thank you

---

### Post by grahammechanical on 2021-05-18
The important question as far as I can tell is: For how long will the Linux developers continue to provide and maintain a 32 bit i386 kernel? Finding the answer is not easy. I have seen reports of this or that distribution providing i386 support up to 2023 or the latest 2024. What does a person with a 32 bit x86 CPU do in 2 or 3 years time? There are several posts in this thread that answer that question.

Even if a i386 Linux kernel is maintained by the Linux developers beyond 2024 who is going to merge the security patches into the i386 distribution. Debian has the developer resources to do so. Ubuntu has the developer resources but is not going to maintain a i386 kernel any longer. In my opinion any distribution based on Debian or Ubuntu will not have the developer resources to do the merging of the patches.

I found this an interesting read.

[https://www.magzter.com/stories/Computer-Mobile/Linux-Format/The-End-Of-32-Bit](https://www.magzter.com/stories/Computer-Mobile/Linux-Format/The-End-Of-32-Bit)

> Ubuntu isn&#8217;t alone in dropping 32-bit support. Fedora let it go  officially in version 27, released in November 2017, although a 32-bit  netinstall was available up until version 30, released in April 2019.  Arch Linux has been 64-bit only since 2018, but a community-driven Arch  Linux 32 port is available. Debian will continue to support 32-bit  Buster until 2024, and we&#8217;ll hear nearer the time whether its successor  (codenamed Bullseye) will support the older architecture. Mint 20 won&#8217;t  have a 32-bit edition, but Mint fans wanting to keep 
their 32-bit  systems minty should check out Linux Mint Debian Edition. As chance  would have it, the next two pages cover just that.

Suggest giving a Debian 32 bit net install a serious consideration if a person wants to keep 32 bit x86 machines working beyond 2024.

Regards

---

### Post by mikewhatever on 2021-05-18
> **ubu112 said:**
> @guiverc,I tried "ubuntu-support-status"and I have 81,3% files supported until April 2023.

I made a live USB with Debian 10.09 with LXQt,it's much slower than Lubuntu 18.04.

I can't make changes because I just  have a live USB.

@ajgreeny,if I change Libre Office with Abiword+Gnumeric,Thunderbird with Sylpheed,Firefox with a light weight browser,which one?

Can I improve? I mean reach almost the Lubuntu speed.

Need I to use "openbox" too?I mainly use it for web browsing.

@guiverc,can you,please,explain to me what are WMs and how to install and change multiple desktop.

Thank you

LXDE is lighter then LXQT, so your findings are expected. Light wieght programms, especially command line, could help .
If you are sure 18.04 must go, I doubt LXQT is a good candidate. Try AntiX instead.

PS: You can check which packages aren't supported with <ubuntu-support-status --show-unsupported>.

---

### Post by guiverc on 2021-05-18
> **ubu112 said:**
> 
I made a live USB with Debian 10.09 with LXQt,it's much slower than Lubuntu 18.04.


I compared Lubuntu 18.04 LTS using LXDE generally with Debian 10 using LXDE (Debian is available with LXDE, with LXQt and other desktops too). 

When comparing Debian with LXQt I was generally comparing it with Lubuntu with LXQt (ie. 18.10 & 19.04 ISOs for i386 or 32-bit i386; both those are EOL now).

On single core pentium M, pentium 4 machines I found LXQt very fast; far faster than XFCE & the like (GTK3 is rather heavy on those really old cpus).

I did have one really *limited* hp [2003] box (`hp d220mt (dr159p), (celeron 2ghz, 1gb (732mb useable), 82845G/GL Brookdale-G/GE (i915))` where Lubuntu 18.04 LTS did outperform Debian using LXDE.. but I never explored if it was the crappy celeron, or lack of RAM (732mb usable of 1GB is small!), the box just wasn't *fun* to use with Debian (using LXDE or LXQt).

> **ubu112 said:**
> 
I can't make changes because I just  have a live USB.


I don't know what you're asking here sorry.

> **ubu112 said:**
> 
@guiverc,can you,please,explain to me what are WMs and how to install and change multiple desktop.


LXDE & LXQt are desktops, but don't do everything.  Neither (LXDE or LXQt) actually puts a border around a window, or provides the CLOSE, MINIMIZE, MAXIMIZE etc. buttons on the window - it's the *window manager *that actually does that.

Lubuntu uses `openbox` to perform those tasks.  Debian though by default uses `xfwm4` or the XFCE window manager (you can change whichever you use).

Next time you login you, you'll see you can choose to login using `openbox` as a session, which will use less RAM as you won't have LXDE running on your system. It'll mean the loss of panel, menu & options LXDE provides; but openbox has it's own menu you can access when you right-click the background...   (it may seem like the system is broken, as you may not have a wallpaper or a clean background - that's normal until you define one using openbox).  Using a WM only is lighter than any desktop as well.

I'll provide

- [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

 which lists a few WMs 

- openbox
- IceWM
- Fluxbox
- FVWM-Crystal

Note: the link I provided goes off-track here & lists XFCE (a desktop that uses xfwm4) & LXDE (which uses openbox) but the pages intention was for low-memory-systems and not really limiting itself to WMs.  There will be better links on the web, but I prefer using *official* Ubuntu pages.

A debian page, as I don't mind using Debian pages :)  is closer to what I was looking for

- [https://wiki.debian.org/WindowManager](https://wiki.debian.org/WindowManager) 

Personally, of the ones I listed I prefer IceWM, but they are small with regards disk space so I usually have a few loaded on my i386 systems and use the one that suits my temperament (mood) at the time of login.

But don't expect them to provide panel & have nice features found with desktops (some do, but as they use resources, many skip that & provide only what you need to get something done; ie. the minimum).

---

### Post by ubu112 on 2021-05-20
Now I'm using Lubuntu 18.04 and I know that 81,3% files are supported until April 2023.

I'm trying AntiX,thank you for the advice.

it's based on Debian Buster but I don't know how long it's supported.

Can,please,someone let me know.

Thank you

---

### Post by guiverc on 2021-05-20
Debian Buster's EOL hasn't been announced, but is "**~2022**"  See [https://wiki.debian.org/DebianReleases](https://wiki.debian.org/DebianReleases)

The **LTS** project on Debian is  a little clearer with Buster saying June 2024 (see [https://wiki.debian.org/LTS](https://wiki.debian.org/LTS) but don't forget the LTS coverage is only specific packages of Debian; just as Lubuntu 18.04 LTS still has many Ubuntu packages supported; and packages no longer supported).   You should evaluate how useful the LTS is yourself, just as per using Lubuntu 18.04 LTS.

I can't speak to AntiX as I know nothing about it.

---

### Post by tea for one on 2021-05-21
Here is a recent article about 32-Bit distros:-

[https://www.makeuseof.com/linux-distros-with-32-bit-support/](https://www.makeuseof.com/linux-distros-with-32-bit-support/)

---

### Post by ubu112 on 2021-05-23
I'm not sure if to change or not Lubuntu 18.04 with 81,4% files supported.

Is it better to check unsupported files  to decide if change or keep Lubuntu?

I'm not an expert user,I mean if I read unsupported packages,I don't  know what to do.

In this case can someone help me?

Thank you

---

