---
title: "Using 2nd HDD"
date: 2007-06-08
forum: General Help
---

### Post by musicguycool on 2007-06-08
Hi, i am a complete newbie to linux, i wanted to use linux and i have installed Ubuntu on my PC.  As i am completely new and i can see there is a lot for me to learn. right now the problem i am facing is that i am not able to use my 2nd HDD. at the time of installing the other drive was NTFS. i later used Partition magic to format it to ext3. even then i am not able to use the drive. I can see the drive in "computer" places. but it says Read Only. i cant change the permissions to read-write. i used the suggestion in the form to use the code:

sudo chown -R sharky:sharky /media/disk

(sharky is my username). yet no progress. Please help me with this issue.

---

### Post by BatsotO on 2007-06-08
First please do check the permission : ls -al /media

 here is mine : bina@admin:~/MyDownloads$ ls -al /media
total 20
....
drwxrwxrwx 22 root root 4096 2007-06-07 07:10 disk
....

you see the owner is still root, but I set the permission to read-write-execute on owner, groups and other. if you the sole user of the machine, then changing user name will be fine, but if you also have other user on the machine, and want to allow them to have all access to the 2nd HD, then setting the permission is more effective.

---

