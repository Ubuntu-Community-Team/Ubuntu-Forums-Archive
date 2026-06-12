---
title: "Permamounting Hard disk/Partition"
date: 2015-01-13
forum: General Help
---

### Post by mohamad2 on 2015-01-13
Hey to all, happy new year tp all of you, hope that this new year brings you all joy and happiness and succes, money, women, all that your hearts desire.

Im here on a quest, to seek help:

I have Linux on a dual-boot with windows 7. I have some files (large files to be precise) on the windows partition. Everytime i need to acces them i have to wait a couple of minutes so that Ubuntu mounts the partition, and many times i have to mount using terminal.. he just cant seem to do it on his own sometimes (weird though...)

so the question is, how to make it auto mount a partition (or a HDD for that matter) on startup? 

I have checked some answers on this forum before seeking help. If i understood correctly i have to create a mounting point usinfg /mkdir then change something using fstab? But id really like an explanation on how, and why, and what each command does? I mean, to copy paste, i can do that, but id like to undestand what im really doing

the name of this partition (using df in terminal): /dev/sda3.

So thanks all for reading this message, and thank you for those who are going to answer.
Mohamed

---

### Post by TheFu on 2015-01-13
I won't copy/paste the documentation that is already on your system here.  I'd rather teach you to fish for yourself than hand you a fish for today ... 
```

man fstab
```
explains the options and use for fstab entries in great detail.  This is how to mount partitions at boot.  There are many, many, many how-to guides if you need more help. Google easily finds them or any Linux admin book will have a page about it.  I like this book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by ajgreeny on 2015-01-13
Whilst I accept TheFu is correct to allow you to try to do this yourself, here is some more detail for you; I am very aware that I would have been totally stumped if I had tried to understand this simply from reading **man fstab** as a new user.

[LIST=1]
[*]First you need to find which partition is the one you want to mount from command ```
sudo parted -l
``` 
[*]You really need the UUID of that partition which you can get from command ```
sudo blkid -c /dev/null
``` 
[*]Now make a mountpoint folder eg /media/windows with command```
sudo mkdir /media/windows
``` 
[*]Backup /etc/fstab as root with command ```
sudo cp /etc/fstab /etc/fstabbak
``` 
[*]Edit /etc/fstab with command ```
gksudo gedit /etc/fstab
```though you may need to install the **gksu** package first. 
[*]Add a line with syntax ```
UUID=66E53AEC54455DB2 /media/windows/    ntfs-3g        auto,user,rw 0 0
```changing the UUID to your partition. 
[*]Before rebooting run command ```
sudo mount -a
``` to test the new fstab. If it returns to the prompt all is good. 
[/LIST]

---

### Post by TheFu on 2015-01-13
@ajgreeny, you were too kind.  There is a written rule on these forums against saying RTFM and I wouldn't have said to read it if exact detail was requested.  manpages are great and they suck at the same time. It takes time to learn to read them, grok them. If you ever find yourself working on a network that doesn't have any internet, the manpages will be all you have, probably.

BTW - that free book on page 177 has the same information, with more details and clear examples. There are multiple pages on mounting - it is a good reference all around. Highly recommended. Plus since it is free, no hassle to download - well - get it.  Read the first 100pgs to get the background, then skim the rest of the book over about an hour to learn what information it has - what is possible. Google is great, but it doesn't provide information in an organized way like a book can.

Again, my intent was not to give you a fish for today, but to show how to fish yourself for many future questions.  We all have them and we were all less experienced yesterday than today. 

There is another way to do this too - called automounting. It is more complex, but it is how I handle non-OS drives on my network - especially USB storage.  **Automount** is an intermediate administration skill, so not in that book.

Anyway, hope this helps.

---

