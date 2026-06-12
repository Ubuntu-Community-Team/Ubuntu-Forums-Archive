---
title: "archive manager .... on raspberry pi 4"
date: 2021-08-19
forum: General Help
---

### Post by Old Jimma on 2021-08-19
Hello Forum People:

The archive manager app for Ubuntu 20.04 on a raspberry pi 4 does not seem to work.
Here is what I've been doing:

[LIST]
[*]click on the archive manager app
[*]from menu, choose "new archive"
[*]enter a file: filename
[*]choose zip
[*]choose other options
[*]specify password
[*]click on "CREATE"
[*]
[/LIST]

NOthing happens.

Ideally, I'd like to encrypt my files, also, and have tried this procedure choosing the 7z option, also. However, that does not work, either.

ALso, I've installed p7zip and p7zip-full using synaptic... but those do not work either.

How do I encrypt, compress, and zip with a password a folder with Ubuntu 20.04 on Raspberry Pi 4?

Thanks,
Old

---

### Post by TheFu on 2021-08-19
IF you aren't tied to 7zip, here's a how-to for using LUKS encryption with an external flash device. [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)  There are some videos which go with that too.
He makes it not need manual decryption on your system, but it would require the passphrase to open on any other systems.  Sorta cool, unless you have state secrets.  Then go with LUKS and 2FA, which is what I use with a Yubikey in challenge/response mode.

Nothing against using 7zip, BTW.  It is not too bad to share files that are password protected, say with an accountant, over email. Certainly better than many other options.  I just haven't used 7zip in some time and never with a GUI.

---

### Post by Old Jimma on 2021-08-20
This is pretty cool, TheFu! I'm going to try it.

BTW, I have a "secure server" raspberry pi 4 now, 3 hard drives:[LIST]
[*]one dedicated to rsync,
[*]one that just uses scp on a weekly basis, and
[*]one that uses scp on a monthly basis.
[*]
[/LIST]

It is all prototype, since I know that I don't know what I'm dong and am likely to change things as I learn more. But at least I've got a start instead of nothing.

As indicated above one hard drive is dedicated to pulling using rsync. To tell you the truth, ignorant old Old me can understand the theoretical value of rsyc, but don't yet understand all the buzz about rsync that makes everybody go a-fliver. There seem to be more websites that describe how to create a back up, and not to many on how to use and rsync backup creatively, and actually not many web sites on how to make a back up as your files were on a specific date. Probably just my ignorance, that I'll eventually grow out of next year when I turn 106. Perhaps when I gain that knowledge, I'll ditch the doing the weekly and monthly "copy" to the other 2 hard drives.

Also, while I've seen some of the other stuff your wrote on the forums in discussions about ssh keys (or something like that) where you said something like "... I don't know why everybody doesn't use them...'

At this point in the development of my understanding and trust in myself, I don't use SSH keys.... because I understand that installing them is a little tricky, and I don't trust myself to get it right. I'm told that if I screw it up... I'm totally I'm screwed. Besides sshpass works well enough

BTW, your recommendation for using a pi 4 was a good one... works quite well enough, especially for the price.


If I had it to do over again, and I just might to it all over again soon since it isn't so difficult, if its possible on a raspberry pi I would install an encrypted system on both the pi and also my laptop. Seems like it would resolve a few more of my paranoia problems that originated with the 2015 OPM data breach.

In the mean time, your suggestion about encrypted removable media looks cool. I'll try it on a thumb drive.

Hope all is well,

Old Jimma from the Old Country

---

### Post by TheFu on 2021-08-20
Bad news.  The OpenSSH team has decided to deprecate scp.  Must be a bunch of kids running it now OR some unstated security issue.  

rsync does the same and more, so it won't change anything I do, except when I need 1 file transferred. It is like they've never noticed that the default bash prompt is exactly what scp needs for pushing/pulling files?  I don't get it.

ssh-keys are bonehead simple.  1 command to create a key. 1 command to push the public key to the other system.  That's it.
[Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)  simple. 2 commands.

1 key can be used across all the connections from 1 client just fine. There are reasons NOT to do that, but if you don't have state secrets, it is probably fine to reuse the same key everywhere ... unless you are using public services like github.  I'd create a different private key for each public service and setup the connection information for non-standard key use in my ~/.ssh/config file.  But that isn't mandatory and really not THAT important if you aren't paranoid.

Instead of using rsync, please consider **rdiff-backup**.  The command is basically the same and you get versioning for free.  And when you create an ssh-key for backups, make that key without a passphrase.

---

### Post by Old Jimma on 2021-08-21
Ok. I'll look at rdiff-backup. I wondered where the versioning was with rsync.

Being 1,200 years old, I have to do 1 thing at a time. Once I get rdiff-backup going, I'll look at the encryption keys.


BUt I've got one dumb question for you TheFu: All I'm doing is swapping files from one computer to another that are both on my own home network. To boot, I set up the client to only allow traffic from the raspberry pi server.

Why should I care a hoot about security? The only think I can think of is that the commands are easier and don't require nfs.

---

### Post by TheFu on 2021-08-21
You should do the ssh-keys first.  Just copy those 2 commands and be done with it.

It is far to easy to make a mistake and have poor security that accidentally is available over the internet than it is to always be secure.  BTW, keys aren't just more secure, they are 1000x more convenient.  You'll see.

rsync doesn't have versioning built-in.  There are scripts that can make rsync have versioning via hardlinks, if you like.  rsnapshot does that, but rdiff-backup doesn't use hardlinks and does a number of other things better than rsync or rsync+hardlinks.

I'm confused now.  Don't you backup all your files, from all systems, to an external HDD on the r-pi?

---

### Post by Old Jimma on 2021-08-22
Hi TheFU:

I've had trouble:

> 
$ ssh-copy-id -i ~/.ssh/id_ed25519.pub fider@192.168.1.136
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/camillesmith/.ssh/id_ed25519.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed

**/usr/bin/ssh-copy-id: ERROR: ssh: connect to host 192.168.1.136 port 22: Connection refused**



Here is UFW on the server (192.168.1.136):

> 
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                    ALLOW       Anywhere                  
22                         ALLOW       Anywhere                  
Anywhere               ALLOW       192.168.1.75            .......... this is the ip address for the client
22/tcp (v6)             ALLOW       Anywhere (v6)             
22 (v6)                  ALLOW       Anywhere (v6)  


Old

---

### Post by TheFu on 2021-08-22
Is the "ssh" package installed on all the systems?

---

### Post by Old Jimma on 2021-08-22
yes

---

### Post by TheFu on 2021-08-22
[https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)  has the steps I use.

---

### Post by Old Jimma on 2021-08-23
Hi TheFU:

I've made progress. 

I discovered that the ssd was formatted as nfs. That was a problem: changed it to ext4.

Also, ufw was so !&*#$! on both machines, I reset UFW on client and server, and fixed that, too.

With those fixes, I followed your prescription to install ssh keys.

OH MY GOD!!!!

You were right. You said, "You'll be glad you did."

You were right. It is a "snap" (not the snap app) with ssh keys. Wow!!!

Gonna take a break for a few hours, come back and do that rdiff-backup thing again.... except no more sshpass.

To answer an old question of yours: I was using scp to to copies of my client's home director on 2 other drives. if rdiff works, I'm not sure why I'd use scp. Maybe just for comfort. But what a pain: takes an ice age... an the kids are gonna depricate it, anyway. Hope the kids know what they are doing. "Its good to learn from your mistakes. Its better to learn from someone else's mistakes.


Old

Old Jimma from the Old Country

---

### Post by TheFu on 2021-08-23
NFS isn't a file system that you can format.  I suspect that is a typo.  NFS is a network protocol to access remote storage - storage on other systems. While native Linux storage works best with NFS, I've heard of people using it to access NTFS storage. Don't know why anyone would do that, but there are lots of crazy people in the world.

Just for clarity - **rdiff** is very different from **rdiff-backup**. Don't confuse them.

---

### Post by Old Jimma on 2021-09-22
Hi TheFu:

Thanks for your suggestion about getting a pi 4  and using it as a server to do backups. I've followed your recommendations, like pull not push, and have a pretty nice server working pretty well... I had trouble with syntax of rdiff-backup and rsync, read the manpages, decided to do things as simply as possible... and it all working well now.

Thank you for offering your advice.

Sincerely,
Old

---

### Post by TheFu on 2021-09-22
> **Old Jimma said:**
> Hi TheFu:

Thanks for your suggestion about getting a pi 4  and using it as a server to do backups. I've followed your recommendations, like pull not push, and have a pretty nice server working pretty well... I had trouble with syntax of rdiff-backup and rsync, read the manpages, decided to do things as simply as possible... and it all working well now.

Thank you for offering your advice.

Sincerely,
Old

If you need to have the server ask the remote backup client to run some commands BEFORE, then AFTER the actual backups are run, we can feed a script over ssh in using stdin.
```
# ################################################
function [COLOR="#FF0000"]Pre-Backup-Info[/COLOR](){
  sudo ssh $RUSER@$REMOTE '/usr/bin/bash -s' <<ENDSSH

    # #############################################
    function [COLOR="#006400"]EmptyTrash[/COLOR](){
        if [[ -f /usr/bin/gio ]] ; then
           echo "Empty GIO trash"
           /usr/bin/gio trash --empty
        fi
    }
* .... other functions follow .... *
    [COLOR="#006400"]EmptyTrash[/COLOR]  # has to be called inside the ENDSSH-wrappers 
ENDSSH
}
```
Then just call the [COLOR="#FF0000"]Pre-Backup-Info[/COLOR] function in your regular backup script.
It can feel a little like "inception" (the movie) doing this, especially if you use functions like I do. ;)

---

### Post by TheFu on 2021-09-22
> **Old Jimma said:**
>  if rdiff works, I'm not sure why I'd use scp. Maybe just for comfort.  

When I change backup methods, I usually have a 30 day overlap where I do both for each system involved.  Plus, until I actually do a restore, I don't believe the backups are good enough to be trusted.

---

