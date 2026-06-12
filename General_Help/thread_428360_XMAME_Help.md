---
title: "XMAME Help"
date: 2007-04-30
forum: General Help
---

### Post by CarlosinFL on 2007-04-30
So I installed a program called XMAME. I installed this via APT-GET which also picked up all the required dependencies. Now that it is installed, it appears to be located in /usr/share/games/xmame/

My question is has anyone used this "arcade simulator"?

I don't have any ROM games stored right now but I just wanted to check out the emulators interface and when I attempt to start the program in 7.04 Ubuntu, I get this message.

```
root@cwilliams:/usr/share/games/xmame# xmame
GLERROR: cannot access OpenGL library libGL.so
GLERROR: dlerror() returns [libGL.so: cannot open shared object file: No such file or directory]
Use of OpenGL mode disabled
XDGAOpenFramebuffer failed
Use of DGA-modes is disabled
info: trying to parse: /etc/xmame/xmamerc
error: unknown option history_file, on line 13 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option mameinfo_file, on line 14 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option fuzzycmp, on line 33 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option skip_disclaimer, on line 35 of file: /etc/xmame/xmamerc
   ignoring line
info: trying to parse: /root/.xmame/xmamerc
info: trying to parse: /etc/xmame/xmame-x11rc
info: trying to parse: /root/.xmame/xmame-x11rc
info: trying to parse: /etc/xmame/rc/pacmanrc
info: trying to parse: /root/.xmame/rc/pacmanrc
xmame: could not connect to socket
xmame: No such file or directory
LIRC disabled
loading rom 0: pacman.6e                       
loading rom 1: pacman.6f                       
loading rom 2: pacman.6h                       
loading rom 3: pacman.6j                       
loading rom 4: pacman.5e                       
loading rom 5: pacman.5f                       
loading rom 6: 82s123.7f                       
loading rom 7: 82s126.4a                       
loading rom 8: 82s126.1m                       
loading rom 9: 82s126.3m                       
done
pacman.6e    NOT FOUND
pacman.6f    NOT FOUND
pacman.6h    NOT FOUND
pacman.6j    NOT FOUND
pacman.5e    NOT FOUND
pacman.5f    NOT FOUND
82s123.7f    NOT FOUND
82s126.4a    NOT FOUND
82s126.1m    NOT FOUND
82s126.3m    NOT FOUND
ERROR: required files are missing, the game cannot be run.

```

---

### Post by renzokuken on 2007-04-30
i have used this. i did have a load of roms for it too, most of which worked fine. (although i feel it wouldnt be prudent to tell you where i got them from)

i installed from synaptic on dapper i think it was.

the error log above pretty much says it cant find opengl, which is a grafix related issue. which grafix driver are you using?

also seems to be an issue with your xmamerc file. could you post the contents of it?

EDIT: i think i may be being a bit retarded here. have you installed a GUI for it? xmame on its own is a backend. you need a frontend too such as gxmame. have a look here

[http://my.opera.com/Mr%20Green/blog/show.dml/171040](http://my.opera.com/Mr%20Green/blog/show.dml/171040)

---

### Post by CarlosinFL on 2007-04-30
Damn - this sucks. It appears there is no 64 bit OS love...

```
root@cwilliams:/home/cwilliams/Desktop# wget http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb
--11:02:41--  http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb
           => `gxmame_0.35beta2-1_i386.deb'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 277,072 (271K) [application/octet-stream]

100%[========================================================>] 277,072      185.13K/s             

11:02:43 (184.87 KB/s) - `gxmame_0.35beta2-1_i386.deb' saved [277072/277072]

root@cwilliams:/home/cwilliams/Desktop# dpkg -i gxmame_0.35beta2-1_i386.deb 
dpkg: error processing gxmame_0.35beta2-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 gxmame_0.35beta2-1_i386.deb

```

Do you know if they make gxmame for 64 bit OS's?

---

### Post by renzokuken on 2007-04-30
may be. check the sourceforge site gxmame.sf.net

failing that you could build from source.

also, the install line should include a 'sudo'

as in ```
sudo dpkg -i gxmame_0.35beta2-1_i386.deb
```

---

### Post by CarlosinFL on 2007-04-30
I am root so I would not think I would have to run the sudo command but thanks!

---

### Post by MaindotC on 2007-12-03
I found the tutorial on installing gxmame very helpful as I thought there was only kxmame.  I'm still running into problems.  When I start gxmame, i get the blank screen of death, and I log in to pty2 and kill the bash associated with it in pty7.

Then I can access gxmame, but if I click something that follows with an action, such as one of the items in the menus across the top of gxmame, I get blank screen of death, and kill it in pty2.

There was some mention earlier about the type of driver so I just thought I'd say that I'm using 7.04 on a Thinkpad T60 with the ATI restricted driver in use.

---

### Post by MaindotC on 2007-12-03
Actually, for every action that gxmame makes my screen go blank, if I switch to pty2 and then back to pty7 the blank screen goes away. Wierd.

---

### Post by disturbedite on 2007-12-03
here is my advice (and ironically, i've said this on this forum about 4 or 5 times in the last week):
don't use xmame.  its dead and super outdated.  use [sdlmame]("http://wallyweek.altervista.org/index.php").  if you need a frontend/gui use sdlmame w/ [kxmame]("http://sourceforge.net/project/showfiles.php?group_id=145736&package_id=174814&release_id=514402"). (<-- use that build specifically, not any other or the version available in the official ubuntu repos, its too old & doesn't support sdlmame).

you have to compile kxmame tho.  if you can't get it to compile try this:
```
./configure --disable-joystick
```(of course that will disable joystick/joypad support, but some ppl have reported that is what is needed to get it compile).

btw, kxmame is faster.

---

### Post by MaindotC on 2007-12-04
Sorry if you're repeating yourself as I would imagine that happens a lot in this community - I found this thread: [http://ubuntuforums.org/showthread.php?t=104222](http://ubuntuforums.org/showthread.php?t=104222) which I don't know if it is a solution or just a band-aid.  In any event, gxmame works for me, but I'd like to utilize netplay.  I can wine the mame32 version and use netplay, but I'll look into this sdlmame.  I wonder why sdlmame didn't show up when I did an apt-cache search...

Update - ok I installed per your advice and it's pretty nice but still no netplay.  Can you perhaps help me compile the Mame Plus source?  Oh, and I didn't read all of your post so I just installed kxmame via the repos and it still works fine :(

---

### Post by disturbedite on 2007-12-04
thats ok, repeating myself isn't harmful.  ;)
the reason sdlmame doesn't show up in the repo is cuz it isn't there.  it hasn't received enough reviews on launchpad to get approved to go into the repo.  that is why i gave you a link ^^^.
no, no, no.  you didn't read my post carefully enough.  read it again.  *don't* install the kxmame package from the repo.  again, read my post above.

---

### Post by MaindotC on 2007-12-05
> **disturbedite said:**
> thats ok, repeating myself isn't harmful.  ;)
the reason sdlmame doesn't show up in the repo is cuz it isn't there.  it hasn't received enough reviews on launchpad to get approved to go into the repo.  that is why i gave you a link ^^^.
no, no, no.  you didn't read my post carefully enough.  read it again.  *don't* install the kxmame package from the repo.  again, read my post above.

I know you said not to install the one from the repo but I did it anyway just to spite you and it works fine.

Wine'ing the MAME32 executable is actually faster than xmame (for me) but I don't have the ability to change controls :(  Gotta keep sdlmame installed for SpyHunter.

---

### Post by disturbedite on 2007-12-05
ok.
to clarify:
if you wanna use kxmame with sdlmame, the repo version of kxmame will not work, its too outdated and does not support sdlmame.
but...
if you don't need a frontend/gui, then yeah, kxmame doesn't matter.

---

### Post by MaindotC on 2007-12-06
Ok, now let me clarify what I said - I installed sdlmame from the deb, and I installed kxmame from the repos and they worked fine.  I guess it depends on several factors but I thought you should know.

---

