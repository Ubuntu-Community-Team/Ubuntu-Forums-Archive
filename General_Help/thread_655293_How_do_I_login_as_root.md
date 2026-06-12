---
title: "How do I login as root?"
date: 2008-01-01
forum: General Help
---

### Post by o55555o on 2008-01-01
Quite new to ubuntu/linux.
When installing it prompted me to import existing acctounts under win xp, it won't let go if choose not to import so I selected one.
Today Ive been trying getting my old ati mobility radeon 7500 card work for visual effects, so need to modify xorg.conf, but it won't let me because it belongs to root.
So I try login using the user name root and pswd accordingly, the error pops up saying you cant login as root at this stage.
Now could anyone please tell me AT WHICH STAGE could I login as root???
MANY MANY thanks!

---

### Post by bigken on 2008-01-01
try using** sudo** in the terminal 

ie sudo dpkg-reconfigure xserver-xorg

---

### Post by knutschr on 2008-01-01
You should never log in as root.
To edit xserver.org, paste into terminal
```
gksu gedit /etc/X11/xorg.conf
```
That makes gedit open with root privileges.

---

### Post by MighMoS on 2008-01-01
On Ubuntu, you shouldn't have to log in as root; You can just use sudo <command>.  However, if you /really/ need it, there are two ways:

The following will log you in as root from a user who already has sudo access.  
```
sudo -s
```

If that isn't good enough for some reason, The second will actually set a password for the root user.  Note that you should /never/ log in graphically as root.
```
sudo passwd root
```

If you enable the root account, make sure that your box is secure, as previously it would have been a lot harder to gain root access.

---

### Post by o55555o on 2008-01-01
thanks for that.
I tried that command line and went through a series of questions,however,
I wanted to insert a few lines into that xorg.conf file, how could I do that? What I just did was: Places-Computer-system-etc-X11, then double click that file, added 3 lines, then click save, then warning popped up, saying u dont have authority da da da...
Is there any way I can login to ubuntu with a root identity? Thatll be the easiest way i guess.
many thanks!

---

### Post by bigken on 2008-01-01
open a terminal and paste this 


sudo gedit /etc/X11/xorg.conf

---

### Post by o55555o on 2008-01-01
Thank you sooo much for your help!!!! 
Wish you all the very best this new year!!!:guitar:

---

### Post by taurus on 2008-01-01
> **bigken said:**
> open a terminal and paste this 


sudo gedit /etc/X11/xorg.conf

Better to use **gksudo** when you run gedit editor.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jamaisvu on 2008-01-01
> **o55555o said:**
> Quite new to ubuntu/linux.
When installing it prompted me to import existing acctounts under win xp, it won't let go if choose not to import so I selected one.
Today Ive been trying getting my old ati mobility radeon 7500 card work for visual effects, so need to modify xorg.conf, but it won't let me because it belongs to root.
So I try login using the user name root and pswd accordingly, the error pops up saying you cant login as root at this stage.
Now could anyone please tell me AT WHICH STAGE could I login as root???
MANY MANY thanks!

[FONT=Franklin Gothic Medium]Of course, if you really really want to be root (***and you understand and accept the risks of doing this***), hit Alt-F2 and type in:

[/FONT][FONT=Courier New]kdesudo konsole[/FONT] [FONT=Franklin Gothic Medium](in KDE); or[/FONT]
[FONT=Courier New]gksudo gnome-terminal[/FONT] [FONT=Franklin Gothic Medium](in GNOME)[/FONT]
[FONT=Franklin Gothic Medium]
And then (obviously) press enter. This will give you a root terminal session, from which you can then issue commands (such as gedit, kate, and apt-get) without typing sudo (and its variants) all the time.

Do, however, bear in mind that there are risks involved in doing this: it removes a safeguard between you and doing something idiotic, and most people here would disapprove of doing anything so cavalier (despite the factoid that they probably all do this themselves).
[/FONT]

---

### Post by jken146 on 2008-01-01
> **jamaisvu said:**
> [FONT=Franklin Gothic Medium]Of course, if you really really want to be root (***and you understand and accept the risks of doing this***), hit Alt-F2 and type in:

[/FONT][FONT=Courier New]kdesudo konsole[/FONT] [FONT=Franklin Gothic Medium](in KDE); or[/FONT]
[FONT=Courier New]gksudo gnome-terminal[/FONT] [FONT=Franklin Gothic Medium](in GNOME)[/FONT]
[FONT=Franklin Gothic Medium]
And then (obviously) press enter. This will give you a root terminal session, from which you can then issue commands (such as gedit, kate, and apt-get) without typing sudo (and its variants) all the time.

Do, however, bear in mind that there are risks involved in doing this: it removes a safeguard between you and doing something idiotic, and most people here would disapprove of doing anything so cavalier (despite the factoid that they probably all do this themselves).
[/FONT]

Or use ```
sudo -i
``` to become root for a little while.

---

### Post by knutschr on 2008-01-01
> Do, however, bear in mind that there are risks involved in doing this: it removes a safeguard between you and doing something idiotic, and most people here would disapprove of doing anything so cavalier (*despite the factoid that they probably all do this themselves*).

I  think, also, that most people stop doing this after a couple of times, when they themselves experience the mess it can very easy make.

I use Krusader as my file browser.
You can start a second instance of that in root mode. (Tools-->Start Krusader in Root Mode)
I use that instance only if i have too. (minimised most of the time).

One should allways, if one is not sure, use any command as a normal user first, and only if that not works use sudo, kdesu or gksudo.

---

### Post by jamaisvu on 2008-01-01
> **knutschr said:**
> I  think, also, that most people stop doing this after a couple of times, when they themselves experience the mess it can very easy make.

[FONT=Franklin Gothic Medium]You can make a mess either way -- if you're not in a root session and try executing a file called, say, "install.sh", it's likely that you'll get a screenful of impenetrable error messages and a broken app.
[/FONT] 
> I use Krusader as my file browser.
You can start a second instance of that in root mode. (Tools-->Start Krusader in Root Mode)
I use that instance only if i have too. (minimised most of the time).

[FONT=Franklin Gothic Medium]Yeah, Krusader's great! It should come with Kubuntu instead of that Dogfish.[/FONT]

> One should allways, if one is not sure, use any command as a normal user first, and only if that not works use sudo, kdesu or gksudo.

[FONT=Franklin Gothic Medium]That sounds too much like using "sudo" to mean "abracadabra" to me. If you're not sure, you should read up, learn, and make yourself sure. Or maybe I'm just a Linux fascist...[/FONT]

---

