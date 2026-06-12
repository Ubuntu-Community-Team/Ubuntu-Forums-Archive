---
title: "connect to another computer from live cd?"
date: 2012-12-28
forum: General Help
---

### Post by garyed on 2012-12-28
I have a windows laptop that is unbootable & I want to backup what I can before doing anything else to it. I want to copy files to my Ubuntu desktop that is connected to my wireless router but can't figure how to connect. I've booted the laptop with a 10.04 liveCD, mounted the hard drive & have  a connection working thru my router. Can anyone tell me what steps to take to connect the two computers?

---

### Post by raja.genupula on 2012-12-28
[http://askubuntu.com/questions/65155/how-to-access-my-computer-remotely](http://askubuntu.com/questions/65155/how-to-access-my-computer-remotely)

---

### Post by Luigi2012SM64DS on 2012-12-28
> **garyed said:**
> I have a windows laptop that is unbootable & I want to backup what I can before doing anything else to it. I want to copy files to my Ubuntu desktop that is connected to my wireless router but can't figure how to connect. I've booted the laptop with a 10.04 liveCD, mounted the hard drive & have  a connection working thru my router. Can anyone tell me what steps to take to connect the two computers?
You cannot access a computer when it is turned off and i believe you cannot access windows from ubuntu.
Best thing you can do is take out the hard drive and connect it to your computer using a usb enclosure.

---

### Post by steeldriver on 2012-12-28
> **garyed said:**
> I've booted the laptop with a 10.04 liveCD, mounted the hard drive & have  a connection working thru my router. Can anyone tell me what steps to take to connect the two computers?

If you have an NFS or SAMBA server running on the desktop machine (or can install/start one), you can mount a share from the LiveCD on the laptop and copy stuff to it - even easier if your router has an attached USB share that you can mount inside the LiveCD session

Alternatively you could install OpenSSH-server from the LiveCD session and then connect in from the desktop and copy using scp

---

### Post by garyed on 2012-12-28
I can use ssh from the bad laptop to connect to my desktop so I can connect the two computers. The problem is neither rsync nor scp commands will work from the laptop.

---

### Post by windscape on 2012-12-28
Hi,

You probably need to install openssh-server on your Ubuntu Desktop. On 12.04 it will automatically start it after it is installed. Once that is done, you should be able to ssh and scp from the laptop to the desktop using your Ubuntu username on the desktop. If that doesn't work, please post the output of your commands so we can see why they aren't working.

---

### Post by CharlesA on 2012-12-28
If you can use ssh, you should be able to use rsync and scp/sftp.

---

### Post by garyed on 2012-12-28
Actually sftp works but scp & rsync do not. Its just a lot slower but I'm 
using sftp to copy 30 gig off the old HD. I wanted to use rsync & just copy everything with one command but I couldn't get it to work even on one individual file.

---

### Post by CharlesA on 2012-12-29
What message does rsync give you?

---

### Post by garyed on 2012-12-29
> **CharlesA said:**
> What message does rsync give you?

I'm not at my computer now but I don't remember getting any error messages from rsync or scp. The only way I knew they weren't working was by checking the desktop I was trying to copy the files to. I have another laptop that I use rsync all the time with to copy files to the same desktop & never have any problems. I think it has something to do with either the live CD or a file that needs to be altered .

---

