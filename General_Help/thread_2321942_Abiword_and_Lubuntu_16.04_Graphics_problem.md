---
title: "Abiword and Lubuntu 16.04 Graphics problem"
date: 2016-04-25
forum: General Help
---

### Post by Download_Descenden on 2016-04-25
[COLOR=#000000]As soon as you open a file or actually type anything, I get this large, rolling and flickering greyscale chunk on the top section of the page irrespective of which page size you choose or minimised etc.[/COLOR]

[COLOR=#000000]This makes it pretty unusable.[/COLOR]


[COLOR=#000000]Didn't have this in 14.04[/COLOR]

---

### Post by tom-bellas3rd on 2016-04-25
Its a bug that wont go away. Its been like that for ages now. I at least had it in 14.04. as well as others if I look at the bug reports over time.

---

### Post by tom-bellas3rd on 2016-05-15
I just installed Lubuntu 16.04 today on an older machine and yes, I can confirm that this bug is still present. Anyone know a fix for it?

---

### Post by Jacques_Beckand on 2016-06-13
Same problem for me. Abiword 3.01 running on Lubuntu 16.04 
Didn't have that issue with Lubuntu 14.04

---

### Post by vasa1 on 2016-06-13
There's a ppa for abiword here: [https://launchpad.net/~dholbach/+archive/ubuntu/ppa](https://launchpad.net/~dholbach/+archive/ubuntu/ppa)

Unfortunately, the flickering is still there :(

---

### Post by vasa1 on 2016-06-20
And, FWIW, [[ubuntu/xenial-proposed] abiword 3.0.1-6ubuntu0.16.04.1 (Accepted)]("https://lists.ubuntu.com/archives/xenial-changes/2016-June/013570.html") though there's no mention of the graphics issue. Maybe it's just a Lubuntu thing and the devs use some other desktop environment?

---

### Post by jrrpnani on 2016-07-05
> **vasa1 said:**
> Maybe it's just a Lubuntu thing and the devs use some other desktop environment?
I have start session with Lxde desktop environment and the flicker issue does not happen. With Lubuntu desktop give me the graphic problem.:(

---

### Post by sudodus on 2016-07-05
> **jrrpnani said:**
> I have start session with Lxde desktop environment and the flicker issue does not happen. With Lubuntu desktop give me the graphic problem.:(

Interesting observation. I tried with a current (up to date) Lubuntu 16.04 LTS installed system.

Abiword flickers in a Lubuntu session.

But at the login screen I can also select Openbox (only the window manager, no fancy desktop environment).

Abiword does not flicker in an Openbox session.

The difference is very obvious and repeatable. I need not reboot, only log out, switch session (near the top right corner) and log into the other session.

---

### Post by vasa1 on 2016-07-05
> **sudodus said:**
> ...
Abiword does not flicker in an Openbox session.
...
I'm pretty sure it flickered for me! That was the one from the ppa. Which one did you use?

It still flickers in an Openbox session for me. The abiword I installed is from the software center:
```
07:25 AM ~ $ apt-cache policy abiword
abiword:
  Installed: 3.0.1-6ubuntu0.16.04.1
  Candidate: 3.0.1-6ubuntu0.16.04.1
  Version table:
 *** 3.0.1-6ubuntu0.16.04.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     3.0.1-6 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
07:25 AM ~ $ 
```

While the initial (blank) abiword screen didn't flicker, I used File > Open to load a text file and that's when the fun starts.

---

### Post by sudodus on 2016-07-06
I tried with a clean installed system with no tweaks, installed from "day before yesterday's" daily iso file of ***Lubuntu Xenial i386***,

```
$ ls -l xenial-desktop-i386.iso
-rw------- 1 nio nio 939524096 jul  4 16:40 xenial-desktop-i386.iso

$ md5sum xenial-desktop-i386.iso
b4a82ddc7cb34d8fce6e79e2be5c6dc9  xenial-desktop-i386.iso
```

***Edit: ***But we have different computers, which might make a difference in flickering too. I installed it into a Toshiba laptop according to this link

[http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

---

### Post by sudodus on 2016-07-06
I tried again with the current Lubuntu Xenial i386 iso file - installed into a small partition on an SSD connected via USB 3 (using my Toshiba). This computer uses Intel graphics (as described in the link in my previous post).

```
$ ls -l xenial-desktop-i386.iso
-rw------- 1 nio nio 897581056 jul  5 16:58 xenial-desktop-i386.iso
$ md5sum xenial-desktop-i386.iso
21e8fdd3a7f02d75f02d44501606d943  xenial-desktop-i386.iso
```

And I see the same thing with Abiword, flicker in the Lubuntu session, no flicker in the Openbox session. This is the case also after rebooting.

-o-

I booted from this SSD in another computer (with different graphics, this time a built-in nvidia chip in a computer from 2008:

[http://www.asus.com/Motherboards/M2NVM_DVI/](http://www.asus.com/Motherboards/M2NVM_DVI/)

and the same things happened: Abiword flickered in the Lubuntu session, but there was no flicker in the Openbox session.

---

### Post by sudodus on 2016-07-06
> **vasa1 said:**
> I'm pretty sure it flickered for me! That was the one from the ppa. Which one did you use?

It still flickers in an Openbox session for me. The abiword I installed is from the software center:
```
07:25 AM ~ $ apt-cache policy abiword
abiword:
  Installed: 3.0.1-6ubuntu0.16.04.1
  Candidate: 3.0.1-6ubuntu0.16.04.1
  Version table:
 *** 3.0.1-6ubuntu0.16.04.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     3.0.1-6 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
07:25 AM ~ $ 
```

While the initial (blank) abiword screen didn't flicker, I used File > Open to load a text file and that's when the fun starts.

Please try with a fresh installed Lubuntu system (installed from the current Lubuntu Xenial i386 iso file) :-)

Have you tweaked your Openbox session - is it the crude grey background without any bells and whistles, or have you added some panel or other enhancement? If you have tweaked it, maybe you can identify what may cause the flicker.

See also this link

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278)

Do you think it is about the same issue as we are discussing here?

---

### Post by vasa1 on 2016-07-06
> **sudodus said:**
> Please try with a fresh installed Lubuntu system (installed from the current Lubuntu Xenial i386 iso file) :-)
Sadly, I won't be able to oblige. This month is tax filing month :(

> **sudodus said:**
> Have you tweaked your Openbox session - is it the crude grey background without any bells and whistles, or have you added some panel or other enhancement? If you have tweaked it, maybe you can identify what may cause the flicker.
I have a very simple textual conky and tint2. The background is a tiny png file that covers the entire screen. Other than that, nothing else, not even a session manager

> **sudodus said:**
> See also this link

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278)

Do you think it is about the same issue as we are discussing here?
One of the guys over there kept going on about only the cursor flickering. I've made a video but I can't upload it because of a network issue with my ISP --- only downloads, no (=very,very slow) uploads. That shows a band of about 4 cm across the width of the page flickering. Very much like described in [https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278/comments/13](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278/comments/13)

BTW, I do not use the default Lubuntu gtk3 theme. I use a modified Greybird. I'll try other themes as well.

---

### Post by sudodus on 2016-07-06
> **vasa1 said:**
> Sadly, I won't be able to oblige. This month is tax filing month :(


No worries. Let us assume that my findings about a clean untweaked Openbox can be reproduced by other people.
> 
I have a very simple textual conky and tint2. The background is a tiny png file that covers the entire screen. Other than that, nothing else, not even a session manager

Maybe because of a change in Abiword, it can no longer cope with [one of] those tweaks (including your modified Greybird). Maybe it is caused by some change in the x window system.
> 
One of the guys over there kept going on about only the cursor flickering. I've made a video but I can't upload it because of a network issue with my ISP --- only downloads, no (=very,very slow) uploads. That shows a band of about 4 cm across the width of the page flickering. Very much like described in [https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278/comments/13](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278/comments/13)

BTW, I do not use the default Lubuntu gtk3 theme. I use a modified Greybird. I'll try other themes as well.

It is like that for me too: very much like described in [https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278/comments/13](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278/comments/13).

---

### Post by vasa1 on 2016-07-06
Okay, I've tested (all from with my Openbox Session) the following themes (unmodified by me in any way):
[LIST]
[*]Lubuntu-default
[*]Greybird and Numix (provided by the shimmer themes package)
[*]Ambiance and Radiance (provided by the light themes package)
[*]Adwaita which I think comes by default with any *buntu?
[/LIST]

```
GTK_THEME=Adwaita abiword ~/Dropbox/_MyMkd/cut.mkd
```

Of these, only Adwaita and Adwaita:dark were flicker-free. I went on to test them with a longish .odt file ... no complaints.

---

### Post by sudodus on 2016-07-06
Interesting result :-)

---

### Post by vasa1 on 2016-07-06
And the same results from a Lubuntu session.

FWIW,
the only terminal output looks like this:
```
04:00 PM ~ $ GTK_THEME=Adwaita abiword ~/Dropbox/_MyMkd/tips.odt
librdf warning [9&#65533; - Variable ev was bound but is unused in the query
04:01 PM ~ $ 
```

---

### Post by sudodus on 2016-07-06
***Another ultra-light alternative, where Abiword works in Xenial alias an Ubuntu 16.04 LTS based system:***

I installed a mini system with Fluxbox, xinit and xterm from the tarball

[X32-Txt-Startx-Intl_2016-06-29.tar.xz](http://phillw.net/isos/linux-tools/OBI/trusty/tarballs/X32-Txt-Startx-Intl_2016-06-29.tar.xz)

with the ***One Button Installer*** according to this link

[Tested and debugged system to install [Ubuntu flavours of] Xenial 32-bit alias 16.04 LTS](http://ubuntuforums.org/showthread.php?t=2172971&page=3&p=13511441#post13511441)

After booting into the installed system, I started Fluxbox with the ***startx menu entry***, right-clicked to start xterm, installed Abiword with

```
sudo apt-get install abiword
```

started Abiword and ran it without flickering issues. This way you can cherry-pick the application programs you want and tweak your system as you like, but avoid what makes Abiword flicker ;-)

-o-

Read more about the One Button Installer at this link

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by sudodus on 2016-07-06
vasa1,

I suggest that you share your findings at the bug report [https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1574278) :-)

---

### Post by sudodus on 2016-07-06
More test results, this time with Xubuntu Core: Abiword does not flicker with bands, but the cursor is invisible except when I move it, when it flickers :-P

Greybird is the default. I changed it to Adwaita, and the cursor improved to 'normal'. The rendering of marked text is rather bad, the text is rather dark on black background. But it works.

I think this result ties to the flickering of the cursor described in the bug report.

---

### Post by vasa1 on 2016-07-06
> **sudodus said:**
> ... I think this result ties to the flickering of the cursor described in the bug report.IIRC, there was a bug report that dealt with the massive flickering of the top part of the page rather than just the cursor. I'll see if I can dig that one up.

---

### Post by vasa1 on 2016-07-06
@sudodus, I saw your comment #18: in there, you wrote> For example the first one in the list, Clearlooks, works for me in a Toshiba laptop with Intel graphics from 2013,

Abiword currently is a gtk3 application:```
ldd /usr/bin/abiword | grep gtk-3
``` 

Clearlooks, at least the one that comes with Lubuntu, doesn't support gtk3. You can see that by running```
ls /usr/share/themes/Clearlooks

```There's no gtk3 folder there. I suspect when Clearlooks is selected, Adwaita is used as the "fallback" thereby giving the impression that Clearlooks works. I just checked this and I think my suspicion is true. You can try even with a non-existent theme. The system will still load Adwaita.

```
GTK_THEME=Moonpie abiword /usr/share/doc/abiword/copyright
```

Edit: passing reference to Adwaita being the fallback instead of Raleigh:> Adwaita is the user facing façade of GTK+. In the past GTK+ had no face; there was no properly defined look for the toolkit. Like many things in the FOSS world, it was a bring your own. There was Raleigh, a fallback skin that only showed up if something went sideways with theming or the system settings. And you didn’t really want to see that.Source: [https://blog.gtk.org/2016/06/22/adwaita/](https://blog.gtk.org/2016/06/22/adwaita/)

---

### Post by sudodus on 2016-07-07
I see. This is more complicated than I thought. Thanks for explaining, vasa1!

---

### Post by vasa1 on 2016-07-09
Hi Nio,

I just saw your post in the mailing list: [Abiword in Lubuntu 16.04 LTS - how to get rid of flickering]("https://lists.ubuntu.com/archives/lubuntu-devel/2016-July/000593.html") and the responses.

[You wrote]("https://lists.ubuntu.com/archives/lubuntu-devel/2016-July/000597.html"):> Hi Rafael, Simon and Julien,

What about switching the default theme for Lubuntu in 16.04.1 LTS so 
that it will come with a working Abiword? In other words to do the 
work-around instead of leaving it to the end user?

Or will that break some other functionality?

Best regards
Nio
A way to do what you want for just Abiword *without* switching Lubuntu's default theme, would be to edit its **Exec=** line in **/usr/share/applications/abiword.desktop** from```
Exec=abiword %U
```to```
Exec=bash -c 'GTK_THEME=Adwaita abiword %U'
```

---

### Post by jrrpnani on 2016-07-09
The solution works fine. But I encounter two problems. When you touch the menu bar first time, the default view mode jump from 'print mode' to 'normal mode', maybe still a bug in the program. And the second problem that I saw it's about selection color, that change to dark, like the font color. I hope this problems could be corrected soon. :P

---

