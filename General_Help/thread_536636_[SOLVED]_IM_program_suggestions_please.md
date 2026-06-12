---
title: "[SOLVED] IM program suggestions please"
date: 2007-08-28
forum: General Help
---

### Post by Bethrine on 2007-08-28
I Hello everyone. I am looking for a good IM program. Please suggest one!

---

### Post by strabes on 2007-08-28
Gaim (pidgin) for GTK/gnome, kopete for KDE.

---

### Post by evissecx on 2007-08-28
[aMSN]("http://www.amsn-project.net/") isn't bad at all. Got some nice skins to make it cool. Got support for webcam, but not voice I believe.

---

### Post by likemindead on 2007-08-28
Gotta be [Pidgin]("http://www.getdeb.net/release.php?id=1307") (uh... I'm not sure why the screenshot there is screwed up, but click on it for the full image). Also, [here's the homepage]("http://www.pidgin.im/") where you can compile it from source yourself, if you so desire. :)

---

### Post by zoobave on 2007-08-28
pidgin is wonderful

---

### Post by Crafty Kisses on 2007-08-28
> **Bethrine said:**
> I Hello everyone. I am looking for a good IM program. Please suggest one!

Pidgin.

---

### Post by TeaSwigger on 2007-08-28
Kopete is great.

Pidgin is no slouch either. 

They beat any Windows only IMs I'd tried.

---

### Post by Bethrine on 2007-08-28
can I use ...

apt-get install pidgin      ?

Does it just work or do I have to subscribe to some sort of service?

Thanks all!!

---

### Post by Rocket2DMn on 2007-08-28
You should be able to, I think pidgin is in the repositories now.
You need to registered with whatever IM service you prefer, like AIM, yahoo messenger, etc...
It is free, so you just set it up with them and then sign on from pidgin.

---

### Post by Bethrine on 2007-08-28
I've never used IM before, any suggestions for that? The service that is..

---

### Post by Rocket2DMn on 2007-08-28
> **Bethrine said:**
> I've never used IM before, any suggestions for that?

You will probably want to go with what your friends use, you should ask them.  AIM, ICQ, MSN, and Yahoo Messenger are probably the most common.  It's just a matter of preference.

---

### Post by Bethrine on 2007-08-28
Ok, what did I do wrong?

c:~$ sudo apt-get install pidgin
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package pidgin
:~$

---

### Post by Rocket2DMn on 2007-08-28
I guess it's not in the repos yet - you can download a .deb package from [http://www.getdeb.net/release.php?id=1307](http://www.getdeb.net/release.php?id=1307)
Make sure you get both the pidgin and pidgin-data
You can then just double click to install (do the data one first).

---

### Post by notwen on 2007-08-28
+1 Pidgin --- Should cover the majority of your chatting protocols.  Reminiscent of Adium for OSX if you've used it by chance. =]

---

### Post by Bethrine on 2007-08-28
Can you walk me through it? I haven't done that yet.  Open or save to disk?

---

### Post by Bethrine on 2007-08-28
I opened it and the pkgs were already there (pkgs first). Then I opened the "main" and got this...

Error: Dependancy is not satisfiable: libatk1.0-0

---

### Post by Bethrine on 2007-08-28
ok, Just figured out I already had Gaim installed, doh. Doesn't it conflict with pidgin? Should I uninstall one entirely?

---

### Post by Vadi on 2007-08-28
You want to "upgrade" your Gaim to Pidgin.

Follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=474071&highlight=gaim+to+pidgin](http://ubuntuforums.org/showthread.php?t=474071&highlight=gaim+to+pidgin)
 and feel free to ask for help if something doesn't work.

---

### Post by Bethrine on 2007-08-28
Thanks!..ok, I can't complete step 4...

pidgin-2.1.1/share/sounds/send.wav
pidgin-2.1.1/pidgin.spec
:~/Desktop$ cd Pidgin
bash: cd: Pidgin: No such file or directory
:~/Desktop$ ls
evolution-mail.desktop  gaim.desktop  pidgin-2.1.1
firefox.desktop         pidgin        pidgin-2.1.1.tar.bz2
:~/Desktop$ ./configure
bash: ./configure: No such file or directory
:~/Desktop$ cd pidgin-2.1.1.tar.bz2
bash: cd: pidgin-2.1.1.tar.bz2: Not a directory
:~/Desktop$ cd Pidgin
bash: cd: Pidgin: No such file or directory
:~/Desktop$

nevermind..I got it, it was...

cd pidgin-2.1.1

---

### Post by Bethrine on 2007-08-28
:) yay! all installed. Thank you all!

---

### Post by strabes on 2007-08-28
By the way, pidgin is the default IM client in ubuntu gutsy.

---

