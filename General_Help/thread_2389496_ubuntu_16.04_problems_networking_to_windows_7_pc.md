---
title: "ubuntu 16.04 problems networking to windows 7 pc"
date: 2018-04-17
forum: General Help
---

### Post by seekertom on 2018-04-17
My pc is running only ubuntu 16.04 lts. My other pc is running only win 7 pro. Both are plugged into a wired network switch. Both pcs have access to internet. Windows pc can access other windows pcs on the network. My ubuntu pc only shows windows network under networks. I also have connect to server available. My windows pc is shared as \two-hpc, full r/w/ access.

I also have one more ubuntu 16.04 pc on the same network that I will try to access either way. I hope to be able to copy files between all pcs and share all connected printers.

My problem: I cannot connect to my windows network. when I open files, network, windows network, the response is unable to access location. failed to receive share list from server: no such file or directory.

Where do I go from here to get to there?
any help would be appreciated.
st
):P

end result is I quit trying to use ubuntu networking like I have used it in winders. Instead, I went the 'connect to a server' path, out of frustration, not by design, and this did what I needed. Now I can copy my files from my Ubie pcs to my win pcs, and also access my win pc printers.

Life is good again. thanks to all.
st

---

### Post by nlee2 on 2018-04-17
Did you install and configure samba on ubuntu?

What is the output of
pdbedit -L:

---

### Post by seekertom on 2018-04-18
probly not. it's been a battle for me, these days. Pls correct me if wrong, I need to open term, then sudo apt-get install samba. is this right? anything else?

Thanks, st

---

### Post by yancek on 2018-04-18
Read the Ubuntu documentation at the link below which explains it.

[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)

---

### Post by seekertom on 2018-04-18
my brain must be on hold. I am trying to access the windows machine from my ubuntu machine. if I read the bottom line in the directed-to instructions, "From a Windows client you should now be able to browse to the Ubuntu  file server and see the shared directory. If your client doesn't show  your share automatically, try to access your server by its IP address,  e.g. \\192.168.1.1, in a Windows Explorer window. To check that  everything is working try creating a directory from Windows." this process gives me access From windows To ubuntu. I need the other way around... perhaps I am missing something. Will this process let me see the files on my windows pc From my ubuntu pc?
st

---

