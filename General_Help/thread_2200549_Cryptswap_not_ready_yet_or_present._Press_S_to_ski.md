---
title: "Cryptswap not ready yet or present. Press S to skip, M for..."
date: 2014-01-20
forum: General Help
---

### Post by Psil0cybin on 2014-01-20
[U]Information Dump

[/U]Xubuntu 12.04 LTS

 I have ran a few outputs, I am wondering if this is the cause to my issues.

```



[LIST=1]
[*][COLOR=#000000]sudo blkid | grep swap[/COLOR]
[*][COLOR=#000000]/dev/mapper/cryptswap1: UUID="0876b988-0180-442a-8671-2f25fd37e672" TYPE="swap"[/COLOR]
[*][COLOR=#000000]ls -l /dev/disk/by-uuid/0876b988-0180-442a-8671-2f25fd37e672[/COLOR]
[*][COLOR=#000000]lrwxrwxrwx 1 root root 10 Jan 19 23:03 /dev/disk/by-uuid/0876b988-0180-442a-8671-2f25fd37e672 -> ../../dm-0[/COLOR]
[/LIST]

```

and 

my **/etc/fstab** shows

```

[LIST=1]
[*][COLOR=#000000]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/COLOR]
[*][COLOR=#000000]proc            /proc           proc    nodev,noexec,nosuid 0       0[/COLOR]
[*][COLOR=#000000]# / was on /dev/sda5 during installation[/COLOR]
[*][COLOR=#000000]UUID=331d6d2c-2d1d-48e1-ad62-4e14993a393c /               ext4    errors=remount-ro 0       1[/COLOR]
[*][COLOR=#000000]# swap was on /dev/sda6 during installation[/COLOR]
[*][COLOR=#000000]#UUID=05aa896f-0f12-4b8b-a410-01f33a7f44ef none            swap    sw              0       0[/COLOR]
[*][COLOR=#000000]/dev/mapper/cryptswap1 none swap sw 0 0[/COLOR]
[/LIST]

```

I am wondering if the issue I am facing is due to the fact that the link between the swap is not accurately, made. (within /etc/fstab)

Going on IRC I was given this advice [within #ubuntu-offtopic]:

> I'm pretty sure cryptswap recreates the swap partition on each boot. I could be wrong. Probably am. Usually am.

> because it's taking longer than normal,because it's wiping swap and that's not normal. it's working fine, just keeps triggering a timeout.  

...does the above make any sense?

Thus I am left more confused, plus with plenty of questions such as:

[LIST=1]
[*]is my swap encrypted? (Running the commands, and looking at outputs, suggest that it is, or it is not being linked properly)
[*]is my OS loading the encrypted swap? or is it loading some other swap after the time out?
[*]is their a way of fixing/amending this issue?
[*]is it fine to leave this issue as it is, if my system functions normally?
[/LIST]

[B]_Outputs (Continued):_
[/B]```
/dev/mapper/cryptswap1: UUID="0876b988-0180-442a-8671-2f25fd37e672" TYPE="swap" 


```

[B]cat /etc/crypttab

[/B]
```
cryptswap1 /dev/sda6 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
```



Running commands, from tutorials...suggest that my swap is in fact encrypted, I just want to double check and confirm as I personally am confused...if any of the above makes sense.

I also notice I am not the only individual having these issues, perhaps this guide will help someone in the future, who is also wondering what this message is about....I cannot seem to find a single up-to-date validated guide. 

[HR][/HR][B][U]Outdated References / Guides I have already looked at: 

[/U][/B]Ubuntu Forum Reference 1: [http://ubuntuforums.org/showthread.php?t=2071617](http://ubuntuforums.org/showthread.php?t=2071617)
Ubuntu Forum Reference 2: [http://ubuntuforums.org/showthread.php?t=1943899](http://ubuntuforums.org/showthread.php?t=1943899)
Ubuntu Bug Report : [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1037703](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1037703)
AskUbuntu Reference: [http://askubuntu.com/questions/332625/swap-partition-not-recognized-the-disk-drive-with-uuid-is-not-ready-yet-or](http://askubuntu.com/questions/332625/swap-partition-not-recognized-the-disk-drive-with-uuid-is-not-ready-yet-or)
[HR][/HR]
Thanks in advance, Ubuntu Community!

---

