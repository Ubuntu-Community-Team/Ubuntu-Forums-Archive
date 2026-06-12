---
title: "gmailfs howto"
date: 2005-04-06
forum: General Help
---

### Post by lateo on 2005-04-06
hi,
wanted to use gmailfs but i just can't. Mr Google didn't find anything interesting. help plz!

in /etc/fstab
-----------------------
/usr/share/gmailfs/gmailfs.py   /mnt/gmail  gmailfs  noauto

in /etc/gmailfs/gmailfs.conf
-----------------------------------------------
username & passwd 
fsname = S1lLyNaM€

then when i
#mount /mnt/gmail

all i get is
"fusermount: old style mounting not supported"

---

### Post by Jad on 2005-04-08
Try [http://www.gmailforums.com/](http://www.gmailforums.com/)
I'm not sure if there is a howto for gmailfs for ubuntu

---

### Post by Lord C on 2005-04-11
[QUOTE=lateo]
all i get is
"fusermount: old style mounting not supported"[/QUOTE]

I have this same issue, I have [submitted a bug report](https://bugzilla.ubuntu.com/show_bug.cgi?id=8943).

---

### Post by Lord C on 2005-04-11
Well - they told me they wouldnt solve the bug. Nice one.

So i've submitted it to [here](https://launchpad.ubuntu.com/malone/bugs/352).

---

### Post by lao_V on 2005-04-11
[QUOTE=Lord C]Well - they told me they wouldnt solve the bug. Nice one.[/QUOTE]

Obviously its not Ubuntu's fault there is a bug in gmailfs (fuse-utils to be precise?) since the package is in universe and as such unsupported!

---

### Post by lateo on 2005-04-13
thx a lot for your bug reports lord_c 
let's hope it will be corrected soon!  [-o<

---

### Post by id_sonic on 2005-04-14
[QUOTE=lateo]thx a lot for your bug reports lord_c 
let's hope it will be corrected soon!  [-o<[/QUOTE]
 I get the some report..

---

### Post by danielti on 2005-05-02
I am having the same problem.
IT is a shame that gmailfs does not work!

---

### Post by lateo on 2005-05-04
[QUOTE=danielti]I am having the same problem.
IT is a shame that gmailfs does not work![/QUOTE]

why a shame?
- it is not supported by ubuntu
- if something has changed in FUSE, gmailfs dev(s) may not know about it in time.
- GPL 11. "BECAUSE THE PROGRAM IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY FOR THE PROGRAM [...] THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE PROGRAM IS WITH YOU."
- other?

---

### Post by lao_V on 2005-05-05
[QUOTE=lateo]why a shame?
- it is not supported by ubuntu
- if something has changed in FUSE, gmailfs dev(s) may not know about it in time.
- GPL 11. "BECAUSE THE PROGRAM IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY FOR THE PROGRAM [...] THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE PROGRAM IS WITH YOU."
- other?[/QUOTE]
 I don't think anyone was blaming Ubuntu or the app's devs, rather just disappointed that it doesn't work. We all appreciate the free software and the effort put in by the devs!

---

### Post by freelsjd on 2005-08-06
OK.  I got this to work in Ubuntu...sort of.

1) follow the basic instructions over here

[http://www.debian-administration.org/articles/198]("http://www.debian-administration.org/articles/198")

(which is an excellent site BTW)

2) however, because we are ubuntu and not debian, there are some differences. add the following entry to your /etc/apt/sources.list

deb-src [http://http.us.debian.org/debian]("http://http.us.debian.org/debian") stable main contrib non-free

and apt-get update (comment out when done with this to be safe)

3) get the newer version of gmailfs from debian (0.4 versus 0.3 in ubuntu)
by installing from  source

apt-get -b source gmailfs python-libgmail python-fuse

4) there will also be several dependent packages you may have to add

5) relinked python to python2.3

6) that is about it I think. I was able to mount, cp, umount. However, I could not ls without error messages so I will have to remember what I copy over to use this. It works, but I probably won't use it until it is officially in ubuntu

---

### Post by lateo on 2005-08-09
thx !
at last i've an answer :)

---

### Post by confused_user on 2005-09-30
when i add the debian sources into my /etc/apt/sources.list i get the following message

<Malformed line 27 in source list /etc/apt/sources.list (dist)>

hmm, 

it looks like this

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

 deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian)
 deb-src [http://http.us.debian.org/debian](http://http.us.debian.org/debian)


*Any help would be appreciated, cheers*

---

### Post by Wombley on 2005-10-02
Change the last two lines to this:

deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
deb-src [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free

---

### Post by lateo on 2005-11-13
FUSE will be in 2.6.14 kernel.
should work soon \\:D/

---

### Post by hatefulthreatening on 2005-11-14
[QUOTE=lateo]why a shame?
- it is not supported by ubuntu
- if something has changed in FUSE, gmailfs dev(s) may not know about it in time.
- GPL 11. "BECAUSE THE PROGRAM IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY FOR THE PROGRAM [...] THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE PROGRAM IS WITH YOU."
- other?[/QUOTE]

It is a shame is a stupid English expression that doesn't quite mean what it sounds like in common usage. It was not meant to imply that it's shameful of Ubuntu to not support it.

---

### Post by khermans on 2005-11-21
It will work after a slight modification.  Tested on Ubuntu Breezy updated to most recent as of today.  Try this link for info on the fix.  Apparantly it is a libgmail issue and Ubuntu repos depend on the old version, which is broken...

[http://ubuntuforums.org/showthread.php?t=87777](http://ubuntuforums.org/showthread.php?t=87777)
--
Kristian Hermansen

---

### Post by fakie_flip on 2006-07-28
Someone should email the maintainer of gmailfs, and let him know it is not working in Ubuntu. Do this to get his email "apt-cache show gmailfs" I would do it, but I'm not at home with my Ubuntu computer.

---

### Post by thegooglemaven on 2006-07-28
;) Even Im not sure...

[http://www.googlemaven.com](http://www.googlemaven.com)

---

### Post by fakie_flip on 2006-08-11
I've got the email of the maintainer, so if someone would like to email him, and to let him know, so he can fix the software in the repositories that is not working. here is his email. Also let him know that, we probably need a newer version of gmailfs in the repositories. I will be emailing him soon, but it would be better if several people did, and he will be more likely to fix this problem.

```
ubuntu@ubuntu:~/Desktop/a$ apt-cache show gmailfs
Package: gmailfs
Priority: extra
Section: universe/utils
Installed-Size: 136
Maintainer: Sebastien Delafond <sdelafond@gmx.net>
Architecture: all
Version: 0.6-2ubuntu1
Depends: fuse-utils (>= 2.0+2.1pre0), python2.4, python-libgmail (>= 0.0.8+cvs20041108), python-fuse (>= 2.0+2.1pre0)
Recommends: encfs
Filename: pool/universe/g/gmailfs/gmailfs_0.6-2ubuntu1_all.deb
Size: 23756
MD5sum: 9105f4b5c43bf074045ed2c81ae7e6b6
Description: Use your GMail account as a filesystem
 GmailFS provides a mountable Linux filesystem which uses your Gmail
 account as its storage medium. GmailFS is a Python application and
 uses the FUSE userland filesystem infrastructure to help provide the
 filesystem, and libgmail to communicate with Gmail.
 .
 To use GmailFS, please use fuse-source to compile appropriate modules
 for your running kernel.
 .
 GmailFS supports most file operations such as read, write, open,
 close, stat, symlink, link, unlink, truncate and rename. This means
 that you can use all your favourite unix command line tools to operate
 on files stored on Gmail (e.g. cp, ls, mv, rm, ln, grep etc. etc.).
 .
 [http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

ubuntu@ubuntu:~/Desktop/a$
```

---

### Post by jackn on 2006-08-24
> **freelsjd said:**
> 

5) relinked python to python2.3

6)...I was able to mount, cp, umount. However, 

 Thanks a lot, Freelsjd.

I don't understand the following instruction:
'relinked python to python2.3'

In addition, (once I get this to work...), how do you go about mounting the 
gmailfs? Is it a conventional 'mount' command? If so, what is the 'device'? 
And does it need to be listed in /etc/fstab?

Thanks for any help.

Jackn

---

### Post by jackn on 2006-08-24
When I try to download the new gmailfs from deb repositories, as advised, I get:
```
E: Could not open file /var/lib/apt/lists/http.us.debian.org_debian_dists_stable_main_source_Sources - open (2 No such file or directory)
```

I have added two lines, one with 'deb' and one with 'deb-src' to the /etc/apt/sources.list file. And I've logged out and back in.

```
## debian source, used to update gmailfs to more recent
deb http://http.us.debian.org/debian stable main contrib non-free
deb-src http://http.us.debian.org/debian stable main contrib non-free
```


Why isn't the source recognized?

Thanks, 
Jackn

---

### Post by fakie_flip on 2006-08-25
Has anyone got gmailfs to work lately? I think google is making it hard to get it working. Mine failed.

---

### Post by Ptero-4 on 2006-10-13
Hi. I have some questions about gmailfs. Can I set a custom icon for the gmail drive? Will it stay put?

---

### Post by Adanufgail on 2006-12-04
Wha?
```
sudo mount -t gmailfs /usr/share/gmailfs/gmailfs.py /media/gdrive -o username=*****,password=*****,fsname=Fl00dz
mount: unknown filesystem type 'gmailfs'
```
I think it looks easy, but I have no idea. Any help?

---

### Post by shanmuha on 2007-06-15
is gmailfs working in feisty?
I am getting the following error, when tryiing to use it with proxy:
[HTML]<pre>
Traceback (most recent call last):
  File "/usr/bin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/usr/bin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1135, in main
    server = Gmailfs(mountpoint, **namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 607, in __init__
    self.ga.login()
  File "/usr/lib/python2.5/site-packages/libgmail.py", line 302, in login
    pageData = self._retrievePage(req)
  File "/usr/lib/python2.5/site-packages/libgmail.py", line 331, in _retrievePage
    resp = urllib2.urlopen(req)
  File "/usr/lib/python2.5/urllib2.py", line 121, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 380, in open
    response = meth(req, response)
  File "/usr/lib/python2.5/urllib2.py", line 487, in http_response
    code, msg, hdrs = response.code, response.msg, response.info()
AttributeError: addinfourl instance has no attribute 'code'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/usr/bin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1135, in main
    server = Gmailfs(mountpoint, **namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 607, in __init__
    self.ga.login()
  File "/usr/lib/python2.5/site-packages/libgmail.py", line 302, in login
    pageData = self._retrievePage(req)
  File "/usr/lib/python2.5/site-packages/libgmail.py", line 331, in _retrievePage
    resp = urllib2.urlopen(req)
  File "/usr/lib/python2.5/urllib2.py", line 121, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 380, in open
    response = meth(req, response)
  File "/usr/lib/python2.5/urllib2.py", line 487, in http_response
    code, msg, hdrs = response.code, response.msg, response.info()
AttributeError: addinfourl instance has no attribute 'code</pre>[/HTML]

---

### Post by rodrigo666 on 2007-06-18
I'm trying to get it work on Feisty, but can't find any working tutorial on Google. Seems there's a bug or something.

---

### Post by floibler on 2007-08-21
I think the following works;

create a /media/gmailfs mountpoint

then

sudo mount.gmailfs none /mnt -o username=gmailusername,password=gmailpassword,fsname=WhAtEvEr

this should give you a working gmailfs - the problem is that only root can do anything.

hope this helps - anything further would be useful.

Floi

---

### Post by garak on 2007-10-09
I was an happy user of gmailfs until few months ago. One day it stopped to work, giving a **HTTP Error 400: Bad Request** error. My first think was something about a change in gmail protocols, so I waited Gutsy packages. Now I upgraded to Gutsy beta, but the problem is still there :(

---

### Post by SiCkTiMe on 2007-10-24
I have the same problem garak. I've been searching all day for a solution, but did't find anything... If you solve the problem, post here the solution :guitar:

---

### Post by arjanhs on 2007-11-30
Got the same problem to, please post the answers when found.

---

### Post by jaromrnelson on 2007-12-11
I posted a solution in this thread:
[http://ubuntuforums.org/showthread.php?t=596352](http://ubuntuforums.org/showthread.php?t=596352)

It might be simpler than I thought, but I tried a few things to get past the obstacles I was having.  (I think I captured those steps in the other thread).
I think in the end the only thing necessary to get it working from an up-to-date Gutsy installation is the following:

```

# Get the package
sudo apt-get install gmailfs

# tip from this thread: http://ubuntuforums.org/showthread.php?t=596352
# update libgmail to latest version via python-setuptools
# I think this was causing HTTP Error 400 with for me when I tried to connect
sudo apt-get install python-setuptools
sudo easy_install --upgrade libgmail

# make the mount point (-p = and parent directories, if needed)
sudo mkdir -p /media/gmail/username

# do the mount
sudo mount -t gmailfs none /media/gmail/username/ -o username=username@gmail.com,password=secretstuff,fsname=RandomKey

```

At this point, I was able to get it working, as long as I was in a super user (root) session.
Ie.
```

# after the above this fails
cd /media/gmail/username

# open a root session
sudo -s
# this succeeds
cd /media/gmail/username
echo TEST > test.txt
cat test.txt

```

I haven't been able to figure out how to make it accessible to a specific group or user.   I've tried changing the permissions and group of the mount point, but as soon as I mount it, it seems to no longer have the same permissions. 

Anybody know how to make the mount point accessible to normal users?

---

### Post by jaromrnelson on 2007-12-11
> **jaromrnelson said:**
> 
```

# after the above this fails
cd /media/gmail/username

# open a root session
sudo -s
# this succeeds
cd /media/gmail/username
echo TEST > test.txt
cat test.txt

```


Also, "[FONT="Courier New"]ls -l[/FONT]" gives weird output:

[FONT="Courier New"]
jarom@zeta-ubuntu:/media/gmail$ ls
username/
jarom@zeta-ubuntu:/media/gmail$ ls -l
total 0
?--------- ? ? ? ?                ? username
jarom@zeta-ubuntu:/media/gmail$ sudo ls -l
total 0
?--------- ? ? ? ?                ? username
[/FONT]

Anybody know how to make the mount point accessible to normal users?

---

### Post by db0 on 2008-01-05
I managed to have some progress on mounting it as a user but I haven't succeded yet.

I added the following line in fstab
```
none 	/media/gmail gmailfs	user,rw,noauto,username=username@gmail.com,password=password,fsname=stuff 0 0
```

And granted access to the necessary places
```
sudo chmod 777 /etc/fuse.conf
sudo chmod 777 /media/gmail
sudo chmod 777 /bin/fusermount
sudo chmod 777 /dev/fuse

```

But unfortunately, it fails to mount from the user
```

$mount /media/gmail

Ignored option :rw
Ignored option :noexec
Ignored option :nosuid
Ignored option :nodev
Ignored option :noauto
Ignored option :user
fusermount: mount failed: Operation not permitted
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1180, in main
    server.main()
  File "/usr/lib/python2.5/site-packages/fuse.py", line 713, in main
    main(**d)
fuse.FuseError: filesystem initialization failed
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1180, in main
    server.main()
  File "/usr/lib/python2.5/site-packages/fuse.py", line 713, in main
    main(**d)
fuse.FuseError: filesystem initialization failed

```

But it works if I run the command with sudo.
Apparenty fusermount does not recognise all commands from mount (i.e. user, rw etc) and I do not know if that can be fixed. 

Ideas?

---

### Post by klaith on 2008-03-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/114212](https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/114212)  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Problem is that normal user does not have permission to open /dev/fuse.
First you need to add dev/fuse to the fuse group:

```
sudo chgrp fuse /dev/fuse
```

Then you need to add yourself to the fuse group:

```
sudo usermod -a -G fuse username
```

Now logout and log back in to become a member of the fuse group viola!

---

### Post by thebender on 2008-06-28
Hi!

Sorry for warming this up... but I have some issues here. 
I set everything up like described in [https://wiki.ubuntu.com/GmailFS](https://wiki.ubuntu.com/GmailFS)
When i reboot now, i get no drive or anything. THis is in the logfile: 


```
06/29/08 11:58:33 ERROR      OpenSSLProxy is missing. Can't use HTTPS proxy!
06/29/08 11:58:33 INFO       Starting gmailfs in child process (PID 4508)
06/29/08 11:58:33 INFO       Mountpoint: /mnt/ggmail
06/29/08 11:58:33 INFO       Named mount options: {'username': 'myemail@gmail.com', 'password': '********', 'fsname': 'h$
06/29/08 11:58:33 INFO       waiting for /mnt/ggmail to become a mountpoint
06/29/08 11:58:34 ERROR      gmailfs child died, exiting...

```

plus i am getting some weird emails to my gmail accout. seems like something is wrong with the script :/


If it try 
```

mount -a
```

then i get back

```
Ignored option :rw
```

and in the log: 
```

06/29/08 12:10:04 ERROR      OpenSSLProxy is missing. Can't use HTTPS proxy!
06/29/08 12:10:04 INFO       Starting gmailfs in child process (PID 8609)
06/29/08 12:10:04 INFO       Mountpoint: /mnt/ggmail
06/29/08 12:10:04 INFO       Named mount options: {'username': 'myemail@gmail.com', 'password': '********', 'fsname': 'randomstuff'}
06/29/08 12:10:04 INFO       waiting for /mnt/ggmail to become a mountpoint
06/29/08 12:10:06 INFO       Connected to gmail
06/29/08 12:10:09 INFO       /mnt/ggmail is now a mountpoint
```


now i can access /mnt/ggmail but just as root. i dont even see it with my normal user. 

i can copy files to the folder but then i get weird emails with temp-attatchments....




help please?

---

