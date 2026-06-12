---
title: "[SOLVED] TAR, pipe and netcat - is it possible?"
date: 2007-12-03
forum: General Help
---

### Post by ruibernardo on 2007-12-03
Hi,

I've made a backup of a server using TAR based on [Over the network]("https://help.ubuntu.com/community/BackupYourSystem/TAR#head-9a7ccc486ce96873954add0c77af4526138a82fd") section of  [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR). On the receiving side end (a workstation without any server or file sharing) I typed:
```
nc -l -p 1024 > backup.tar.bz2
```And on the backup end I typed:
```
tar -cvj --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys / | nc -q 0 <receiving host> 1024
```The result was that the backup file wasn't created on the backup side (didn't have space on disk for it) and on the receiving side it didn't make me install any server on the workstation.

Now I would like to restore the server backup. The backup file is on the workstation. I'm sure (am I?) there is a way to do the reverse thing, but I tried many forms of nc commands and tar with pipes on both sides but I couldn't get any results.

Can I restore the files on the server without copying the backup file to it without space on disk for it using TAR and netcat like when the backup was done? NOTE: I have a SSH server on the server if needed, but can it be done with TAR and netcat?

Thanks for any answers.

---

### Post by mellowd on 2007-12-03
I've never done it, but it should be possible as long as you have connectivity.

---

### Post by ruibernardo on 2007-12-03
Hey mellowd,

I do have connectivity, I made the backup over the network. My question is how do I restore the backup file using netcat and tar and without copying the backup file to the partition/disk/computer I want to restore.

What I'd like to know is the syntax of the netcat commands on the sending side and the receiving side and where do I put the pipe so that TAR can uncompress the file that is on the workstation side on the disk of the server.

Thanks.

---

### Post by trobbins on 2007-12-03
I tested this a bit because I've been wanting to know more about nc as well.  It is possible to extract an archive onto your server but this method does not appear to uncompress your file before sending it.

From what I can tell, you are wanting some type of way to decompress your archive on your client and then send the files to the server including the ability to restore directories.  nc is used to redirect data from standard input and doesn't deviate from that. 

Here is a way to at least restore an archive onto a remote computer, but it doesn't uncompress the file before sending:


sender:

cat test.tgz | nc myserver.com 5555


receiver:
 nc -l -p 5555 | tar xzf -


If I were you, I'd investigate SSHFS and mount my remote partition and then restore my archive onto it.  You'd have to install a couple more apps and make some config changes to your server, but I think this may be the easiest way considering your options are limited to use SSH or NC.

Check out:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_remote_host_folders_into_local_Ubuntu_machine_.28sshfs.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_remote_host_folders_into_local_Ubuntu_machine_.28sshfs.29)

---

### Post by ruibernardo on 2007-12-03
Thanks for your reply trobbins.

I didn't really wanted to uncompress the file in the sender machine. I wanted to uncompress the file in the server, sending its content with nc (so I didn't install any server like SSH), but without saving the file in the server (because of the disk space).

Finally I got it working by myself, but it is very much similar to the way you posted, but extracting the file content to the disk while it receives through netcat (the file is never saved to the server, no disk space used). 

While I was testing, I changed the backup options a little, so I'll post here all the process with the tar options I used:


**[SIZE=3]To backup[/SIZE]**

On the receiver:
```
sudo nc -l -p 1024 > backup.tar.bz2
```On the sender:
```
sudo -i
tar -cvpjf - --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/media --exclude=/sys / | nc -q 0 receiver_ip.com 1024

```The backup is done on the receiver and no file is created on the sender.


**[SIZE=3]To restore[/SIZE]**

On the receiver (with a LiveCD and the / partition mounted in /mnt/disk):
```
sudo -i
nc -l -p 1024 | tar -xvpjf - -C /mnt/disk
```On the sender:
```
cat backup.tar.bz2 | nc -q 0 receiver_ip.com 1024
```I was pretty close yesterday. I think that yesterday I was testing without the "-q 0" option in netcat and without "- -C /destiny_folder". Or maybe I was needing some sleep over this.

That's it. Thanks again trobbins.

---

### Post by trobbins on 2007-12-04
It looks like you knew were closer to your goal than I had thought.  I was under the impression that the whole archive has to be transmitted before it could be uncompressed.  I'll have to research that some more.  Have a good day now.

---

### Post by mellowd on 2007-12-04
Very useful. I'll need to make a note of it.

---

