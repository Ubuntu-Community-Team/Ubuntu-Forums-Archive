---
title: "netselect"
date: 2007-02-11
forum: General Help
---

### Post by shdawson on 2007-02-11
Hi,


# apt-get install netselect comes back with nothing.  I need to edit so I can hit other mirrors.

How do I get netselect?


Thanks.....

---

### Post by nyinge on 2007-02-11
It's in the universe repo.  Have you turned it on?

---

### Post by shdawson on 2007-02-12
universe repo?  Never heard of it.  Will you please tell me more about this?

---

### Post by shdawson on 2007-02-12
for clarity, i am ussing ubuntu server.  so, no graphical interface.


thanks...

---

### Post by seppo on 2007-02-12
Here is a commandline version of enabling more repositories:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by shdawson on 2007-02-12
Thanks.  I will go through this and (hopefully) update my ubuntu with webmin.


FYI, do you know what mirror has webmin?

---

### Post by Topsiho on 2007-02-12
You should download it from webmin itself:

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

Topsiho

---

### Post by shdawson on 2007-02-12
Yeah, tried that.  The error message I am getting is "No such file or directory".

#sudo dpkg --install webmin_1.320_all.deb 

Present working directory is root ( / )


It seems I need to point the syntax to the cdrom, yes?  If so, what is that syntax?


Thanks......

---

### Post by shdawson on 2007-02-12
For clarity, when I am at the root directory and do an ls command, I see cdrom in a teal color.  So, if the cdrom drive is being seen, I guess I just need to mount that file system, yes?  Or, copy that file to a local folder and run from there ???


Thanks.....

---

### Post by Topsiho on 2007-02-17
Sorry for being late in replying: I don't remember having any problem installing Webmin on at least 3 or 4 computers. I don't remember though whether I used the .deb or the tarball file. If you don't succeed with one you could try the other, see if all dependencies are met though.

Topsiho

---

