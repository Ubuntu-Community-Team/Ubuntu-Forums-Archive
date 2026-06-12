---
title: "how to copy files from one computer to another"
date: 2007-12-31
forum: General Help
---

### Post by zbog on 2007-12-31
Hello, I have 2 computers running Kubuntu 7.10, they are called bogdan and bogdan-duo.

I try to transfer some files (the whole /home/zbog on machine bogdan to /home/bogdan  on machine bogdan-duo). I had some trouble setting up Samba (both server+client on both machines), but although I think I have set it up correctly, yet it does not work.
I installed samba using the "task name" feature in Synaptic (Synaptic menu -> Edit -> Mark packages by task)

When I try access the shared files on the other machine, I get an error:
> An error occurred while loading smb://bogdan/ZBOG:
The file or folder smb://bogdan/ZBOG does not exist.
I tried accessing smb://bogdan/ZBOG from bogdan-duo and from bogdan (i.e. localhost), same error!

---

### Post by icheyne on 2007-12-31
The GUI tools never work for me, but I found NFS pretty easy to set up.

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by zvacet on 2007-12-31
Maybe foldername is** bogdan/zbog** not /bogdan/ZBOG

---

### Post by zbog on 2007-12-31
On the filesystem it's /home/zbog. "Samba Name" was smb://bogdan/ZBOG (it was the default name).
I changed the samba name for the folder to smb://bogdan/zbog.

I atached Some more screenshots with the problem:

I'll try the non-gui guides posted by icheyne.

---

### Post by cybervegan on 2007-12-31
First of all, are you sure that both the computers are correctly attached to the network?

Have you tried the following test?

You will need the network address of both machines - I will call them A and B.

Ping test - using the IP address of B try to ping it from A: From machine A, open a terminal window and type 'ping' followed by the IP address of machine B, for example:

ping 192.168.0.1

You should get messages like 'xxx bytes received from 192.168.0.1 in 8 ms' - if you get errors, this is your first problem.

If you got no errors, then repeat from machine B, pinging machine A. 

Once you are sure your basic networking is functioning correctly, you can go back to setting up your data transfer.

Personally, I find it easier to use NFS as pointed out above, or even scp for 'one off' copies, as they are much easier, and built-in to Linux. Samba is better for when you want to connect Windows computers to Linux computers - it's overkill when you have just Linux machines.

-cybervegan

---

