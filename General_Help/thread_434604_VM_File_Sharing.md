---
title: "VM File Sharing"
date: 2007-05-06
forum: General Help
---

### Post by diablo69er on 2007-05-06
I have spent a few hours trying to find the answer to this--and so far I haven't been able to.

My question is, I run 7,04 ubuntu, and I have a windows VM through vmware server, that I would like to transfer files from onto my ubuntu box.  At first I was using nero and dvds to transfer files, but thats a pain--so is there a easier way to do this?


I'd appreciate steps to be able to accomplish this

---

### Post by lw5 on 2007-05-06
I'm using a mapped network drive...

---

### Post by total wormage on 2007-05-06
yes there is,

you can try to connect to your host OS using the local network you probably have.
If you already have a configured Samba, you can try to make the Windows install have a place in your local network by giving it a other ip address than your Ubuntu install :]

i hope this is enough information, i don't have a configured VM right now, so i can't go into specifics :]

---

### Post by diablo69er on 2007-05-06
> **total wormage said:**
> yes there is,

you can try to connect to your host OS using the local network you probably have.
If you already have a configured Samba, you can try to make the Windows install have a place in your local network by giving it a other ip address than your Ubuntu install :]

i hope this is enough information, i don't have a configured VM right now, so i can't go into specifics :]

I thought I should use Samba--however there isn't a Definite tutorial to my knowledge....

If there is I would appreciate a link.

If there isn't one, i'd like to learn a little more about it so I am more knowledgable the next time around.

---

### Post by spliskin on 2007-05-06
you need to install samba first 

sudo apt-get install samba

then within windows right click on the folders you want to share with your host and then choose sharing and security and share the folder.

looking in Places>Network within Ubuntu you should see your machine listed. 


If you are still having problems have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=294514&highlight=vmware+share+host](http://ubuntuforums.org/showthread.php?t=294514&highlight=vmware+share+host)

Cheers!

---

### Post by diablo69er on 2007-05-06
Got it working--I am in the process of writing a tutorial, that will show users how to install it step by step.  Figured it was a pain in the **** for me, so I might as well make it easier for others.  Thanks.

---

### Post by barmaley on 2007-05-09
Hello, ubuntu people

diablo69er, I'm interested in the tutorial on sharing files between vm and ubuntu.
So far, I only managed to see ubuntu shared folder from vm with samba, but still cannot write to that folder.
I will appreciate your help.

---

### Post by beerorkid on 2007-05-09
[URL="http://easylinux.info/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service[/URL] can help

also mounting is a bit below the link posted.

---

