---
title: "Remotely access Ubuntu from PC + Mac"
date: 2005-09-23
forum: General Help
---

### Post by redmoon on 2005-09-23
Hello,

I was wondering if it is possible to access my Ubuntu machine at home from PC and Mac machines at university? 

Thanks.

---

### Post by Zensunni on 2005-09-23
I'm really curious about this too. I'd really like the idea of being able to access my house from work.

The only thing I've thought of is to throw in an ubuntu live CD on a windows machine. Has anyone done this?

....I'll report back if I have any success with this.

---

### Post by redmoon on 2005-09-23
Hmm...

what I would really like to be able to do is to just grab the odd file from my Ubuntu machine when im away from it and accessing any old random PC or Mac on the University network.

When I ran XP, i used to use foldershare.com as a way of being able to transfer the odd document. 

I guess I was really wondering if there's anything like that for linux machines.

---

### Post by tktreload on 2005-09-23
Hello

If your PC at home is turned on you can set up ssh, and use a small program called putty to access it from any windows pc..
Mac computers have a built in ssh client so there you do the same.

---

### Post by redmoon on 2005-09-23
can you please tell me how to do that, or point me in the right direction? would really appreciate it.

Thanks.

---

### Post by sickdude on 2005-09-23
first start up your ssh server

```
sudo /etc/init.d/sshd start
``` 

if it isnt there 

```
sudo apt-get install ssh
``` 

then when your somewhere else and you have a windows machine open up putty (google it) and type in your ip number or your domainname press enter

this will open up a black screen and ask for your username and password and this will work

if you have a linux box go into commandline and enter 

```
ssh ***.***.***.*** -l username -X
``` 

the -l means wich user you want to log in with, your password will be asked later

and the -X means you cacn start up x window apps, try gaim or another app and be amazed

---

### Post by jrib on 2005-09-23
[https://wiki.ubuntu.com/SSHHowto?highlight=%28ssh%29](https://wiki.ubuntu.com/SSHHowto?highlight=%28ssh%29)

That should help you set up an ssh server on your Ubuntu system(I haven't done this myself however).  

I am going to agree with tktreload and tell you that you can use [putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/)  to access your ssh server.

If you are looking at copying a lot of files I am going to recommend using [WinSCP](http://winscp.net/eng/index.php) for that.  It will give you a nice gui interface for dragging and dropping files.

Good luck!

---

### Post by redmoon on 2005-09-25
Hmm... thanks for your help everyone it is all much appreciated. I am not in a position where i can install programs on university computers since they are basically there for internet, word processing and email. It looks like the only way i can access my ubuntu machine from uni would be via an installed program. darn.

---

### Post by jrib on 2005-09-25
[QUOTE=redmoon]Hmm... thanks for your help everyone it is all much appreciated. I am not in a position where i can install programs on university computers since they are basically there for internet, word processing and email. It looks like the only way i can access my ubuntu machine from uni would be via an installed program. darn.[/QUOTE]

If your university has some macs then you can run "terminal" or "X11".  I don't know too much about macs but I do know these programs are included in OSX (take a look at: [http://www.apple.com/macosx/features/x11/)](http://www.apple.com/macosx/features/x11/)).  X11 will give you the ssh -X functionality someone spoke about before.  Terminal will work fine; you just won't be able to run remote programs that have a gui.

---

### Post by tomchuk on 2005-09-25
For macs, if they run OS X, just open terminal (Finder -> Applications -> Utilities -> Terminal) you can then use ssh to login to your Ubuntu box, and scp and sftp to transfer files.

For windows, put putty.exe and the standalone WinSCP???.exe on a thumb drive. ssh and sftp away.

If you want to interact with your Ubuntu box graphically, install the freeNX server and keep the nomachine nx clients for Windows and Mac on you thumb drive.

---

### Post by artinla on 2005-09-25
Why not just use VNC?

It is just like remote desktop for windows.

Art

---

### Post by tomchuk on 2005-09-26
[QUOTE=artinla]Why not just use VNC?[/QUOTE]

freeNX > *

---

### Post by ubuntme on 2005-09-26
If you just want to access files, the uni puters may have ssh installed on them.

---

### Post by redmoon on 2005-09-29
Excellent. Thanks for your help everyone, it is very much appreciated :)

I'm starting to learn a bit more about ssh.

Is there a way to list a directory on a remote computer (ie. my Ubuntu machine when I'm away from it and looking for a file I need).

Cheers.

---

