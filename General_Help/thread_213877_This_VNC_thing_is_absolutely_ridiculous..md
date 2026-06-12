---
title: "This VNC thing is absolutely ridiculous."
date: 2006-07-11
forum: General Help
---

### Post by NinjitsuStylee on 2006-07-11
<frustration>

So after spending almost all day browsing the Ubuntu forums, I've decided that I'm quite lost.

Just like the rest of the world, I want to be able to set up a VNC solution that fits my needs.  And what are my needs exactly? 

I've been using Vino this entire time, and for the most part I have no complaints.  It shows me my currently logged-in session, which is exactly what I want.  However, if there is a power-outage or some other crazy happening, my machine restarts, and I can't use vino anymore because obviously it only works once someone has logged into a session.

There are numerous guides out there on [how to enable VNC with persistant sessions]("http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc+dapper") etc etc, but none of this applies to what I want.  VNC starts a new session, and I want to use my CURRENT session, unless there IS no session, in which case I would like to login via GDM, and then when disconnecting from the server, STILL have that session be running on my MAIN DISPLAY, so when I come home and sit down on my computer, I see the session I started remotely.

I'm using Dapper 6.06.   Nevermind the SSH business, I'll figure that out later.  I just want to be able to restart my computer remotely and not get locked out of my system! :(


Sigh.  Why can't they just make the Vino server start at the login screen?

Quick update:  I've heard about x11vnc, and supposedly it not only works better than Vino (and allows you to see your current X session).  However, everyone seems to have guides that are either old, or incomplete for what I need it to do.

Again, here is a summary:[LIST]
[*]Want to have the exact same functionality as Vino (Gnome's default Remote Desktop server) but would like to be able to remote in and log on to the machine in case of an accidental restart (ie power outage).
[*]Only want to have one session running on this machine.  Ever.[/LIST]Excuse me if I'm exhausting the subject, but when it comes to the subject of remoting, this forum is filled with lots of scattered bits and pieces.  ](*,)

</frustration>

UPDATE:  Oh.  One more thing.  Is there any way to get the screen to "lock" when I'm remoting in?  Sorry if this sounds too windows-ish, but if there is one feature I loved about windows, it was the remoting.  If I'm remoting in to my current session, I don't want anybody with physical access to be able to mess with anything.

---

### Post by Macchi on 2006-07-13
I believe that you should try FreeNX if you wish a very simple, efficient, and safe remote access to your desktop  environment over a local network or through the internet.

The protocol used in FreeNX is optimized for X and ssh, thus offering compression and encryption. You will not have to bother about most technical details, just install, configure and use it. Observe that persistent sessions require no extra configuration steps, just choose to hibernate the session upon the termination of a connection from a FreeNX client. There are clients for Linux, Mac, Win, etc  available from Nomachine. 

For installation of the client and server please check the following link:
[http://www.ubuntuforums.org/showthread.php?t=97277&highlight=howto+freenx](http://www.ubuntuforums.org/showthread.php?t=97277&highlight=howto+freenx)

Just post a (kind) message if you need further help!



PS: I strongly recommend a constructive attitude when dealing with difficult technical challenges in software and in life. People will certaily be much more responsive, specially in this forum where there are lots of people willing to help others. VNC has been an excellent piece of software and personally I would not criticize it. I understand though that sometimes it can be very frustating to work with computers ;) .

---

### Post by NinjitsuStylee on 2006-07-13
Macchi, thanks for your reply.

I apologize for sounding frustrated and I did not mean to criticize VNC.

However, I was pointing out its "flaws" relative to the situation.

Your suggestion to use FreeNX is appreciated, however after some research I came to realize that it won't do what I need it to, and that's to display an already-running physical session.

I did, however, find a solution to my problem on the Gentoo Wiki and I will post the link here:

[http://gentoo-wiki.com/HOWTO_Use_VNC_to_connect_to_existing_X_Sessions#Method_2:__X_Server_.28system-started.29_method](http://gentoo-wiki.com/HOWTO_Use_VNC_to_connect_to_existing_X_Sessions#Method_2:__X_Server_.28system-started.29_method)

Ssince I couldn't find the vnc.so file on my system after using apt-get to install vnc4server, I decided to manually download the tar from [http://www.realvnc.com](http://www.realvnc.com) and copy the file myself (see below).

IMPORTANT NOTE:  Install vnc4server instead of "emerging" vnc, and any paths that say "/usr/lib/modules/extensions" should read
"/usr/X11R6/lib/modules/extensions"
[FONT=Verdana]
[/FONT] [FONT=Arial][FONT=Verdana]One other note:  There have been multiple postings on various forums that suggest renaming vnc.so to libvnc.so.  Even though this is a bit silly, I wasn't quite sure which one would work, so I simply copied vnc.so and renamed it to libvnc.so (so I now have two of the exact same file in the extensions directory but with different names).  It's a bit of a hack, but it gets the job done.


This method will start the vncserver from X, rather than after GDM Login (like Vino does).  Make sure you disable Vino before you try this (System->Preferences->Remote Desktop).

One "bug" i have noticed is that I often get a "sticky-key" problem:  whenever I use my shift-key on the local machine to type something, the character (or sometimes the unshifted character) ends up getting repeated, making it look like the key is stuck, and I have to hit the delete key or another key in order to get it to stop repeating.  I'm not sure if the problem has to do with the vnc client I'm using here (TightVNC client) or if it's an X issue or what, but aside from being a minor annoyance, it's not a big deal.

On that note, has anyone ever had that problem? 
[/FONT] [/FONT]

---

### Post by NinjitsuStylee on 2006-07-13
By the way, in case anyone is confused and really wants to know how I managed to set up VNC so that it uses my currently running session and also lets me log in using GDM if there is no session running, and you get lost on the Gentoo Wiki page I linked above, let me kno

I'm at work right now, but I might just post a clear-cut HOWTO later tonight, if there's any demand for it :)

---

### Post by shoyer on 2006-07-14
Indeed, such a guide would be greatly appreciated. Thanks :).

---

### Post by Castar on 2006-07-14
There is demand! :D

---

### Post by rbannan on 2006-07-14
I'd also like that how to doc!

---

### Post by jnev on 2006-07-14
I'd like to know myself, thanks!

---

### Post by breuerp on 2007-01-08
I seem to keep fighting this thing.  I have VNC running by forcing install of the amd64 packages:

```
sudo dpkg -i --force-all xvnc4server_4.0-7.3_amd64.deb
sudo dpkg -i --force-all vnc4server_4.0-7.3_amd64.deb
```

The problems are:
a)  This is not the latest version (by a long shot) so I'm concerned about vulnerabilities
b) *MORE* importantly, apt-get/synaptic report the application as broken (since it's not the latest version) and won't let me update/upgrade any other packages until I "fix" it.  Of course "fixing" it means that I upgrade to the latest version which appears to not have the AMD64 bug corrected on it.  

Does anyone know where I can get a newer version of a vnc server package that will run on AMD64?  FreeNX is not an option because resumable sessions are an absolute requirement.

Thanks.

---

### Post by madmailman on 2007-09-24
Hey NinjitsuStylee,

Did you ever post that "How to" of yours. I'm very much a Noob and would love to see how you got it working.

Thanks
MadMailMan

---

### Post by HermanAB on 2007-09-24
Well, basically you are laboriously rediscovering why nobody uses VNC...

The best way to do remote control of a Linux machine is via ssh with X forwarding.  If you wish to have a remote menu for easy point and click, then the secret is to launch a different desktop taskbar than the one you are using on your local machine.  So if your local is running Gnome, launch KDE kicker remotely, or launch a Rox panel and vice versa, otherwise the local machine desktop may get confused.

These all work:
$ ssh -X -C -c blowfish user@server
password
$ kicker
$ gnome-panel
$ rox -r panel

Cheers,

H.

---

### Post by NinjitsuStylee on 2007-09-24
Wow, it's been ages since I've posted on this thread.

My apologies for not posting that Howto...life can get kinda crazy.

@HermanAB:  What if you're local is a windows machine? :)  Besides, I tunnel my VNC thru SSH anyways.


I can't fully remember what I did, but I know it involves modifying xorg.conf (/etc/X11/xorg.conf   and MAKE A BACKUP FIRST) to include this under the Section "Module":

> Load   "vnc"

I believe what this does is start the vnc server upon xorg load instead of after.  That way, you can VNC in even if your power goes out and reboots your computer (which is the original problem I was having).

Also, at the bottom of your Section "Screen", just before the EndSection, include:

> Option "PasswordFile" "/home/YOURHOME/.vnc/passwd"

to include your password file.

Hope that helps...and if not, my apologies again...It's hard to go unnoticed posting on Linux forums while working at an MS partner shop :-p

---

