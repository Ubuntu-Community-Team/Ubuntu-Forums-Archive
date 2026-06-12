---
title: "Incremental backup between windows workstation and ubuntu"
date: 2013-05-06
forum: General Help
---

### Post by lbunbuntu on 2013-05-06
Hi
I'm begining in ubuntu world. I have several years of experience in windows, but ubuntu or other linux system I know nothing. So I'm asking for your help.
I need a way to make backups between windows workstation and ubuntu. What would be the best way to do it?

I thank you in advance.

Best Regards

---

### Post by papibe on 2013-05-06
Hi lbunbuntu. Welcome to the forum ):P

This would be the general idea:
[LIST]
[*]Install 'samba' on Ubuntu.
[*]Create a samba share on Ubuntu.
[*]Test that you have access to the share from Windows.
[*]Use any Windows backup software of your preference that supports backing up to a network share.
[/LIST]
Hope it helps. Let us know if you need more details.
Regards.

---

### Post by lbunbuntu on 2013-05-06
Thanks for your answer. 

One of my problems is that the windows workstation is a remote one. And I have big files to backup. 

I've read about using rsync/ssh and i think this would be a good solution because I can do a full backup for the first time and after i can do incremental backups. What is your opinion? Do you know where can I find help to create this solution?

Thank you very much.

---

### Post by papibe on 2013-05-06
There are several ports of rsync in Windows, e.g., deltacopy, cwRsync, or even the CygWwin framework.

However, if you are thinking on a more high level solution (that may even use rsync on the background), take a look at LuckyBackup, BackupPC, or even CrashPlan.

We may come out with better ideas if you tell us a little more about what you want to do. For instance:

Are the computer in different LANs then?
Is one or both of the computers at a home?
How much broad band do you have to make the transfer?

Regards.

---

### Post by lbunbuntu on 2013-05-07
I have several computers to make a backup copy, but none of them is in the same lan, so I need to make the backup over the internet. So let's say I have 3 computers in diferent locations. In those pc's I have broadband with a minimum of 8 mb download and 512 k upload,  in my server I have 120mb download and 12 mb upload. The files I want to backup will have normal 3 gb.   Thank you for your answer.

---

### Post by papibe on 2013-05-07
This is what I would do:
[LIST]
[*]Initiate the backup on the client side. That way you only need to open ports on one machine: the server.
[*]Make sure your server has either a fully qualified domain name, an static public IP, or you have a subscription to a dynamic DNS service.
[*]I would physically transfer the first full backup using an external media. This is because  you are limited by the lowest transfer rate (512Kbps), and that means that a 3GB transfer would take about 13-14 hrs.
[*]I would use rsync over ssh. I would install openssh-server on Ubuntu, create an special user for the transfer, and create one passwordless key for each client so they can create unattended scripts.
[/LIST]
Does that help a little bit? Let us know how it goes.
Regards.

---

### Post by lbunbuntu on 2013-05-07
Yes, that's help a lot. Can you tell me where can i find help to implement this solution? And if I user an external media for the first backup, can I do an incremental backup next time?

Thank you for all your answers. It's my first time in a forum and i'm a begginer in ububtu world ( i always worked with windows system's)

Best regards

---

### Post by papibe on 2013-05-07
I would start on a LAN setup first (as a control environment, think it as a testing lab). When you have work it locally, you could start testing from a remote location.

For the server part take a look at this tutorials:
[LIST]
[*][Installing OpenSSH-Server]("https://help.ubuntu.com/12.04/serverguide/openssh-server.html").
[*][Configuring SSH]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring").
[*][Creating Public Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").
[/LIST]
For Windows. I took a look at several Windows clients, and I think this one would be the easiest: [Duplicati]("https://sites.google.com/a/duplicati.com/duplicati/"). Start by reading their howtos, starting with this [beginners]("http://www.duplicati.com/howtos#BeginnersGuides") video.

I hope that points you in the right direction. Let us know how it goes.
Regards.

---

### Post by lbunbuntu on 2013-05-10
Hi

When I create Public Keys, I think I should do it in my ubuntu server, right? If so, in ubuntu waht files should I have and where should I place them?

And in my windows workstation? what files should I have and where should I place them?

Thanks a lot for your support

Best regards

---

### Post by lbunbuntu on 2013-05-16
Hi

Thank you for all your support. I have finished my solution and know it's working fine. I had to pass some dificulties because it's my first time in linux world.

Best regards

---

### Post by papibe on 2013-05-16
Sorry I missed your previous post about the keys, but I'm glad your solution is working :)

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Regards.

---

