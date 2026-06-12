---
title: "how can i find out my pc hardware specifications without formatting my PC drives ?"
date: 2024-08-04
forum: General Help
---

### Post by amoalabuba on 2024-08-04
Please Answer that if my PC is using the latest Ubuntu release compatible with a 4 MB RAM PC

---

### Post by him610 on 2024-08-04
From a terminal, shows hardware specs
```
inxi -Fxx

```
From terminal, shows latest LTS *buntu version installed
```
uname -a  && lsb_release -a

```

Latest LTS version is...
```
$ uname -a  && lsb_release -a
Linux ma90x 6.8.0-38-generic #38-Ubuntu SMP PREEMPT_DYNAMIC Fri Jun  7 15:25:01 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 24.04 LTS
Release:	24.04
Codename:	noble

```

---

### Post by ajgreeny on 2024-08-05
Is it really a "4 MB RAM PC"?

4 GB maybe, but 4MB, I think it can not be true!

---

### Post by Andreyshel on 2024-08-05
Assuming it is 4GB. Not really. It will not be good. Lubuntu probably will work. [https://cdimage.ubuntu.com/lubuntu/releases/24.04/release/](https://cdimage.ubuntu.com/lubuntu/releases/24.04/release/)

---

### Post by him610 on 2024-08-05
What? "4 MB RAM"
I completely missed that. My mind must have somewhere else.

---

### Post by TheFu on 2024-08-05
No Ubuntu has ever worked in 4MB of RAM. Sorry.  

I've been using Linux long enough that I have run it on systems with 4MB of RAM ... along with Win 3.1 and OS/2.  All were painful enough that I spent $650 to get to 8MB of RAM and they all ran great ... besides my 14400 baud modem.  

At the time, typical PCs only came with 4MB of RAM.  I ran Slackware back then.  I doubt Slackware will run in less than 384MB of RAM these days.  I did have a very small Debian server that ran great in 384MB of RAM, but that's without any GUI and very few nice convenience helpers.

The lightest Linux with a GUI I know today is TinyCorePlus and it needs about 100MB. You can get it here: [http://www.tinycorelinux.net/downloads.html](http://www.tinycorelinux.net/downloads.html) . The entire OS is loaded into RAM so it flies on all hardware, provided it has enough programs to meet your needs.

If your PC has 4GB of RAM, there's the theory for which versions will run and there's the don't-need-to-tune-everything carefully versions that won't feel slow.  There's also a question of which are still supported, since more GUI versions lose support/patching after just 3 yrs, with 1 exception - the most bloated version with Gnome4.  In theory, that will run, but you won't like it.

---

### Post by HermanAB on 2024-08-08
In general, to test and evaluate a machine without altering it in any way, boot with install media to the desktop (do not install), then explore the machine. When done checking things out, remove install media and reboot.

---

