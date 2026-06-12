---
title: "Trouble getting irexec to run on login?"
date: 2007-02-27
forum: General Help
---

### Post by Bogaurd on 2007-02-27
Hi,
I'm having trouble getting irexec running when I login to my gnome session - I initially had trouble with getting lircd to run, I had specified for it to start in /etc/rc.local, and it would start, but for some reason it would not pickup any events until i stopped it, and then started it again. I got around this by setting the SUID bit on the lircd file, then running it from my user account on login, by choosing preferences -> session -> startup.

When i add 'irexec' or 'irexec --daemon' to the startup area under sessions, it does not seem to run when I login.. I can't see the process running, and my remote doesnt do anything. If i start it manually once i'm logged in though, it works flawlessly. Anybody have any idea why this would be?

Thanks :)

---

### Post by energiya on 2007-02-27
I had a lot of problems with lircd and irexec. 

The way I fixed it:
**1)** Put in rc.local
> 
setserial /dev/ttyS0 uart none
modprobe lirc_serial
modprobe lirc_dev
sleep 1
ln /dev/lirc0 /dev/lirc
**/usr/local/sbin/lircd**

to start lircd, and seems to work perfect. Ok. You might  not need the "set serial... bla bla bla ln /dev/lirc0 /dev/lirc" part (I have a homemade reciver), only "/usr/local/sbin/lircd". The thing is that it might not be installed in the same path as mine, so in a terminal type
```

whereis lircd

```
and copy-paste that (not the .conf part).

**2)** Now for irexec. This needed a lot of research to make it work.
as root, open "/etc/X11/xinit/xinitrc.YOUR_WINDOW_MANAGER" with a editor, and just add
> 
/usr/local/bin/irexec -d /home/YOUR_USER_NAME/.lircrc

after the > #!/bin/sh part.

**Make a backup of you xinitrc file in some other path, just in case !**

Again, check where irexec is installed with the "whereis" command. Don't forget to make a .lircrc file! It should be something like [this]("http://people.atrpms.net/~pcavalcanti/scripts/lircrc.txt"), but for your own needs, of course. 

Hope this helps!

---

### Post by Bogaurd on 2007-02-27
Hrm.
My windows manager is gnome, but i dont have an xinitrc.gnome file, just an xinitrc... I tried adding the irexec command below this, but it still didnt work...

This is the output of my 'whereis irexec' command:
"irexec: /usr/bin/irexec /usr/X11R6/bin/irexec /usr/bin/X11/irexec /usr/local/bin/irexec /usr/share/man/man1/irexec.1.gz"

Any other ideas? :(

---

### Post by energiya on 2007-02-28
Did you put lircd to start in your rc.local file ? And does it run fine?

> **Bogaurd said:**
> 
This is the output of my 'whereis irexec' command:
"irexec: /usr/bin/irexec /usr/X11R6/bin/irexec /usr/bin/X11/irexec /usr/local/bin/irexec /usr/share/man/man1/irexec.1.gz"


check if "/usr/bin/irexec" starts fine. If not, then "/usr/local/bin/irexec" (even thow I think one is a simlink to another).

---

### Post by Bogaurd on 2007-02-28
Yeah, lircd starts fine, no dramas there, it's just irexec that doesnt want to start when I login.
I'll try with the other paths when i get home in a few hours.

Is there any other reason it woulndt start? I mean, if i start it manually when I'm logged in it works fine =\

---

### Post by energiya on 2007-02-28
I've tried for almost a week to make it work in Ubuntu, but never managed. My conclusion was that they don't work if i put them to start close one to another (I know, not a very scientific conclusion). 

I'm now trying another distro and had exactly the same troubles as in Ubuntu, but found this xinitrc hack and now I have my remote working ! This explains the fact that I have xinitrc.xfce and you only xinitrc, but in both cases should start, as long as you go beyond the GDM login screen. 

Just to be sure you could put something like
```

echo "this is a test"

```
I'm now going to test and see where/if it outputs.

**edit:** it doesn't output in a easy readable log. Anyway...

---

### Post by Bogaurd on 2007-02-28
I got it working.
What I did was create the file /usr/local/bin/irexeclauncher, and put this in it:

#!/bin/bash
# Launcher for IREXEC because it's STUPID and won't launch properly in startup scripts!
sleep 30
irexec -d
exit 0

Then I added the launcher to my login scripts (sessions options), and now it works! :)

---

### Post by energiya on 2007-03-01
You could try by trial and error to lower the sleep time, because... 30 seconds?
The linux world seems full of improvisations (I consider myself a linux noob after all these years).

---

### Post by Bogaurd on 2007-03-01
Yeah, I know I could try and lower it... but this is not a mythtv box or anything, just my desktop, so I figure I wont be using my remote within 30 secs more than likely :P

I'm just glad it worked, hehe. :)

Thanks for your input!

---

