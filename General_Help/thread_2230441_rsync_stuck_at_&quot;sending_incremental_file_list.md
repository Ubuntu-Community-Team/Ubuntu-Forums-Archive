---
title: "rsync stuck at &quot;sending incremental file list&quot;"
date: 2014-06-19
forum: General Help
---

### Post by aknob2 on 2014-06-19
Hallo,
I'vean older machine  freshly set up with an ubuntu percise server version. 
This special machine always get stuck when i try to copy files from other machines with rsync. Only  "sending incremental file list" is shown, no list is set up.
I also can't push files from other machines to this particular one. Rsync on same machine does work.
Directories are written if i push from an other machine, but they are empty. Those direcories are shown in the file list on the other machine.

Thought it to be an rights issue, but i have no idea whats wrong.
Does anyone has an idea?

Thanks a lot in advance
Andreas K.

---

### Post by SeijiSensei on 2014-06-19
Try running rsync with sudo:
```
sudo rsync -av source/ target/
```
You'll have root permissions that way and should be able to transfer any file.

---

### Post by aknob2 on 2014-06-19
> **SeijiSensei said:**
> Try running rsync with sudo:
```
sudo rsync -av source/ target/
```
You'll have root permissions that way and should be able to transfer any file.

Thanks a lot - but i forgot - the same with sudo!

---

### Post by nerdtron on 2014-06-19
Have you tried sending onto a different folder on the destination? You may have permission issues on the destination.

Just to confirm that you can transfer files to the remote computer, can you "ssh" to that computer? Does "scp" also fails when you try to push to that computer?

---

### Post by SeijiSensei on 2014-06-20
> Thanks a lot - but i forgot - the same with sudo! 

If you cannot copy the files as the root user, then there is a deeper problem.

Perhaps the target's drive is marked read-only.  If there are any problems with the file system, Linux will mount the drive read-only.

Can you create files locally on the target machine?  What do you see if you run the "mount" command on that machine?

---

### Post by aknob2 on 2014-06-24
Sorry, that i didn't answer for 3 days,

i can normally write and edit files on the partition, so it is surely not mounted 'ro'.
I've just checked, i can copy files with the scp command from the remote-host. 
'scp [email]server@xxx.xxx.xxx.xxx[/email]:/root/scripts/* scripts' does work, where
'rsync -avz [email]server@xxx.xxx.xxx.xxx[/email]:/root/scripts/ scripts' is stuck in 'receiving incremental file list'

???, thanks a lot in advance,
Andreas K.

---

### Post by nerdtron on 2014-06-25
Are you sure it is stuck on "receiving incremental file list"? Maybe because of the -z option it is taking too long to compress, or maybe you have thousands of file/large files that is why rsync takes too long to build the list.

Try rsync with just the options -avh only and let's see if there is any difference.

---

### Post by HermanAB on 2014-06-25
Also, rsync requires a good network connection.  If you have network errors, then rsync will misbehave.

---

### Post by aknob2 on 2014-06-26
Thanks a lot for your comments. No, it does not make a difference if I don't use the -z option and because I'm logging in via ssh, skipping the -v option does also make no difference and the computers are standing side by side in the same local network, there are only about 200kbytes (30 script files) to copy. 

As the problem seems to become even more tricky (if i used a -avvvvvvvz option AND pipe the output to a file, i'll get some of the desired files syncronised, if i use it serveral times, the files arrive drop by drop) i want to thank all who have contributed to that thread. If i find a solution, i'll post it here.

Thanks a lot

Andreas K.

---

### Post by SeijiSensei on 2014-06-26
Try using "-avn" and seeing what it reports.  That just builds the list of files to be transferred but doesn't actually copy them.  If there are lots of files to check, it can take quite a while to build the list.  Have you let it run overnight?

---

### Post by ITfromScratch on 2014-11-14
I ran into this error when I was trying to rsync a symbolic link.

---

### Post by Thekow on 2015-11-08
I am also getting this problem i am backing up to a FREEnas server. I can copy the files across if i don't use the delete option (which I want to use). When i used --delete it just hangs at "Sending incremental list". A dry run works perfectly. I have tried running sudo , root. There is no output to track down what is happening.  

command i am using.

sudo rsync -vr --ignore-existing --delete --progress --stats TARGET DESTINATION. If i add dry run it happens ok. The files are 777 / 775 so it should not be a permissions issue! Any suggestions guys?

---

### Post by brianbuchanan on 2016-06-13
Sorry to necro this thread.  I was having this problem and it was a Jumbo Frames problem.  My source and destination had jumbo frames enabled (9000) but not my switch.  After enabling Jumbo frames on the switch this problem went away.

---

### Post by DuckHook on 2016-06-13
> **brianbuchanan said:**
> Sorry to necro this thread.  I was having this problem and it was a Jumbo Frames problem.  My source and destination had jumbo frames enabled (9000) but not my switch.  After enabling Jumbo frames on the switch this problem went away.Necro, indeed. Thank you for your update. And with that...

**Closed**

---

