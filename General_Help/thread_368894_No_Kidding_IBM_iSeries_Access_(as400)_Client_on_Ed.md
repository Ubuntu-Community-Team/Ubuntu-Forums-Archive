---
title: "No Kidding IBM iSeries Access (as400) Client on Edgy"
date: 2007-02-23
forum: General Help
---

### Post by n8bounds on 2007-02-23
UPDATED 080412
I made a deb!

[http://ngbnet.homelinux.com/repository/unrestricted/linux/ibm5250/iseriesaccess_5.4.0-2.4_i386.deb](http://ngbnet.homelinux.com/repository/unrestricted/linux/ibm5250/iseriesaccess_5.4.0-2.4_i386.deb)

===========================================================


This are my notes for installing IBM iSeries Client Access Emulator for Linux on Ubuntu 6.10 Edgy.

I have successfully done this on four machines, one was a few minute old install, two more had edgy installed on them three months ago and have been in constant use since then and another had edgy freshly installed just a few days ago.  This is bound to work for you!

**Be sure to add universe and multiverse repos and update aptitude first..**

Go here and get the RPM from IBM:

[http://www-03.ibm.com/servers/eserver/iseries/access/linux](http://www-03.ibm.com/servers/eserver/iseries/access/linux)

This link may break with time, but its more direct:

[http://www-03.ibm.com/servers/eserver/iseries/access/linux/downloads.html](http://www-03.ibm.com/servers/eserver/iseries/access/linux/downloads.html)


Make it easy on yourself and save it to your home folder, not your desktop...


Then open a terminal and do a 
```

sudo /bin/bash

```

..to become root for a minute (it will ask you for your passwd)


DO THESE COMMANDS ONE AT A TIME AS ROOT

Warning, the first one takes FOREVER....

```

apt-get install msttcorefonts -y



fc-cache -f -v



apt-get install libmotif3 libxaw6 libstdc++5 alien -y



alien -i iSeriesAccess-5.4.0-1.0.i386.rpm -cv

```

Please note the last command (alien.....) might require editing as your downloaded version may be different than mine.  I'd offer you the rpm I used, but that's probably against some EULA.  It's also too large to be allowed as an attachment here.   PM me if you get lost...

Then type **exit** or close the terminal and open a new one.  (The point is to NOT be root any more.)  Now, being certain that you are NOT root, say this in a terminal:


```

xset fp

```


Remember this command.  If you reboot after changing things and you can't get Client Access to work (after it once worked properly), running this little command again will likely fix everything.

Just to test things, put this in a terminal to run the iSeries Client Access Emulator for Linux.
```

ibm5250 192.168.1.1 -geometry 9999x9999+0+0 -title LinuxCanWorkTheFourHundred -DISPLAY_NAME "PCNAMEA PCNAMEB PCNAMEC" -LANGID en_US

```

Replace the ipaddress above with the address of your eServer/as400.  You may change the PCNAME... bits to reflect the device naming scheme of your iSeries system.  Adding more than one lets you run the same command and automagically create multiple sessions.  The bit about the geometry in there is an ugly way to fix a wide screen problem...it does not actually draw the window that big, but it refuses to shrink if you leave it as is.  Experiment with the args to find your own solution.  The LANGID part is important.  If you don't have the english/U.S. version installed, I'm not sure what you should do here.  The TITLE is a local window setting and can be changed to your preference.

For more tips, the book was located here as of this posting:

[http://publib.boulder.ibm.com/infocenter/iseries/v5r4/topic/rzatv/rzatv.pdf](http://publib.boulder.ibm.com/infocenter/iseries/v5r4/topic/rzatv/rzatv.pdf)

..which I got from here:

[http://publib.boulder.ibm.com/infocenter/iseries/v5r4/index.jsp?topic=/rzatv/rzatvkickoff.htm](http://publib.boulder.ibm.com/infocenter/iseries/v5r4/index.jsp?topic=/rzatv/rzatvkickoff.htm)

The next logical step would be to add a launcher to the gnome menu using alacarte or something.  If you got this far, I'm sure you can figure that part out.

Cheers!

---

### Post by n8bounds on 2007-02-23
If anyone knows how to fix any of this in a more elegant way, please say so...I feel like some of this is ugly...

---

### Post by ColdBeer on 2007-02-26
> **n8bounds said:**
> If anyone knows how to fix any of this in a more elegant way, please say so...I feel like some of this is ugly...

Well, thank you very much for your note!!!

Now, it works withouth restarting gdm every day ;-)

I have a bash script to start "setup5250" and launch from it the different terminals:

```
#!/bin/sh
xset fp
LANG="es_ES.ISO-8859-1"
setup5250 -LANGID es_ES
```

Which seems to work right for my non-english language ;-) even my version is:

iSeriesAccess-5.4.0-1.2.i386.rpm

I'm still looking for a way to 'debianize' this work and make a deb to automatize everything for everyone.

---

### Post by n8bounds on 2007-02-26
Okay, a friend of mine noticed that the fonts directories in the xorg.conf are screwed up.  Further evidence its not just us can be found here:

[http://ubuntuforums.org/showthread.php?p=2130191](http://ubuntuforums.org/showthread.php?p=2130191)

Edit your xorg.conf file and change:
FontPath "/usr/share/X11/fonts/misc"

to:
FontPath "/usr/share/fonts/X11/misc"

Repeat for all of the font paths, reboot, and you should never need to xset fp any more.

---

### Post by djearwig on 2007-03-02
Excellent!  This worked beautifully...  Thanks

---

### Post by Cono_Sce on 2007-03-08
Thanks for the notes, I got it to work on the first try, as for xset fp I haven't tied renaming the the font files yet, what I did, I put the command in the startup and works perfectly.

---

### Post by n8bounds on 2007-03-10
I'm glad to hear it.  Anyone tested this on Fiesty yet..?

---

### Post by joethenoob on 2007-03-22
I got all the way to the end and received the following error when I tried to test it.

5250: [ INFORMATIONAL ]: Build Date: September 2006 (1.2).
5250: [ ERROR ]: NSC0017: Xt Warning: Cannot convert string "-*-lucidatypewriter-medium-r-normal-*-14-*-100-100-m-*" to type FontSet.

Obviously its a font issue, but my noobness prevents me from figuring it out. Any suggestions anyone?

---

### Post by n8bounds on 2007-03-23
try saying ```
 xset fp 
``` in a terminal and/or fixing the font paths in your xorg config file --or-- use Feisty ;)

---

### Post by joethenoob on 2007-03-26
> **n8bounds said:**
> try saying ```
 xset fp 
``` in a terminal and/or fixing the font paths in your xorg config file --or-- use Feisty ;)

Thanks for the reply, but xset fp didn't work. I got the same error. Since I am a linux noob, I'm hesitant to move to the Feisty beta just for this client. I'm affraid it will create more questions than answers.

---

### Post by Red_October on 2007-04-03
I am new to ubuntu, and also need IBM's 5250 emulator.
I tried to run the first command of: apt-get install msttcorefonts -y and receive this error.
Can any help with this?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

---

### Post by ColdBeer on 2007-04-09
> **Red_October said:**
> E: Package msttcorefonts has no installation candidate
Check your /etc/apt/sources.list file, or activate every repositories (main, restricted, universe and multiverse) to find this package.

---

### Post by n8bounds on 2007-04-09
its in Multiverse
```

$ aptitude show msttcorefonts
Package: msttcorefonts
State: installed
Automatically installed: no
Version: 1.8ubuntu1
Priority: optional
Section: multiverse/x11
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 213k
Depends: wget (>= 1.9.1-4), cabextract, xfonts-utils, debconf (>= 1.2.0) |
         debconf-2.0, defoma
Recommends: x-ttcidfont-conf
Description: Installer for Microsoft TrueType core fonts
 This package allows for easy installation of the Microsoft True Type Core Fonts
 for the Web including: 
 
  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings
 
 You will need an Internet connection to download these fonts if you don't
 already have them.

```

---

### Post by StarkD on 2007-04-11
Thanks! This works great!

But the text is enormous. How can I make it smaller?

Oh, I just found font size in the options menu ;)


What is the difference between this ibm5250 and the tn5250?

---

### Post by n8bounds on 2007-04-13
the ibm5250 is proprietary stuff from IBM, and the tn5250 is free (see sourceforge page)

[http://tn5250.sourceforge.net/](http://tn5250.sourceforge.net/)

---

### Post by n8bounds on 2007-04-13
You made me curious about tn5250

Here are my notes:
STEP ONE:  Read this PDF:

[http://www.chowhouse.com/~james/tn5250-HOWTO.pdf](http://www.chowhouse.com/~james/tn5250-HOWTO.pdf)



STEP TWO:  Here are my notes, take them for what they are:

sudo aptitude install tn5250 -y

an example:

xt5250 env.DEVNAME=ubuntua env.TERM=IBM-3477-FC 10.0.0.1



(no thats not a typo, the "xt" is intentional) or just make a file in your home folder called 

  .tn5250rc

and put something like this in it:

sessionA {
    host = 10.0.0.1
    env.DEVNAME=ubuntua
    env.TERM=IBM-3477-FC
}

sessionB {
    host = 10.0.0.1
    env.DEVNAME=ubuntub
    env.TERM=IBM-3477-FC
}

and then just say (in a terminal or an ALT+F2 prompt)

xt5250 sessionA


Side notes:
You can even add autologin to your configs with variables like these:
env.USER = MYUSER
env.IBMSUBSPW = MYPASSWORD

KEYMAP:

You can change your keymap, but its not so simple that you will feel unchallenged by the efforts, see section five of:  [http://www.chowhouse.com/~james/tn5250-HOWTO.pdf](http://www.chowhouse.com/~james/tn5250-HOWTO.pdf)

 Keyboard Mapping
       The following table lists the 5250 functions implemented by tn5250, and  the  corresponding  key&#8208;presses.   Keys  are  represented as Emacs does: C-a means hold Ctrl and press A, M-a means press Esc or C-g followed by A, and C-M-a means press Esc or C-g followed by C-a.  Most setups also let you use the Alt or Meta key for M- keypresses.

       Function     Keypress
       ----------------------------------------
       F1 - F10     f1 to f10, M-1 to M-
       F11          f11 [1], M--
       F12          f12 [1], M-=
       F13 - F24    f13 to f24 [1], M-! to M-+
       Enter        return, enter, C-j, C-m
       Left         left
       Right        right
       Up           up
       Down         down
       Roll Up      next, pagedown, C-d, C-f
       Roll Down    prev, pageup, C-b, C-u
       Backspace    backspace [1]
       Home         home, C-o
       End          end
       Insert       insert, M-i, M-delete
       Delete       delete [1]
       Reset        C-r, M-r
       Print        C-p, M-p
       Help         M-h
       SysReq       C-c, M-s
       Clear        M-c
       FieldExit    C-k, M-x
       TestReq      C-t
       Toggle       M-t

       Erase        C-e
       Attn         C-a, M-a
       Dup          M-d
       Field+       C-x, + [2]
       Field-       M-m, - [2]
       NewLine      C-M-j
       Next Field   tab, C-i
       Prev Field   backtab [1]
       ----------------------------------------
       Refresh      C-l, M-l
       Quit         C-q

       1. Which keys generate f11-f24, backtab, backspace and delete is very dependent on the configuration of the terminal.
       2. + and - only work as Field+ and Field- in signed numeric fields.


Again, see section 5 of the PDF available via link from this page:  [http://www.chowhouse.com/~james/tn5250-HOWTO.pdf](http://www.chowhouse.com/~james/tn5250-HOWTO.pdf)

You can also apparently fool with the fonts--as in make the window bigger--(see section 6) although I never got very far with that...


See also:
[http://tn5250.sourceforge.net/](http://tn5250.sourceforge.net/)

don't forget to RTFM

---

### Post by Bill Van Dusen on 2007-05-18
I'm getting the same error with Feisty Fawn (7.04)

bvd

---

### Post by n8bounds on 2007-05-18
which is that?

---

### Post by Bill Van Dusen on 2007-05-22
Sorry for the long delay.

I'm getting the font error when attempting to start IBM5250.  I have Feisty Fawn.

Here's the log ...

vandusen@vandusen-desktop:~$ ibm5250
5250: [ INFORMATIONAL ]: Build Date: September 2006 (1.2).
5250: [ ERROR ]: NSC0017: Xt Warning: Cannot convert string "-*-lucidatypewriter-medium-r-normal-*-14-*-100-100-m-*" to type FontSet.
vandusen@vandusen-desktop:~$ 


bvd

---

### Post by n8bounds on 2007-05-22
hey, np

are you sure your msttcorefonts installed properly?

have you done a 

fc-cache -fv

since then too?

---

### Post by Bill Van Dusen on 2007-05-23
here's what i get when rerunning the msttcorefonts install ...

vandusen@vandusen-desktop:~$ sudo apt-get install msttcorefonts -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

when i run fc-cache -fv it says 

.
.
.
/var/lib/defoma/fontconfig.d/j: caching, 1 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/m: caching, 4 fonts, 0 dirs
/var/lib/defoma/fontconfig.d/u: caching, 1 fonts, 0 dirs
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/vandusen/.fontconfig: cleaning cache directory
fc-cache: succeeded

---

### Post by Bill Van Dusen on 2007-05-23
n8bounds,

I got it!  I wasn't putting the -LANGID en_US at the end.

Thanks for your postings.  Raw recruits like me would be totally lost if it wasn't for people like you.

thanks
bvd

---

### Post by n8bounds on 2007-05-24
Glad you made it!  If I can help in any way at all, feel free to PM/IM me! :)

 I see vmware server made it into the commercial repo, I wonder what he have to do to request that they work with IBM to get this in there also....  sudo aptitude install ibm5250 would be SO much nicer, wouldn't it?

---

### Post by rstewartmailacct on 2007-05-27
Works like a champ on Feisty!  Thanks for the work.!

---

### Post by n8bounds on 2007-05-27
Excellent!  By the way, I never had that font problem once I upgraded to Feisty.  They must have accidentally fixed the font paths in the xorg.conf when they made 7.04.  :)

Oh, and for another alternative, besides xt5250, I've used this once I had java installed.  The neat thing is, it puts multiple sessions into TABS!

[http://tn5250j.sourceforge.net/](http://tn5250j.sourceforge.net/)

---

### Post by Ken Gingrich on 2007-06-06
I'm new to Linux and truing to install iSeries for Linux on Feisty.  When I type in the command below nothing happens.

ibm5250 192.168.1.1 -geometry 9999x9999+0+0 -title LinuxCanWorkTheFourHundred -DISPLAY_NAME 

When I run setup5205 i get the following error "Xt Warning: local not supported by C Library, local unchanged." and on the next line
"Xt Warning: Missing charsets in String in String to Fontset conversion
Segmentation fault (core dumbed)

Any suggestion on what to do next?

---

### Post by n8bounds on 2007-06-07
Try (all on one line)

ibm5250 192.168.1.1 -geometry 9999x9999+0+0 -title LinuxCanWorkTheFourHundred -DISPLAY_NAME "PCNAMEA PCNAMEB PCNAMEC" -LANGID en_US

Change 192.168.1.1 to whatever the hostname or ipaddress of your as400 is

Change LinuxCanWorkTheFourHundred to whatever you want

Change PCNAMEA and PCNAMEB to whatever you want, it has to be all caps and if you want more than one, they have to be different, certain device naming schemes may be enforced by your as400 system administrator, look to your windows client for hints...or just ask him/her.

The "-geometry 9999x9999+0+0" part is purely optional, actually so is the title I think

SO, lets say your as400 lives at 192.168.250.25 and you are supposed to name your session devices something like a123b45 with a letter at the end for each session...you could say:


ibm5250 192.168.250.25 -title iSeries -DISPLAY_NAME "A123B45A A123B45B" -LANGID en_US

..in a terminal


I don't know about the setup thing, you probably don't need it in your case, but I can't get it to work on feisty...worked fine on edgy...i swear........

---

### Post by Ken Gingrich on 2007-06-08
Thank you, the revised command worked fine.  I used setup5250 on a Xandros installation to open and configure an AS400 session.

---

### Post by Robertobg on 2007-08-03
Good morning,
i'm a newbie in ubuntu world and i installed the "iseries for linux pack" as i read in this thread but when i try to execute the command:

ibm5250 192.168.0.240 

i obtain the error:

-bash :: ibm5250: command not found

even if i execute the command from 

/opt/ibm/iSeries/bin

What can i try to do?

Thanks and best regards.

Roberto

---

### Post by ColdBeer on 2007-08-06
Please, execute:

```
youruser@yourpc:~$ /opt/ibm/iSeriesAccess/bin/ibm5250
```

Perhaps it works... and, another option:

```
youruser@yourpc:~$ cd /opt/ibm/iSeriesAccess/bin
youruser@yourpc:/opt/ibm/iSeriesAccess/bin$ ./ibm5250
```

---

### Post by Robertobg on 2007-08-06
I tryed many times but i receive the error:

cannot load shared libraries ...  libcwbcore.so ......  (this is not the exact message)

so i ind these commands on the IBM site:

# ln -sf /opt/ibm/iSeriesAccess/lib/libcwbcore.so /usr/lib/libcwbcore.so
# ln -sf /opt/ibm/iSeriesAccess/lib/libcwbrc.so /usr/lib/libcwbrc.so
# ln -sf /opt/ibm/iSeriesAccess/lib/libcwbxda.so /usr/lib/libcwbxda.so
# ln -sf /opt/ibm/iSeriesAccess/bin/ibm5250 /usr/bin/ibm5250
# ln -sf /opt/ibm/iSeriesAccess/bin/setup5250 /usr/bin/setup5250
# ln -sfn /opt/ibm/iSeriesAccess/mri/en /opt/ibm/iSeriesAccess/mri/en_US
# ln -sfn /opt/ibm/iSeriesAccess/mri/zh_HK /opt/ibm/iSeriesAccess/mri/zh_TW

Also, Ubuntu does not include en_US locale by default, just include en_US.utf8, but the emulator requires en_US to exist. So please execute this as root:

# locale-gen en_US

but now i obtain the error:

Error: Can't open display.

I do all my test in the command screen (ctrl+alt+F1) because when i try to open a terminal window, ubuntu reboot (every time).
The same thing happen when i execute the command "xterm": the pc reboot!!

Help please.

Thanks.
Roberto

---

### Post by ColdBeer on 2007-08-06
> **Robertobg said:**
> I tryed many times but i receive the error:

cannot load shared libraries ...  libcwbcore.so ......  (this is not the exact message)

so i ind these commands on the IBM site:

# ln -sf /opt/ibm/iSeriesAccess/lib/libcwbcore.so /usr/lib/libcwbcore.so
...
# ln -sfn /opt/ibm/iSeriesAccess/mri/zh_HK /opt/ibm/iSeriesAccess/mri/zh_TW

Also, Ubuntu does not include en_US locale by default, just include en_US.utf8, but the emulator requires en_US to exist. So please execute this as root:

# locale-gen en_US

but now i obtain the error:

Error: Can't open display.

I do all my test in the command screen (ctrl+alt+F1) because when i try to open a terminal window, ubuntu reboot (every time).

Yes, you need to link those libraries, perhaps (because you don't need to link language libraries):

```
sudo ln -s /opt(ibm/iSeriesAccess/lib/*.so /usr/lib
sudo ln -s /opt/ibm/iSeriesAccess/bin/* /usr/bin
```

But you need to launch ibm5250 from the window manager (gnome or kde) because it's an X application. You don't need to generate your locales again. You need to set the right locale to the ibm5250 environment I use a little script to launch setup5250 -where I manage every connections-:

```
#! /bin/sh
export LANG="es_ES.ISO-8859-1"
setup5250 -LANGID es_ES
```

I think this could help you.

---

### Post by Robertobg on 2007-08-06
Thanks Coldbeer,
i try to run the command from the window manager and after many time, the "new 5250 session" window appear (many time!) but when i input address, user-id and password and connect i receive an error:

CWBLM0011  An internal license error has occured, rc=6211

and the ibm site, for this error, says:

[I]CWBLM0011 

Cause
Internal application error.

Recovery
The application software is in error. Make sure you have applied the latest code levels.[/I]

I think i'll never use the ibm5250 emulation software  because i obtain one error for each command i try!!

Thanks and have a nice day.

Roberto

---

### Post by ColdBeer on 2007-08-06
> **Robertobg said:**
> CWBLM0011  An internal license error has occured, rc=6211

and the ibm site, for this error, says:

[I]CWBLM0011 

Cause
Internal application error.

Recovery
The application software is in error. Make sure you have applied the latest code levels.[/I]

I think i'll never use the ibm5250 emulation software  because i obtain one error for each command i try!!

Mmmmm.... I think this is an error at your iSeries, not at the terminal emulation program.

It seems your license program is not right. Perhaps your OS400 version, or your Client Access level number... perhaps you are not writing a session ID specified in any subsystem...

I'm not an iSeries administrator, so it seems to be a good idea to ask yours.

Tell us what is your ending point. Best regards.

---

### Post by darknuala on 2007-08-28
I have done the install, and everything went great!  I do have another question however.  Is there a way to do data transfers from the AS/400???  I have not seen anything regarding the capability to do this.

---

### Post by ColdBeer on 2007-08-29
Yes: FTP, HTTP, ODBC... ;-)

---

### Post by n8bounds on 2007-08-30
> **ColdBeer said:**
> Yes: FTP, HTTP, ODBC... ;-)

LOL, I think the question was regarding the DTF (direct file transfer) feature of CA Navigator or whatever that thing is called in Windoze.  I don't think there is a direct analogue of that feater in yvahk...sorry.

---

### Post by warped6 on 2007-09-12
I'm trying to get this to work in 64bit Feisty and am getting the dreaded...
"ibm5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory" error.

I had to do a "force-architecture" when I did the install of the .deb because of the X86-64 vs i386 but everything seemed to go alright. I do have all of the packages mentioned above (at the beginning of this thread) installed.

Any ideas? :confused:

Mike

---

### Post by ColdBeer on 2007-09-13
I think the libraries (as libXm.so.3)  in the rpm package are binaries compiled for i386 arquitecture, so probably you will have problems trying to run them in yolur x64.

Did you think to use [chrooted tecnique]("http://ubuntuforums.org/showthread.php?t=24575") to run it in a 32bit environment?

---

### Post by warped6 on 2007-09-13
No I haven't tried that yet.

Relatively new to Ubuntu/Linux especially the 64 bit version so I didn't know about it.

I'll give it a shot.
Thanks.

---

### Post by dmfatur on 2007-09-25
I am new at using Ubuntu.  On the Second Paragraph of your message you say 

"Be Sure to add universe and multiverse repos and update aptitude first"

What is this and how do I do it?

thanks

Diego

---

### Post by ColdBeer on 2007-09-26
At **[Ubuntu Documentation]("https://help.ubuntu.com/7.04/")** you could find basic rules about Ubuntu.

---

### Post by elvisd on 2007-11-02
Hi all.
I have fresh installed my system with gutsy (7.04) and the procedure works fine.
The client access works without problems.

Kindly 
elvisd

---

### Post by n8bounds on 2007-11-04
Excellent!  Glad to hear that.  I've been using tn5250 (xt5250) for some time now instead.  It's so much easier to install, and once you get used to it, its just as useful.

---

### Post by mastro on 2007-11-23
I've been requested by a guy in my lug (who is not registered here) to reply at this thread..
below his reply.

--begin--

sincerely i find this thread a little overwhelming....
the iaccess ibm package, if not _really_ needed, it's a bit ugly and a 
little uncomfortable to setup.

i personally use tn5250 or xt5250, which i think it's the lightest 
program to do that, and a lot customizable and it's already deb packaged.

anyway, on client pc's, i usually install tn5250j (tn5250j.sf.net), 
which only depends on java runtime, and has a very nice installer.
then you can configure the session, the keymap, the colours, the fonts, 
and so on, easily, via a very nice done GUI.
i really advise using that one.
the tn5250 if you are stronger-hearted

--end--

---

### Post by n8bounds on 2007-11-25
No doubt, thats a perfectly fine solution.  Maybe you can tell me something....... do you know how to make the font in xt5250 bigger?

---

### Post by n8bounds on 2008-04-12
I made a deb!

[http://ngbnet.homelinux.com/repository/unrestricted/linux/ibm5250/iseriesaccess_5.4.0-2.4_i386.deb](http://ngbnet.homelinux.com/repository/unrestricted/linux/ibm5250/iseriesaccess_5.4.0-2.4_i386.deb)

---

### Post by simplysimple on 2008-05-19
not sure why there is a duplicate of this topic but wanted to share my experience installing iSeries from the RPM on 8.04....i posted the following in the other topic:

followed the instructions to install the rpm on 8.04(32bit) the only difference was the version which was iSeriesAccess-5.4.0-1.**6**.i386.rpm

worked like a charm...i used 'setup5250' in the terminal to configure everything and then created a launcher to run 'ibm5250' for convenience.

thanks for the guide!!

---

### Post by elvisd on 2008-06-11
> **n8bounds said:**
> No doubt, thats a perfectly fine solution.  Maybe you can tell me something....... do you know how to make the font in xt5250 bigger?

[http://archive.midrange.com/linux5250/200108/msg00016.html](http://archive.midrange.com/linux5250/200108/msg00016.html)

---

### Post by n8bounds on 2008-06-15
Perfect, thanks!

---

