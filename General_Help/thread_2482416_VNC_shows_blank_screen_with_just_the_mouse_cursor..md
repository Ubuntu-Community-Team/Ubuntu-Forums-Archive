---
title: "VNC shows blank screen with just the mouse cursor."
date: 2022-12-30
forum: General Help
---

### Post by david503 on 2022-12-30
I'm upgrading to a new PC. My current one is running 18.04 and I'm going to install 22 on the new one.  
Before I do I want to get VNC working on the current one so I dont have to juggle two keyboards and mice right.


I'm running vncserver and using vinagre as the client.  

I'm following this tutorial: 

[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04)

Right now I'm just connecting to myself.  

So here's the behavior:

I can connect fine (either with an ssh tunnel or without), but the result is a gray screen with the X mouse cursor.  That's it.  No menus, no icons nothing (see screencap).

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291485&stc=1[/IMG]

I've tried a few configurations in .vnc/xstartup 

```

#!/bin/sh
#xrdb $HOME/.Xresources
#x-window-manager &
# Fix to make GNOME work
#export XKL_XMODMAP_DISABLE=1
#/etc/X11/Xsession
#startx &
startxfce4 &

```

(and yes, my xfce does work, I was able to confirm that.  I also tried regular startx as you can see.)

Any ideas?  I'm not using the .Xresources because I didn't have one. As I understand it, it's just tweaks the colors or whatever, right?  If it's more than that, can someone paste theirs in here.


thanks
dw

---

### Post by TheFu on 2022-12-30
Is the DISPLAY environment variable set correctly?
Have you tried running a WM, window manager, not the full XFCE DE?
Is X11 or Wayland installed?  I suspect that VNC only works with X11, but I don't know, as I don't use VNC.

If you aren't tied to VNC, there are more secure and faster solutions, like x2go.
[https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)   It is 100% F/LOSS, uses ssh for tunneling and encryption of all traffic.  ssh handles setting the DISPLAY correctly.

---

### Post by david503 on 2022-12-30
> **TheFu said:**
> Is the DISPLAY environment variable set correctly?
Have you tried running a WM, window manager, not the full XFCE DE?
Is X11 or Wayland installed?  I suspect that VNC only works with X11, but I don't know, as I don't use VNC.

If you aren't tied to VNC, there are more secure and faster solutions, like x2go.
[https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)   It is 100% F/LOSS, uses ssh for tunneling and encryption of all traffic.  ssh handles setting the DISPLAY correctly.

Um ok how do I know if Wayland or X11 is installed?  from the CLI if I type wayl tab I get

$ wayland-scanner

And here's what I get for DISPLAY:

$ echo $DISPLAY
:0


I have an update: I noticed that when I mouse around on the gray screen my terminal floods:

(vinagre:16412): Gtk-WARNING **: 18:13:04.813: Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node box owner ViewAutoDrawer)


Honestly I think I need something in that [COLOR=#000000][FONT=&quot].Xresources file.  Can you (or anyone) paste me the guts of your .Xresources file?  I didn't even have one so I touched an empty one. 

[/FONT][/COLOR]thanks

---

### Post by HermanAB on 2022-12-31
VNC is still a majour way to get machines hacked. There are multiple better secure solutions.

---

### Post by david503 on 2022-12-31
> **HermanAB said:**
> VNC is still a majour way to get machines hacked. There are multiple better secure solutions.

I'm doing this over the LAN.  (see op post I'm just moving from the old PC to the new one).

---

### Post by TheFu on 2022-12-31
> **david503 said:**
> I'm doing this over the LAN.  (see op post I'm just moving from the old PC to the new one).

If the DISPLAY is wrong, it won't work. That's a fact.  That applies to local, remote, VNC, x2go ssh, methods of running programs.  ssh and x2go set the display correctly, automatically.

Back when I used VNC, before finding NX-based solutions, I never setup a ~/.Xresources file for it.  That line is a complete boondoggle.


So, we've made suggestions and you don't like them for some reason.  Instead of running xfce, for a test, run openbox instead. That's a WM. It has a menu and manages windows and their placement.  Heck, if your local system is running X11, you can remotely run any GUI application on the remote system over standard X11 forwarding through ssh.  Comment out the startxfce line and put in 'openbox &' instead.  I'm assuming that openbox is already installed.  If is isn't, it is tiny, so install it.

```
$ ssh -X remote-user@remote-server  someprogram and options
```
I run thunderbird on a remote system every day, all day long.  It is a risk-management thing, since email is a risk. A simple version of the command used is:
```
ssh -X  regulus /usr/bin/thunderbird $@ &
```
Where
* regulus is the remote system.
* My username on both systems is the same, so it doesn't need to be specified.
* $@ passes any options to my script into the remote thunderbird command.

Simple, clean. Thunderbird will be displayed on my local desktop in about 1 second and fully integrate like any other local Window.  I actually run thunderbird inside a firejail sandbox to locally control file and directory access for that program, but that's a different question.

Terminals are a little different, to get a terminal with full GUI on the remote system,  I'd use
```
$ xterm -geometry 80x22+0+630 -u8 -fs 12 -fa Monospace -sb -fg green -bg black  -e ssh -X regulus &
```
From that xterm into the other system, I can launch **any** GUI program, which will open a new window on my local machine, fully integrated into the local window management.  Because ssh is used, all the traffic is encrypted in a way that makes local and remote programs equal.  

With ssh-keys exchanged (2 commands), I won't be prompted for a password after the local key is unlocked, once per local session.  That makes ssh-based connections not just more secure, but 1000x more convenient than other methods.

Again, I don't use Wayland, so I don't know if any of these things work or don't work under Wayland.  That is definitely the first thing you need to solve.  3 seconds of web search found this: [https://wayland.freedesktop.org/faq.html](https://wayland.freedesktop.org/faq.html)   --- seems there is a special version of VNC for Wayland.

---

### Post by david503 on 2022-12-31
> **TheFu said:**
> If the DISPLAY is wrong, it won't work. That's a fact.  That applies to local, remote, VNC, x2go ssh, methods of running programs.  ssh and x2go set the display correctly, automatically.

Back when I used VNC, before finding NX-based solutions, I never setup a ~/.Xresources file for it.  That line is a complete boondoggle.


Oh no did I miss a suggestion?  Sorry. Oh! wait on the old post right- I said I was doing ok with x2go boy did that ever fail.

Yea from what I read about .Xresources it looks like  it's just a #incude type of thing; unnecessary.  

Should I just switch to something like NoMachine?  I mean I'm not married to using VNC, I'll take whatever works, that's "NX-based" right, and there's a free version...

But anyway as for X11, well  I don't really need to run foreign apps locally (although that's pretty cool); just a view of the desktop. (btw I use Thunderbird too, for like 17 years, before that it was Eudora. I know what you mean about email being a risk- IMAP has everything living on the server, I'm like no no no, I want it local only. POP is like the "snapchat" of email protocols haha.) 

What I want is just to see and use the desktop like I could in vnc. This is just a temporary step in the process of setting up the new pc. Oh and I'd need to be able to copy and paste text between the two screens, is that doable in NX stuff like nomachine? I wouldn't even need file transfer because I'll have samba running.

Yea I'll look into the wayland stuff, but it sounds like your keen on NX, and while the free version of nomachine doesn't support ssh, but I don't really need it for what I'm doing, there's no security issue here.

Anyway though, if I should still go the VNC route, here's what happened when I installed openbox and replaced startxfce & with openbox & - the results were the same gray screen and X cursor. Here's what the logs said:

```


31/12/22 08:05:27 Xvnc version TightVNC-1.3.10
31/12/22 08:05:27 Copyright (C) 2000-2009 TightVNC Group
31/12/22 08:05:27 Copyright (C) 1999 AT&T Laboratories Cambridge
31/12/22 08:05:27 All Rights Reserved.
31/12/22 08:05:27 See http://www.tightvnc.com/ for information on TightVNC
31/12/22 08:05:27 Desktop name 'X' (lenovo:1)
31/12/22 08:05:27 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
31/12/22 08:05:27 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
Obt-Message: XKB extension is not present on the server or too old
Obt-Message: Xinerama extension is not present on the server
Obt-Message: XRandR extension is not present on the server
Xlib:  extension "XInputExtension" missing on display ":1".
Openbox-Message: Requested key "Print" does not exist on the display
Openbox-Message: Requested key "Print" does not exist on the display
Openbox-Message: Unable to find a valid menu file "/var/lib/openbox/debian-menu.xml"


31/12/22 08:05:34 Got connection from client 127.0.0.1
31/12/22 08:05:34 Using protocol version 3.8
31/12/22 08:05:37 Full-control authentication passed by 127.0.0.1
31/12/22 08:05:37 Pixel format for client 127.0.0.1:
31/12/22 08:05:37   32 bpp, depth 24, little endian
31/12/22 08:05:37   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
31/12/22 08:05:37   no translation needed
31/12/22 08:05:37 Using tight encoding for client 127.0.0.1
31/12/22 08:05:37 rfbProcessClientNormalMessage: ignoring unknown encoding -258
31/12/22 08:05:37 rfbProcessClientNormalMessage: ignoring unknown encoding -261
31/12/22 08:05:37 rfbProcessClientNormalMessage: ignoring unknown encoding -223
31/12/22 08:05:37 rfbProcessClientNormalMessage: ignoring unknown encoding 1464686185
31/12/22 08:05:37 rfbProcessClientNormalMessage: ignoring unknown encoding -259
31/12/22 08:05:37 Enabling full-color cursor updates for client 127.0.0.1
31/12/22 08:05:37 Enabling X-style cursor updates for client 127.0.0.1
31/12/22 08:05:37 rfbProcessClientNormalMessage: ignoring unknown encoding -257
31/12/22 08:05:37 rfbProcessClientNormalMessage: ignoring unknown encoding 16
31/12/22 08:05:41 Client 127.0.0.1 gone
31/12/22 08:05:41 Statistics:
31/12/22 08:05:41   key events received 0, pointer events 9
31/12/22 08:05:41   framebuffer updates 2, rectangles 25, bytes 1992
31/12/22 08:05:41     cursor shape updates 1, bytes 82
31/12/22 08:05:41     tight rectangles 24, bytes 1910
31/12/22 08:05:41   raw bytes equivalent 6291480, compression ratio 3293.968586
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
      after 689 requests (689 known processed) with 0 events remaining.



```

But again this is all moot if I just switch to nomachine right...

thanks!

---

### Post by HermanAB on 2022-12-31
Why remote the whole desktop house of cards, when you already have a working desktop on your local machine? Once you understand that notion, you will see why remoting only the programs you want to run using SSH makes more sense.

---

### Post by david503 on 2022-12-31
> **HermanAB said:**
> Why remote the whole desktop house of cards, when you already have a working desktop on your local machine? Once you understand that notion, you will see why remoting only the programs you want to run using SSH makes more sense.

I understand the notion.  What I want to do is more than run some applications. Well, or "less" depending on how you look at it.    In fact when I'm "done" setting up the new pc I'll barely use the old one except as a file and web dev server.  
I won't be employing the notion of running any desktop GUI programs on it remotely. When installing the new PC mainly what I'll be doing is cloning whatever I did on the old one, including the interface.  Right down to he order I list icons and the coding colors inside of IDE's.  Mainly, of course, the config files.  If I can't remember where I have gimp save files to by default I just open it in VNC (or whatever), look, and then close it. No elaborate remote-application setup necessary. 

Dramatically easier to just see the desktop.

---

### Post by david503 on 2022-12-31
> **TheFu said:**
> 
Back when I used VNC, before finding NX-based solutions, I never setup a ~/.Xresources file for it.  That line is a complete boondoggle.

NoMachine was totally awesome until:

UPDATE:
No, wait.  It's killed the audio on the host machine (I used an old laptop as the client).  Now even when I kill the service and even restart, the audio is permanently so quiet you can't even tell it's working. It's inaudible. Even when I stop the server. Even when I restart.  It's like permanently quieted the audio!?!

I'm having this problem: 


[https://forums.nomachine.com/topic/nomachine-disables-sound-permanently-on-server-ubuntu-22-04](https://forums.nomachine.com/topic/nomachine-disables-sound-permanently-on-server-ubuntu-22-04)


There's apparently no fix if you don't have backup of that specific file. 

do I have to reinstall ubuntu?!?!?!

---

### Post by HermanAB on 2022-12-31
You can run a remote file manager over SSH and launch remote programs with the click of a mouse.  VNC is mainly a Windows thing. VNC can be made to work, but Linux has easier ways to get things done. 

Anyhoo, š&#357;astný nový rok!

---

### Post by TheFu on 2022-12-31
> **david503 said:**
> I understand the notion.  What I want to do is more than run some applications. Well, or "less" depending on how you look at it.    In fact when I'm "done" setting up the new pc I'll barely use the old one except as a file and web dev server.  
I won't be employing the notion of running any desktop GUI programs on it remotely. When installing the new PC mainly what I'll be doing is cloning whatever I did on the old one, including the interface.  Right down to he order I list icons and the coding colors inside of IDE's.  Mainly, of course, the config files.  If I can't remember where I have gimp save files to by default I just open it in VNC (or whatever), look, and then close it. No elaborate remote-application setup necessary. 

Dramatically easier to just see the desktop.

Copy over the HOME directory and you'll have all your former settings.

Whenever people want to use VNC, it is 99% of the time because they prefer doing things the hard way.  Linux is designed to have thousands of concurrent users on the same machine.  Imagine if everyone had to transfer their settings, 1-by-1.  That's crazy.  You don't need to do crazy things either.

Normally, when someone says they want to move to a new system, I'd suggest what I do.
Do a fresh install, minimal for the environment you want, then follow your normal restore process for the backups from the other system.  The install deals with any hardware changed.  The backup restore places your data, settings, selected system settings and system data back.  Then, the last step is to feed a list of manually installed packages into APT.  If the same release is involved, it will just work.  

Moving from 18.04 to 20.04, I think 3 packages didn't work out of about 1000.  All that takes about 45 min, once you have it practiced.  Moving to a new system or moving to a new HDD/SSD are perfect times to get your backups working if you don't have them already.

About this time is when we'd say there it almost no need for any remote desktop. The only time I use x2go these days is when traveling and I don't want to bring anything with me that's sensitive.  I WANT everything to be remote for security reasons.

There are many ways to copy files between systems.  When migrating or restoring the most recent backup that I have, I'll just use rsync.  ssh, bash, rsync are my top 3 tools that every Unix/Linux user should know how to use to an intermediate level.

To access files (put/pull) on remote systems, almost every Linux file manager supports sftp:// URLs when ssh is setup, so you can copy/paste in a GUI, if you like.  From MS-Windows, use filezilla or WinSCP.  From Android, I use Ghost Commander, but there are lots of options.  rsync is faster, once you learn the basics.

Please don't do things the hard way, just because that's how MS-Windows requires it.

---

### Post by TheFu on 2022-12-31
> **david503 said:**
> NoMachine was totally awesome until:

I don't like the NoMachine license, so I've never used it.  To be clear, I never suggested NoMachine.  Most people never read the license and accept things they don't think will ever matter far too often.  Of course, we all have different feelings about that stuff, which is fine.

All remote desktops have limitations.  Common limitations are Wayland and heavy GUIs, like Gnome3 or Gnome4.  If you want Gnome to work, you'll need to figure out the Ubuntu Remote Desktop which I think only works with Wayland, but there's a well-known problem between Wayland and nVidia GPUs.  If you have nvidia, at least last time I checked, Wayland was very unstable and not recommended.

---

### Post by HermanAB on 2023-01-01
Note that a “Desktop” is essentially just a file browser in fullscreen mode.

---

### Post by david503 on 2023-01-01
Copy the home directory from where?  

When you say "The backup restore places your data, settings, selected system settings and system data back." what's "the backup restore"? Are we just talking about copying files or do you mean something  equivalent to timeline?  I don't use something like that (do you? which one), I just have the config files and a list of what applications and services I have installed (hell I don't even need the list it's all in my head.)  
So I don't know what you mean by "normal restore process for the backups from the other system".  The automatic backups I do are mostly just config files and data files (I do some video editing work), documents, phone call recordings, etc. There's no "restore process" other than me copying files down from Crashplan. 

I've a 50 gig partition dedicated just to the ubuntu install and installed programs/services.  How would I merge that into the skeletal install on the new machine. (I guess I should start another thread instead of laboring you, so feel free to point me at in a direction and say RTFM!) 

Yea the APT thing makes sense but it didn't coccur to me because in my manual plan (which I thought was the only possible plan), apt would fetch what it needs like it normally does each time I install something.   But you're saying apt has a feature whereby you can have the old apt spew out it's list of everything that's installed, and the new apt would install/update everything on the list while I watch and (in my case dumbly) press return for Y haha. That would be great.  
Actually between that and the config files that would be most of the job. Wow.

Yea, and I've used rsync before for admining servers (and also 10 years ago I used rsyncbackup, dunno if that's still supported.)

Yea and sure winscp and/or mounting samba share. But I won't be in windows often (hopefully).

> **TheFu said:**
> I don't like the NoMachine license, so I've never used it. To be clear, I never suggested NoMachine. Most people never read the license and accept things they don't think will ever matter far too often. Of course, we all have different feelings about that stuff, which is fine.

To your other response- right you didn't, what do you use for NX if not Nomachine? Wayland but only if nvidia isn't an issue?

You've been so great!

---

### Post by TheFu on 2023-01-01
> **david503 said:**
> Copy the home directory from where?  


You have 2 computers.  A is the old. B is the new.  Copy from A ---> B.  Use rsync.

> **david503 said:**
> When you say "The backup restore places your data, settings, selected system settings and system data back." what's "the backup restore"? Are we just talking about copying files or do you mean something  equivalent to timeline?  I don't use something like that (do you? which one), I just have the config files and a list of what applications and services I have installed (hell I don't even need the list it's all in my head.)  
So I don't know what you mean by "normal restore process for the backups from the other system".  The automatic backups I do are mostly just config files and data files (I do some video editing work), documents, phone call recordings, etc. There's no "restore process" other than me copying files down from Crashplan. 
Sorry. I expect you to already have a good backup tool and to be using it.  If your data isn't important enough to backup, then why move any to a new computer? Seems a waste.
Every backup tool has a method to restore it entirely or partially or 1 file.  When I say to use a restore process ... I mean you should use the restore process that works with the backup tool you are using.

This isn't supposed to be encrypted words.  I thought they were obvious.  Backups are useless without knowing how to restore.  Right?

> **david503 said:**
> I've a 50 gig partition dedicated just to the ubuntu install and installed programs/services.  How would I merge that into the skeletal install on the new machine. (I guess I should start another thread instead of laboring you, so feel free to point me at in a direction and say RTFM!) 

There are lots and lots of threads here about creating backups and a few about restoring them.  Go and read those, over and over, until it makes since.

> **david503 said:**
> Yea the APT thing makes sense but it didn't coccur to me because in my manual plan (which I thought was the only possible plan), apt would fetch what it needs like it normally does each time I install something.   But you're saying apt has a feature whereby you can have the old apt spew out it's list of everything that's installed, and the new apt would install/update everything on the list while I watch and (in my case dumbly) press return for Y haha. That would be great.  

How to do this is covered in a few different tools.  The backup and restore threads list them.  But as with most things, until you actually DO IT YOURSELF, you don't really know.  There's a point where you have to try something to actually learn.

> **david503 said:**
> Actually between that and the config files that would be most of the job. Wow.

Exactly.  Any time you modify a system config file, add a comment to that file so you'll have a way to know later which files to backup and which to restore.  For me, those are all in /etc/ somewhere.  Some config files cannot just be restored, but many can.  You'll need to recognize which and handle them correctly.

> **david503 said:**
> Yea, and I've used rsync before for admining servers (and also 10 years ago I used rsyncbackup, dunno if that's still supported.)
You should figure that out.  I've heard of this really great web search tool.  It usually has answers for many questions like this.  Think it is called DDG or startpage or ... it will come to me ... .gooogle.  I could be wrong.

> **david503 said:**
> Yea and sure winscp and/or mounting samba share. But I won't be in windows often (hopefully).
To your other response- right you didn't, what do you use for NX if not Nomachine? Wayland but only if nvidia isn't an issue?

You've been so great!
Samba is for Windows-only stuff.  Please never use it for Unix-to-Unix stuff. There are better options.
'x2go'   .... didn't I mention that already?  But that is a last resort, only when I'm traveling.  I don't use wayland.  Thought I was clear about that.  If you have wayland questions, use some websearch and try it.  Or just use X11.  You can switch between them just before login.  There are threads about that in these forums.

---

### Post by david503 on 2023-01-01
Oh I thought the "copy the home directory" was a suggestion for a fix for my null audio problem. -I missed that you were quoting a different response from two comments of mine ago instead of one ago, my fault sorry.

> **TheFu said:**
> 
Sorry. I expect you to already have a good backup tool and to be using it. If your data isn't important enough to backup, then why move any to a new computer? Seems a waste.
Every backup tool has a method to restore it entirely or partially or 1 file. When I say to use a restore process ... I mean you should use the restore process that works with the backup tool you are using.

This isn't supposed to be encrypted words. I thought they were obvious. Backups are useless without knowing how to restore. Right?


Ok that's a bid odd- "If your data isn't important enough to backup" - um I just told you I do back it up, and how. My backup "method" is specifying this to go up to Crashplan, as I said, so it's not like I'm not backing up the data at all. Also I told you my (admittedly crude) method of restoration too. So it's not "a waste", it's just that my method sucks, hence I'm here.
My data *is* important enough to backup..... which is why, um, I do back it up. You just said that I don't back it up at all. "[COLOR=#000000]*If your data isn't important enough to backup"*[/COLOR] &#65533;&#65533;

> **TheFu said:**
> 
But as with most things, until you actually DO IT YOURSELF, you don't really know. There's a point where you have to try something to actually learn.


Yea, like for example maybe I should ask humble questions from gurus... um.... like for example.........?
As for "DOING IT MYSELF", maybe I should've said something to the effect  of "feel free to point me in a direction and just say RTFM!"  Oh, wait, I did.

> **TheFu said:**
> 
You should figure that out. I've heard of this really great web search tool. It usually has answers for many questions like this. Think it is called DDG or startpage or ... it will come to me ... .gooogle. I could be wrong.


Great thanks, I've never heard of startpage, that's new to me. Thanks for shifting into snide mode about google. Your google skills might be better, but how would I stumble on smartpage from google? Well or recognize it's value among the haystack if I did. I know it's surely possible but once again, my inexperience isn't a form of unwillingness. (You're going to respond to this  with some crafted search criteria, and we'll end up debating whether the query and/or its results are obvious, and that's fine.)

Snidely pointing me at DDG and google is a cop out. You could do that with anyone asking help about anything. You could write a response bot that just says that.  I'm not exceptional. 

Ok I didn't realize x2go was NX based, sorry. Wait, you never explicitly said it is. (I guess I could've figured that out by context perhaps.)  So, because it was crashing me, I threw it out. Yea, I could've explicitly checked if it was NX based, but at that point I just googled (yea that thing... I've heard of somewhere... what's it called....) for "NX desktop", like, yknow, a diligent **learner** and the fist thing that came up was Nomachine, which (in spite of license), is also free. I'm only using it temporarily on the LAN as I said, so I'm less worried about license than most.

> **TheFu said:**
> 
Samba is for Windows-only stuff. Please never use it for Unix-to-Unix stuff. There are better options.


Ok yep so I'm guessing NFS? I guess the reason I'd default to samba is for the rare times when I need to boot into windows. I guess I could do both...

And as for looking at other threads in the forums- I enthusiastically said I should just either start a new thread or you can point me in a direction or just tell me to RTFM! I already agreed, I just said so!

---

### Post by TheFu on 2023-01-02
Seems my wording wasn't the best and came across in a way that wasn't intended.  Sorry.

We aren't allowed to say RTFM here.  We can say that other threads have possible solutions.  For some vast answers, pointing someone at other threads or other links **is** all we have time to do.  I've had a terrible week (last week).  

I suspect we have different definitions for what a "backup" means. It doesn't matter.  What matters is that simply copying files isn't really a backup.  That's only 50% of what a backup needs.  The other 50% is contained in the owner, group, permissions, ACLs, xattrs.  That's ignoring the need for different backup sets being available which contain 100% of what makes for good backups.  That's why I suggested reading other threads here to learn more about backups.  Searching online is fine, but most of those hits will be for MS-Windows backups, which aren't the same as what Unix needs.

NFS is 1 option to CIFS/Samba, but not what I'd use for this.  I'd use rsync.  For a 1-time need, especially when ssh is already working, that would be much easier.  For personal files only, you can be less careful with permissions and use sftp/scp, but expect to have to fix some of the permissions.  For example, ~/.ssh/ has strict requirements for ownership and permissions or no ssh connections will work.

Rather than make you unhappy again. I'll just step away. Perhaps someone else can help.

---

