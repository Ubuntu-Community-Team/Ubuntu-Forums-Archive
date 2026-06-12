---
title: "black screen with blinking cursor on start-up"
date: 2016-04-18
forum: General Help
---

### Post by timothy_george on 2016-04-18
So, I've been having a bit of an issue lately, and I hope ya'll can help with it. I dual boot windows 7 and ubuntu 13.10 (at least, I'm pretty sure it's 13.10). My windows 7 install is exclusively for gaming. As such I can go months at a time without bothering to connect it to the internet.  Friday night i decided to connect my windows install to the internet to update my games, get some DLCs and get a new game. while that was going on windows apparently decided to download all the updates I had missed out on over the past nine months or so (I thought I had auto-update turned off, but apparently not). So when I went to shut down the computer I had nearly fifty updates to install - at which point I decided to just let the computer sit overnight and do its thing.

The problems started the next morning, when I booted the computer back up. First up, I immediately noticed the screen seemed a bit dimmer than it should have been, both the starting screen and the grub menu. I ignored it, and tried to bring up ubuntu. At which point I got a black screen with a blinking underscore in the upper left corner. I let it sit for about five minutes before shutting it down and trying again - same result. So I booted up windows, let it configure the updates, then restarted to try again. This time the start screen and the grub menu were back to the proper level of brightness. Unfortunately I still got the black screen with cursor when I tried to load Ubuntu. So I restarted and tried to get in using recovery mode, but that just gave me a wall of scrolling text that ended up getting stuck - both times I tried it (got stuck in the same place both times, but I didn't write down what it said). So, next I tried to boot Ubuntu normally, then just let it sit, hoping it would get past the black screen spontaneously. No joy. I did notice that after about ten minutes the blinking cursor would go away, and I'd have to press a key to get it back.

So far I've only really done one thing to try and fix this. I assumed this was a boot error of some sort and tried using the tool described here - [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) . I used UNetbootin to put it on a jump drive. Then I restarted my computer and told my bios to boot from the jump drive. Unfortunately it didn't work - I got a black screen that said either "boot failed" or "boot failure" or "boot fail" - can't remember which. So I wasn't able to run the boot repair too. My next plan is going to be making a ubuntu boot drive (thumb drive) and seeing if that will boot. If it does I'll at least be able to access my files.

And that's pretty much all I've got. Has anyone else had a similar problem? I'd very much appreciate any advice on how to fix this. Ubuntu is my daily use OS and I kinda need it working, especially with finals coming up.

thanks

edit 4/18 5:45: So, the ubuntu thumb drive didn't work. I made it the same way I made the boot repair drive (using UNetbootin) but I got the same error - "boot fail". I'm going to try it on a different computer in a few hours to check and see if its a problem with the thumb drive or not.

---

### Post by edgar14 on 2016-04-18
Hi Timothy_George,
I am new to the Forums but I've got some experience and notion of Ubuntu. What I think that just happened to you is that when your Windows 7 updated it must have updated itself to a new version (like a new install) and in the processes it replaced the Ubuntu boot loader (GRUB) with its own boot loader; that is, it assumes it's the only OS on the machine. The screen you see with the blinking underscore will probably be the tool you will need to use to get Grub back on. I've been researching this on the web and there are several ways to do this (To change the boot loader back to GRUB). However, I'd like more people to comment on and check if my understanding of the root cause of this issue is correct so next steps can be taken.

---

### Post by yancek on 2016-04-18
The best option is to post more detail so that people with more knowledge will be able to point out potential problems.  The way you get the most information is to get the boot repair downloaded and run.  Make sure that when you run it, you select the option to create bootinfo summary and do NOT try to repair.  Most likely some update modified the boot code in the MBR or the partition table which is not uncommon for windows.  If you are going to use Ubuntu, always keep the installation DVD or flash drive to make repairs.  It also has the GParted Partition Manager on it which can be useful.

---

### Post by sammiev on 2016-04-18
I hope you are not still using Ubuntu 13.10 as it has expired sometime a go.

Fix your Windows issue and then install a valid LTS version of Ubuntu.

---

### Post by timothy_george on 2016-04-19
So, I've finally got the boot-repair tool to load and this is what it spit out for me - [http://pastebin.com/5f9JqgiF](http://pastebin.com/5f9JqgiF) .
I tried uploading the file as an attachment but apparently there's a 19 KB limit on file size for .txt files. So, given what the report says, should I just let boot-repair do its thing? Also, are there any other details that might be needed to help run down this problem?

---

