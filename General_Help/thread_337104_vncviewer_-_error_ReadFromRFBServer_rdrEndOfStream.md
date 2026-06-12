---
title: "vncviewer - error ReadFromRFBServer: rdr::EndOfStream"
date: 2007-01-12
forum: General Help
---

### Post by grahams on 2007-01-12
Hi

I've been using vnc on edgy for a while without issue (apart from an initial X11 fonts issue, like everyone else).  I set it up using the howto at [http://www.ubuntuforums.org/showthread.php?t=122402&highlight=ReadFromRFBServer%3A+rdr%3A%3AEndOfStream](http://www.ubuntuforums.org/showthread.php?t=122402&highlight=ReadFromRFBServer%3A+rdr%3A%3AEndOfStream)

Today I can not access it, even from the local machine 'vncviewer :1'. I get a "ReadFromRFBServer: rdr::EndOfStream" error after I enter the password.

I have checked the obvious and even resorted to a reboot. 
Anyone else seeing the same issue?

---

### Post by anaspeople on 2007-02-19
I had the same error and doing this helped me:

```
sudo apt-get install vnc4server/edgy xinetd
```

more info at [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/]("http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/")

---

### Post by claypole on 2007-02-23
Thanks!  I had this problem for a while and it has been driving me mad.  This fixed it.

---

### Post by notquitehere188 on 2007-04-28
i entered that and i got an error saying there was no edgy release for vnc4server

---

### Post by slAoD on 2007-06-05
> **notquitehere188 said:**
> i entered that and i got an error saying there was no edgy release for vnc4server

if you have feisty fawn release then you have to add the edgy repositories listed in your sources.list file... i did this and it, i downgraded it to vn4server 4.1.1 + xorg1.0.2-0ubuntu1and im ready to go

---

### Post by claypole on 2007-06-06
Since upgrading to Feisty I had the same problem (I was downgrading in Edgy), I found a fix in one of the threads a few days ago (possibly the one referenced at the beginning of this thread) and updated all my machines and everything works perfectly now, and no need to downgrade vnc4server :D

I just added " -extension XFIXES" to the end of the server_args line in /etc/xinetd.d/Xvnc, so the final /etc/xinetd.d/Xvnc looks like this:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

Hope this helps!

---

### Post by rapchee on 2007-06-06
i get this message  when i try to connect to osx, so i hope this will help
however
i might be really a noob, but i cannot find nor xinet.d nor Xvnc file
where should i be looking 
(using feisty)

---

### Post by slAoD on 2007-06-07
> **claypole said:**
> 
I just added " -extension XFIXES" to the end of the server_args line in /etc/xinetd.d/Xvnc

That worked for me too.. Thank you a lot for the tip!!!


As for rapchee, you should read this post [http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc+resumable](http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc+resumable)      
( HOWTO: Set up VNC server with resumable sessions )

---

### Post by wajiw on 2007-06-18
> **claypole said:**
> I just added " -extension XFIXES" to the end of the server_args line in /etc/xinetd.d/Xvnc

Got rid of the error for me too! 

I was also having troubles getting the gdm login screen to appear using feisty.  All I would get is the X11 pixels and X cursor.  I edited /etc/gdm/gdm.conf and set Enable=true right after [xdmcp] and finally got the login screen after I rebooted.

---

### Post by jdarias on 2007-06-23
I had the same trouble in feisty.

Now i get a gray screen with an X as a mouse pointer, nothing more.

---

### Post by XProgrammer on 2007-06-29
> **claypole said:**
> Since upgrading to Feisty I had the same problem (I was downgrading in Edgy), I found a fix in one of the threads a few days ago (possibly the one referenced at the beginning of this thread) and updated all my machines and everything works perfectly now, and no need to downgrade vnc4server :D

I just added " -extension XFIXES" to the end of the server_args line in /etc/xinetd.d/Xvnc, so the final /etc/xinetd.d/Xvnc looks like this:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

Hope this helps!





--

Hi claypole, 

Thanks alot buddy.. This is really worked out for me. I had problem like first plain X gray screen with X mouse pointer. After that, EndOfStream problem. I tried various option like x11vnc,etc. Nothing met my requirements. Your suggestion really worked out. I'm very happy today. 

Thanks alot and I appreciate your helping..

Great work.. Keep it up..

Thanks,
Regards,
XProgrammer.

---

### Post by _oOMOo_ on 2007-07-01
Just to say thanks, this worked a treat for me.

---

