---
title: "Tar Gz Files Problem"
date: 2006-11-23
forum: General Help
---

### Post by linuxquest on 2006-11-23
After viewing some tutorials in ...
[http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif](http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif) 
and 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

on how to compile tar gz files, I still can't compile a tar gz file. Below, are the command that I typed in my gnome-terminal.

alex@alex-desktop:~$ cd /home/alex/Desktop/tplitelx_complete.tar.gz_FILES
[email]alex@alex-desktop:~/Desktop/tplitelx_complete.tar.gz[/email]_FILES$ ./configure
bash: ./configure: No such file or directory
[email]alex@alex-desktop:~/Desktop/tplitelx_complete.tar.gz[/email]_FILES$ make
bash: make: command not found
[email]alex@alex-desktop:~/Desktop/tplitelx_complete.tar.gz[/email]_FILES$ sudo checkinstall
sudo: checkinstall: command not found
[email]alex@alex-desktop:~/Desktop/tplitelx_complete.tar.gz[/email]_FILES$


Pls help me. Thx.

---

### Post by taurus on 2006-11-23
What's the output of this command from a terminal then?

```
ls -la ~/Desktop/tplitelx_complete.tar.gz_FILES
```

---

### Post by linuxquest on 2006-11-23
After viewing some tutorials in ...
[http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif](http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif) 
and 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

on how to compile tar gz files, I still can't compile a tar gz file. Below, are the command that I typed in my gnome-terminal.

alex@alex-desktop:~$ cd /home/alex/Desktop/tplitelx_complete.tar.gz_FILES
[email]alex@alex-desktop:~/Desktop/tplitelx_complete.tar.gz[/email]_FILES$ ./configure
bash: ./configure: No such file or directory
[email]alex@alex-desktop:~/Desktop/tplitelx_complete.tar.gz[/email]_FILES$ make
bash: make: command not found
[email]alex@alex-desktop:~/Desktop/tplitelx_complete.tar.gz[/email]_FILES$ sudo checkinstall
sudo: checkinstall: command not found
[email]alex@alex-desktop:~/Desktop/tplitelx_complete.tar.gz[/email]_FILES$


Pls help me. Thx.

---

### Post by Ensnared on 2006-11-23
Try to install the checkinstall-tool ;)
```
sudo apt-get install checkinstall
```

---

### Post by taurus on 2006-11-23
Please do not double post.  Merged your threads...

---

### Post by podunk on 2006-11-23
No compiling required?

I downloaded the file from here:
[http://www.treepad.com/download/#tplitelx](http://www.treepad.com/download/#tplitelx)
and stored it in my Desktop folder (so I could see it while working)
I right clicked and chose "extract here"

It created an icon on my desktop to launch the app.

---

