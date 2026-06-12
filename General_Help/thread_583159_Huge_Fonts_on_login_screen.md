---
title: "Huge Fonts on login screen"
date: 2007-10-20
forum: General Help
---

### Post by GrantShoe on 2007-10-20
Hey everyone, I just installed Kubuntu 7.10 and my ONLY issue that I've had with it is the login screen.  The font size on it is huge, I know which boxes are for my name and password so I can easily just put in my login information and move along but its a bit annoying.  I searched around and found a couple things that could help me but I'm not sure

[http://ubuntuforums.org/showthread.php?t=235214](http://ubuntuforums.org/showthread.php?t=235214)
- it's exactly like that font size but I don't know about messing with xorg.conf file, isn't there a graphical way to do it now so that I'm not deleting the wrong thing?

[https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745](https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745)
- that's with gnome but I'm running Kubuntu so I don't think that would effect me... unless the login screen is run with gnome?

I tried to take a screen shot but it doesn't seem to be working.

any ideas out there?

---

### Post by pashashome on 2007-10-20
I have the exact same problem. I did not have this issue in 7.04, I'll look at the links you provided and let you know if they help.

---

### Post by GrantShoe on 2007-10-21
any luck with that?  I just rebooted and was reminded of this.

---

### Post by pashashome on 2007-10-21
Yeah, not so much! I see that there are a few links with possible solutions: this one seemed promising [http://ubuntuforums.org/showthread.php?t=575978&highlight=huge+fonts+login]("http://ubuntuforums.org/showthread.php?t=575978&highlight=huge+fonts+login")

I tried drvistas suggestion from the link but it didn't work for me. Hopefully, there will be a patch to fix it.

---

### Post by pashashome on 2007-10-21
Ok drvista's suggestion did work I needed to reboot like he said instead of just restart X.

Try this, seems to work for me. 

I managed to fix the problem ,
sudo gedit /etc/gdm/gdm.conf
find
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0

and change it into
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96

then restart ubuntu and it's fixed now
__________________

---

### Post by marcw on 2007-10-22
> **pashashome said:**
> Ok drvista's suggestion did work I needed to reboot like he said instead of just restart X.

Try this, seems to work for me. 

I managed to fix the problem ,
sudo gedit /etc/gdm/gdm.conf
find
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0

and change it into
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96

then restart ubuntu and it's fixed now
__________________

This solution worked perfectly for the Gutsy login page font problem (huge fonts) I was having.  Thanks!

---

### Post by sdinh07 on 2007-10-22
the above worked for me too. this is my first time using ubuntu (boo vista) and i am so glad there is so much support to be found in just these forums alone. i'm also glad that i'm running legit software now too (reason for no microsoft support.)

---

### Post by sdinh07 on 2007-10-22
i was also wondering if anyone here had a problem with their title bar. sometimes when i start ubuntu the title bar would be huge (1/5 of my screen height!!!) i thought it may be linked with this huge login screen font. it would usually go away after i log out and back in.

---

### Post by pashashome on 2007-10-22
> **sdinh07 said:**
> i was also wondering if anyone here had a problem with their title bar. sometimes when i start ubuntu the title bar would be huge (1/5 of my screen height!!!) i thought it may be linked with this huge login screen font. it would usually go away after i log out and back in.

That was happening with my install also at the same time that the fonts on the login screen were crazy huge. I haven't had the problem since.  If I remember correctly go to System/Preferences/Appearance. Click on the Visual Effects Tab and select none. If that corrects it select whatever effects you want afterward and see if that fixes it.

---

### Post by kiyolee on 2007-10-23
Great, that solves the same huge font problem I have.
But unfortunately, the Visual Effects setting cannot be saved somehow and get reset after reboot. That's very annoying.

---

### Post by drama1981 on 2007-10-23
> **sdinh07 said:**
> i was also wondering if anyone here had a problem with their title bar. sometimes when i start ubuntu the title bar would be huge (1/5 of my screen height!!!) i thought it may be linked with this huge login screen font. it would usually go away after i log out and back in.

do you have an ati card? i had the same exact problem as well as huge fonts on login screen. 

 if you do have ati keep reading.


the latest xserver-xorg-ati driver is bugged. it simply doesnt work for some people. totally erases xorg.conf for others. some end up with overly bright screens (almost white). some others end up with crazy resolutions. my suggestion is either to downgrade it to an earlier version. i used the version from my fiesty install cd and it worked great. you can also use fglrx (from the restricted manager.) only if your card is supported though. 

if you use nvidia i can offer much help aside from maybe drop to a shell ctrl+alt+f2

do sudo dpkg-reconfigure xserver-xorg 

this will give you a new xorg.conf but its been reported to fix this issue for nvidia users.

---

### Post by GrantShoe on 2007-10-23
> **pashashome said:**
> Ok drvista's suggestion did work I needed to reboot like he said instead of just restart X.

Try this, seems to work for me. 

I managed to fix the problem ,
sudo gedit /etc/gdm/gdm.conf
find
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0

and change it into
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96

then restart ubuntu and it's fixed now
__________________



hmm... how do i get into the conf file for **k**ubuntu?  /etc/kdm/kdm.conf isn't there...

---

### Post by mohansoundar on 2007-10-27
> **pashashome said:**
> Ok drvista's suggestion did work I needed to reboot like he said instead of just restart X.

Try this, seems to work for me. 

I managed to fix the problem ,
sudo gedit /etc/gdm/gdm.conf
find
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0

and change it into
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96

then restart ubuntu and it's fixed now
__________________
However this didn't work for me :(
but setting DisplaySize property in Monitor section of  xorg.conf solved the title bar problem of mine.  

Still left out with the huge login page font size

---

### Post by nick_h on 2007-10-27
> hmm... how do i get into the conf file for kubuntu? /etc/kdm/kdm.conf isn't there...
Try /etc/kde3/kdm/kdmrc

---

### Post by nikhilsinha on 2007-11-03
I too had this problem on my Machine with a SIS Chipset.

The Method described by "pashashome" i.e.
Editing the file...
sudo gedit /etc/gdm/gdm.conf

Works perfectly!:)
Thanks a ton!:guitar:

---

### Post by nutz on 2007-11-07
I have a Toshiba A105-S4284 with the Intel GMA 950 video chipset and was also experiencing the huge font on the login screen in addition to the huge titlebar problem. The login screen was messed up on every boot but the huge title bar problem would only happen on 2 out of every 3 boot-ups.

I did what was sugested here and so far the problem seems to be fixed. The font size is correct on the login screen and I haven't experienced the huge title bar problem since the change either.

---

### Post by erixoltan on 2007-11-09
This works for me.  I have been trying to figure out how to solve this for weeks!!! thanks.

---

### Post by GrantShoe on 2007-11-11
> **nick_h said:**
> Try /etc/kde3/kdm/kdmrc

I found that file but the line 
[i][server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0[/i]

was no where to be found... :/

---

### Post by happyxix on 2007-11-13
I tried this. Although it works.. It crashes my compiz and I cannot enable it again afterwards. So I had to take it out again. Any other suggestions?

---

### Post by fenixphire07 on 2007-11-14
Ya, setting the dpi solves the problem in Ubuntu Gutsy Gibson

---

### Post by livinjean on 2007-11-21
> **GrantShoe said:**
> I found that file but the line 
[i][server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0[/i]

was no where to be found... :/

i am also using kubuntu 7.10 and stuck with the same issue, were you able to resolve this ?

---

### Post by peterthewolf on 2007-11-28
dpi 96 aslo solved my problem which was tiny font on login screen when using 32" LCD :)

---

### Post by millermobile on 2008-01-09
> **pashashome said:**
> Ok drvista's suggestion did work I needed to reboot like he said instead of just restart X.

Try this, seems to work for me. 

I managed to fix the problem ,
sudo gedit /etc/gdm/gdm.conf
find
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0

and change it into
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96

then restart ubuntu and it's fixed now
__________________



Good job, man!
I barely had to search and I found this!
I have to wonder how common the huge font problem is... that could be fairly deterring for people who are just trying Ubuntu for the first time.

---

### Post by jplegat on 2008-01-21
> **pashashome said:**
> Ok drvista's suggestion did work I needed to reboot like he said instead of just restart X.

Try this, seems to work for me. 

I managed to fix the problem ,
sudo gedit /etc/gdm/gdm.conf
find
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0

and change it into
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96

then restart ubuntu and it's fixed now
__________________

I confirm that it works perfectly, you just need to restart the system and not just X.
Thanks for the solution!

Cheers.

JP

---

### Post by kylcrow on 2008-02-01
I am experiencing this problem still. I have tried all suggestions, and still the fonts are very large. Any ideas?

---

### Post by nutz on 2008-02-01
Try this on the monitor section of your xorg.conf...


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
	Option  "DPMS"  "true"
        [B]Option "UseEdidDpi" "FALSE"
        Option "DPI" "100x100"[/B]
EndSection

The part in bold is what I am talking about, add it to your xorg.conf...But make sure you set it to the DPI you want.

---

### Post by n00rt on 2008-02-02
hi - i have the problem with huge fonts on login screen - and also in some applications such as beast and ardour - probably more - i tried the dpi setting but nothing changes there - am using gutsy ubuntu studio and have a intel mobile grapics card - any other suggestions?

---

### Post by n00rt on 2008-02-04
Ah ha - if the above techniques haven't worked for you you can try this

-small fonts on the GDM login window, you can do this:

   1. Open System->Administration->Login Window
   2. Select the 'Security' tab
   3. Click the 'Configure X-Server' button
   4. Append '-dpi 96' (without quotes) to the text in the 'Command' field
   5. Reboot the computer. 

this worked for me.

good luck

---

### Post by Salosalo on 2008-02-12
In kubuntuforums I fount the following advice, which worked for me:

I managed to solve this problem by adding -dpi 100 argument to X in kdmrc
(to be clear - this is in /etc/kde3/kdm/kdmrc)
(ServerCmd=/usr/bin/X -br -dpi 100). This drove me crazy btw. Details:
[http://kubuntuforums.net/forums/index.php?topic=3087975.0](http://kubuntuforums.net/forums/index.php?topic=3087975.0)

---

### Post by m3alnemer on 2008-03-05
> **pashashome said:**
> Ok drvista's suggestion did work I needed to reboot like he said instead of just restart X.

Try this, seems to work for me. 

I managed to fix the problem ,
sudo gedit /etc/gdm/gdm.conf
find
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0

and change it into
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96

then restart ubuntu and it's fixed now
__________________

This worked for me, but had to restart the compuer (Alt+Ctrl+Del   then Restart). (Alt+Ctrl+BackSpace) will NOT work

Thanks

---

### Post by Martym on 2008-03-08
> **n00rt said:**
> Ah ha - if the above techniques haven't worked for you you can try this

-small fonts on the GDM login window, you can do this:

   1. Open System->Administration->Login Window
   2. Select the 'Security' tab
   3. Click the 'Configure X-Server' button
   4. Append '-dpi 96' (without quotes) to the text in the 'Command' field
   5. Reboot the computer. 

this worked for me.

good luck

This is the one, after trying all the other solutions, that worked for me, Thank you.

---

### Post by learning on 2008-04-26
Finally found a fix!  Thanks n00rt!

---

### Post by RyanVanDiemen on 2008-05-27
Hi guys, I had the same issue in Ubuntu and new about this fix from some other post. However, my problem is now similar but still a bit different. I`d like to try new KDE 4 in Kubuntu, but because of this huuuge font issue, I can`t even start my installation. Obviously, I can`t even edit any kdmrc file before the system is installed. How can I give this dpi information to kubuntu before installation, so I can install the system? I`m already back with SuSe because of this issue but still missing ubuntu/kubuntu...and if solved I`d give it a shot...

---

### Post by spimby on 2008-07-08
This must be a big problem, as I've done two installation where this has happened. 

* Desktop upgrade from 7.10 to 8.04, suddenlty login window font is HUGE
* Laptop install to 8.04 login window font is huge

Funny thing is, I fixed the desktop and forgot what the fix was.  I'm pretty sure it DID NOT involve editing the /etc/gdm/gdm.conf  file. I coulld have sworn it had to do with running **dpkg-reconfigure xserver-xorg**

---

### Post by james_vanb on 2008-07-08
Don't know if this has been suggested.  Too lazy to read through entire thread.  Have had this issue a couple of times.  Edit xorg.conf.  Under "Screen"  you should find a line for "Modes".  The Login Screen picks up the first resolution listed.

```
sudo gedit /etc/X11/xorg.conf
```

After "Modes" - Find the resolution you want and copy and paste to the beginning of the line.

Replace gedit with whatever your default text editor is.

---

