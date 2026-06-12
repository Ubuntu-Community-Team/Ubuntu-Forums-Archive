---
title: "backing up files from ftp"
date: 2006-12-29
forum: General Help
---

### Post by linuxbun on 2006-12-29
I've had a look at a few programs and I haven't really found what I want.

I'm looking for something that will work like rsync does to backup files FROM ftp to my local directory but to only download the changed / newer files etc.

Any ideas?

---

### Post by evilghost on 2006-12-29
Check out ncftpget

---

### Post by linuchsan on 2006-12-29
You can with rsync and the -u option.

---

### Post by linuxbun on 2006-12-30
> **linuchsan said:**
> You can with rsync and the -u option.

Looked at the man, this looks to do what I want, BUT.. I can't work out the ftp protocol to use.

I have to put a username & password to connect but it doesn't say how to in the man :confused:

---

### Post by linuxbun on 2006-12-30
Does rsync even support ftp with a username & password?

I've been googling for hours and I haven't found a solution :rolleyes: :rolleyes: ](*,) ](*,) ](*,) ](*,)

---

### Post by evilghost on 2006-12-30
> **linuxbun said:**
> Does rsync even support ftp with a username & password?

I've been googling for hours and I haven't found a solution :rolleyes: :rolleyes: ](*,) ](*,) ](*,) ](*,)

man rsync

> 
 RSYNC_PASSWORD
              Setting  RSYNC_PASSWORD  to  the required password allows you to
              run authenticated rsync connections to an rsync  daemon  without
              user  intervention. Note that this does not supply a password to
              a shell transport such as ssh.

       USER or LOGNAME
              The USER or LOGNAME environment variables are used to  determine
              the  default  username  sent  to an rsync daemon.  If neither is
              set, the username defaults to “nobody”.


These are environment varibles so you'll likely need to set them prior to running rsync:
```

export RSYNC_PASSWORD=my_ftp_password
export USER=my_ftp_username

```

It also looks like it suppots the rsync://user:password@host syntax.

---

### Post by koenn on 2006-12-30
> Does rsync even support ftp with a username & password?
 
AFAIK it doesn't.
you can synchronise files to/from remote hosts, but that depends on ssh or some other ssl application - not ftp. 

you may want to look at wget. I think it can use ftp (else, why not use http ?) and i believe it has sufficient options and switches to compare file timestamps or do "never overwrite newer".

---

### Post by linuxbun on 2006-12-30
> **koenn said:**
> AFAIK it doesn't.
you can synchronise files to/from remote hosts, but that depends on ssh or some other ssl application - not ftp. 

you may want to look at wget. I think it can use ftp (else, why not use http ?) and i believe it has sufficient options and switches to compare file timestamps or do "never overwrite newer".

But that totally contradicts what evilghost has said :confused: 

Evilghost, thanks for your reply. I didn't find that as I was searching for "ftp" and anything that said "username" or "password" within the same paragraph. I should have read the man page a bit thorougher :) 

I still can't managed to get that to work. Seem to be having all sorts of hiccoups. I have however find a work around...

I've used curlftpfs to mount my ftp folder. Once mounted, I can run a rsync command which works well (rsync [options] ~ftpfolder ~ftpbackup) etc.

Working on this, I'm now trying to make a script that runs all this which I'll set as a cron to run every day. As I don't think it's wise to have my ftp space mounted all the time (which might fail the backup if it disconnects) I'm trying to build a script that does this...

1) mount ftp folder
2) run rsync cmd
3) dismount ftp folder

I'm COMPLETELY NEW to making scripts, needles to say I'm having fun :mrgreen: 

These are the commands I want to run, if anyone can give me any pointers as to which order, how to insert them into my script (bkup.sh) I would greatly appreciate it. This is what I've got so far...

```
#!/bin/bash

curlftpfs -o user=useracc:password ftp://ftp.mysite.co.uk/path/to/backup ~/ftpspace

rsync -r -t -v --progress ~/ftpspace ~/ftpbackup

umount ~/ftpspace
```

I've run it and it won't work. It doesn't seem to mount the folder unless I do it manually. Also umount cmd won't work until I can find out to make it so a user can umount and not have to sudo it.

---

### Post by koenn on 2006-12-30
> But that totally contradicts what evilghost has said
That, *I *can't help. 

a common way to use rsync is
rsync [options] /home/tarzan   jane@some_server:/home/ jane
which would sync the files in /home/tarzan with the files in /home/jane on some_server.
That requires you have access to /home/jane, hence the need to specify the account : jane@some_server. It will prompt for jane's password. 

It also works the other way arouns, from some_server to a local filesystem, or between directories on a local filesystem.

from [http://samba.org/ftp/rsync/rsync.html](http://samba.org/ftp/rsync/rsync.html)
> There are two different ways for rsync to contact a remote system: using a remote-shell program as the transport (such as ssh or rsh) or contacting an rsync daemon directly via TCP. 

On the other hand, it's interesting that you found it possible to mount a remote filesystem over ftp - maybe then rsync will see it as just copying between local directories (as in the rsync statement you use). Clever. 

I don't see why your script won't work. If the statements you posted work when you type them in a terminal, they should also work in a script. Is that only because you need sudo, or are there other problems as well ?

---

### Post by linuxbun on 2006-12-31
> **koenn said:**
> 
On the other hand, it's interesting that you found it possible to mount a remote filesystem over ftp - maybe then rsync will see it as just copying between local directories (as in the rsync statement you use). Clever. 

Ta :mrgreen:
After quite of bit of googling, I've got the script to work. I could mount it as user as I added myself to the fuse group, but I couldn't umount it with using sudo somewhere. Then I looked up fuse, if I used **fuse** umount cmd, I could do it without being prompted for the sudo pw.

Also, the script (at first) went straight to the rsync cmd and didn't seem to mount the ftp folder. So I put the script "sleep" in between. After all that, it's working successfully!! :D 

My script is copied down below for those who want to use it...

```
#!/bin/bash

curlftpfs -o user=username:pw ftp://ftp.website.co.uk/public_html/ ~/ftp

sleep 2

rsync -r -t -v --progress --delete -c ~/ftp/ ~/ftpbackup

sleep 2

fusermount -u ~/ftp
```

my first working script! I'm well happy :tongue: :biggrin: :biggrin: :biggrin:

Just need to cron that now ;) :D

---

### Post by koenn on 2006-12-31
> So I put the script "sleep" in between
this indicates that you need the script to wait for the previous command to be completed (succesfully) before executing the next one. 
with 'sleep 2' you wait 2 seconds, so if it takes longer then that to complete the ftp mount or the rsync, your script will fail again.

suggestion:
string the commands together with && ('AND') - this way a command is only executed after succesfull completion of the previous one
try something like
```

curlftpfs -o user=username:pw ftp://ftp.website.co.uk/public_html/ ~/ftp  &&  \
rsync -r -t -v --progress --delete -c ~/ftp/ ~/ftpbackup  &&  \
fusermount -u ~/ftp

```
(see if that works, can't test it here)

an other good scripting practise is to check for unsuccesful commands, eg by using || ('OR'). the part after || is only executed if the part before it failed, so you can do

```
curlftpfs -o user=username:pw ftp://ftp.website.co.uk/public_html/ ~/ftp  || echo "curlftpfs failed" 
```

---

### Post by linuxbun on 2006-12-31
That's brilliant! Just what I needed, thanks very much!!!!!!!!1 :D

---

