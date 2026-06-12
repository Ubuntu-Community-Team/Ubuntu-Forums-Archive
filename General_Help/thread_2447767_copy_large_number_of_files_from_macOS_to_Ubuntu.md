---
title: "copy large number of files from macOS to Ubuntu"
date: 2020-07-25
forum: General Help
---

### Post by gebseng on 2020-07-25
Hi there,

I'm trying to copy a 150GB directory containing 150,000 jpegs from a macOS 10.13 to a ext4 HDD on a Ubuntu Server 20.04 machine. The Ubuntu machine is shared locally over wired ethernet via SMB.

For the love of god, I can't seem to finish this copy. 

I tried it as a macOS finder operation first, but after 24hrs the finder message still said "preparing to copy". 

I also tried ```
rsync --progress -auv 
``` and ```
cp -rv
``` in the Mac terminal. The process starts OK, but after about 10,000 files it slows down more and more, stopping with an eror code after some time. 

for the heck of it, I even created a .zip archive on the Mac and successfully copied it to the Ubuntu machine. However, when I SSH in the the Ubuntu machine and try ```
unzip
```, it stops with an error message warning of a zip bomb.```
 tar -x
``` also didnt work.

Copying the same directory on the Mac itself poses no problem at all. What could be the problem? I also want to mention that I already successfully copied another 5TB of data via rsync in the same setting (just not containing a directory with that many files in it)

thanks,

geb

---

### Post by ActionParsnip on 2020-07-25
I suggest you use SFTP (install openssh-server on Ubuntu). You can then connect using FileZilla or the default Mac file manager if it can connect to SFTP. Use your Ubuntu username and password to authenticate.

---

### Post by gebseng on 2020-07-25
Thanks for the suggestion! Just out of curiosity: what is the advantage of ftp in this case?

---

### Post by TheFu on 2020-07-25
Are the filenames all compatible on both OSes? 
Is there a specific file where it fails each time?  Skip that file and get the others.

I'd use rsync -avz and log the output so any issues can be seen later.

---

### Post by gebseng on 2020-07-25
The file names are compatible. As I said, it does not stop at a specific file, but gets slower and slower with each file. Thanks for the rsync tip!

---

### Post by HermanAB on 2020-07-25
SFTP is not FTP.  SFTP is SSH Secure FIle Transfer Protocol.  Mac supports it out of the box.  Just type ssh://addressofothermachine in the file browser and then it will ask you for the user name and password.  There really is no good reason to use SMB between UNIX machines.

---

### Post by gebseng on 2020-07-25
Thanks Herman. As I wrote, I know how to SSH into the Ubuntu machine from the Mac. But how do I use that for transferring the files?

---

### Post by TheFu on 2020-07-25
> **gebseng said:**
> Thanks Herman. As I wrote, I know how to SSH into the Ubuntu machine from the Mac. But how do I use that for transferring the files?

I don't have a Mac, but in Linux, sftp:// or ssh:// in almost any file browser will create a remote connection to other machines, assuming the ssh client is installed on the client-side and a working sftp-server is working on the other side. If sftp:// doesn't work, try ssh://.    On every Linux I know, just installing openssh-server will setup sftp-server for use too.  In ubuntu, there is a meta-package "ssh" which includes both the client and server parts.

Did you try it?

ssh and sftp are considered secure enough to be used over the internet, provided the defaults in the sshd_config on the server aren't changed. Of course, ssh should be used without using a password, use ssh-keys for authentication ... then sftp, rsync, ssh, scp, and 50 other ssh-based tools will authenticate automatically, once the ssh-key is unlocked.

If things aren't failing in the same place, perhaps there is a fault with the storage or somewhere in the networking?  Since a ZIP failed, I'm inclined to think it is a storage problem.  Check the file system and check the SMART data for issues.  Once the storage has a certain number of failures, it is much likely to fail faster.

I've only used a Mac for about 3 weeks the last 10 yrs. Gave it back. It wasn't for me. At the time, the samba implementation was broke. Think they fixed it a few weeks later, so that wouldn't be the issue here.

---

### Post by Doug S on 2020-07-25
There is likely little value added with this reply. I was just interested is all.

On one Ubuntu 20.04 server I created 150,000 files, each with 1048576 random bytes, for a total of 150 Gigabytes. I used rsync to send them to another Ubuntu 20.04 server. It all worked fine, and I got these file per minute rates (will not add up to 150,000, because of the way I post processed had to be on exact minute boundaries):

```
6592
6530
6466
6442
6386
6304
6155
6085
6098
5964
5941
5994
6064
4011
4998
6341
6213
6090
6277
5453
4065
6272
6125
6311

```

---

### Post by gebseng on 2020-07-25
> **TheFu said:**
> I don't have a Mac, but in Linux, sftp:// or ssh:// in almost any file browser will create a remote connection to other machines, assuming the ssh client is installed on the client-side and a working sftp-server is working on the other side. If sftp:// doesn't work, try ssh://.    On every Linux I know, just installing openssh-server will setup sftp-server for use too.  In ubuntu, there is a meta-package "ssh" which includes both the client and server parts.

Did you try it?

ssh and sftp are considered secure enough to be used over the internet, provided the defaults in the sshd_config on the server aren't changed. Of course, ssh should be used without using a password, use ssh-keys for authentication ... then sftp, rsync, ssh, scp, and 50 other ssh-based tools will authenticate automatically, once the ssh-key is unlocked.

If things aren't failing in the same place, perhaps there is a fault with the storage or somewhere in the networking?  Since a ZIP failed, I'm inclined to think it is a storage problem.  Check the file system and check the SMART data for issues.  Once the storage has a certain number of failures, it is much likely to fail faster.

I've only used a Mac for about 3 weeks the last 10 yrs. Gave it back. It wasn't for me. At the time, the samba implementation was broke. Think they fixed it a few weeks later, so that wouldn't be the issue here.

thanks a lot! What I did now: I moved both source and target to different HDDs on the respective machines to rule out disk problems. I then used scp to copy the files. It was really fast and did not slow down either. After about 80,000 of the 150,000 files it stopped with this message:

```
[COLOR=#000000][FONT=Menlo]Sink: E[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]debug1: client_input_channel_req: channel 0 rtype exit-status reply 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]debug1: channel 0: free: client-session, nchannels 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]debug1: fd 0 clearing O_NONBLOCK[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Transferred: sent 149844637384, received 51240516 bytes, in 2937.6 seconds[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Bytes per second: sent 51009828.3, received 17443.2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]debug1: Exit status 0[/FONT][/COLOR]

```
Is there a way to continue scp, similar to rsync?

btw: AFAIK the unzip failed because it thinks that the 150,000 files with similar sizes are a zip bomb. At least that's what the error message said. Does that make sense?

---

### Post by Skaperen on 2020-07-25
maybe we need to investigate.  those various commands should all work.  what unzip does to think there is a zip bomb is a curiosity.  what happens when extracting from that tar file?

here is another alternative.  i often needed to do huge transfers between 2 machines i was remotely connected to and wrote this script to do the work with compression and encryption (uses openssl) instead of trying to set up a shell session between machines to do it in.  i have not tried this on Mac :-(

[http://ipal.net/free/tarnet.bash](http://ipal.net/free/tarnet.bash)

it works by running a listener of one machine first (must be able to connect to a choice port number on this one) then run a connector on the other machine.  the direction of transfer can be made to go either way.  put the host address on the command in the machine doing the connection (port alone on the listener).  put file and/or director name(s) on the machine to do the sending (else it will listen after it tells you it will listen).

if you want the cpio version, change the url like s/tar/cpio/

*edit*:

FYI: this script depends on the wonderful *socat* package.

---

### Post by gebseng on 2020-07-26
Thanks Skaperen! unzip won't let me continue after that message. Thanks for the script!

---

### Post by ActionParsnip on 2020-07-26
Something like
```

rsync directory user@192.168.0.1:directory

```
Go to bed, in the morning, done.

---

### Post by gebseng on 2020-07-26
Ah I see, that uses rsync via ssh. thanks!

---

### Post by TheFu on 2020-07-26
If you've switched storage on the client and server and are still having issues, that leaves 
[LIST]
[*]OSX having incompatible version of ssh + rsync
[*]Networking problem
[*]HW problem somewhere
[/LIST]

I rsync about 10+TB of media files a few times each week without issues on Ubuntu, so it isn't likely that is the issue. I have a script which does it to ensure I get exactly the same source-target when running the sync operation.

To my knowledge, scp doesn't have a restart capability. You could check the manpage to see. Sometimes they sneak in new features that old guys don't know about.  That has happened to me a few times - **ssh-copy-id** and **sort -h** are examples - both have changed/simplified my scripting life for the better.

To figure out the root cause, simplify and test.  Repeat.

rsync *just works*, so I'd stay with it rather than using some non-standard method.  If you are able to swap out HDDs, couldn't you directly connect the source disk to the Ubuntu system to remove network issues from the complexity?

---

### Post by gebseng on 2020-07-26
> **TheFu said:**
> If you've switched storage on the client and server and are still having issues, that leaves 
[LIST]
[*]OSX having incompatible version of ssh + rsync
[*]Networking problem
[*]HW problem somewhere
[/LIST]

I rsync about 10+TB of media files a few times each week without issues on Ubuntu, so it isn't likely that is the issue. I have a script which does it to ensure I get exactly the same source-target when running the sync operation.

To my knowledge, scp doesn't have a restart capability. You could check the manpage to see. Sometimes they sneak in new features that old guys don't know about.  That has happened to me a few times - **ssh-copy-id** and **sort -h** are examples - both have changed/simplified my scripting life for the better.

To figure out the root cause, simplify and test.  Repeat.

rsync *just works*, so I'd stay with it rather than using some non-standard method.  If you are able to swap out HDDs, couldn't you directly connect the source disk to the Ubuntu system to remove network issues from the complexity?


Thanks again for your considerate replies! I'm sure you're right about sticking with rsync. At the moment I'm running ActionParsnip's suggestion ```
[COLOR=#000000][FONT=&quot]rsync -auv directory user@192.168.0.1:directory[/FONT][/COLOR]
``` That seems to be working pretty well, let's see if it finishes.

Yes, mounting the Mac's HFS+ file system is definitively an option, but I have developed some blind ambition now to finish this over the network.

---

### Post by HermanAB on 2020-07-26
If you connect from a mac file browser with ssh, then you end up with a file browser window on the other machine.  Open a second browser (or a tab) on the local machine and click drag drop the directory accross.

---

### Post by TheFu on 2020-07-26
> **gebseng said:**
>  
Yes, mounting the Mac's HFS+ file system is definitively an option, but I have developed some blind ambition now to finish this over the network.

I understand completely. At a job, decades ago, I was working as a cross-platform software developer. There were 15 devs on my team, each checking code in and out all day long as we made changes for bugs and new features.  Every time one specific developer checked in his code, it was always corrupted whenever anyone else pulled a copy out.  We did some troubleshooting and determined it wasn't his account or the server or the code. I got a copy of the code on a floppy disk and checked it in - it worked fine for everyone.  So, we were down to his computer or the networking between it being the issue.  Did trouble shooting with the computer vendor and they determined it was a problem with the hardware. Cross-shipped it to them overnight. A few days later they called to say it was a cracked motherboard near the onboard NIC.  Fluke issue. I've never seen anything exactly like that again.  I've seen failing NICs (just a few) cause corruption on the wire.  I've seen a few NICs die completely.  In my career, I've deployed thousands of servers and over 40K desktops/laptops. Fortunately, I wasn't the "tech" doing this, just an architect around the systems.  When some systematic problem happened for specific hardware, I'd be notified.  I've seen cooling issues on hardened laptops (same model used by the military).  I've seen VoIP traffic freak out Intel NICs made in a specific Mexican factory, but if there wasn't any VoIP traffic, then the NIC was 100% great.

It could be an over heating issue with the NIC or the switch or the router.  Try different ports on the network.

Anyways, simplify and test.  Repeat.

May want to consider copying the files from HPFS to NTFS, then have Ubuntu read the NTFS.

---

### Post by Doug S on 2020-07-27
> **gebseng said:**
> At the moment I'm running ActionParsnip's suggestion ```
[COLOR=#000000][FONT=&quot]rsync -auv directory user@192.168.0.1:directory[/FONT][/COLOR]
``` That seems to be working pretty well, let's see if it finishes.Don't leave us wondering. Did it finish?

By the way, that is exactly what I did in [post #9 ]("https://ubuntuforums.org/showthread.php?t=2447767&p=13975072#post13975072").

---

### Post by gebseng on 2020-07-27
Hah, the suspense! Yes, using rsync over SSH worked flawlessly and very fast too. Can it be that the SMB protocol has problems with large numbers of files? Anyway, problem solved for now! Thanks again for all your helpful input and insight.

A side question: Can I also use diff over SSH just the same way I used rsync? I tried diff with the same directory names as with rsync previously, but got a "[COLOR=#000000][FONT=Menlo]No such file or directory[/FONT][/COLOR]" error.

---

### Post by TheFu on 2020-07-27
Best to open a new thread for each specific question.  

Different people have different expertise in different areas.
ssh can be used for many things.  Right now i have 10 terminals open to 7 different systems to do work.  Only a few specific tools, say 50, are designed for direct use with ssh, but any cli command can be used and ssh can create tunnels between systems.  There's also a way to mount remote storage over sshfs.

---

