---
title: "Hoary: vncserver on screen 0 - is it possible?"
date: 2005-06-24
forum: General Help
---

### Post by Teo on 2005-06-24
Hi,
How to run vncserver on screen 0? Is it possible to setup vncserver to run at system startup for screen 0?  :confused: 

I saw vino (System -> Preferences -> Remote Desktop) and hate it (slooowly).
I saw x11vnc - it didn't match my needs.
I saw x2vnc - it didn't match my needs.

Why I want vncserver so badly? - java-vnc and vncserver is quite fast (mutch faster than vino).

ps. my vncserver is configured and run on screen >1 - but not 0 :cry:
ps2. my vncserver is vnc4server form repos.

---

### Post by intangible on 2005-06-24
Is this what you're looking for? : [http://ubuntuforums.org/showthread.php?t=42941](http://ubuntuforums.org/showthread.php?t=42941)

---

### Post by Teo on 2005-06-24
[QUOTE=intangible]Is this what you're looking for? : [http://ubuntuforums.org/showthread.php?t=42941](http://ubuntuforums.org/showthread.php?t=42941)[/QUOTE]
Saw it too and didn't like it - I really have to connect to a currently logged in user's screen.
Connceting to gdm and start a new session don't interest me.
I want to control currently logged user's apps - that's why I need screen 0 on vncviewer so badly.

---

### Post by intangible on 2005-06-24
x11vnc seems to do what you want and it has many configuration options to make it quicker (like vncserver).  Why did you decide against it?

You could also install freenx and use that in combination with x11vnc and really speed things up.

---

### Post by Teo on 2005-06-24
[QUOTE=intangible]x11vnc seems to do what you want and it has many configuration options to make it quicker (like vncserver).  Why did you decide against it?[/quote]
Hmm... I'll give it second chance.

[QUOTE=intangible]You could also install freenx and use that in combination with x11vnc and really speed things up.[/QUOTE]
Can't do:
- I need a platform intependend solution,
- Viewer could be run from browser (java-vnc).

---

### Post by intangible on 2005-06-24
If there's problems with x11vnc, let me know, I might be able to help you fix them.

---

### Post by Teo on 2005-06-24
[QUOTE=intangible]If there's problems with x11vnc, let me know, I might be able to help you fix them.[/QUOTE]
Got 2  :-| 

1st
Can't setup x11vnc as a service - or can't connect to x11vnc when using initd :/
This is my **/etc/inetd.conf**:
```
5900 stream tcp nowait nobody /usr/local/bin/x11vnc -q -inetd -display :0 -auth /home/tomek/.Xauthority -rfbauth /home/tomek/.vnc/passwd -httpdir /usr/share/tightvnc-java -o /var/log/x11vnc.log
```

This is what I get after **vncviewer host:0**
 CConn:       connected to host teo port 5900
 main:        End of stream

If I run x11vnc by hand from terminal everything works great.

2nd
When startin x11vnc from terminal I can't connect using browser - I can connect only by vncviewer.
```
x11vnc -display :0 -auth /home/tomek/.Xauthority -rfbauth /home/tomek/.vnc/passwd -forever -httpdir /usr/share/tightvnc-java
```

This is what I get when type code abowe:
25/06/2005 02:06:57 Using X display with 32bpp depth=24 true color
25/06/2005 02:06:57 Autoprobing TCP port
25/06/2005 02:06:57 Autoprobing selected port 5900
25/06/2005 02:06:57 Listening for HTTP connections on TCP port 5800
25/06/2005 02:06:57   URL [http://teo:5800](http://teo:5800)
25/06/2005 02:06:57 screen setup finished.
25/06/2005 02:06:57 The VNC desktop is teo:0
PORT=5900

So everyting should be OK

Path to index.vnc is correct - I'm using **tightvnc-java** package.

---

### Post by intangible on 2005-06-28
Since you are only interested in sharing the desktop that is logged in, why not just have x11vnc startup automagically when the user tomek logs into his session?

---

### Post by crashtest on 2005-06-28
Did you try System --> Preferences --> Remote Desktop?  This will share desktop:0

---

### Post by intangible on 2005-06-28
He had tried that, but didn't like the speed (and I agree, it is slower than the other vnc options and no clear way to configure any of the details).

It is nice that it's included with Gnome, but I just wish it performed better :D

---

### Post by Teo on 2005-06-28
[QUOTE=intangible]Since you are only interested in sharing the desktop that is logged in, why not just have x11vnc startup automagically when the user tomek logs into his session?[/QUOTE]
 Good idea - I'm gonna think 'bout this :)

Edited:
[QUOTE=intangible]He had tried that, but didn't like the speed (and I agree, it is slower than the other vnc options and no clear way to configure any of the details).

It is nice that it's included with Gnome, but I just wish it performed better :)[/quote]
Yup, exactly :)

---

### Post by crashtest on 2005-06-28
[QUOTE=intangible]He had tried that, but didn't like the speed (and I agree, it is slower than the other vnc options and no clear way to configure any of the details).

It is nice that it's included with Gnome, but I just wish it performed better :D[/QUOTE]


Oh, right - he did say that, but I missed it.  How about installing 'rfb'?  I don't know if it's any faster, but it might be worth a try.

---

### Post by Teo on 2005-06-28
[QUOTE=crashtest]Oh, right - he did say that, but I missed it.  How about installing 'rfb'?  I don't know if it's any faster, but it might be worth a try.[/QUOTE]
 x11vnc author's words:
I wrote x11vnc because x0rfbserver was basically impossible to build on Solaris and had poor performance. The primary x0rfbserver build problems centered around esoteric C++ toolkits. x11vnc is written in plain C and uses only standard libraries. I also added a few enhancements to improve the interactive response, add esoteric features, etc.

Didn't check rbf, but I bolive him :) Besides, I had send mail to author and he said this:
Hmmm, I don't quite know.  Looking at the debian tightvnc-java package,
yes, -httpdir /usr/share/tightvnc-java should point to the correct place
(contains VncViewer.jar and index.vnc files).

Ah, searching my mail for httpCheckFds+fcntl I see I had a discussion
with an x11vnc user in May 2004 what seems to be the same problem you
are seeing.  And I fixed it about that time.

Your x11vnc 0.6-3 is fairly old.  Seems to be from Jul 2004 so one might
think the bug was fixed, but IIRC the Debian maintainer for x11vnc was
doing some somewhat strange stuff: a number of times he would take my
newest x11vnc.c file and drop it into an old libvncserver source tree
and make a new package.  This would work, but he wasn't picking up the
bugfixes in libvncserver (where your bug resides).

This words are true, and the new version of x11vnc (0.7.2) works perfectly. So Ubuntu's package (old version - 0.6-3) is the one to blame.

Please tell me how to let Ubuntu's authors know bout this ugly bug, and ask to update x11vnc package in repos?

---

### Post by intangible on 2005-06-28
Looks like the next version of Ubuntu, breezy already has the newest version ([http://packages.ubuntu.com/breezy/x11/x11vnc](http://packages.ubuntu.com/breezy/x11/x11vnc))

If you think it's serious enough that it should be backported to the current version as a fix. post a bug report here: [https://bugzilla.ubuntu.com/buglist.cgi?component=x11vnc](https://bugzilla.ubuntu.com/buglist.cgi?component=x11vnc)

---

