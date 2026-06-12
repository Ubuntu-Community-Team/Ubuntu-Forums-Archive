---
title: "how do I install 32-bit software on Xubuntu 20.04?"
date: 2020-11-01
forum: General Help
---

### Post by ardouronerous on 2020-11-01
I need 32-bit software because the driver of my printer is 32-bit. Now, there is a driver for my printer available in CUPS, but the drivers from Canon are more feature complete then the one in CUPS, unfortunately.

My printer is a Canon PIXMA iP2700 and I made this tutorial for myself and others to install the 32-bit printer drivers: [https://ubuntuforums.org/showthread.php?t=2395967&page=2](https://ubuntuforums.org/showthread.php?t=2395967&page=2)

However, the instructions don't seem to work anymore. I've already installed 32-bit architecture:

 ```
sudo dpkg --add-architecture i386
sudo apt-get update
```

However, when I tried to install one of the dependencies with GDebi, this is the result:

```
sudo gdebi libtiff4_3.9.7-2ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
This package is uninstallable
Dependency is not satisfiable: multiarch-support
```

---

### Post by HermanAB on 2020-11-02
I would use a $20 Raspberry Pi with 32bit Raspbian and set it up as an ethernet print server.

---

### Post by ardouronerous on 2020-11-02
> **HermanAB said:**
> I would use a $20 Raspberry Pi with 32bit Raspbian and set it up as an ethernet print server.

My printer doesn't have ethernet capabilities unfortunately.

---

### Post by CelticWarrior on 2020-11-03
> **ardouronerous said:**
> My printer doesn't have ethernet capabilities unfortunately.
You wouldn't need a "[COLOR=#000000]$20 Raspberry Pi with 32bit Raspbian" if the printer had Ethernet.[/COLOR]

---

### Post by ActionParsnip on 2020-11-03
The raspberry pi would connect to the printer via USB and you can then share the printer online using the raspberry pi's ethernet port or even WiFi.
Have you contacted Canon support? Do they have guides on their website for this?

---

### Post by ardouronerous on 2020-11-03
> **ActionParsnip said:**
> The raspberry pi would connect to the printer via USB and you can then share the printer online using the raspberry pi's ethernet port or even WiFi.
Have you contacted Canon support? Do they have guides on their website for this?

I cannot buy a Raspberry Pi right now due to the pandemic, I'm on lockdown and ordering online isn't an option, we don't have online shopping here in my country, we're a third-world country.

Is there no way to implement 32-bit support on Xubuntu 20.04?

---

### Post by CelticWarrior on 2020-11-03
The problem isn't the lack of 32-bit support.
The problem is your driver is too old and now has unsatisfiable dependencies. With 18.04 it was an hack already with the installation of deprecated libraries.

---

### Post by ardouronerous on 2020-11-03
> **CelticWarrior said:**
> The problem isn't the lack of 32-bit support.
The problem is your driver is too old and now has unsatisfiable dependencies. With 18.04 it was an hack already with the installation of deprecated libraries.

What about installing multiarch-support? Where can I find that?

---

### Post by CelticWarrior on 2020-11-03
[https://packages.ubuntu.com/search?keywords=multiarch-support](https://packages.ubuntu.com/search?keywords=multiarch-support)

---

### Post by ardouronerous on 2020-11-03
I installed multiarch-support:

```
 sudo gdebi multiarch-support_2.27-3ubuntu1.2_amd64.deb
```

But the dependency still wont install:

 ```
sudo gdebi libtiff4_3.9.7-2ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
This package is uninstallable
Dependency is not satisfiable: multiarch-support
```

Do I need to restart my system after installing multiarch support?

This is very frustrating that I can't get my printer to run on this, well, my workaround is to use Windows XP on Virtualbox to run my printer, but still, I want to use Xubuntu to print stuff.

I have my printer's ppd file from Canon, is there a way to use that?

---

### Post by HermanAB on 2020-11-03
Hmm, another way is to enable virtual machines with GnomeBoxes or Virtualbox and then download a suitably old version of Ubuntu that can provide the required 32 bit support and set it up as a virtual machine.  Then, you can hook the printer to the virtual machine and set it up as an ethernet print server, so that you can print from your real machine to the virtual machine to the printer.  This is all a bit easier said than done, but you won't be sorry to learn how to make virtual machines and configure the networking - it is extremely handy and a much sought after skill - may even land you your next job.

---

