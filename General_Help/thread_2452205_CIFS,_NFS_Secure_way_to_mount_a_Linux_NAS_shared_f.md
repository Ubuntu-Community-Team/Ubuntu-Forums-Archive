---
title: "CIFS, NFS :Secure way to mount a Linux NAS shared folder on Linux desktop ?"
date: 2020-10-18
forum: General Help
---

### Post by alain.roger on 2020-10-18
Hi,

i would like to know what is the best secure way to mount a Linux NAS shared folder on Ubuntu Desktop ?

I understood that CIFS is used when client/server is a mix of windows and linux. NFS is when client / server are both on Linux.
However, NFS is described as not secure way to mount shared folders. 

thx

---

### Post by ActionParsnip on 2020-10-18
I prefer SSHFS/SFTP. All you need to do is install openssh-server and you are good to go. You authenticate as your system user and you will be presented with the user's home folder. Dead easy and very secure

---

