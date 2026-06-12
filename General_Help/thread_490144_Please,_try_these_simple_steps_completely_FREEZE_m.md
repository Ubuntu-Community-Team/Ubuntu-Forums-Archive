---
title: "Please, try these simple steps: completely FREEZE my system!!"
date: 2007-07-02
forum: General Help
---

### Post by Zannax on 2007-07-02
Please try this, it completely FREEZES my system 100% of the times (let's see if it's a common issue):

1- Reboot the system and login (don't try it with open programs as you can loose your data)
2- Go to the "power off" menu and choose "SWITCH USER" 
3- Login as a different user, say "User2"
4- Open the F-Spot program on the User2 desktop
5- Close it (optional)
6- Go to the "power off" menu and choose "LOG OUT" 

(My system freezes so badly that I can't even bring up a terminal with ctrl+alt+f2: I can only hard-reset it!!) :-(
Maybe it's a problem with my ATI radeon 7000 video card switching between different resolutions... it seems not to be 100% reliable/supported, I don't know.
My system is a Feisty (upgraded from Edgy), with ubuntustudio packages installed...

---

### Post by glangollor on 2007-07-02
When you freeze it, can you still log in via ssh from an other computer?? Might be intresting to know to see if it is just some graphics stuff.
You could also try to reboot it a little bit nicer by pressing 
ALT+Sysrequest           //the key is most often lables with print and SysRq
hold the two keys and press (in sequence)
r s e i u b      (let there be a little delay of ~2s betwen them)
This is often described in internet with the mnemonic "Raising Skinny Elephants Is Utterly Boring"
So I could't help you that much, since I can not reproduce your error. Hope the elephat trick helps fixing it.:-)

---

### Post by FuturePilot on 2007-07-02
Would you happen to be using the Desktop Effects? I've had the same thing happen with the Switch User option on my computer. I've filed a bug report
[https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/112518]("https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/112518")
I'm pretty sure it's related to Compiz

---

### Post by Zannax on 2007-07-03
@Futurepilot: I've seen there are many bugs relating to freeze on logout on launchpad. It's quite a common issue... I'm pretty sure I've compiz disabled when it freezes, this evening I'll check it again.
Anyway, F-Spot program too seems to use some kind of effect/acceleration: if I don't open that program it doesn't freeze...

@glangollor: I have another PC with windows, I'll try the remote login and the raising elephant trick too (I admit I've never heard of it :-) )

I've seen there's a workaround, too: setting "AlwaysRestartServer=true" in gdm.conf but it doesn't work for me :-(

---

### Post by Zannax on 2007-07-03
The trick of  "raising skinny elephants" worked, indeed: it resets my system even after freezing: it's a "hardware" thing or it means that somehow the system was still responding?

Anyway, it freezes even if compiz is turned off. 

I've tried dpkg-reconfigure gdm but not solved anything...
I'll try remote login (as soon as I manage to... :-) ) and see if I there is some clue.

---

### Post by louieb on 2007-07-03
> **Zannax said:**
> Please try this, it completely FREEZES my system 100% of the times (let's see if it's a common issue):

1- Reboot the system and login (don't try it with open programs as you can loose your data)
2- Go to the "power off" menu and choose "SWITCH USER" 
3- Login as a different user, say "User2"
...
**Its a Feisty problem**
my laptop freezes here. my desktop get a little further. 
sometimes can ctrl+alt+f1 to get to the cli. sometimes can ssh from another pc. and reboot. Dapper does not have this problem. there is a bug report for fast user switching.   [Bugs in Ubuntu]("https://bugs.launchpad.net/ubuntu")

---

### Post by Zannax on 2007-07-04
YEAH! I did it!!!** I did it!!**

Following the vague idea that "composite" was somehow buggy, I followed a post suggesting how to disable it, i.e. I added the following at the end of my xorg.conf:

```

Section "Extensions"
       Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
       Option  "AIGLX" "off"
EndSection

```

(And btw I had already set  in gdm.conf, as said before)
```
AlwaysRestartServer=true" 
```

So now it works perfectly and **doesn't freeze ** any more! Yes!
(I don't know which one of the 3 settings above did the trick but I'll find out by exclusion) :-D

---

### Post by glangollor on 2007-07-14
> **Zannax said:**
> The trick of  "raising skinny elephants" worked, indeed: it resets my system even after freezing: it's a "hardware" thing or it means that somehow the system was still responding?

Anyway, it freezes even if compiz is turned off. 

I've tried dpkg-reconfigure gdm but not solved anything...
I'll try remote login (as soon as I manage to... :-) ) and see if I there is some clue.

Its talking directly to your kernel. its no hardware thing. 
Have phun with your X!:guitar:

---

### Post by regomodo on 2007-07-14
don't do a hard reset. You can save yourself by following this

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by Zannax on 2007-07-15
Glangollor:
Thx... I've googled for it too.

Thus it is not "the system" that freezes, just the X server or some component.
I've checked launchpad too, there are many bugs open for similar freezes... Too bad I can't use desktop effects until they fix it :-( (or maybe until I get a new card with better support) well... I will survive :-)

Btw it was the option:
```
Section "Extensions"
       Option  "Composite" "Disable"
EndSection
```

in my xorg.conf that fixed it, the AIGLX thing does nothing (apparently).

---

### Post by redcharlie on 2007-07-15
Logout results in a hang for me too.
I'm running xubuntu 7.04 (fiesty) on a toshiba satellite a135-s2386 and also on an ECS k7som+5c
If I do a graphical login (via gdm) and then log out, the system hangs.  No gdm, ctl-alt-f# will not give me a terminal.

So, to log out I just shoot X in the head with ctl-alt-backspace (crude, but does the job) and then things work fine. gdm comes back, and I can even logoff normally without issue.

It only seems to be a problem with that first logout.  The k7som board is for a server, so it's a very minor issue as I don't reboot it but once in a very long while.  Having to remember to use ctl-alt-backspace instead of logging out is more of a pain for the laptop, but generally only one user uses it between cycles, so that's not too big either.

---

### Post by Zannax on 2007-07-17
> **redcharlie said:**
> Logout results in a hang for me too.
I'm running xubuntu 7.04 (fiesty) on a toshiba satellite a135-s2386 and also on an ECS k7som+5c
If I do a graphical login (via gdm) and then log out, the system hangs.  No gdm, ctl-alt-f# will not give me a terminal.

So, to log out I just shoot X in the head with ctl-alt-backspace ...

It just seems that these kind of freezes are due to different reasons, I've read many descriptions on launchpad too.
For instance, in my case ctrl+alt+backspace doesn't work either... Someone has a white screen with blinking cursor, someone says it freezes only with desktop-effects, someone even says it freezes only WITHOUT desktop effects... It must be quite an headcache for the developers trying to fix it! :-)

Just out of curiosity: have you tried disabling composite extension as I've described some post before (i.e. in xorg.conf)?

---

### Post by redcharlie on 2007-07-18
Sorry zannax, no extensions in my /etc/X11/xorg.conf  (my k7s0m board is long in the tooth)
And note that ctl-alt-backspace only works BEFORE I try to logout! (I'm outta luck if I try to logout first and it hangs :(  )

But it happened to me again, this time not on the first logout. Funny thing was, I was also logged on via vnc and ssh, and they were not affected, so it's obviously not my system that's hanging, just gdm.

First I tried just  /etc/init.d/gdm restart, but no luck, ps -ef | grep gdm showed:
root     19066     1  0 Jul17 tty7     00:12:15 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root     22662     1  0 07:21 ?        00:00:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root     22666 22662  0 07:21 ?        00:00:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root     22677 22666  0 07:21 ?        00:00:00 /usr/lib/gdm/gdmopen -l /bin/sh -c /usr/bin/whiptail --yesno 'There already appears to be an X server running on display :0.  Should another display number by tried?  Answering no will cause GDM to attempt starting the server on :0 again.  (You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to console 7.  X servers usually run on consoles 7 and higher.)' 16 70
root     22678 22677  0 07:21 tty9     00:00:00 /usr/lib/gdm/gdmopen -l /bin/sh -c /usr/bin/whiptail --yesno 'There already appears to be an X server running on display :0.  Should another display number by tried?  Answering no will cause GDM to attempt starting the server on :0 again.  (You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to console 7.  X servers usually run on consoles 7 and higher.)' 16 70

gdm is getting confused, and I certainly didn't  see this whiptail msg.

So, I just killed all the gdm's, then to kill X I did a "sudo kill -9 19066" and then /etc/init.d/gdm restart did the trick, all via my vnc session.

So, this is an annoyance, but not a show stopper for me.  It's funny that this issue has so many different flavors, but I'm getting the same behavior (flaky first logout, but ctl-alt-backspace works) on two very different systems (very old ECS k7som board, and brand new toshiba laptop a135-s2386)

---

### Post by redcharlie on 2007-07-18
More strangeness:

After doing the above, I got gdm to work again, but Ctl-Alt-F# no longer works.  All I get is the gdm login screen , frozen, for F1 thru F8, 

But Ctl-Alt-F9 brings me back to a working gdm logon!!

ps -ef | grep gdm shows that it's now up to "vt9"...like it's slowly working it's way up the function keys...

lemme try cycling gdm again  (/etc/init.d/gdm restart)...nope, still on vt9, for whatever reason...
ps -ef | grep getty
shows that all my getty's are running (for vt1-vt6) but I can't get to them.  fooey.

---

### Post by Zannax on 2007-07-18
> **redcharlie said:**
> Sorry zannax, no extensions in my /etc/X11/xorg.conf  (my k7s0m board is long in the tooth) 


There was no "extension section" in my xorg.conf either (if I remember well, I'll check this evening :-) ): actually you must **add those 3 lines** at the end of xorg.conf if you want to try and disable composite extension... See if it works, just curiosity. (Of course make a backup copy of your xorg.conf, before...)

---

