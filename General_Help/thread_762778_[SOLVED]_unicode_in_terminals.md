---
title: "[SOLVED] unicode in terminals"
date: 2008-04-22
forum: General Help
---

### Post by chochem on 2008-04-22
I recently installed hardy from scratch with an alternate install, opting not to install any 'desktop' package but installing X and a DE myself (the basics being: sudo apt-get install xorg xfce4 slim). 

Now, the problem is this: In xfce4-terminal and xterm I cannot enter any non-ascii characters, such as æøå. I setup my keyboard with some X configuration utility and it is recognised as a Danish keyboard - I can enter any characters I want in any X app, I've tried, *as well as any of the text terminals (Ctrl+Alt+F1-6)*. When I try in xfce4-terminal or xterm, I either get question marks (xfce4-terminal) or just nothing (xterm). 

I'm a bit nonplussed about this one. Is it just a coincidence that it's two terminals that have this problem? Or do they rely on the same things? That nothing else (have tested: text terminals, mousepad, medit, thunar, firefox, opera, openoffice writer, ...) seems to require?

---

### Post by gsmanners on 2008-04-22
I'm not sure about xfce4-terminal, but xterm needs the -u8 option to handle UTF8.

---

### Post by chochem on 2008-04-22
Thanks. I hit alt-f2 and started xterm by the command: 'xterm -u8' but it still doesn't respond to æøå...

---

### Post by chochem on 2008-05-20
a few thins I have discovered: 

First, it stems from installing from scratch, that much is certain, as I have since used the same method to install openbox and the same problem occurs. 

Secondly, the problem is universal for all terminals with the exception of 'uxterm' which as far as I can tell is consistently right. rxvt-unicode which might be supposed to act likewise simply ignores my repeated hammering on the keys.

Thirdly, my best guess is that it's matter of encoding, not of keyboard setup, not least because of uxterm, but also since most other national/European peculiarities about my keyboard are picked up on (where the commas, quote marks, parentheses etc. are placed). It's only non-ascii characters that are misrepresented: ½§æøå. These are either 'approximated', as by roxterm which converts ½ into 1/2 and æ into ae (when encoding is set to UTF-8) or just ignored (xterm, rxvt-unicode, aterm, Eterm, roxterm with encoding set to ISO-8859-1)

Finally, I think it's an X thing, since it's present only in X (as I said, not on the other terminals) and in X from the moment I get the Login screen (SLIM display manager - the only non-terminal app where it's also present).

Most infuriating of all, is that I have got it to work, I just don't know what I did and when I logged in again it was gone. Which I suppose suggests that it's a faulty setting not a missing dependency.

---

### Post by chochem on 2008-05-21
a oneway-conversation this is proving to be... running some obscure old utf8-migration tool told me something about my locale settings. Getting a bit more information, running the program 'locale':

```
LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

```

None of these settings seem particularly relevant but comparing to the example in [this thread]("http://ubuntuforums.org/showthread.php?t=6394") the system has just not been configured properly. However the web is very scant on information about how to actually set you xorg locale... Any help?

---

### Post by bingoUV on 2008-05-21
> **chochem said:**
> a few thins I have discovered: 

Finally, I think it's an X thing, since it's present only in X (as I said, not on the other terminals) and in X from the moment I get the Login screen (SLIM display manager - the only non-terminal app where it's also present).



But gedit, firefox etc are known to accept non ascii characters even though they run in X. Did you mean something else?

---

### Post by chochem on 2008-05-21
> **bingoUV said:**
> But gedit, firefox etc are known to accept non ascii characters even though they run in X. Did you mean something else?

well that's what I'm saying, right? That most apps work fine, just not terminals....

at any rate, I think I have found part of the answer, well at least the root cause: setting the following two parameters will get terminals started from within that shell to work correctly:

 export LC_CTYPE=en_DK.UTF-8
 export LANG=en_DK.UTF-8

running 'locale charmap' before gave some weird ANSI value - now I get UTF8.

The only problem is where to put it so it will actually be a systemwide setting, not limited to one shell....

EDIT: Put them into my openbox startup file (autostart.sh). This is obviously a hack of sorts - there must be some /etc/ config file where it more properly belongs, but it works.

---

### Post by aimpau on 2008-05-25
get rxvt-unicode


```

sudo apt-get rxvt-unicode

```

Faster, slimmer and can have the pseudotransparency.

[edit[
Ooops. You already are using that. I'll try and research more.

---

### Post by koenn on 2008-05-25
> **chochem said:**
> 
at any rate, I think I have found part of the answer, well at least the root cause: setting the following two parameters will get terminals started from within that shell to work correctly:

 export LC_CTYPE=en_DK.UTF-8
 export LANG=en_DK.UTF-8


your 'locales' is probably not installed, or not configured right. Maybe 'dpkg-reconfigure locales' helps

---

### Post by gatewayasteroid on 2008-06-15
> **chochem said:**
> I recently installed hardy from scratch with an alternate install, opting not to install any 'desktop' package but installing X and a DE myself (the basics being: sudo apt-get install xorg xfce4 slim). 

Now, the problem is this: In xfce4-terminal and xterm I cannot enter any non-ascii characters, such as æøå. I setup my keyboard with some X configuration utility and it is recognised as a Danish keyboard - I can enter any characters I want in any X app, I've tried, *as well as any of the text terminals (Ctrl+Alt+F1-6)*. When I try in xfce4-terminal or xterm, I either get question marks (xfce4-terminal) or just nothing (xterm). 

I'm a bit nonplussed about this one. Is it just a coincidence that it's two terminals that have this problem? Or do they rely on the same things? That nothing else (have tested: text terminals, mousepad, medit, thunar, firefox, opera, openoffice writer, ...) seems to require?

I had the same...I played a little bit and found that it was the display manager! KDM worked great (assuming that you add "LANG=en_US.UTF-8" or whatever to your "/etc/environment").

---

### Post by chochem on 2008-06-16
> **gatewayasteroid said:**
> I had the same...I played a little bit and found that it was the display manager! KDM worked great (assuming that you add "LANG=en_US.UTF-8" or whatever to your "/etc/environment").

That does sound odd - can't see the connection - but maybe you're right. What dm did you use before? I've got Slim.

---

### Post by gatewayasteroid on 2008-06-20
> **chochem said:**
> That does sound odd - can't see the connection - but maybe you're right. What dm did you use before? I've got Slim.

Trust me :) it's a known SLIM bug, see for example here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=441630](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=441630)

I had a "bare" XFCE desktop with SLIM as display manager.

---

### Post by chochem on 2008-06-20
Cool, thanks for letting me know, gatewayasteroid. It's always nice to know that you're not the only one with the problem. 

I guess then that my hack is the right solution (at least apart from scrapping slim) since the only thing that comes after slim is the openbox autostart file.

Setting this as solved....

---

### Post by gatewayasteroid on 2008-06-22
> **chochem said:**
> Cool, thanks for letting me know, gatewayasteroid. It's always nice to know that you're not the only one with the problem. 

I guess then that my hack is the right solution (at least apart from scrapping slim) since the only thing that comes after slim is the openbox autostart file.

Setting this as solved....

Thanks to you for your openbox hack hint! I'm planning to go back again to openbox, XFCE seems too much for me LOL

---

