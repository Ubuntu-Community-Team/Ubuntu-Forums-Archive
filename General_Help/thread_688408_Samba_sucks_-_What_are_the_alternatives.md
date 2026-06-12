---
title: "Samba sucks - What are the alternatives?"
date: 2008-02-05
forum: General Help
---

### Post by RudolfMDLT on 2008-02-05
Hi,

I'm giving up on Samba in 7.10. I've had loads of help from the forum and friends but there comes a point in life where you just say STOP! The sharing only sometimes works, and the permissions change at will and whim. Using a 4gb flash drive at the moment and scp. Though I need something that I can use on my backup server that can be used by windows users as well.

I would like to know what are the alternatives? Has anybody used NFS? What was your experience? And does it work with windows? Anything that you found that I need to watch out for?

Thanks for any help and advice!

Rudolf

---

### Post by wieman01 on 2008-02-05
NFS does not work with Windows, that's the drawback. But it is very simple to use. Guess this is a good starting point:

[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

I will replace Samba very soon, too. I have had enough. Performance is poor in terms of transfer rates and it has a very random behavior at times. So reverting to NFS will be a big improvement I hope.

The only drawback is that you have to actually "mount" shared drives. Samba lets you access them without the need to specifically mount them. But I can live with that.

---

### Post by Borbus on 2008-02-05
Not being funny, but if you're having those sort of problems then you're doing it wrong. I use samba on a debian box to serve files to windows PCs (it works with linux PCs too, but I just nfs for that).

Have you tried some configuration apps for samba? There's a web based one, can't remember what it is called though.

---

### Post by Seisen on 2008-02-05
> **Borbus said:**
> Not being funny, but if you're having those sort of problems then you're doing it wrong. I use samba on a debian box to serve files to windows PCs (it works with linux PCs too, but I just nfs for that).

Have you tried some configuration apps for samba? There's a web based one, can't remember what it is called though.

Your thinking of Swat I believe.

---

### Post by sturmey on 2008-02-05
You may be thinking of webmin.

Realistically Samba is a PITA to configure, but until last year worked fine. XP usually works once it is setup, but Vista is a different matter. Somehow it is writing it's own permissions onto files in our installation.

I have to research this more, but we may be switching away from Vista to something less troublesome.

Sturmey

---

### Post by kuja on 2008-02-05
> **RudolfMDLT said:**
> Hi,

I'm giving up on Samba in 7.10. I've had loads of help from the forum and friends but there comes a point in life where you just say STOP! The sharing only sometimes works, and the permissions change at will and whim. Using a 4gb flash drive at the moment and scp. Though I need something that I can use on my backup server that can be used by windows users as well.

I would like to know what are the alternatives? Has anybody used NFS? What was your experience? And does it work with windows? Anything that you found that I need to watch out for?

Thanks for any help and advice!

Rudolf

sftp is braindead easy to use, just install openssh-server and that's all the setup necessary .... Should be usable by windows as well though you'll probably need to find  a client for it .... and probably a server also if you want the windows machine to serve.

---

### Post by bodhi.zazen on 2008-02-05
> **wieman01 said:**
> NFS does not work with Windows, that's the drawback. But it is very simple to use. Guess this is a good starting point:

[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

I will replace Samba very soon, too. I have had enough. Performance is poor in terms of transfer rates and it has a very random behavior at times. So reverting to NFS will be a big improvement I hope.

The only drawback is that you have to actually "mount" shared drives. Samba lets you access them without the need to specifically mount them. But I can live with that.

Just a FYI, you can mount NFS shares in Windows XP and Vista. It takes some patience as configuring Windows is not so straight forward, but it is possible.

[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

[http://doc.gwos.org/index.php/MountNFS](http://doc.gwos.org/index.php/MountNFS)

[http://www.openfree.org/pet/index.php/Mount_an_NFS_share_from_Windows](http://www.openfree.org/pet/index.php/Mount_an_NFS_share_from_Windows)


If you do not want to use samba, you can try ssh (scp), ftp, http, or nfs. Just be sure you understand the security implications of those protocols.

---

