---
title: "Mounting Google Drive as a Local Drive"
date: 2014-07-07
forum: General Help
---

### Post by matthewrdifrancesco on 2014-07-07
I am trying to mount Google Drive as a local drive, so I can stream off of it for my plex media server. I found a guide ([http://goo.gl/GwBaEd](http://goo.gl/GwBaEd))
This is what I did. I ran
```
$ sudo add-apt-repository ppa:alessandro-strada/ppa 
$ sudo apt-get update 
$ sudo apt-get install google-drive-ocamlfuse
```
all went well then I ran ```
$ google-drive-ocamlfuse
```[COLOR=#FFFFFF][FONT=monospace]
[/FONT][/COLOR]and signed in and authorized ocamlfuse

then I went to mount it and ran 
```
root@test:~# google-drive-ocamlfuse ~/googledrive
fuse: device not found, try 'modprobe fuse' first

```
after getting this error I ran modprobe fuse and got this
```
root@test:~# modprobe fuse
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module fuse not found.
```



Im so lost, any help is appreciated and sorry for being a helpless noob. I will provide any info you need to assist me
also, if you know of an alternitive way I can mount my google drive as a local drive let me know, what ever gets it to work!
thank you,
matthew

---

### Post by slooksterpsv on 2014-07-08
In the root's home directory, did you create the folder googledrive?

---

### Post by matthewrdifrancesco on 2014-07-08
yeah :l
[http://puu.sh/a1H0O/7bf3181423.jpg](http://puu.sh/a1H0O/7bf3181423.jpg)

---

### Post by slooksterpsv on 2014-07-08
Try installing libfuse2:
sudo apt-get install libfuse2

---

### Post by matthewrdifrancesco on 2014-07-08
Thank you for the responses (sorry I did not say so in my first response to you:)
```
root@test:~# sudo apt-get install libfuse2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libfuse2 is already the newest version.
libfuse2 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@test:~#
```

Huh... allready installed

---

### Post by slooksterpsv on 2014-07-08
```

  NEEDED               libsqlite3.so.0
  NEEDED               libz.so.1
  NEEDED               libcurl-gnutls.so.4
  NEEDED               librt.so.1
  NEEDED               libpthread.so.0
  NEEDED               libfuse.so.2
  NEEDED               libm.so.6
  NEEDED               libdl.so.2
  NEEDED               libc.so.6

```

Make sure you have the following installed, or run this:
```

sudo apt-get install libsqlite3-0 zlib1g libcurl3-gnutls libc6 

```

What else... hmm... I run a lot of dev stuff so it just works for me. Let me boot up a VM, try and install it and post back (fresh installed VM, no new software added).

EDIT:
Fuse-wise, I have the following installed as well
```

shawn@shawn-Satellite-C75D-A:~$ dpkg --get-selections | grep fuse
fuse						install
google-drive-ocamlfuse				install
gvfs-fuse					install
libfuse2:amd64					install

```

So make sure gvfs-fuse is installed as well.

---

### Post by matthewrdifrancesco on 2014-07-08
```
root@test:~# sudo apt-get install libsqlite3-0 zlib1g libcurl3-gnutls libc6Reading package lists... Done
Building dependency tree       
Reading state information... Done
zlib1g is already the newest version.
libc6 is already the newest version.
libcurl3-gnutls is already the newest version.
libsqlite3-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@test:~# apt-get install gvfs-fuse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gvfs-fuse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@test:~# 
```

Does it matter that its a VPS, and not a dedicated server?

---

### Post by slooksterpsv on 2014-07-08
If it's a 3rd party company hosting the VPS, they could have a block on accessing outside drives for services. Not sure on that one. Everything's setup correctly from what I'm seeing. Did you try this on a regular user?

---

### Post by matthewrdifrancesco on 2014-07-09
We MAY be getting somewhere........ I made my own user and ran these two commands (as per the guide I initianlly followed told me to do) and ran the google-drive-ocamlfuse ~/googledrive command, diffrent output this time! 
```


matt@test:~$ google-drive-ocamlfuse ~/googledrive
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: links2: not found
/usr/bin/xdg-open: 461: /usr/bin/xdg-open: links: not found

```

---

### Post by slooksterpsv on 2014-07-10
It's going to try to open the authorization page - if you don't have a gui you'll need a web browser like links or link2 to open it text wise. - [http://www.linuxquestions.org/questions/programming-9/xdg-open-no-method-available-for-opening-889242/](http://www.linuxquestions.org/questions/programming-9/xdg-open-no-method-available-for-opening-889242/)

---

### Post by matthewrdifrancesco on 2014-07-11
Weird [IMG]http://i.imgur.com/sWagrIl.png[/IMG]

---

### Post by slooksterpsv on 2014-07-11
Try installing google chrome, mozilla should be firefox not mozilla. I have chrome and that's what it opened on mine.

---

### Post by matthewrdifrancesco on 2014-07-11
[http://puu.sh/a7dsG/df89132fe8.jpg](http://puu.sh/a7dsG/df89132fe8.jpg) - was logged in as the other account, and logged in when the browser link to google drive opened... now I get the same error

---

### Post by slooksterpsv on 2014-07-11
Make sure you're pointing to the directory in the following syntax

If it's in your home directory:
~/googledrive

If it's in a different directory such as /home/*username*/Documents/googledrive type it in like this:
~/Documents/googledrive

---

