---
title: "bizzare endless login cycle"
date: 2006-07-08
forum: General Help
---

### Post by arborealguy on 2006-07-08
Moderators, if this is in the wrong forum, I apologize.

Ok, so I just finished setting up a dual boot XP/Ubuntu 6.06 on my laptop. So, I restart, select the ubuntu option in the GRUB loader, and it starts up. Everything starts up normally, and that default maroon background color appears and the cursor appears with the busy indicator. After a little while, the screen goes blank and then I get a screen that says:

> Ubuntu 6.06 indiewanke ttyl

indiewanker login: _

(indiewanker is what I named the computer in setup, it's an inside joke, and had I known I would be sharing it with the world, I would have named it something else)

So! I think, I'll just enter the user name I specified in setup, I type the first two letters and then it goes back to the desktop with the same maroon background and cursor. After a while it takes me back to the screen before, so I type in the last two letters of my four letter login name and hit enter, it goes BACK to the maroon screen w/ the cursor. Huh?! So then after a while it goes BACK into the login screen and now it's asking me for a password, I start to enter it, but the screen goes back to the maroon with the cursor, it's moves too fast for me to physically enter in my password! Worse, it's ghosted, so I have no idea if I've typed it in right or how many chacters I've typed when it gets back to that login screen.

What is going on, and how do I fix it?

I would like to say that I have exactly zero experience with Linux command line stuff, however, I know how to boot into command line with Grub, but would just need to know what to imput. Thanks!

---

### Post by encompass on 2006-07-09
sounds like a video driver issue... it is trying to start your screen up for a graphical login only to get kicked.  It keeps retrying, again and again.  Does the screen ever stop at the text based login?
If so... lets see if we can get your graphics card working.
What kind of graphics card does your computer have?

---

### Post by arborealguy on 2006-07-09
Well, after I posted, I did manage to get to the command promt, sort of. I hit ctrl+alt+F1 at that screen and it got me to where it was at the 

login: 

part, and it went slow enough that i could type in my user name and password, but it would still try to startup and then get dumped back in, at one point I had what I think was the command prompt, it was a string of text with my username and the computer name followed by the $.

I have an ATI Mobility X600, I just did a quick google for my video card and found these:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
[http://www.thinkwiki.org/wiki/Fglrx](http://www.thinkwiki.org/wiki/Fglrx)

For the first link, it wouldn't be a big deal for me to type in those commands, if I knew what enabling restricted repositores was and how to do it, I tried googling it, but am not certain what to do.

---

### Post by arborealguy on 2006-07-09
Ok, well I decided to just go for it and tried method 1 in the first link, and nothing happend, it still dumps me back out into the login screen exactly the same.

---

### Post by encompass on 2006-07-09
try method two now....
If that doesn't work... you can always drop back to vesa with no accell.

---

### Post by arborealguy on 2006-07-09
Ok, before I try method two, is there any way to disable the OS from trying to boot to the gui? What should have taken me about 30 seconds to type in took a lot longer because I was constantly having to force the OS back to the command promt

---

### Post by encompass on 2006-07-09
sure... when booting... you want to go into "safe mode"  press escape to see the menu at boot.. then select it
it should get you to a single user login and should beable to do what you need.

---

### Post by jimmygoon on 2006-07-09
Mine did this when I had attempted to use xdm rather than gdm, so I had to drop to a console prompt and apt remove xdm and reinstall gdm

---

### Post by arborealguy on 2006-07-09
Thanks for sticking with me on this, encompass.

Ok, so in method two described here: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I get the following errors, when I try to "blacklist old fglrx module from linux-restricted-modules" I get the error:

>  cannot open display: (null)

So, I thought i would continue on. When I get to the part about installing the necessary tools after the command:

> sudo apt-get install module-assistant build-essential

I get an error similar to "couldn't find package module-assistant".

So continuing on, when creating the deb packages after this command:

> ./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper

I get an "extraction failed" error and I cannot continue.

One other thing, I KNOW this can work with my video card, because the live CD version I used to install the OS in the first place looked absoutly beautiful.

---

### Post by encompass on 2006-07-09
This is because you were probably running the vesa driver with no 3d features.
```
sudo dpkg-reconfigure xserver-xorg
```
leave everything the way it is by just pressing enter... but when it gets to choosing the module that you want... I think you should choose vesa.  Let it go threw all the default options from there.
Then reboot.  You should be in a normal screen now.

As for your driver problem.. hmm  Lets see if you get this far.  I will look into your card further.

---

### Post by arborealguy on 2006-07-09
I'm sorry, could you be a bit more specific? When do you put in the command you listed?

---

### Post by encompass on 2006-07-09
run that commmand at any time... this should get your basic graphics up.  And at least make you computer more funtional for you.

---

