---
title: "Typing with scim in firefox"
date: 2007-08-17
forum: General Help
---

### Post by JcZndeR on 2007-08-17
is it just me or does firefox not like scim?  i did that scim-bridge thing and firefox runs fine.. but the ctrl-space thing doesnt work in firefox.. nor does clicking the icon on the toolbar... i can only type english.. scim inputs fine in programs like gedit and gaim, the terminal, etc... i had an install that worked once.. after i did a whole load of things. but i dont happen to remember what i did.. and now everytime i reinstall to type chinese in a webpage i have to type it somewhere else and then copy... now i type chinese more and more, its getting really annoying.. if someone could help with this, it would be awesome.
this has been bothering me for a while, thanks

---

### Post by JcZndeR on 2007-08-21
alright.. maybe nobody has this problem =P

---

### Post by Jiawen on 2007-08-29
I'm having the same problem. I've asked for help on the SCIM mailing list, but gotten none. I've also tried many different configurations of SCIM/Firefox but not gotten one that works. I'll let you know when I do.

---

### Post by OsakaWilson on 2007-09-28
Same problem here. One year and counting. The weird thing is, when I first installed Feisty, Japanese worked in Firefox, but only until I restarted it. After that, nothing.

---

### Post by Jiawen on 2007-10-05
I got a response, which was "Upgrade to Scim-1.4.7". Unfortunately, that's only available in Ubuntu 7.10. It's too bad they're unwilling to do bug fixes.

---

### Post by nanbudh on 2008-02-28
friend i have the same problem and i have tried on ubuntu7.10 as well as fluxbuntu7.10. And to make the matters more interesting there is nothing i could find on this topic on internet. Nothing! Strange. One thing is clear that it is a scim thing only cos i can type gurmukhi(from indic group, punjabi language) characters right into firefox on windows XP after enabling that language but it does not work on ubuntu. So its a scim thing not a  firefox thing. 
The surprising thing is that this problem should have been reported a lot by now. Only goes to prove how english has sidelined all other languages(at least in india).

---

### Post by shurufa on 2008-03-01
I finally have the solution to this very frustrating problem! (Please note that CJK input works out of the box with no problems on a CJK installation of ubuntu -- this problem only exists for people who use more than one language. That's not very good for encouraging multilingualism, is it...?)

Following the instructions in the SCIM documentation that everyone keeps citing here won't help at all.  As far as I can tell, these instructions have never worked. Editing /etc/X11/xinit/xinput.d/scim will do you no good whatsoever. The problem is with the "default" and locale files in that folder.

Basically what I did was I replaced the contents of the files  /etc/X11/xinit/xinput.d/scim,  /etc/X11/xinit/xinput.d/default, and  /etc/X11/xinit/xinput.d/none with the following:

```
#
# Use "X input Method" for all applications
#
# Per Ming's Documentation in SCIM, XIM Input Method is activated
# not only for old X-applications but also for GTK and QT appplication.
#
# If a user wish to use, GTK Input Method, (s)he can right-click input 
# area and select "Input Methods" and change from "X input Method" to 
# "SCIM Input Method".
#

XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
GTK_IM_MODULE=xim
QT_IM_MODULE=xim
DEPENDS="scim,scim-anthy|scim-canna|scim-chewing|scim-pinyin|scim-hangle|scim-prime|scim-skk|scim-tables-additional|scim-m17n|scim-uim|scim-tables-ja|scim-tables-ko|scim-tables-zh"

```

This is exactly what the default Chinese installation has in  /etc/X11/xinit/xinput.d/scim. You'll have to open nautilus as root (Alt+F2 then "gksu nautilus") to make these changes.

There are a bunch of files in that folder with different locale names like zh_CN and zh_TW. Make a copy of the "default" file above and name it with your current locale (like en_GB or fr_FR or whatever).

Make backup copies of these files before replacing them if you want. EDIT: You also have to edit/create the file ~/.scim/global and add the line "/SupportedUnicodeLocales =" followed by your locale. So if you want scim to work in en_US and en_GB locales, you add this line to the file:

```
/SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8
```

Then log out and log in again, and you should notice that there is a keyboard icon in the top right menu bar. Open up firefox or any other program and press Ctrl+Space, and the scim input method editor should pop up.

This works fine on a brand new installation of ubuntu gutsy: I'm in firefox right now, &#20449;&#19981;&#20449;&#30001;&#20320;&#65281;&#65281; 8)

Ok, that's it. See you all on the [[COLOR="DarkOrange"]Ubuntu Chinese Forums[/COLOR]]("http://forum.ubuntu.org.cn/")! :)

EDIT: All of this also assumes that you have already added CJK support (i.e. you have Chinese fonts etc.) using the tool found at System/Language Support.

[http://forum.ubuntu.org.cn/](http://forum.ubuntu.org.cn/)

---

### Post by seshomaru samma on 2008-03-03
To get SCIM working in firefox what I usually do is:
```
sudo apt-get install scim-bridge
```
```
sudo gedit /etc/X11/xinit/xinput.d/scim
```
change 
```
GTK_IM_MODULE=xim
```
to
```
GTK_IM_MODULE="scim-bridge"
```

if this doesn't work (never worked for me on Gutsy, and Debian Etch, and Sidux)
then use the im-switch
```
locale | grep LANG=
```
the output should be something like:
```
LANG=en_US.UTF-8
```
then run
```
im-switch -z en_US -s scim

```
(change en_US to whatever your locale is)

---

### Post by johnraff on 2008-03-04
I'm using Xubuntu Feisty and never had to do any of that.
I'm typing this on Swiftweasel (a version of Firefox) and here's a bit of Japanese:
&#12371;&#12428;&#12399;&#26085;&#26412;&#35486;&#12391;&#12375;&#12423;&#8230;&#65311;
My locale is en_GB.UTF-8, but there is another user on this machine with a Japanese locale so all the Japanese stuff is installed - maybe that makes the difference.

---

### Post by zard002 on 2008-04-02
Okie --  (Ubuntu 6.06)
I was having some issue with SCIM / firefox...
With firefox from Ubuntu depository (v 1.15 ), SCIM seems to
work fine.  However, if i take the tarball (v2.0.13) from Mozilla site,
firefox would crash with a segmentation fault.  If you un-install SCIM then
firefox would behave normally.  

The only solution I found around this is to get rid of firefox and install
a version of "swiftfox" of the same version -- they are supposed to be
of similar code.

---

