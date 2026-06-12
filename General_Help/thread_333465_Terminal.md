---
title: "Terminal"
date: 2007-01-07
forum: General Help
---

### Post by Rich78 on 2007-01-07
Does anyone know how I would go about connecting to a remote Linux box running Red Hat.

Currently a business I'm helping has Windows desktops running a terminal emulator known as Host Access to allow them to connect to the remote host which provides their POS software.

I'm currently analyzing the possibility of migrating them to Ubuntu as their primary desktop but I would need to provide a way for them to connect to this remote session.

Any help would be appreciated.

Thanks :-D

---

### Post by bodhi.zazen on 2007-01-07
Yes it can be done, but I do not understand the connection you want.

What os do you want to use (ubuntu ? windows ?) to connect to what other os (windows?  or red hat? or Ubuntu ??) ?

What protocol ? terminal (ssh, putty), or desktop (rpc, vnc, ssh with x forwarding).

---

### Post by Rich78 on 2007-01-07
Sorry I wasn't too specific.

I want the desktop (ubuntu) to connect to a red hat session.

It would be at a remote IP address accessed over the internet.

I'm not sure of the protocol, I think it's Wyse 60, which is normally configure in the Host Access terminal emulator.

---

### Post by Rob_H on 2007-01-07
Still unclear what you mean by "Red Hat session". A remote desktop session? If so, google XDMCP and VNC. Not sure what exact tools Red Hat provides to set those up, but those are the protocols involved.

If you just want a remote shell terminal, use SSH.

---

### Post by bodhi.zazen on 2007-01-07
ssh will give you a CLI interface (no gui)

VNC will give you X (a gui)

---

### Post by Rich78 on 2007-01-07
Sorry by remote session I mean a terminal type session, as in it brings up the Red Hat shell.

You then login to the shell and it launches the console application.

It's quite old fashioned, no gui.

---

### Post by bodhi.zazen on 2007-01-07
ssh is what you want.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Your red hat box is the ssh server

[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/ch-ssh.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/ch-ssh.html)

---

### Post by Rich78 on 2007-01-07
Thanks alot.  I'm a windows convert you see :cool:

---

### Post by bodhi.zazen on 2007-01-07
LOL aren't we all :p

Welcome to Ubuntu.

As an afterthought, if you are running a red hat server you may want to look at [Fedora core](http://fedora.redhat.com/) or [Centos](http://www.centos.org/).

Both are outstanding OS and it may be easier for you if you are familiar with red hat to stay in the red hat vein.

HTH 8)

---

### Post by Rich78 on 2007-01-07
Thanks but I've fallen in love with Ubuntu so far, having said that I haven't tried any other distro, but from the research I've done it seems to be the one that fits all and does it simply, which is what I like.

The Red Hat server isn't and never was out of choice, it's provided by POS software supplier and hosted by them, hence I have to connect to it remotely over the net.

---

### Post by justifier on 2007-01-07
install a SSH server on your red hat server, i cant help with this im afraid as i havnt used RH much, then in an ubuntu terminal

user@host~$ sudo apt-get install ssh (may allready be installed)
user@host~$ ssh <ip of RH server>

it will then ask you for a login, use the same as the server. and volia you have access to your RH server 

Hope this helps

---

### Post by Rich78 on 2007-01-07
Thanks very much, I'll give it a whirl.

---

### Post by Rich78 on 2007-02-05
Ok, I've used ssh to login to the Red Hat Server no problem, however when the POS app is launched the display is all messed up.

The POS app uses a text based menu system, I can see that it's launched ok and it is operable but looks a mess, I assume it's something to do with the fact that when we use it in windows we use a terminal emulator using Wyse.

Does anyone know how to rectify this?  Also why it happens?

Thanks

---

### Post by Rob_H on 2007-02-05
This can be affected by a few things, depending on what terminal program you're using (GNOME Terminal, Konsole, etc.). In Konsole, for example, you can go to "Settings > Configure Konsole..." and try changing some of the settings there such as "Allow programs to resize terminal window". Also, Konsole comes preconfigured with some different session types, one of which might work for your app.

If you just want to run the POS app in full-screen text mode and don't need the X Windows GUI, you can switch to a text mode virtual terminal by pressing Ctrl+Alt+F1 and log in there. Then start your SSH session. To get back to X Windows, press Ctrl+Alt+F7.

---

### Post by Rich78 on 2007-02-06
I'm using Gnome Terminal at the moment but I'll try switching to text mode to see if that sorts it.

I assume it's not a terminal protocol problem being that I know I have to choose Wyse60 protocol in the Terminal Emulator we use in the current Windows environment.

I just assumed since it's a Linux console app running from the prompt within Red Hat, it should run fine over SSH?

Thanks again

---

### Post by Rob_H on 2007-02-06
It should run fine over SSH, but the application might be making assumptions about the geometry of the terminal window (e.g. 50 lines by 80 columns) or the terminal type (e.g. vt100), which could be causing it to draw itself incorrectly in the dynamically-proportioned GNOME terminal.

---

### Post by Rich78 on 2007-02-06
Excuse my ignorance but if it is the terminal type is there a way to configure Gnome Terminal?

Thanks

---

### Post by Rob_H on 2007-02-06
You can try setting the TERM environment variable after you make the connection. Something like:
```
export TERM=vt102
```
By default, I think the term is set to "xterm," which some older apps might not recognize. Take a look in */etc/terminfo* or */lib/terminfo* for other possible values. This can vary by Linux distribution.

---

### Post by Rich78 on 2007-02-06
Thanks I'll look into it. :)

---

