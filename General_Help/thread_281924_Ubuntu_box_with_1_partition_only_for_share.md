---
title: "Ubuntu box with 1 partition only for share"
date: 2006-10-21
forum: General Help
---

### Post by rappol on 2006-10-21
Hi everyone,
ive just installed ubuntu, and made 3 partitions

1 for root
1 for swap
and 1 for share & archive

but in the installation process, i didnt format the 3 partition.

Now the questions..

Whats the best format to the share partition? I would like to use that partition to share docs,music and images with windows computers in my local network and also to use it as a FTP server to i can access it at work..

How can i do that in ubuntu (format)
What's the steps that i should do to make it work like i said? (configure samba?)


obs: sorry for my bad english and for my question but im really newbiew

---

### Post by foxmulder881 on 2006-10-21
You have to install Gparted for partition formatting, resizing etc.

As far as what file system to use for sharing with Windows, you would have to ask someone else on that one. I don't know of a file system that both OS's will co-operate with. I wouldn;t recommend it.

---

### Post by CatKiller on 2006-10-22
> **rappol said:**
> Whats the best format to the share partition? I would like to use that partition to share docs,music and images with windows computers in my local network and also to use it as a FTP server to i can access it at work..

As far as I know, if you're sharing files over a network it really doesn't matter what filesystem the partition uses, as long as Ubuntu can read it. If you want to share the files with Windows **on the same computer** use FAT32. Otherwise, use ext3, since it's a lot better than either of the Microsoft options.

---

### Post by rappol on 2006-10-22
i will share the files only by the network... this computer has only ubuntu..

so what ur saying is..that i can format the partition as ext3 and then...whith SAMBA i can share the files over the network with windows computers right? Also, how can i share the files by FTP?

---

### Post by hamil on 2006-10-22
> **rappol said:**
> i will share the files only by the network... this computer has only ubuntu..

so what ur saying is..that i can format the partition as ext3 and then...whith SAMBA i can share the files over the network with windows computers right? Also, how can i share the files by FTP?

Yes, you can share these files on a network with Windows computers.

FTP-share, don't know, but take a look at this site, maybe something for you?
[http://ubuntuguide.org/wiki/Dapper#FTP_Server](http://ubuntuguide.org/wiki/Dapper#FTP_Server)

---

### Post by CatKiller on 2006-10-22
There's no reason why FTP should care. After all, what is the filesystem used by some random FTP server on the Internet?

---

### Post by ser1alsn1per on 2006-10-22
theres a program that is used in windows to veiw + write to ext2 filesystems but it works for ext3 as well so if yo go in to my computer you can see the other partitions and write to them 


wehn looking for the program on google 

type something like ext2 + windows 

and i think the program gets listed

---

### Post by ser1alsn1per on 2006-10-22
i have the program my self
 
but its on the other partition if you want it email me @    [email]serialsniper@gmail.com[/email]

---

