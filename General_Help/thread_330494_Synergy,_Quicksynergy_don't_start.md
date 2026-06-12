---
title: "Synergy, Quicksynergy don't start"
date: 2007-01-03
forum: General Help
---

### Post by AEngineer on 2007-01-03
I'm attempting to set up Ubuntu 6.10 machine so that I can use the keyboard and mouse on my XP machine to access it.

I've installed both synergy on both machines and quicksynergy on the ubuntu.  I am now trying to configure the ubuntu machine as instructed at: [http://quicksynergy.sourceforge.net/](http://quicksynergy.sourceforge.net/)

My problem is that quicksynergy doesn't start so I cannot get anywhere.

Any suggestions on what to do?
Should I just forget quicksynergy and find instructions on dealing with synergy via command line - ugh.  If so, can you point me to good instructions.

Thanks

---

### Post by Calculator on 2007-02-04
I have a similar problem: 

I have set quicksyergy up on the server (Ubuntu 6.10) and synergy on this machine and on the client machine running XP.

Problem

XP machine shows that it is connected - the icon in the systems tray has a lightening bolt through it.

However, I cannot move between my Ubuntu screen and my XP screen.

Any ideas?

Thanks all

---

### Post by Andy_D on 2007-02-05
If the lightning bolt is on the icon in the Win XP system tray then a connection has been made. Have you setup the screens correctly in quick synergy? 

Type the hostname (though I find typing the IP address works the best) into the appropriate box in the server tab of quick synergy on Ubuntu in order to let synergy know which screen is positioned where and hence which edge of the server screen links to which edge of the client screen. 

The same applies when serving from Win XP but the screen setup looks a little more complex. Just add the number of screens you are using and give them a name then select the position of each screen relative to the other (this must be done for both screens so 2 links are required if using 2 screens).

---

### Post by epine on 2008-02-02
I use ubuntu 7.10 as server with quicksynergy connect to winxp as client with synergy1.31.
the connection works SOMETIMES and when it works it works really well. but after a reboot it might stop working with nothing change on setting. just weired. now it stopped working. I'm wondering why synergy client on Xp need to set the port but quicksynergy no such request so should I use like 192.168.0.100[COLOR="Red"]**:2480**[/COLOR] for quicksynergy ? well I just  tried still doesn't work:confused:. waiting for the magic moment it'll work in a sudden like before. but I'd like to find out why?

---

