---
title: "installing software"
date: 2017-06-20
forum: General Help
---

### Post by paul2495 on 2017-06-20
Guys so sorry about all this but i really cant get my head around installing software on this i have tried with Komodo and now i am trying to install pycharm and although i can download them they download to archive manager i really dont understand what to do or how to install them from there can some one please please help

---

### Post by howefield on 2017-06-20
Thread moved to the "*General Help*" forum.

The default in both the cases that you mention is to open in Archive Manager, which isn't really a problem because you simply then extract to where ever you want it extracted. Choose the "save as" option when downloading if you want the original tarball/package ect.

---

### Post by paul2495 on 2017-06-20
see i have extracted some files to my download folde but i cant navigate to it using terminal here is what i keep getting really frustrating 

```
paul@paul-110-530na:~$ cd bin/home/paul/download
bash: cd: bin/home/paul/download: No such file or directory
paul@paul-110-530na:~$ cd bin/home/paul/downloads
bash: cd: bin/home/paul/downloads: No such file or directory
paul@paul-110-530na:~$ bin/home
bash: bin/home: No such file or directory
paul@paul-110-530na:~$ home/paul
bash: home/paul: No such file or directory
paul@paul-110-530na:~$ cd ~/downloads
bash: cd: /home/paul/downloads: No such file or directory
paul@paul-110-530na:~$ /home
bash: /home: Is a directory
paul@paul-110-530na:~$ /home/paul
bash: /home/paul: Is a directory
paul@paul-110-530na:~$ /home/paul/downloads
bash: /home/paul/downloads: No such file or directory
paul@paul-110-530na:~$ home/paul/pycharm
bash: home/paul/pycharm: No such file or directory
paul@paul-110-530na:~$
```

why does it say downloads and download is not a directory

---

### Post by Dennis N on 2017-06-20
The folder should be Downloads with a capital D.

---

### Post by howefield on 2017-06-20
Probably because you do not have a "downloads" folder, but rather a "Downloads" folder - note the capitalisation.

---

### Post by 1clue on 2017-06-20
Where are you getting 'bin' from?

```
cd ~/Downloads
```

or

```

cd
cd Downloads

```

---

