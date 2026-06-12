---
title: "Server help."
date: 2006-10-28
forum: General Help
---

### Post by deadpirate on 2006-10-28
I just installed ubuntu for the second time.. I love it! however.. I am in dire need of some direction. I Do alot of PHP and HTML Coding, and i need to setup a web server. Is this possible to do, easily, on ubuntu? I need mysql databases, php, and hopefully emails. Anywho.. Some pointers would be nice.. In the mean time im going to read up on the documentation. Also.. Pointers for some helpfull web-coding programs would be nice too! thank you everyone..

OH.. i dont know what version im running.. but my install disc is version 6.06.. and i just finished downloading and installing around 190 updates.

-Ryan

EDIT
Why does internet pages load so, and when i scroll its really choppy, slow like im using onboard video? i have a pci-express 128mb video card..

---

### Post by marianom on 2006-10-28
Regarding your question about building a lamp enviroment, I just check the repos and I found everything you need there: apache  (1.3 and 2), php 5 and mysql. Regarding email some said postfix (which you can also find in the repos) is a good MTA. I really cannot discuss this, lacking experience in it.

It seems with Synaptic you should encounter no issue at all in order to install everything.
I suggest you check the repos, verify the possible extensions and addons that you can find there and with that, check what you need and install.

Please, let me know any issues you find or doubts and I'll try to help.

---

### Post by deadpirate on 2006-10-28
Whats a Repo? Im noob at this.
Anywho.. Ive installed apache and FTP.. I just have trouble editing my files.. says i dont have suffecient Permissions. ( When i access files through GUI, not the terminal) Is there a way to make all the files on my machine fully accessable to just myself? Thank you very much for helping, Its greatly appreciated.

---

### Post by Blutack on 2006-10-28
Bad idea I'm afraid.  That would negate one of the biggest security features of linux.  In kubuntu I can right click and in actions there is an option for edit as root.  Is there a similiar thing in ubuntu?  If not then you can start a root file manager session by opening a terminal and typing gksu nautilus.  After asking for a password you should be able to edit all the files.  Just remember...with great power comes great responsibility.  A repo is a server full of debian packages.  These are prebuilt programs ready to install to ubuntu.  If you installed apache and FTP with synaptic then you have already used repos.  If you are interested somewhere in the preferences in synaptic there will be an option to edit repositories.  Good luck, and apologies if any of this is wrong cos I'm a kde person at heart...

---

### Post by marianom on 2006-10-28
I would not advice you to do so, seems dangerous (since processes running in the machine needs permissions to access certain files, you might get in trouble and, the biggest reason, if some files are not yours to modify you can avoid the risk of erasing them by accident).

Several options: 

1- start this GUI application using "sudo". Sudo allows you to invoke administrator rights (the root user) to use a file. For example, I have this application that needs to run with root permissions, so I do

```
mariano@mishima:~$ sudo pptpconfig
```

it let me use it. It prompts you for the root password (try with your own password). After you're authenticated your GUI will run without issues.

2- You can modify the permissions to use a file -without affecting the owner- using "chmod", see [http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)
This way you can set o=rwx to use the file (read the article for a pretty quick and good explanation).

3- If you really want to modify the owner of a file, see chown:
[http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)

---

### Post by marianom on 2006-10-28
I totally forgot your other question. For an brief introduction about what a repository is, see:
[https://help.ubuntu.com/community/CommonQuestions#head-b2f616ebcc51d91427733a29372697acac0f316a](https://help.ubuntu.com/community/CommonQuestions#head-b2f616ebcc51d91427733a29372697acac0f316a)

---

### Post by Blutack on 2006-10-28
When he says dangerous he means changing the ownerships of all the files on the machine, not starting file manager as root :-)
I assume we both posted at the same time...

---

### Post by marianom on 2006-10-28
Blutack: Yeap, thanks a lot for clarify it (boy, my english is horrible today). I failed to notice your post while writing.

---

### Post by deadpirate on 2006-10-28
Thank you very much for the help guys!
Im going through and installing the packages i need.. Im just wondering how i can create new FTP users and access Mysql, setup DNS.. etc.

---

### Post by Blutack on 2006-10-28
[http://www.devshed.com/c/a/MySQL/Beginning-MySQL-Tutorial/](http://www.devshed.com/c/a/MySQL/Beginning-MySQL-Tutorial/)
may be some help.  There are probably howtoes for your other questions as well, its just a case of finding the good ones.  Sorry I can't really help more.  I guess Marianom would be more help on this from his signature though...my little laptop doesn't play webserver very well i don't think :-)

---

### Post by marianom on 2006-10-28
Regarding FTP and DNS there are some good 'n quick guides in the server docs (I'm trying hard to post the link but it always directs me to the castilian version and I cannot find the english one).

This is the best I found:
[https://help.ubuntu.com/ubuntu/serverguide/en_GB/ftp-server.html](https://help.ubuntu.com/ubuntu/serverguide/en_GB/ftp-server.html)
[https://help.ubuntu.com/ubuntu/serverguide/en_GB/dns.html](https://help.ubuntu.com/ubuntu/serverguide/en_GB/dns.html)

Regarding MySql follow Blutack advice and read this too:
[https://help.ubuntu.com/ubuntu/serverguide/en_GB/databases.html](https://help.ubuntu.com/ubuntu/serverguide/en_GB/databases.html)

Any further problems let us know.

---

### Post by Balut on 2006-10-28
Here is a link to a very good resource when it comes to configuration questions: [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

---

### Post by deadpirate on 2006-10-29
thanx for the resources guys! im going to continue my work in the AM after some sleep.

---

