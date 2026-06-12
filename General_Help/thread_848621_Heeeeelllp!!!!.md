---
title: "Heeeeelllp!!!!"
date: 2008-07-03
forum: General Help
---

### Post by amamdispencer on 2008-07-03
Hi everyone, 

still unable to mount my rewrittable cd's keep getting can't mount udf volumes and how do i make use of bluetooth, can't discover the pc from my phone, how do i download and install tar.*,rpm,files, alien ain't solving my problems keep getting wrong architecture when converted to deb and using package manager to open, are there anti-virus programmes for ubuntu? Been trying to pimp my ubuntu with some nice splash screens in tar.* formats and can't. Is ubuntu not supposed to be more

---

### Post by unseend on 2008-07-03
1) udf is just like .iso or what? if yes the command you need to mount them is this:
```
mount -o loop your_file.iso /mnt/dir
``` This command Mounts the cdrom image at /mnt/dir (read only mode). Do not change /mnt/dir. It's the default mounting directory. You can find useful linux commands here: **[http://ubuntuforums.org/showthread.php?t=846097](http://ubuntuforums.org/showthread.php?t=846097)**
 
2) to use bluetooth simply go System>Preferences>Bluetooth Settings and tick under the General tab the Automatically Authorize Incoming requests.

3) to install .tar.* programms you need to open a console terminal and write
```
cd
./configure [or sometimes sudo ./configure]
make
make install
``` but BEFORE doing that ALWAYS read the README file because some programms may have different instructions.

4) There anti-virus programms in Ubuntu but they are not used. You don't need them. :-)

5) .deb files are the most easy to install because they are similar to .exe in Windows.

6) for .rpm files I think it's also easy. You just open a console terminal and type:
```
/home/your_username/Where/Your/RPM/File/Is
/home/your_username/Where/Your/RPM/File/Is/./the_filename_you_want_to_run
```

I hope I help you. :D

---

### Post by nick_h on 2008-07-03
[How to install ANYTHING in Ubuntu!](http://monkeyblog.org/ubuntu/installing/)

---

### Post by amamdispencer on 2008-07-04
Thanks you guys for the reply,

my re-writtable cd is empty, just want to open it as i used to with vista on my toshiba a100, and copy some files unto it.

as for the bluetooth still can't discover the pc from my phone a nokia 6300. Does the phone make matter?

Do i have to be learning commands to do such simple tasks?

---

### Post by hyper_ch on 2008-07-04
it is adviced to use a descriptive topic title, that means a topic title that gives some 

clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have 

notices, just about everyone posting in here has some kind of a problem or issue or question 

;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark 

each one individually as solved.

---

### Post by nick_h on 2008-07-04
> as for the bluetooth still can't discover the pc from my phone a nokia 6300. Does the phone make matter?
Try and search for "nokia 6300" on this forum.  Have you seen [this](http://ubuntuforums.org/showthread.php?t=470140) thread?

---

