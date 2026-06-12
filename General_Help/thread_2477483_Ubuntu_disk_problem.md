---
title: "Ubuntu disk problem"
date: 2022-07-26
forum: General Help
---

### Post by lania01 on 2022-07-26
Hello, I started getting such error after restarting my server.

Detail: [https://pastebin.ubuntu.com/p/QZxptSRgw8/](https://pastebin.ubuntu.com/p/QZxptSRgw8/)


The server contains some very important data, so can you please help me recover it? Thanks in advance for your help dear ubuntu experts.

---

### Post by TheFu on 2022-07-26
The image says to run fsck manually.  Have you done that yet?

Google found this answer: [https://askubuntu.com/questions/697190/fsck-error-on-boot-dev-sda6-unexpected-inconsistency-run-fsck-manually](https://askubuntu.com/questions/697190/fsck-error-on-boot-dev-sda6-unexpected-inconsistency-run-fsck-manually)

If the problem file system is the root file system, you'll need a "Try Ubuntu" bootable flash drive. Boot from that then you can run fsck on all the file systems on any connected storage using Linux file systems.  "Try Kubuntu" or Try Ubuntu-Mate or Try Lubuntu are all just as good, but it is best if the release number is the same as the installed version.

---

### Post by lania01 on 2022-07-27
> **TheFu said:**
> The image says to run fsck manually.  Have you done that yet?

Google found this answer: [https://askubuntu.com/questions/697190/fsck-error-on-boot-dev-sda6-unexpected-inconsistency-run-fsck-manually](https://askubuntu.com/questions/697190/fsck-error-on-boot-dev-sda6-unexpected-inconsistency-run-fsck-manually)

If the problem file system is the root file system, you'll need a "Try Ubuntu" bootable flash drive. Boot from that then you can run fsck on all the file systems on any connected storage using Linux file systems.  "Try Kubuntu" or Try Ubuntu-Mate or Try Lubuntu are all just as good, but it is best if the release number is the same as the installed version.

I can't access the command line outside of the GRUB menu, including recovery mode, so I can't run the fsck command. Before your comment, I pressed "E" in the GRUB menu and added the rw init=/bin/bash command to the end of the linux boot command line. Then there is something even more strange. I tried to show it with a short video below.

[https://jumpshare.com/v/rzZ5PtsyFtTWeR36mTD1](https://jumpshare.com/v/rzZ5PtsyFtTWeR36mTD1)


Summary of the situation, ubuntu installation is happening with 50% problem. I can get connection to server from SSH terminal, but when I want to enter root password it gives wrong password warning on ssh connection, but when I try from ubuntu machine it gives tty1 error and doesn't ask for password.

---

### Post by tea for one on 2022-07-27
> **lania01 said:**
> I can't access the command line outside of the GRUB menu, including recovery mode, so I can't run the fsck command.
As mentioned by TheFu, you have to boot into a [COLOR="#0000FF"]live[/COLOR] session to run the file system check (fsck).

---

### Post by lania01 on 2022-07-27
> **tea for one said:**
> As mentioned by TheFu, you have to boot into a [COLOR=#0000FF]live[/COLOR] session to run the file system check (fsck).

Thanks but Sorry, I'm not a linux system expert. This server only hosts our game server so I don't have much technical knowledge.
Wouldn't it be rude of me to ask you to explain more about how I can start a live session? I am really helpless. My Ubuntu 17.10 i386 server edition, I downloaded its installation file, .iso format. My server is running on Oracle VirtualBox. So I can display it like a USB drive. But I don't know what the next steps I need to follow are. A video would be great if possible.

---

### Post by tea for one on 2022-07-27
Ubuntu 17.10 reached End of Life in July 2018 and is now unsupported.
Do you have data backups?

---

### Post by lania01 on 2022-07-27
> **tea for one said:**
> Ubuntu 17.10 reached End of Life in July 2018 and is now unsupported.
Do you have data backups?
No, that's why I want to recover the server. Please help me, I'm about to lose my mind.

---

### Post by rsteinmetz70112 on 2022-07-27
You first need to create bootable media with Ubuntu on it, you can burn a DVD or use a USB stick. To accomplish your recovery you probably can use any version of Ubuntu.
This is a tutorial on how to do that:
[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started).
When you are able to recover you access you need to immediately backup everything of value then migrate to a supported version. I would recommend using only LTS versions 22.04 is the latest LTS version. LTS versions are supported for a longer time.

---

### Post by ActionParsnip on 2022-07-27
I suggest you delete the VM and reinstall with Ubuntu 22.04. This is LTS and will be supported until April 2027. Ubuntu 17.10 (Artful Aardvark) is end of life and supported by nobody

---

### Post by TheFu on 2022-07-27
17.10 support ended in 2018.  People like you (AND me) should stick with LTS releases which get 3 or 5 yrs of support.  Also, when you install, it is important to know you need to migrate to a new release - preferably an LTS in the future - in 2 or 4 yrs.

It is important to learn the cadence of Ubuntu LTS releases. There are lots of documents about those.

Since you are using virtualbox to run the Linux system, you don't need to create a physical flash or DVD, just use the ISO file that we all download. Hook it up to your existing VM as a bootable CD and tell virtual box to boot it.  Rather than repeat what the virtualbox manual says clearly, I'll just point you at that. Google finds it easy.

Saying "This server only hosts our game server" understates the complexity, vastly.  Game servers are constantly attacked and running out of date software, especially the OS, is extremely likely to get hacked.  A few times this year, remote exploits into Linux have been reported and fixed, but not for 17.10.  I'm afraid for you.  

If the system was important, it would have been properly managed, maintained, and backed up.  Learn from this.

And run the fsck from the Try Ubuntu ISO that you boot into the VM.  There are lots and lots of 'how-to' guides all over the internet for this stuff. If you want someone else to manage the system, I'd suggest opening a contract with a local Linux support company. It should be less than US$120/month. OTOH, if you are like most of us, you'll choose to learn how to maintain and backup the system to save that $2K/yr in support.  The learning curve is steep.  After you get the fsck working and hopefully, get the data off the system, you can start with this book as a general guide for Linux: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Learning things in the specific order of that book will save you time.  In Unix and Linux, knowledge builds on prior knowledge that the admin is expected to have. You cannot just jump into the middle and expect success.  That book provides a good, general, background, even with the first 6-12 weeks of working through 1 chapter each week will seem completely unrelated to what you want.  It will save you time in the long run.

Sure, you could spend $50 on an "Ubuntu Administration" book and use the TOC or Index to look up fsck, if you like. A good book will clearly spell out how to do what we've suggested. What a book doesn't usually do is convey the nearly 30 yrs of working knowledge in Unix/Linux administration that people here have.  There are almost always good reasons for why we suggest doing things a specific way.  You'll see different suggestion by different people, because we all have different experience levels, backgrounds, and just knowledge.  I haven't run a game server since the 1990s, but I have been running servers and virtual machines (I don't use virtualbox anymore) for multiple decades, starting in the 1990s.  OTOH, because I worked in huge enterprises from 1999 on, my views lean that way. Prior to that, my admin work was mostly in small companies, startups, that went public and got bought out, while I was still a software developer and team lead.  In small companies, you have to wear many hats.

---

