---
title: "&quot;modem is busy&quot; What to kill?"
date: 2008-07-08
forum: General Help
---

### Post by editrix on 2008-07-08
I'm on dialup, and sometimes my ISP cuts me off (I assume that's the reason I get hangups) and *sometimes* when I try to connect again I get a "modem is busy" message in KPPP.

I've googled but everything I've found regarding the message is for when the modem doesn't work at all.

I tried killing kppp, tried sudo poff and got

/usr/bin/poff: No pppd is running.  None stopped.

Logging out and back in doesn't work. I have to reboot to be able to dial out again.

Any suggestions?

---

### Post by kdorf on 2008-07-08
killall pppd
or killall -9 pppd.

It looks like pppd is just a user app as it's located in /usr/bin, so you shouldn't need to use sudo with it.

---

### Post by VMC on 2008-07-08
I haven't used a dial-up in years, but I do know that your line itself can cause trouble. A noisy line can be the cause of the hang-ups do to the modem seeing a spike on the line.

When I had that sort of trouble in the past , I called my phone company to check the line for static. They have, or most do, a way of checking remotely. I came home one day to find my "drop" was replaced. It was old and was what caused the trouble.

---

### Post by Rick Myers on 2008-07-08
Run this from CLI:

ps -aux | more

That will give you a list of all the processes running on your machine including the app and process ID (PID). Page-down thru the list to find the offending process, then (again from CLI) type;

sudo kill PID  

Replace PID with the actual process number.

Have fun killing processes! Kill too many or the wrong ones and you'll need this too;

sudo reboot


Good Luck!

---

### Post by editrix on 2008-07-08
Thanks for the replies, guys. I've copied all suggestions to my hard drive. Now I have to wait for another unexpected hangup to try them :-)

---

### Post by editrix on 2008-07-10
Ah well, none of the suggestions worked :-(

killall pppd
pppd: no process killed

Attached is the output of ps -aux. Maybe someone can find the process that's occupying my modem?

---

### Post by Joshuwa on 2008-07-10
Are you using an external modem?

I sort of have a similar issue, in that on boot my modem gets activated (I hear it 'click'), and I can't dial out until I physically switch the modem off, and back on again, wait a few moments, then try again.

I know its not a true solution since it does not stop it from happening, but perhaps it might help you redial sooner, if it works for you as well.

---

### Post by editrix on 2008-07-10
> **Joshuwa said:**
> Are you using an external modem?

Yes. Sorry. should have said.

> I sort of have a similar issue, in that on boot my modem gets activated (I hear it 'click'), and I can't dial out until I physically switch the modem off, and back on again, wait a few moments, then try again.

Odd, that doesn't happen to me. But if the computer's off and the modem's on, and the phone rings, the computer turns on :confused:

Maybe I'm not being patient enough. I'll try waiting. Thanks for replying.

---

### Post by editrix on 2008-08-24
Well, I've tried resetting the modem with the KPPP terminal, killing everything having to do with knetwork manager, and discovered a bug in gmome-ppp [https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/108451](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/108451) with a fix, but I'm not using it.

I even tried starting a new session, but absolutely nothing works except rebooting. Could someone please help? I'm attaching the most recent ps-aux output, although I doubt there'll be anything different from the one I posted above.

---

### Post by Elludium_Q-36 on 2009-08-16
I can't believe no one can answer this as I see countless posts on forums going back years!

Everyone offers advice that doed not work modprobe, LS, etc.  If the system calls the modem busy, it reads the modem at some low level!!!!

This affects various distros and does not seem to be affected by the usual suspects (processes).

Most who answer are forum trolls who get off on wasting your time.

I'd rather not reboot as I have things up that took eons to load over my i425 iDEN at a whopping 2Kb/sec (statistical mode, as in mean, median, mode).

LS recognizes it as /dev/ttyACM0 and sometimes it's ACM1 after trouble but I just upgraded to Jaunty 9.04 and that's when I wound up in perpetual, "The modem is busy" land.  Ethernet has not been a problem, when available but this KPPP/usb to iDEN has not been great fun and I had a USR serial modem act goofy.  

The whole system is a bit wonky, even after replacing a power supply missing -5v output AND reinstalling 8.04 on this HP pavillion 3300+ AMD 2.2 Ghz.

Bottom line is that someone should know.  In this current economic environment, many rely on lesser connections.

I read another post that mentioned rules files causing difficulty and remember editing "if up", "if down" under 8.04 but don't recall the location nor file names.  That poster advocated deleting said files and it would seem an upgrade would handle such but perhaps one who types complete sentences on thirty three little keys assumes too much.

---

