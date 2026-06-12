---
title: "Transferring files"
date: 2007-06-01
forum: General Help
---

### Post by creamcheeze77 on 2007-06-01
I have about 30 gb of music that i'm trying to transfer from a windows computer to my new ubuntu computer.  They are connected to the same router, and i can run a cable directly between them if necessary.  What's the easiest way to transfer everything? thanks in advance

---

### Post by bmartin on 2007-06-01
Personally, I like the SSH client [here]("http://ftp.ssh.com/pub/ssh/").

Install that on your Windows machine, then install the SSH server on your computer:
```
sudo apt-get install openssh-server
```

Then you should be able to use the SFTP client on Windows to login to your Linux box with your name and password. After that, you can simply drag-and-drop the files you want to transfer.

---

### Post by trak87 on 2007-06-01
It's possible to play your Windows files on the Windows computer from Linux with the Samba networking protocol.

Otherwise, rsync is a great transfer tool. The best thing about rsync is it won't upload/download a file that already exists on the destination. Hmm, I don't know if rsync exists for Windows, but scp (secure copy) does, and you would use it thusly from your Windows box:

scp -r mp3rootdir/ yourubuntuname@192.168.1.5:/home/yourlogin/somedirectory/

This will copy all the files from the mp3rootdir directory and all the directories below it over to your linux box at 192.168.1.5 (use 'ifconfig' on Linux to determine your ip address) and store them at /home/yourlogin/somedirectory/mp3rootdir . You will be asked for your Linux login password before the transfer takes place.

You will need to install the "ssh" package on Linux first though. This is the program that will let you login from windows to linux.

As far as finding the windows version of scp, I don't have a source. Search the net for a trustworty download.

---

