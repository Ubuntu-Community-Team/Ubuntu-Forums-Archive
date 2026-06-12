---
title: "Copying Files Across The Network??"
date: 2008-06-17
forum: General Help
---

### Post by matey3 on 2008-06-17
Hello All;
As I said before the new updates have locked my system tight to the point of stupidity where neither ftp nor ssh work any more!

I am to copy 3 files to this server which is actually a virtual; server and I cannot do it for the reasons I mentioned above.
Can I use the cp command and IP address of the server which has the files?
Also I was able to copy my files to the main physical server which is hosting these 3 virtual servers where that one particular (trouble) server resides.
Is there any thing I can do to copy/send these 3 small files over to this virtual (xen) server?

Thanks in advance...
PS I inherited this mess from some 1 who was long gone b4 i got here, so I am still new to this (but learning a lot) so please give me a break and little more detail.
thanks a lot!

---

### Post by cmnorton on 2008-06-17
Why can't you use ftp or ssh? That is why don't they work? Can you ping the "virtual" server?

Can you connect using either of these if you use its ip address instead of the server's name?

Suggesting copying means you're using SAMBA of NFS, and if you cannot ssh or ftp, you probably cannot mount shares. All that's left would be "sneaker net"; that is get the files on media and install them without the network.

However, you might get more help by posting more information.

---

### Post by matey3 on 2008-06-17
Thank You CmNorton
I just now remembered that we do have a samba setup.

I had no problems with ssh or ftp before installing the new security updates.
and also before I could ssh to the name of the server now I can only type in the IP address. (may be unrelated ?) but any ways there are problems with this network and I am trying to sort it out. of course the last time I used Liux was back in 1995 lol and then I didnt have to do all these virtual/xend/xm  stuff but thanks any ways for the reply. I may be able to go thru that samba server...?
Regards;




> **cmnorton said:**
> Why can't you use ftp or ssh? That is why don't they work? Can you ping the "virtual" server?

Can you connect using either of these if you use its ip address instead of the server's name?

Suggesting copying means you're using SAMBA of NFS, and if you cannot ssh or ftp, you probably cannot mount shares. All that's left would be "sneaker net"; that is get the files on media and install them without the network.

However, you might get more help by posting more information.

---

### Post by matey3 on 2008-06-18
I found a better command than cp to do this;

scp file.name IP Address of remote machine:/directory/folder/ 
for instance if I want to copy many files to the remote machine and into /etc/new/ directory I could do this ( I could use -r like this);

scp -r *.* 192.168.1.10:/etc/new/

the key is the semicolon at the end of the IP address and NO spaces before the fwd. slashes/!
I think I put the : (semicolon) in the wrong place before and that is why it didnt work.
Any way it comes and asks you for the root/su password then copies really fast.

SCP/RCP and RSYNC are great tools. (but not in CAPs) lol :)#

:guitar:

---

