---
title: "Trojan Horse?"
date: 2005-10-14
forum: General Help
---

### Post by PereUbu on 2005-10-14
On the 12. of october, the day before Breezy final was released, I realized that someone had taken control over my Breezybox. When I was reading the news on the web, someone out there in cyberspace was moving my cursor around on my screen, klicking links and opening new windows, and probably having a good laugh at me. :(

The first thought that struck my mind was to format my Ubuntu partition and start from scratch again. But then I would never find out wether I have done something stupid, or if there's some other reason for this happening.

I've been running Breezy for about a month, when I upgraded from Hoary.
Firestarter firewall is installed and I believe it's running well? Or isn't it?
Well I'm confused, and would be thankfull for any help and good advice in this matter.

What should I do? 
:confused:

---

### Post by localzuk on 2005-10-14
Do you have any remote-desktop servers installed such as VNC? If so, did you put a password on them so that you need it in order to control it.

The likelyhood of someone actually having rooted your box is slim. Have you looked at logs? Take a look around in /var/log/ - especially ssh logs etc...

Do you have a root password set? If so ensure you have a strong one (numbers, letters, > 10 long etc...)

---

### Post by PereUbu on 2005-10-14
Thanx for your advice, localzuk.

No, I have not VNC installed.
And I have a strong password. (I should change it just in case, shouldn't I?)
I don't have a root account but uses sudo.

I will look at my logs when I come home over the weekend.
But I have never looked at these logs before, so I don't know what I should be looking for.

---

### Post by jdtanner on 2005-10-14
Hi PereUbu,

It sounds to melike you have a problem with your mouse drivers. I've experienced the same problem in the past with Fedora and several other distros. It might look like somebody else is moving the mouse, but it is normally the computer getting very confused. Just a thought, are you using an external mouse on a laptop?

Cheers,
JohnT

---

### Post by PereUbu on 2005-10-14
Hi jdtanner

It might be a mouseproblem. I have a wireless mouse and keyboard connected to my ordinary beige box PC. I also have a bluetooth USB dongle connected. 

I hope this can explain my experiences, but I'm not sure...

How can I find out?

Best regards PereUbu

---

### Post by jdtanner on 2005-10-14
Hi there,

Maybe you could post the InputDevice section(s) of your /etc/X11/xorg.conf file for us all to have a look at. I've found that sometimes if you have too many 'wireless' items connected to your PC you can sometimes see this behaviour. I've seen it happen on two PCs, and the only solution was to dump the wireless mouse (I think they are overrated anyway :-) ).

Oh...and you might want to have a look at [http://www.ubuntuforums.org/showthread.php?t=35951](http://www.ubuntuforums.org/showthread.php?t=35951) :-)


Cheers,
JohnT

---

### Post by Screevo on 2005-10-14
Actually, from what it sounds like, someone could just be connecting through that bluetooth device.

SM

---

### Post by PereUbu on 2005-10-15
Thank U jdtanner & Screevo

I will post my xorg.conf section and unplug my bluetooth-dongle when I get back home over the weekend.

Until then, have a nice weekend!

---

### Post by localzuk on 2005-10-16
Yep. Wireless mice and keyboards are much overrated. Situations always occur where the battery starts running out.

Try changing the battery before moving any further (unless it is a rechargable version?).

Always have a wired mouse on standby.

---

### Post by buildid on 2005-10-16
dont know if i have to create a new topic , but i have the same problem .

using a logitech cordless mouseman optical .

output from xorg.conf:Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

---

### Post by PereUbu on 2005-10-17
Hello again, I'm back home.

I have now disconnected my bluetooth-dongle, made a new strong password for my account, and replaced firestarter with guarddog which according to grc.com's "Shields up!" test is far better (stealth all over). 

I have looked in /var/log but can't find anything about ssh. And really, I don't have a clue what to look for...
...so I decided to paste the content of my log folder:

> acpid                  dmesg              mail.info.1.gz  mysql.log.4.gz
acpid.1.gz             dpkg.log           mail.info.2.gz  mysql.log.5.gz
acpid.2.gz             dpkg.log.1         mail.info.3.gz  mysql.log.6.gz
acpid.3.gz             evms-engine.1.log  mail.log        mysql.log.7.gz
acpid.4.gz             evms-engine.2.log  mail.log.0      mythtv
aptitude               evms-engine.3.log  mail.log.1.gz   news
aptitude.1.gz          evms-engine.4.log  mail.log.2.gz   samba
auth.log               evms-engine.5.log  mail.log.3.gz   scrollkeeper.log
auth.log.0             evms-engine.6.log  mail.warn       scrollkeeper.log.1
auth.log.1.gz          evms-engine.7.log  mail.warn.0     scrollkeeper.log.2
auth.log.2.gz          evms-engine.8.log  mail.warn.1.gz  syslog
auth.log.3.gz          evms-engine.9.log  mail.warn.2.gz  syslog.0
base-config.log.1      evms-engine.log    mail.warn.3.gz  syslog.1.gz
base-config.timings.1  faillog            messages        syslog.2.gz
btmp                   fontconfig.log     messages.0      syslog.3.gz
btmp.1                 gdm                messages.1.gz   syslog.4.gz
cups                   installer          messages.2.gz   syslog.5.gz
daemon.log             kern.log           messages.3.gz   syslog.6.gz
daemon.log.0           kern.log.0         messages.4.gz   user.log
daemon.log.1.gz        kern.log.1.gz      mysql           user.log.0
daemon.log.2.gz        kern.log.2.gz      mysql.err       user.log.1.gz
daemon.log.3.gz        kern.log.3.gz      mysql.err.1.gz  user.log.2.gz
debug                  kern.log.4.gz      mysql.err.2.gz  user.log.3.gz
debug.0                lastlog            mysql.err.3.gz  uucp.log
debug.1.gz             lpr.log            mysql.err.4.gz  wtmp
debug.2.gz             mail.err           mysql.err.5.gz  wtmp.1
debug.3.gz             mail.err.0         mysql.err.6.gz  Xorg.0.log
dirmngr.log            mail.err.1.gz      mysql.err.7.gz  Xorg.0.log.old
dirmngr.log.1          mail.err.2.gz      mysql.log       Xorg.20.log
dirmngr.log.2          mail.err.3.gz      mysql.log.1.gz
dirmngr.log.3          mail.info          mysql.log.2.gz
dirmngr.log.4          mail.info.0        mysql.log.3.gz


And here's my output from the Input device sections of /etc/X11/xorg.conf:

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

I use a Logitech Cordless Wheelmouse and keyboard. I sometimes use a Wacom graphire USB tablet, too.

I really hope that this information can help someone finding out what was the cause of my experience. But I keep thinking:
- what if it's something else than my mouse or blutooth dongle? I won't dear to do my homebanking again, before I'm absolutely sure my PC is not intruded by some trojan horse or something.

Is there a way to check this?

Best wishes 
from PereUbu (paranoid)

---

### Post by jdtanner on 2005-10-18
I really shouldn't worry too much. It sounds like you have your computer well and truely protected ;-)

I'd try your pc with a wired (not wireless) ps/2 mouse and see if you experience the problems you described. If not, then I'm afraid it is almost certainly your wireless mouse (check the batteries).

Cheers,
JohnT

---

