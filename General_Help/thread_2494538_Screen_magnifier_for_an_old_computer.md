---
title: "Screen magnifier for an old computer?"
date: 2024-01-19
forum: General Help
---

### Post by paul_red2 on 2024-01-19
Hello.

I'm looking for a simple screen-magnifier. I have an old computer so I'm looking for something lightweight.
Compiz ofc would be great but I don't think my old laptop can handle it..
I tried KMag and it was horrible.
Lately in Windows I was using OneLoupe.. very simple and lightweight magnifier.
Is there something similar that would run in Lubuntu?

Thank you!

---

### Post by MAFoElffen on 2024-01-19
The only lightweight ones I know of beside for Gnome are xzoom, KMag, Magnus, GMag and DynaMag. There may be more.

---

### Post by dragonfly41 on 2024-01-19
My weary eyes also require magnification. I go to Settings > Screen Display > Scale.

But often this screws up theme in web browsers.

---

### Post by paul_red2 on 2024-01-20
@dragonfly41 I can't find this section in Lubuntu

---

### Post by paul_red2 on 2024-01-20
I tried xzoom, magnus.. it's a bit like kmag (unusable with a fixed window that you have to move around)
I can't believe there's so few option for such a simple app.
You guys think my computer can handle Compiz?
```
CPU: dual core Intel Core2 Duo T6400 (-MCP-)
speed/min/max: 1995/1200/2000 MHz Kernel: 6.5.0-14-generic x86_64 Up: 42m
Mem: 2359.8/3906.8 MiB (60.4%) Storage: 473.22 GiB (3.4% used) Procs: 210
Shell: Bash
```

p.s. if someone else knows of a simpler lighter app, plz tell me

---

### Post by deadflowr on 2024-01-20
> **paul_red2 said:**
> @dragonfly41 I can't find this section in Lubuntu

We assume you are using the default Ubuntu desktop unless told otherwise.

---

### Post by dragonfly41 on 2024-01-20
Actually my mistake. I did not spot Lubuntu in OP profile. And in post#1. I have no knowledge of Lubuntu.

But I offer the link to the manual .. searching "zoom"

[https://manual.lubuntu.me/stable/search.html?q=zoom&check_keywords=yes&area=default](https://manual.lubuntu.me/stable/search.html?q=zoom&check_keywords=yes&area=default)

and searching "settings"

[https://manual.lubuntu.me/stable/search.html?q=settings&check_keywords=yes&area=default#](https://manual.lubuntu.me/stable/search.html?q=settings&check_keywords=yes&area=default#)

Might help for general settings. I don't know.

But also when viewing in chrome browser (in my Ubuntu 20.04) I can click on triple dot icon (in browser top bar) to select Zoom. I am on 125%.

And also individual apps such as LibreOffice, Thunderbird have their own Zoom settings. So OP should be able to setup Zoom, application by application.

Also spotted this thread.

[https://askubuntu.com/questions/1144213/how-to-magnify-a-screen-area-in-lubuntu-18-04](https://askubuntu.com/questions/1144213/how-to-magnify-a-screen-area-in-lubuntu-18-04)

---

### Post by paul_red2 on 2024-01-20
> Actually my mistake. I did not spot Lubuntu in OP profile
Not your fault.. it wasn't there.. you saw it right :D I added it after I got the criticism

As for lubuntu manual, I didn't see anything about what I'm looking for. But thanks for the link.. That manual might come handy in the future.

> Also spotted this thread.
[https://askubuntu.com/questions/1144...-lubuntu-18-04]("https://askubuntu.com/questions/1144213/how-to-magnify-a-screen-area-in-lubuntu-18-04")

Yes, I saw this one also when I was googling, but nothing useful for me..

At this point, I think i'm gonna try Compiz.. if this old laptop can't handle it, I'll remove it.

One thing also I wanted to ask that has nothing to do with screen magnifing..
I find my self often having to share files between this laptop (Lubuntu) and my Mac (OS-X)
I use a usb stick.. and I would like to have a faster way to do that.
What would you guys suggest for file sharing without having to use internet.. I would like just to link these two machines with an ethernet cable and the tutorials I found online were very hard to follow (all in terminal.. not for a noob like me).
Is there a simple for dummies guide I can follow to do this?
I also read I can also link the two computers with an usb cable.. maybe I misunderstood..
How would you do to share files between these two computers without having to be online (I mean sometimes I'm not connected and I would like to still be able to share files between these machines).

Thanks for the time guys!

---

### Post by MAFoElffen on 2024-01-20
If they are on the same network segment, MAC OSX is is Apple's proprietary, Unix-based operating system. Being unix-based, it has shh and scp capabilities.

it is turned off on MAC by default, but here is how to enable it on your MAC: [https://osxdaily.com/2022/07/08/turn-on-ssh-mac/](https://osxdaily.com/2022/07/08/turn-on-ssh-mac/)

Here is how to do scp from a MAC: [https://appleinsider.com/inside/macos/tips/how-to-use-scp-to-transfer-files-in-the-macos-terminal](https://appleinsider.com/inside/macos/tips/how-to-use-scp-to-transfer-files-in-the-macos-terminal)

---

### Post by paul_red2 on 2024-01-20
> If they are on the same network segment
I don't have any router.. just one laptop with lubuntu and a mac mini with mojave + an ethernet cable

Thanks for the links.. I hope I can understand them .. ssh and scp is new to me xD

edit:
from what i read, scp looks too hard for me (everything done with terminal)
ssh looks a bit easier.. I hope I'll be able to set it up

my goal is to transfer a file quickly from one computer to another faster than i would by using a usb stick
so typing in terminal is too long for me.. i would like to have a folder in my desktop where i drag a file and it's on the other computer.. So hopefully with ssh I will be able..
Thanks for the help.. now I go and hopefully I can do this.

---

### Post by MAFoElffen on 2024-01-20
I am "old". I started using computers in Junior High with Fortran on punch cards. PC's with MS-DOS. Unix in the service back in the late 80's...

But I have helped people learn how to do things on computers since the early 90's.

It sounds like your computers are at your home on the same local network.

shh & scp work hand in hand.

To ssh to a computer 
```

ssh <User>@<IP>

```
Connects to the terminal session of the target computer.

I have an old MacBook here that I use for Dev Testing. It is multi-boot with Mountain Lion, Lion and Ubuntu 22.03.3.

Lion has a very old version of ssh, which, if using ssh, I have to allow an old deprecate host key (not safe outside a local network!!!).

So for example. here is an ssh session with it, from a Linux Host:
```

mafoelffen@msi-ubuntu:~$ ssh -oHostKeyAlgorithms=+ssh-rsa mafoelffen@10.0.0.222
The authenticity of host '10.0.0.222 (10.0.0.222)' can't be established.
RSA key fingerprint is SHA256:6UQdpuzjFkk7/IoAjFJf9I0K2rKw+08KpZtgP2UX6eI.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.0.0.222' (RSA) to the list of known hosts.
(mafoelffen@10.0.0.222) Password:
Last login: Sat Jan 20 12:09:35 2024
Mikes-MacBook:~ mafoelffen$ ls
Desktop        Downloads    Movies        Pictures
Documents    Library        Music        Public
Mikes-MacBook:~ mafoelffen$ ls ./Downloads
About Downloads.lpdf        Install OS X Yosemite.app
Mikes-MacBook:~ mafoelffen$ ls ./Documents
About Stacks.lpdf    [COLOR=#ff0000]File1.txt[/COLOR]
Mikes-MacBook:~ mafoelffen$ exit
logout
Connection to 10.0.0.222 closed.

```

scp is similar to ssh, and uses the same protocol...
```

scp <source-file> <target-file>

```
Where the source or target could be local or remote.

If local, that is the /path/to/file_name format.

If remote, that is in User@IP:/path/to/file_name format

For example... Say I wanted to transfer File1.txt from the my User's Document folder on my MacBook to the Document directory on My Linux PC...
```

mafoelffen@msi-ubuntu:~$ scp -oHostKeyAlgorithms=+ssh-rsa mafoelffen@10.0.0.222:~/Documents/File1.txt ~/Documents/
(mafoelffen@10.0.0.222) Password:
File1.txt                                                 100%   12     2.3KB/s   00:00    

```
If your MAC OSX is recent (mine is ancient on that), then you do not have to use any added options like I had to do for that... Just using that machine as a live example for that.

Once you do that a few times, the more you do that, the more you will be comfortable with doing that and how that works.

Sorry, but I do not know of Any MAC GUI application that does that with drag and drop.

I do know of a way to do that with Midnight Commander (from Linux), but that would require you to install that and learn how that would application works. There is a steeper learning curve before you could be productive with that. That is still not a drag-and-drop solution.

---

### Post by Holger_Gehrke on 2024-01-20
XFCE / XUbuntu has a built-in compositor. One of the options this gives you is the ability to zoom into the desktop with Alt+mouse-wheel. I don't know if your machine is fast enough to handle a "mid-weight" desktop like XFCE. The file-manager of XFCE (Thunar) allows use of ssh for file transfers by entering a URL of the form "ssh://user@machine/path/to/directory/" into its address bar, so access to files over ssh works just like for local files in the file manager (you can even bookmark an URL like this in the file manager for quick access). You might want to try Xubuntu from a live system on a USB stick. It's possible that PCmanfm-qt (the Lubuntu file manager) has a similar way to access ssh-servers.

Holger

---

### Post by paul_red2 on 2024-01-20
Thanks MAFoElffen for taking the time to explain in such length.
I have to read this again and again tomorrow after sleeping (Here where I am is 11PM).
But looks like longer process to go through than just continue using a usb stick.
Anyway I'll try it tho.. maybe as you said after I get used to it, it would be easy and fast.

---

### Post by paul_red2 on 2024-01-20
@Holger Thanks! This looks interesting.. Maybe tomorrow I'll try Xubuntu LIVE and see how it goes

---

### Post by paul_red2 on 2024-01-20
BTW guys the only video I found on how to connect a mac and linux is this:
[https://www.youtube.com/watch?v=FkVY590Wr7o](https://www.youtube.com/watch?v=FkVY590Wr7o)
What do you think of this video.. is it correct the procedure?
The guy speaking sounds Asian.. terrible english xD

Looks easy to do.. but doesn't explain the file sharing part.. just the setting up the network.
I can't even try it right now bcs I have to wait for the ethernal cable to arrive (look like it will be here next week).

---

### Post by HermanAB on 2024-01-21
All Linux file browsers have a Connect to Host feature that supports SSH.  You can make a kind of shortcut for that once you have keys installed on the two machines. Then you can transfer files with a few clicks of a rodent.

---

### Post by ajgreeny on 2024-01-21
Another vote here for Xubuntu!
We don't know which Lubuntu version you're using but if it is up to date it will have the Lxqt DE which is very similar in resource use to Xfce.
You will probably find that Xubuntu runs just as well and fast as Lubuntu so definitely worth trying!

---

### Post by paul_red2 on 2024-01-21
@HermanAB:
> once you have keys installed on the two machines
Thanks for the help! Can you please help me understand what keys is?

@ajgreeny:
Thanks! I'm going to try Xubuntu for sure.. I'm curious now to see how it will run.

One other thing I wanted to ask:

I saw a video where this guy was using his old router (that had a usb input on it) to connect an external hard disc and use it from different computers.. This is an idea that I like.. I could use by external hdd for backup and also for sharing files quickly between my two computers.

---

### Post by him610 on 2024-01-22
In Xubuntu Settings click on listing/topic Accessibility. It shows how to enable how to enable assistive technologies. Follow link...
[https://imgur.com/JKQIfeF.png]("https://imgur.com/JKQIfeF.png")

---

### Post by ajgreeny on 2024-01-23
Much easier if you need only the zoom to go to **Settings manager -> Window-manager-tweaks ->** and enable compositing in the right hand tab then select **Zoom desktop with mouse wheel**

---

