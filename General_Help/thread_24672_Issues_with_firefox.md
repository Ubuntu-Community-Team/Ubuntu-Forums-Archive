---
title: "Issues with firefox"
date: 2005-04-07
forum: General Help
---

### Post by psoulocybe on 2005-04-07
Firefox was repeatedly crashing my machine today

i have since removed firefox, java and flash plugins

still nothing.

I installed opera, and have had no problems for an hour... so it was definatly firefox.

any ideas?

---

### Post by Nis on 2005-04-07
[QUOTE=psoulocybe]Firefox was repeatedly crashing my machine today

i have since removed firefox, java and flash plugins

still nothing.

I installed opera, and have had no problems for an hour... so it was definatly firefox.

any ideas?[/QUOTE]
 Need more info than that.  Did you try running Firefox from a terminal?  Usually when a program crashes it will output useful info if it was run from a terminal.  Were you using a certain theme or extension?  Sometimes poorly written extensions can crash the browser.

---

### Post by psoulocybe on 2005-04-07
the extension was my first thought because i had just installed a couple new ones.

i started from scratch and had no trace of them, and still crashed.

i ran it from a link.

firefox would open, and load a couple pages....

torsmo wouldn't show any unusual usage statistics.

but after i tried going to a couple different pages... whether in tabs or in the same one, it crashed.

---

### Post by Nis on 2005-04-07
[QUOTE=psoulocybe]the extension was my first thought because i had just installed a couple new ones.

i started from scratch and had no trace of them, and still crashed.

i ran it from a link.

firefox would open, and load a couple pages....

torsmo wouldn't show any unusual usage statistics.

but after i tried going to a couple different pages... whether in tabs or in the same one, it crashed.[/QUOTE]
 Which pages did you go to?  Was it crashing only on certain pages, or were the crashes apparently random?

---

### Post by psoulocybe on 2005-04-07
Random.  craigslist, my homesite, my email for work, ubuntuforums, ubuntuguide, google, arstechnica.

different combinations of the above.

---

### Post by Nis on 2005-04-07
[QUOTE=psoulocybe]Random.  craigslist, my homesite, my email for work, ubuntuforums, ubuntuguide, google, arstechnica.

different combinations of the above.[/QUOTE]
 Alright.  The only way some real light will be shed on this problem is with some error messages or a log file.  Try installing Firefox again and running it from a terminal.  Hopefully you'll get some error messages if it crashes.  If not then another solution is to create a temporary user and try running firefox as that user.  If it doesn't crash then some setting in your home directory is causing problems.

---

### Post by psoulocybe on 2005-04-07
well, the problem is that when it crashes, it freezes the whole system.

where would a log be that would show that on my system?  i could go back and see.

i tried /var/log/messages and didn't see anything

---

### Post by Nis on 2005-04-07
[QUOTE=psoulocybe]well, the problem is that when it crashes, it freezes the whole system.

where would a log be that would show that on my system?  i could go back and see.

i tried /var/log/messages and didn't see anything[/QUOTE]
 If it's freezing the whole system then there some problem more severe than just Firefox.  Are you sure it's freezing the system?  Can you switch over to a virtual terminal (try ctrl+alt+F2)?  If so then you can try killing Firefox from there.  I'm not why sure the whole system would freeze.

---

### Post by psoulocybe on 2005-04-07
ok, i have it reinstalled... i'll try to reproduce it....

if it dies again... i'll try going virtual terminal

thanks for your help man... hopefully i'll get this smoothed over

---

### Post by psoulocybe on 2005-04-07
when run from terminal:

psoulocybe@psoulocybe:~$ firefox
*** loading the extensions datasource
*** loading the extensions datasource
Warning: more than one line!

---

### Post by Nis on 2005-04-08
[QUOTE=psoulocybe]when run from terminal:

psoulocybe@psoulocybe:~$ firefox
*** loading the extensions datasource
*** loading the extensions datasource
Warning: more than one line![/QUOTE]
 That looks interesting.  Move your ~/.mozilla/firefox/<random profile string>/bookmarks.html somewhere else and try removing ~/.mozilla.  Now this will wipe any configuration you've done to Firefox, namely extensions, themes, and a few other things.  If you move your bookmarks.html, though, you can always move it back after you restart Firefox.  Hopefully this will solve your problem.

---

### Post by psoulocybe on 2005-04-08
this is a default install... 
I made sure .mozilla didn't exist before i started reinstalling

i moved bookmarks.html though...   i havn't had any problems since re-installing java, firefox, and flashplayer.

---

### Post by Gandalf on 2005-04-08
hello,
i have also issues with firefox, firefox just quit (disappear) without any warning or error or anything else, i tried everything, 
```

sudo apt-get --purge remove mozilla-firefox
sudo rm -rf ~/.mozilla
sudo apt-get install mozilla-firefix

```
and the problem still present couldn't get it solved :(

---

### Post by johndoe on 2005-04-08
I have the same problem.

Let me be a bit more specific. I think it's the Gecko engine that does it. Using Firefox or Galeon randomly hangs my GUI. I can still move the mouse and the system is still running (apache/mysql still serves up content, etc) but the GUI is unresponsive. No keyboard, and other than moving the mouse cursor, I can't do anything with the mouse either. Most people would experience this as a 'computer crash'. I don't have a second system nearby or I'd ssh into the box to examine what's happening, 

The only thing I can find in the logs (/var/log/syslog) is
[INDENT]Apr  8 15:14:18 localhost kernel: NVRM: Xid: 13, 0000 02005600 00001796 00000c2c 00010001 00000080
[/INDENT] 
right before the crash. I don't know if it's related.

Crashes happen randomly. Sometimes it's opening something in a new tab or just the Firefox window getting focus.

I'm guessing (no expert here) that it's some combination of X.org + NVidia drivers (restricted) and something the Gecko rendering engine does. Any ideas? Opera doesn't do it for me and w3m only gets me so far :)

---

### Post by misterlizard on 2005-04-08
I've been getting the same thing too, total lockup except mouse pointer can still move (but isn't animated). Ctrl-alt-delete, ctrl-backspace, ctrl-F1 etc. have no effect. The 'kernel: NVRM: Xid: 13,' appears in syslog. Usually happens within a few minutes of starting Firefox, though the KDE Help Centre seems to trigger it reliably. Most of the time I run with KDE, but I've had exactly the same problem under Gnome.

I've read about this on other forums. The only advice I could find was to go back to the 'nv' driver instead of the 'nvidia' driver in xorg.conf. This will disable 3D acceleration but may stop the problem. To do this:
1. Open /etc/X11/xorg.conf in an editor (you'll need to be root, or do 'sudo gedit /etc/X11/xorg.conf')
2. Look for the Section "Device"
3. find Driver "nvidia", which should be just underneath it.
4. change it to:
    Driver "nv"
5. Restart X (ctrl-backspace)

So far, this seems to have fixed the problem for me with no performance decrease and no crashes since. However, I don't use any 3D apps so I probably wouldn't notice.

It's only the last couple of days I've had this happen. If anyone knows how to roll-back the nvidia drivers I'd be happy to try it out and see if it really is just them causing the problem.

----
EDIT: This may be connected with fonts. I used to run with subpixel hinting, but changed it back to autohinting (using sudo dpkg-reconfigure fontconfig) since I get on better with that. I never noticed any crashes with autohinting before (tried it for a while a few weeks back), but it was only after switching to it again today that the trouble started. Still no idea why though  :(

---

### Post by timczer on 2005-04-08
I wonder if the crashing in firefox has to do with specific content in the web pages visited.  I had an experience a week ago with firefox shutting down when I went to a specific website.  It didn't freeze though, it just simply closed.  I could go right back in again, no problem. Each time I went to this site it would close firefox.   I could go to other sites and browse and there didn't seem to be any issues.  After reading this thread, I went back to the same site and firefox closed again.  The site is mlsnet.com.  If I click on teams and then choose roster under a team name, firefox closes every time.  
    I don't know enough about how websites are put together to understand what happens in this action that firefox doesn't like.  I thought maybe a similar thing might be happening with some of these other people having issues.

---

### Post by SKLP on 2005-04-08
I got this problem, too :(
Just updated (reinstalled my machine) to "stable" hoary from a few-weeks old one with nvidia 66.29 and for the first time in a long time my machine locked up!!
I first thought, "bad luck, prolly nothing to do with the update"
But then i got the crash again!!!

This is probably a problem with the combination of firefox and nvidia 71.67, right?

---

### Post by johndoe on 2005-04-09
Thanks lizard, I've switched back to the nv driver and so far, so good. I think I'll keep track of the NVidia forums and see if future driver updates fix this (and then wait for them to make it to -restricted ..)

This thread has a lot of info - most of which boils down to 'it could be anything' :)

[http://www.nvnews.net/vbulletin/showthread.php?t=47502](http://www.nvnews.net/vbulletin/showthread.php?t=47502)

---

### Post by misterlizard on 2005-04-14
I think I've narrowed it down a bit more. I'm pretty sure it's a font rendering problem connected with the nvidia driver. If you run 'sudo dpkg-reconfigure fontconfig' and set the rendering method to be anything other than autohinting, it seems to fix it.

This is fine unless you want to run with autohinting (which I do), so you can just disable RenderAccel in the device section of xorg.conf, which seems to work too.

I would post it to that nvnews.net forum, but they won't accept free email accounts in the registration.

---

### Post by skoal on 2005-04-14
When firefox crashes on you unexpectedly and quite often, you can try this to diagnose the cause:

* I'm on another distro right now, so forgive the lack of completeness here.

1. find the firefox script with 'which firefox' (or similiar).
2. I assume Ubuntu doesn't make any changes to that script, so 'vi <path>/firefox' as root (or with sudo).
3. Uncomment the '#set -x' (around line 73 w/version 1.01).
4. open up a terminal and launch firefox this way: 'firefox &> /tmp/firefox.log'

That should capture all the debugging output to a temp logfile.  When it crashes, Check the log.  Outside of that simple method, you'll need to run an strace on it.

Comment that line back after you're done (if you want).

---

### Post by woahdae on 2005-04-16
fontconfig thing didn't do anything for me. still no renderaccel...

btw, worked fine on yoper 2.2 pre, which is kde 3.3, 2.6.10, and I'm not sure what version video drivers, but noone knows if that matters anyways...

grrr.

---

### Post by mdm on 2005-04-17
I've got the same problem as you. After reinstalling, removing extensions, themes, and the .mozilla directory, and seeing that it didn't had effect, I thought about plugins. And only after removing the flashplayer-mozilla package Firefox stopped freezing. Well, this worked for me (without touching the Nvidia drivers or anything else) :)

PD: I''ve also written the solution [here](http://www.ubuntu-es.org/node/3080?PHPSESSID=b4558515075de7912605dd17728ed253)  (in spanish, sorry)

---

### Post by vtrac on 2005-04-20
Arg.. this is starting to happen to me too.  Unlike most of you, I am on an ATI Radeon card instead of an Nvidia card, so would that eliminate a source of problems?  I've also noticed that it happens only when I have firefox open (usually with 2-3 tabs) and then I switch to another application and then try to switch back to firefox. It'll lock up then, and the entire system is unresponsive until I force firefox to close, at which time my system is normal.  Only started noticing this yesterday.

I've also had firefox randomly close on me for seemingly no reason.  Once I right clicked on a link to a file, and as soon as I clicked "Save link as.." it closed on me.  I started another instance of firefox and did the exact same thing and it worked fine.  1.0.2 is really screwy.

---

### Post by Miguel on 2005-04-21
While I don't suffer from freezes, I do suffer *a lot* of crashes. I mean, this is linux, ain't it?

Hardware: Dell Inspiron 8600c, with an ATi Mobility Radeon 9600 Pro Turbo (128 Mb ram). I use the "fglrx" 3d accelerated module.

Software: Firefox 1.0.2, because I have an out of the box Hoary. All packages installed from official repositories (including multiverse), with the exception of: [list][*] the w32codecs (download, then dpkg -i), 
[*] Acrobat Reader 7 (alien, then dpkg -i), 
[*] Scilab 3.1 RC1 (built from source)
[/list]

My plugins are: [list][*] MPlayer plugin from synaptic 
[*] Java (installed manually)
[*] Flash player plugin installed manually
[/list]

I can provide more data, if anyone is interested. A friend of mine that works 5 meters away from me and also uses Hoary, this time on a desktop, and also suffers from a lot of crashes. Will a Bugzilla help? I have noticed far more crashes in a week with Hoary than in a month with Warty.

---

### Post by DaveB on 2005-04-21
I have experienced total system freezes here too.  I dunno if this is relevant but here it happens after  apm -s  and leave in suspend overnight (trying to be a good citizen and save power   :) ). Also happens after a few minutes in suspend. Then I try to use Firefox on Ubuntu forum, and/or try to minimize Firefox window. Firefox is frozen, not responding. 
Next I tried a terminal, typed  top  but no response. Then try ctrl-alt-F1, type userid, won't respond. So I gave up and hit reset. After reboot it seems to be OK except for few seconds of pause after internet activity, before Firefox displays a new page; perhaps this is due to my ancient S3virge 2MB PCI video card?

Here's the output from  tail .xsession-errors

** (gnome-cups-icon:5907): WARNING **: failed request with status 1030

** (gnome-cups-icon:5907): WARNING **: failed request with status 1030

** (gnome-cups-icon:5907): WARNING **: failed request with status 1030

** (gnome-cups-icon:5907): WARNING **: failed request with status 1030

** (gnome-cups-icon:5907): WARNING **: failed request with status 1030

Some lines from  lspci
0000:00:0a.0 VGA compatible controller: S3 Inc. 86c325 [ViRGE] (rev 06) (prog-if 00 [VGA])
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at d8000000 (32-bit, non-prefetchable) [size=64M]
        Expansion ROM at 000c0000 [disabled] [size=64K]

HTH,  Dave

Edit: Oops looks like s3virge video card or something is acting up; no internet in Libranet, wimpdoze M.E. won't boot, ugh!  Posting from another computer.

---

### Post by Miguel on 2005-04-22
Well, I was running a firefox instance ran from a terminal... until it finally crashed. I was visiting OSnews (waiting for the windows security link to open), formula1.com and the forums at f1live.com. It crashed after clicking on a certain button on the forum. This is what XTERM said:

```

miguel@lcpybm:~$ firefox 
Warning: more than one line!
Violación de segmento
miguel@lcpybm:~$ tail /var/log/messages
Apr 22 11:48:32 lcpybm kernel: atkbd.c: Use 'setkeycodes e005 <keycode>' to make it known.
Apr 22 11:48:33 lcpybm kernel: atkbd.c: Unknown key pressed (translated set 2, code 0x85 on isa0060/serio0).
Apr 22 11:48:33 lcpybm kernel: atkbd.c: Use 'setkeycodes e005 <keycode>' to make it known.
Apr 22 11:48:33 lcpybm kernel: atkbd.c: Unknown key pressed (translated set 2, code 0x86 on isa0060/serio0).
Apr 22 11:48:33 lcpybm kernel: atkbd.c: Use 'setkeycodes e006 <keycode>' to make it known.
Apr 22 11:48:34 lcpybm kernel: atkbd.c: Unknown key pressed (translated set 2, code 0x86 on isa0060/serio0).
Apr 22 11:48:34 lcpybm kernel: atkbd.c: Use 'setkeycodes e006 <keycode>' to make it known.
Apr 22 11:48:34 lcpybm kernel: atkbd.c: Unknown key pressed (translated set 2, code 0x86 on isa0060/serio0).
Apr 22 11:48:34 lcpybm kernel: atkbd.c: Use 'setkeycodes e006 <keycode>' to make it known.
Apr 22 12:03:15 lcpybm -- MARK --
miguel@lcpybm:~$ 

```

I did an inmediate "cat /var/log/messages" after that. FF crashed 12:08, so the last /var/log/messages seems unrelated.

As you can imagine, "Violación de segmento" means "segment violation" though my ignorance doesn't rule out "segmen fault".

BTW: Firefox had been running for about two hours.

---

### Post by vtrac on 2005-04-22
I'm having to post this from Opera because firefox is unusable.  It freezes within 5 minutes, where I have to click on the X, wait a few seconds, and then force kill it.

I ran firefox from a terminal and this is what happens when it freezes:

> victor@omni:~$ firefox
*** loading the extensions datasource
Warning: more than one line!
Warning: more than one line!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Killed
victor@omni:~$ 

---

### Post by nocturn on 2005-04-25
I found this thread searching the forums for this exact problem.
Already 2 reboots today to get the system working again.  I have now removed flashplayer as suggested, we will see how it goes.

Is there a bugreport for this one yet?

---

### Post by vtrac on 2005-04-25
I managed to fix my freezing problem by deleting my profile and starting a new one.  Firefox seems fairly stable now, but a new problem has arisen - I can't install any extensions.  It just does nothing when I click "install."

---

### Post by nocturn on 2005-04-27
This bug seems to be the root problem:[https://bugzilla.ubuntu.com/show_bug.cgi?id=7183](https://bugzilla.ubuntu.com/show_bug.cgi?id=7183)

---

### Post by nocturn on 2005-04-27
This seems to have helped some people (will look for this option):
[http://www.nvnews.net/vbulletin/showpost.php?p=576934&postcount=36](http://www.nvnews.net/vbulletin/showpost.php?p=576934&postcount=36)

The solution for me was to enable "GW-Write Mask AGP Request" in the advanced memory timing area of my system's BIOS

---

### Post by nocturn on 2005-04-27
Another possible trick:
[http://www.nvnews.net/vbulletin/showpost.php?p=577365&postcount=38](http://www.nvnews.net/vbulletin/showpost.php?p=577365&postcount=38)
"yeah... I can't find that option too in my msi with the nforce2ultra... anyway I enabled "video cache bios" or something... for now it seems ok... but only time will tell.. right?"

---

### Post by nocturn on 2005-04-27
It seems that the 6xxx drivers with Xorg did not have this problem (or at least not as common).

Is there a way to revert to them (they used to be in Hoary before the release).

---

### Post by bvc on 2005-04-28
I removed the flash plugin and got the latest hoary upgrade for firefox and have no more freezes with it. I haven't tried the others yet, because it was also happening with epiphany and mozilla, and always with 3 or more tabs open.
nvidia GF2 MX440 64MB AGP

---

### Post by nocturn on 2005-04-29
[QUOTE=nocturn]It seems that the 6xxx drivers with Xorg did not have this problem (or at least not as common).

Is there a way to revert to them (they used to be in Hoary before the release).[/QUOTE]

Scratch that... It happened a lot in 6xxx too, only to different card models.
I'm in contact with Nvidia support over this, I will post my progress.

---

### Post by bvc on 2005-04-29
[QUOTE=bvc]I removed the flash plugin and got the latest hoary upgrade for firefox and have no more freezes with it. I haven't tried the others yet, because it was also happening with epiphany and mozilla, and always with 3 or more tabs open.
nvidia GF2 MX440 64MB AGP[/QUOTE]
scratch that....it happened again. It's not near as often though :-?

---

### Post by Jin on 2005-04-30
[QUOTE=bvc]scratch that....it happened again. It's not near as often though :-?[/QUOTE]
 remove the composite extensions from xorg.conf, then firefox works perfectly fine!

*so happy..*

---

### Post by bvc on 2005-04-30
[QUOTE=Jin]remove the composite extensions from xorg.conf, then firefox works perfectly fine!

*so happy..*[/QUOTE]
thx! but it still freezes the sys :-|

---

### Post by converter on 2005-05-01
I just experienced this on my personal workstation box with Firefox 1.0.3. This box is running a 2.6.11 kernel on gentoo, with xorg 6.8.2 (x11-base/xorg-x11-6.8.2-r1) and nvidia kernel 7174.

Since I can't ssh to the box at the moment (that's another story) I used the sysrq key combo Alt-PrintScr+e to send SIGTERM to all processes. Fortunately, X responded to the signal and shut down, giving me back control of the keyboard so I could switch to a virtual console and restart gracefully. There was no point trying to stay up, when the nvidia driver goes south the only way to recover is a reboot.

Now that I think of it, running a Linux machine with the nvidia drivers **without** magic sysrq keys is probably a bad idea, almost every time I've used the feature to recover my system it's been due to an X crash while using the nvidia driver (several different versions over the last few years).

Magic Sysrq keys are documented in the kernel tree at Documentation/sysrq.txt

---

### Post by bvc on 2005-05-01
yuk, so this sorta thing is common for you? You make it sound so common. I haven't had this kind of trouble in the 4 years (3 with nvidia) that I've run linux.

---

### Post by nocturn on 2005-05-02
I disabled RenderAccel on friday, no crashes so far.
I have read about this though, RenderAccel and composite make the problem worse (more frequent), but turning it off is not the full fix.

---

### Post by bvc on 2005-05-03
[QUOTE=nocturn]I disabled RenderAccel on friday, no crashes so far.
I have read about this though, RenderAccel and composite make the problem worse (more frequent), but turning it off is not the full fix.[/QUOTE]that, and a new ~/.mozilla, seems to have done it for me as well
thx!

---

### Post by bildo on 2005-05-13
I also had a few hard locks... 
another problem firefox slow loading pages even before I installed the nvidia/glx modules. 

I dont see any delay pinging a FQDN so I dont think (firefox slowness) is a problem with name resolution.

I have tried disabling IPV6 and also tried using a diff dns server.  I am going to try disabling the render accel today and will post back. 

 ](*,)

---

### Post by bildo on 2005-05-13
well I removed the render accel from xorg.conf...maybe that will fix the lockups but still firefox is soooo slow :(

---

### Post by jfdill_2 on 2005-05-13
The metadot web page crashes firefox if I have more than one tab open.

[http://freshmeat.net/redir/metadot/37960/url_homepage/index.pl](http://freshmeat.net/redir/metadot/37960/url_homepage/index.pl)

Edit: make that "try to go to a different page" too.  I think it could be flash, will try removing the flash plugin then see what happens.  Also the error is a segfault with little diagnostic output.

Hmm.  Pages with Shockwave content seem to kill Firefox, that seems to be a theme here.

---

### Post by twan on 2005-05-14
I also experienced a lot of problems with firefox lately

it would segfault (and thus shutting the whole firefox window down)

my problem is the libflash-mozplugin package.. i removed that one, and the problem automagically disappeared.

it's not a nice solution, since i don't have flash now but that's nothing big

---

### Post by bildo on 2005-05-15
jfdill_2 - & twan-
I removed libflash-mozplugin and firefox is usable now. 
thanks 
:)

twan-
I installed the flash plugin from macromedia firefox/flash seems to be working fine now.

---

### Post by Vin_L on 2005-05-17
I just installed Hoary 5.04 last night and was delighted because prior to that I tried installing Debian and though the terminal worked fine whenever I tried to boot into the GUI it would freeze up with a blank screen. Ubuntu on the other hand installed flawlessly with the GUI and all. I poked around all over the system and was very happy until I tried to browse the internet. The first time the system froze as firefox came up and the 2nd time it froze after clicking on a link in google (to get the Ubuntu home page). I did not experiment further because the only way I can get out of the freeze is by hitting the reset button and I am afraid of damaging my file system. Please note I did updates that were requested after logging in but I did no further tweaking (loading different drivers etc..) I am new to Linux and was hoping for the best before having to do anything fancy.

Thanks in advance

Dual boot with XP Home
AMD 1700+ Athelon
Asus An266-E MB (Nvidia)
Nvidia GeForce MX 400 128MB AGP
viewsonic A75f monitor
Realtek on board LAN eth0
Netgear WG311 WLan wan0
hda 120G
hda1 win NTFS
hda2 win NTFS
hda3 Linux boot
hda4 Linux swap
hda5 Linux /
hda6 fat32
hdb 30G
hdb1 fat32

---

### Post by jfdill_2 on 2005-05-17
I have installed Crossover Office, removed the flash plugin, and then used the flash and shockwave plugins from Crossover Office.  Now I can go to shockwave sites and Firefox doesn't crash, even if I open additional tabs.  But one strange thing happens: any shockwave content shows up on all of the tabs.  For example, I have the metadot website open in one tab, and ubuntu forums in another tab, and the shockwave from metadot is displayed over the ubuntu forums when I look at that tab :confused:

---

### Post by w4e on 2005-05-17
Do you happen to use the switch-proxy plugin? If so, that will be the cause of your trouble. It tries to connect to an none-existing update server.

---

### Post by zwaardmeester on 2005-05-25
Hi, 

***Loading the extensions datasources
***Loading the extensions datasources
 (...)

I was having this same problem at my University, but the administrator there was familiar with it. This is how to solve it:

1) remove ~/.mozilla
2) install firefox 0.9.3 and run it once
3) remove firefox 0.9.3 and run the version you want (the most recent i guess)

happy surfing! :)

---

### Post by KmL on 2005-05-29
[QUOTE=misterlizard]I think I've narrowed it down a bit more. I'm pretty sure it's a font rendering problem connected with the nvidia driver. If you run 'sudo dpkg-reconfigure fontconfig' and set the rendering method to be anything other than autohinting, it seems to fix it.

This is fine unless you want to run with autohinting (which I do), so you can just disable RenderAccel in the device section of xorg.conf, which seems to work too.

I would post it to that nvnews.net forum, but they won't accept free email accounts in the registration.[/QUOTE]

Works for me...

I had the same problem with firefox (crashed the system or X if you prefer), but not in a randomly way, always with the same page, like backports list one from jdong post (a simple php page with no special multimedia tricks) [http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php).

so, as misterlizard said, I disabled RenderAccel (I tried to use xComposite at one moment) and all ok \\:D/ .

thx masterlizard 

sonoma   ;-)

---

### Post by Miguel on 2005-06-10
Hi folks

Just for the note: I haven't had any crashes of firefox with the latest security updates: (mozilla-firefox 1.0.2-0ubuntu5). I don't dare to say the fix is just this, as I read in a previous thread there ws something related to fonts, and I did update my fonts a while ago.

Is anyone still having problems with the latest official ubuntu firefox? And with backports?

---

### Post by desdinova on 2005-06-10
[QUOTE=Miguel]Hi folks

Just for the note: I haven't had any crashes of firefox with the latest security updates: (mozilla-firefox 1.0.2-0ubuntu5). I don't dare to say the fix is just this, as I read in a previous thread there ws something related to fonts, and I did update my fonts a while ago.

Is anyone still having problems with the latest official ubuntu firefox? And with backports?[/QUOTE]
 Yep me - Java apps freeze FF (with 1.0.4 in BP)

---

