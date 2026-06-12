---
title: "What is the best way to connect to a remote desktop?"
date: 2007-12-31
forum: General Help
---

### Post by Spirotot on 2007-12-31
I'm trying to connect from my laptop to my desktop. The desktop is running Windows Vista, and my laptop is running Ubuntu 7.10. I've surfed the forums for two days now, and I'm not really finding anything that's helping me out a lot. Here's some of the preferred requirements for the solutions you guys can post:

1. The solution has to be free.

2. Preferably, although I don't know if this is possible, I don't want to have to install anything on the Vista machine.

Also, the Vista machine is on the same network as my laptop, usually, but there are times when I'd like to connect to it from different places (so, the connection would have to be via Internet, not the wi-fi network).

Thanks a ton for any help.

---

### Post by Giradman on 2007-12-31
Well, I'm not sure if you want to connect to just share files or if you want to control your VISTA desktop w/ the other machine?  If not already done, you might want to explore the Windows feature [Remote Desktop]("http://www.microsoft.com/windows/products/windowsvista/features/details/remotedesktopconnection.mspx") - I'm not sure how Ubuntu 7.10 would be configured to remotely control your VISTA computer, but maybe others have accomplished this task or have suggestions.

I currently use 'Remote Desktop' @ home on my XP computer to connect to my office computer via a VPN connection (needs a Citrix client) - office computer is XP, also; works fine - just not sure about 'mixing' these OSs - good luck & please let us know 'what' works for you - might help others, including myself! :)

---

### Post by Spirotot on 2007-12-31
I'd like to connect to control the remote desktop... Sharing files isn't super important, but if I could, it'd just make it that much better. Also, the Vista computer is running Windows Vista Home Premium, which, as far as I can tell (I've done quite a bit of screwing around, so I think this is pretty accurate), it doesn't have a Remote Desktop feature built in (well, it does, but it's like, disabled, or something? All I know is that everywhere on Microsoft's website that I've found information about Vista's remote desktop, it says that you have to have Vista Ultimate for it to work.).

I've screwed around with VPN a little bit, but since I was/am completely new to it, I just realized that you need a server (or something) to use it.

What about VNC? I'm very new to this, also... I really know nothing about 

Something like LogMeIn would be awesome, but alas, it's not supported on Ubuntu and/or Linux, as far as I can tell.

---

### Post by freymann on 2007-12-31
Download TightVNC on your windoze machine and install. You can select whether you want to install or activate the server portion on your windoze machine, which in this case, you likely want to select NO (no server started) as you just want to connect somewhere else.

Download TightVNC:  [http://www.tightvnc.com/download.html]("http://www.tightvnc.com/download.html")

On Ubuntu 7.10, click System>Preference>Remote Desktop and tick the first couple options. Read what the other two options mean and use them to your liking.

Now you load the tightvnc viewer on your windoze machine, type in the IP number of your Ubuntu box, and voila.

Very easy.

It's not exactly secure if you're connecting from the outside world though. You can either accept that or look at alternatives, of which there are plenty. On your local LAN the above is likely just fine though.

After re-reading your post, I think you want to do this the other way around

Laptop (running ubuntu) connects remotely to the Vista Machine?

Just as easy. Download TightVNC and ACTIVATE the Server portion, assign a password.

In Ubuntu, click Applications>Internet>Terminal Server Client.

Set the protocol to VNC.

Enter your Vista machines IP number into the computer field. (you may need to include the colon 1 at the end, like this: a.b.c.d:1)

Click Connect. Enter password. Should work that way too.

---

### Post by dlegend on 2007-12-31
I was about to suggest what freymann suggested. It is the same thing I use for remote desktop and is really easy to setup. If you are connecting via the same network in TightVNC you only have to type in the name of the machine to connect rather than an IP/Port. Otherwise the port should default to 5900.

---

### Post by HermanAB on 2007-12-31
This is the best way.  I use it regularly:
$ rdesktop -u username w.x.y.z

Cheers,

Herman

---

### Post by Spirotot on 2007-12-31
freymann,

Sounds easy enough... I'll give it a try. Thanks a ton!

HermanAB... I don't quite understand. Obviously I put a username in the 'username' part, but who's username? The laptop's or the Vista machine?

---

### Post by sethfc on 2007-12-31
so i figured i'd chime in since i'm trying to do the same thing...

currently, i have my ubuntu box in my dorm with enabled remote desktop.

i have tight VNC viewer here at work.

At my dorm, on the linux box, I went to a website that would show my IP.  I wrote that down, and i'm here at work, and I can't connect to that IP.

I also left my macbook on, which is on the same router.

Can anyone think of a reason I cant connect from work?

-seth

---

### Post by HermanAB on 2007-12-31
"HermanAB... I don't quite understand. Obviously I put a username in the 'username' part, but who's username? The laptop's or the Vista machine?"

Well, you are trying to log into the distant machine, so you need to use the username and password of the distant machine.  If you omit it, you'll be prompted.

---

### Post by Spirotot on 2007-12-31
> **HermanAB said:**
> "HermanAB... I don't quite understand. Obviously I put a username in the 'username' part, but who's username? The laptop's or the Vista machine?"

Well, you are trying to log into the distant machine, so you need to use the username and password of the distant machine.  If you omit it, you'll be prompted.

Ok. That's what I thought... Just wanted to be sure.

---

### Post by culley on 2008-01-28
Hi,

Sorry for invading but I've just setup a home server running Xubuntu and I would like to station it somewhere without a monitor and keyboard in my home, my question is can i TightVNC to make a remote desktop connection from my VISTA pc to the Xubuntu server so i can make changes, install some stuff etc etc.

Thanks alot

EDIT: 

After reading the TightVNC FAQ they claim there program doesn't work with Vista :( - sigh! Oh well I'll have to keep looking.

---

