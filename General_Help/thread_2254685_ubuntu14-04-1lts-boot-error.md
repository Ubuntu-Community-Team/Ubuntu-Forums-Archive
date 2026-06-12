---
title: "ubuntu14-04-1lts-boot-error"
date: 2014-11-29
forum: General Help
---

### Post by sreenivas2 on 2014-11-29
Hi,
I desperately need your help. For the past couple of weeks i'm facing serious issues with my laptop, Dell XPS L502X which i bought 3yrs ago. 3 weeks back i installed Ubuntu14.04.1LTS in my laptop by replacing Windows 7. It worked for 1 week or 10days without any issues. But suddenly started giving wierd boot errors.

I followed every forum and tried all the steps but none of them are working to me. So i was tired of Ubuntu and tried installing Linux Mint, Xubuntu etc. All of them having same problem. Once booted, it works fine but if boot gives problems like 'attempt to read or write error...' and then one shown in below image thats it nothing works.

[https://drive.google.com/file/d/0Bz3mj3eoAEUsaW53eVM1SGJIMlh0T2ZzRHBwUVNpbEt2cGVZ/view?usp=sharing](https://drive.google.com/file/d/0Bz3mj3eoAEUsaW53eVM1SGJIMlh0T2ZzRHBwUVNpbEt2cGVZ/view?usp=sharing)

I tried boot-repair n number of times. You won't believe i installed Ubuntu and Ubuntu derivatives nearly 15 to 20 times till now, hoping atleast once it boots up. Installation is getting successful and all problems start while booting.

Now currently i'm back to Ubuntu14.04.1LTS and below is the pastebin URL after running boot-repair:

[http://paste.ubuntu.com/9271773/](http://paste.ubuntu.com/9271773/)

I ran all HDD and RAM diagnostics at BIOS level. But all gives PASS as result. I'm not sure what could be the issue. Please please please help me to resolve this issue.

***UPDATE****

I installed Ubuntu12.10 but getting same error while booting up. Everytime i boot, i see different different errors:

***UPDATE****

I found a discussion related to this partitioning.

[Partition does not start on physical sector boundary?.]("http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary")

I followed the same. Now i don't see any physical boundary related errors for my partitions. Below is latest pastebin URL.

[paste.ubuntu.com/9297554/]("http://paste.ubuntu.com/9297554/")

But still its not booting up. Getting different different errors everytime i boot. Below are some examples.

[COLOR=#ff0000]**Operating System Not Found**

[/COLOR][B][COLOR=#ff0000]error: invalid arch independent ELF magic, grub rescue>

error: incompatible license[/COLOR]

[COLOR=#ff0000]error: font characters not ascending order: 22293 <= some number 
error: no suitable video mode found. 
error: no video mode activated 
error: failure writing sector 0x334920 'hd0'.
[/COLOR][/B]
Please help me.

I posted the same in askubuntu. fyi: [http://askubuntu.com/questions/554015/ubuntu14-04-1lts-boot-error](http://askubuntu.com/questions/554015/ubuntu14-04-1lts-boot-error)

---

### Post by jim1944 on 2014-11-29
This probably isn't going to help much but...

I noticed that in your first pastebin URL that your 500GB hard drive is /dev/sda and a 8GB USB Sandisk is /dev/sdb while in the second pastebin URL that is reversed. Why is the 8GB USB sandisk designated /dev/sda? Does that make sense?

Jim

---

