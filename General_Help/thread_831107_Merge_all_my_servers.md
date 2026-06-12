---
title: "Merge all my servers"
date: 2008-06-16
forum: General Help
---

### Post by 2shae on 2008-06-16
Ok im sick of having 3 pc's on constantly. So im looking to do the following
I want to merge my Smoothwall, Freenas box and Torrent box. I have just got a new pc and my old one is no longer in use so i hope it will be perfect for the job
Amd 3500+
1.5gb ram, 80gb hd and 3 network cards (i want smoothwall to have direct control of two of them)

any guides that could help me with this?

---

### Post by tamoneya on 2008-06-16
there is no magic to putting those three services all on the same box.  Just follow the guides you used for the original installs but just do everything on one box.  Since you want smoothwall controlling two of the NICs I would install that first.

---

### Post by 2shae on 2008-06-16
ive never really done virtualisation before. any hints or tips?

---

### Post by tamoneya on 2008-06-16
You missed my point.  There is no need to virtualize.  You can run several services on one server.  The services will mind their own business.  The torrent deamon will work on some high port number say myserver.com:12345 and the freeNAS will probably be working over ssh port 22 or something like myserver.com:22 the same applies for smoothwall.  My server for example has ftp, sftp, http, https and subversion all running.  They all use serparate ports and the way I went about installing was follow a guide for ssh.  Then follow a guide for http etc...

There was no need to compartmentalize the services.

---

### Post by 2shae on 2008-06-16
smoothwall is an independant os, so is freenas and my torrent box is just a lamp server with torrentflux running

---

### Post by tamoneya on 2008-06-16
okay that was my bad.  I didnt realize that Freenas was only BSD and such.  Taking a quick look at their sites I noticed that most of them have isos as well as vmware images available.  Therefore I would recommend VMWare since it will be the simplest.  You can probably download the free(as in beer) version of vmware called VMWare player since they have the images premade.  That is one of the limitations of the free version: you cant make vmware images you can only run them.

Start with this to get vmware installed: [https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware)

As you get a little more in depth you could look at this to get yourself familiarized with how VMWare works: [http://communities.vmware.com/docs/DOC-1110](http://communities.vmware.com/docs/DOC-1110)

From there you should be able to skip through the nice VMWare docs from their site.  They are rather long but if you use the table of contents you should be able to get the relevant sections.(PDFs ~2-3MB)
[http://www.vmware.com/pdf/server_admin_manual.pdf](http://www.vmware.com/pdf/server_admin_manual.pdf)
[http://www.vmware.com/pdf/server_vm_manual.pdf](http://www.vmware.com/pdf/server_vm_manual.pdf)

---

