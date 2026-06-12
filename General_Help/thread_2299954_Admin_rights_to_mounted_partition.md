---
title: "Admin rights to mounted partition"
date: 2015-10-22
forum: General Help
---

### Post by Billy_Martinez on 2015-10-22
I have an Ubuntu server that I setup with two partitions. For some reason on the root "/" partition I can use the "mkdir" command without any problems, but when I use "mkdir" command on my mounted partition it blocks me and says that I don't permission to write to disk. The only way for me to get around this problem is to use the "sudo" command before the "mkdir" command. How can I fix this problem?

---

### Post by ajgreeny on 2015-10-22
> **Billy_Martinez said:**
> I have an Ubuntu server that I setup with two partitions. For some reason on the root "/" partition I can use the "mkdir" command without any problems, but when I use "mkdir" command on [COLOR="#FF0000"]my mounted partition[/COLOR] it blocks me and says that I don't permission to write to disk. The only way for me to get around this problem is to use the "sudo" command before the "mkdir" command. How can I fix this problem?
What do you mean by "my mounted partition"?  Who is owner of that partition's mountpoint?  You certainly should not be able to use the mkdir command on the root partition without using raised permissions of sudo, so something is obviously wrong with your installation.

Is this a new OS or one that used to work as expected and this has only just started to happen?

---

### Post by Billy_Martinez on 2015-10-22
> **ajgreeny said:**
> What do you mean by "my mounted partition"?  Who is owner of that partition's mountpoint?  You certainly should not be able to use the mkdir command on the root partition without using raised permissions of sudo, so something is obviously wrong with your installation.

Is this a new OS or one that used to work as expected and this has only just started to happen?


I have an old server that I've installed ubuntu server on. The server has a raid 5 array with three hard drives that all together give me a volume consisting of 150 gigs. On that volume I made three partitions, a small partition for the root "/," another small partition for the swap, and then I gave the rest of the space to last partition which i mounted at "/mnt/files."

Here are the results of the lsblk command
[FONT=Menlo]NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT[/FONT]
[FONT=Menlo]sda      8:0    0   148G  0 disk [/FONT]
[FONT=Menlo]&#9500;&#9472;sda1   8:1    0  18.6G  0 part /[/FONT]
[FONT=Menlo]&#9500;&#9472;sda2   8:2    0     1K  0 part [/FONT]
[FONT=Menlo]&#9500;&#9472;sda3   8:3    0 127.4G  0 part /mnt/files[/FONT]
[FONT=Menlo]&#9492;&#9472;sda5   8:5    0     2G  0 part [/FONT]
[FONT=Menlo]sr0     11:0    1  1024M  0 rom[/FONT]

[FONT=Menlo]This is a fresh install. Whenever to go to the files partition, which is mounted in /etc/mnt/ directory, Ubuntu doesn't allow me to create folders without using the sudo command.[/FONT]


[FONT=Menlo]This is the message I'm getting:[/FONT]

[FONT=Menlo]"bill@Ubuntu-server:/mnt/files$ mkdir temp[/FONT]
[FONT=Menlo]mkdir: cannot create directory &#8216;temp&#8217;: Permission denied"[/FONT]

---

### Post by Billy_Martinez on 2015-10-22
I went into the mounted folder and ran the ls -l command, and it showed the root account and anyone that belonging to the root group as having admin rights to that mounted partition. I used the chown command "[FONT=Menlo]sudo chown -R  usr:group folder" [/FONT]to give my user account and the group that I belonged to admin rights to that partition. Don't forget to use the -R option in the chown command or else the changes won't apply to all of the folders inside the partition.

---

