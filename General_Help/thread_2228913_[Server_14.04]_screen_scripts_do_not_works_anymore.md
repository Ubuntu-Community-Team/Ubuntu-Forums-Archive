---
title: "[Server 14.04] screen scripts do not works anymore"
date: 2014-06-10
forum: General Help
---

### Post by nim2 on 2014-06-10
Hi,

I wrote this question a week ago into two other forums, but it looks like noone has a clue what my problem could be :(
I recently upgraded from Ubruntu 13.10 Server to 14.04 Server (clean install) and copied all my stuff to the new installation. Everything works fine, execpt for one thing:

my scripts which start some applications in a detached screen session do not work anymore. They still work on my two debian servers (raspion & cubian), and on a VM using CentOS. I can't even get it to work from the commandline.
The script does the following:

```
screen -dmS TAG MYPROGRAMM -MYPARAMETERS
```

where:

TAG = identifier of the screen session
MYPROGRAM = obviously the application I want to start
-MYPARAMETERS = some parameters...

Nothing happens at all when I enter that. No error message nothing, there is just no screen session afterwards. If I split the call like:

```
screen -dmS TAG
```

then enter the screen session with ***screen -r*** and enter the rest, it works. But I need my scripts to work since they are called from Cronjobs. Is here anyone who has enough knowlegde with screen under Ubuntu 14.04?
Help would really be appreciated!

---

### Post by Habitual on 2014-06-10
```
screen -dmS TAG
``` here creates this session
 23996.TAG    (Detached)

What is the value of MYPROGRAMM supposed to be?

---

### Post by papibe on 2014-06-10
Hi nim2.

I'm using scripts on detached  screen in both 12.04 and 14.04 (even on 10.04).

My first guess is that is a path problem. Try testing launching the screen using the absolute path to your script:
```
screen -dmS name /path/to/MYPROGRAMM -MYPARAMETERS
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by nim2 on 2014-06-10
Hi,

first, thanks for your answers. I already tried using absolute path (which is not needed anyway, since the applications are in /usr/bin), but it does not work either. It has nothing to do with the script itself, since even from the command line it does not work.
I'm using the exact same scripts on three other servers, and everywhere they work without any issues. I also had them working on the previous installation (13.10) without problems.

I can't find any information why the session is not created. no error, no log entry, nothing. I'm really stuck here since there is no indication of a failure.

---

### Post by nim2 on 2014-06-10
OMG! I just figured it out! The problem was, that the application depends on some libs. And somehow, when starting a screen session, it can't find the path. After using:

```
sudo ldconfig /usr/local/myprog/lib64
```

the script now works. I have no idea why it worked without that when starting the screen session manually before. I have set export LD_LIBRARY_PATH in my .bashrc file, but it seems that this information is not transported to the screen session.
Is there a way to fix that?

---

### Post by papibe on 2014-06-10
Glad you figured it out.

You can run your program inside bash, thus forcing the execution of .bashrc. For instance:
```
screen -dmS TAG /path/to/script.sh
```
Where script.sh would be:
```
#/bin/bash
/path/to/MYPROGRAMM -MYPARAMETERS
```
Alternatively you could just do:
```
screen -dmS TAG bash -c '/path/to/MYPROGRAMM -MYPARAMETERS'
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by nim2 on 2014-06-12
Hi,

unfortunately that did not work. I've now added the path to the libraries to /etc/ld.so.conf but I still need to run ldconfig as root after a system reboot. I'm not sure what the best approach would be:

1. add an entry to root crontab with @reboot ldconfig
2. place a script in /etc/init.d/

---

