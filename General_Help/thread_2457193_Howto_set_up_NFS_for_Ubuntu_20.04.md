---
title: "Howto set up NFS for Ubuntu 20.04"
date: 2021-01-27
forum: General Help
---

### Post by Old Jimma on 2021-01-27
Hi Community:

I've tried several web sites to find out how to set up NFS for 20.04

Can't get it to work.

Can somebody recommend an authoritative site that they've tried and works?

Thanks,
OJ

---

### Post by TheFu on 2021-01-27
[LIST=1]
[*]What have you done?
[*]Show the server-side config.
[*]Show the client-side config.
[*]Get help.
[/LIST]


[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs) is the official ubuntu documentation. Follow that.

---

### Post by jay-eich on 2021-01-27
Hello Jimma,
   I don't know your background...
   Pardon this simple question.  Where is the drive?

If it is just an external drive , without a computer, if it has a USB connection, plug it in and do a df to find it.  when done, do a sudo umount....

If it is an external drive, with a local internet connection, you can use Nautilus to access it.
A tutorial: [ [https://www.youtube.com/watch?v=IjeDiChJpws](https://www.youtube.com/watch?v=IjeDiChJpws) ](https://www.youtube.com/watch?v=IjeDiChJpws)

Otherwise, there is Samba...

Happy exploring,
Jay

---

### Post by Old Jimma on 2021-01-27
Hi Fu:

I did this: > [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04)

Old

---

### Post by HermanAB on 2021-01-27
Note that NFS is so simple to set up, that there are few guides on it, since it is a one liner.  Best is to read the man pages first.

The Digital Ocean guide is for exporting your /home directory to a server.  This is a rather extreme thing to do and will only work if your network works perfectly to begin with.  If the network is not up yet when the export wants to happen, your system will be without a home directory and you won't be able to do much and will be left scratching your head, which is most probably exactly what has befallen you.

It is therefore better to export a new data directory and get it to work first, before you mess with your /home file system.

---

### Post by TheFu on 2021-01-27
[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs) is the official ubuntu documentation. Follow that.

---

