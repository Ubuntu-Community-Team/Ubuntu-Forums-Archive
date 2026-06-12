---
title: "I can no longer access shared folders on my network thru SMB or NFS"
date: 2008-02-23
forum: General Help
---

### Post by mkarr on 2008-02-23
Folder shares was working fine when I updated to gutsy back in December? and was working as recently as a month ago but now I'm getting "folder contents can not be displayed". I haven't installed firestarter on any computer in the network so I don't believe it is a firewall. I opened a terminal and entered smbtree and all the shared folders on the network are listed, and I can ping the computers on the network so everything is connecting. Shared internet is working fine too. So why can't the shared folder contents be displayed? Would really appreciate any help! Thanks!

---

### Post by moore.bryan on 2008-02-23
couple of clarifying questions:
     which one are you using, nfs or smb?
     are all your networked comps running linux?

---

### Post by mkarr on 2008-02-23
I was using smb to begin with till that went down. I just tried nfs with the ip addresses and that isn't working either. Yes I have gutsy installed on both computers.

---

### Post by moore.bryan on 2008-02-23
okay, that's a good starting point. can i assume you've read through all the very confusing nfs troubleshooting tutorials running 'round the net, including the official one at sourceforge?

can you ping the server's address from the client machine with success? what does running "rpcinfo -p xxx.xxx.xxx.xxx" from the client machine give you, where the x's are your server ip?

---

### Post by mkarr on 2008-02-23
I can ping the server machine from the client and rpcinfo gives this as output:

  program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  32769  status
    100024    1   tcp  49550  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32771  nlockmgr
    100021    3   udp  32771  nlockmgr
    100021    4   udp  32771  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  46893  nlockmgr
    100021    3   tcp  46893  nlockmgr
    100021    4   tcp  46893  nlockmgr
    100005    1   udp  32772  mountd
    100005    1   tcp  52229  mountd
    100005    2   udp  32772  mountd
    100005    2   tcp  52229  mountd
    100005    3   udp  32772  mountd
    100005    3   tcp  52229  mountd

The only NFS tutorial I read was the one posted in this forum ....sorry.

---

### Post by moore.bryan on 2008-02-23
no worries...
when you try to connect from the cli, what command do you issue and what error is reported?

---

### Post by mkarr on 2008-02-23
I just try to connect through Nautilus by opening the network folder which displays both computers on the network. When I try to access the server from the client (or viceversa) I get the error "folder contents cannot be displayed".

---

### Post by moore.bryan on 2008-02-23
do me a favor and try through a terminal with ```
sudo mount -t nfs xxx.xxx.xxx.xxx:/folder/being/shared /mount/point/on/your/client
```

---

### Post by mkarr on 2008-02-23
That actually worked. I've been trying to find a tutorial that would show how to mount the network file system like that but wasn't having much luck. It took me long enough just to figure out it wasn't yet mounted right. Thanks so much. Don't know how long it would have took me to find that on my own (maybe never). Wish I could figure out what happened to the samba server though.

---

### Post by moore.bryan on 2008-02-23
i'm glad it worked for you, even though it doesn't seem to solve your underlying nautilus problem; perhaps that will work itself out in due time.

i'm curious: with two linux machines, why were you using samba to begin with? from all i've read, nfs is "superior" to samba in almost every way.

---

### Post by mkarr on 2008-02-23
If I could impose on you again, what would the command be to add that permanently to fstab. Thanks so much!

---

### Post by mkarr on 2008-02-23
And the answer to your question is lack of information. Thank god for people like you!

---

### Post by mkarr on 2008-02-23
Ok I found how to edit fstab in the ubuntuguide. Sometimes all I need is to be pointed in the right direction. Thank you.

---

### Post by moore.bryan on 2008-02-24
> **mkarr said:**
> If I could impose on you again, what would the command be to add that permanently to fstab. Thanks so much!
And the answer to your question is lack of information. Thank god for people like you!
Ok I found how to edit fstab in the ubuntuguide. Sometimes all I need is to be pointed in the right direction. Thank you.
glad you found your way... the ubuntuguide is so useful sometimes!

happy ubuntu-ing.

---

