---
title: "Need Advice For A Friend That Wants to Try Linux"
date: 2007-05-14
forum: General Help
---

### Post by kevinbenko on 2007-05-14
Greetings:

I have a friend that, after a serious MS-XP-related problem has asked me about linux.

Now, my personal experience is limited to Debian (testing/unstable) and Slackware, but I figure that Ubuntu might be suitable for the guy.

He does understand that Linux is not a drop-in replacement for MS-XP, and that he's going to have to deal with an initial learning curve.

To be honest, his general computer knowledge is nominal.
The only requirements he has that I'm not 100% certain about are:

The guy has been using PINE for email for the past 10 years.
He needs a complete Latex/Tetex installation.

Does the Ubuntu repository contain the tetex packages?
While I can compile/install PINE from source, I'd rather not have him depend on me for such things.

Will Ubuntu meet his needs?
How user friendly is it for the nominally skilled?
Will there be any potential problems with my remote maintenance of his machine if, if necessary?

---

### Post by smoker on 2007-05-14
why don't you download the live-cd and your friend can try it before an install. a quick look at the repostiory (for fiesty) and it seems to include latex/tetex

if your friend takes to it, then install.

---

### Post by Jussi Kukkonen on 2007-05-14
> While I can compile/install PINE from source, I'd rather not have him depend on me for such things.
The problems of using non-free software... The debian package from the pine site will *probably* install just fine. Note that your administration duties don't end here: who is going to make sure that Pine security upgrades are installed (as an example, Pine had a remote-exploitable buffer overflow exploit about a year ago)?

> 
Does the Ubuntu repository contain the tetex packages?
Yes. More specific info at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by yopnono on 2007-05-14
> **kevinbenko said:**
> 
The guy has been using PINE for email for the past 10 years.

PINE the command line email client? 
Don't you think that you should try to convince him to move to something newer. Like Thunderbird, evolution, etc,etc.

---

### Post by RedSquirrel on 2007-05-14
> **yopnono said:**
> PINE the command line email client? 
Don't you think that you should try to convince him to move to something newer. Like Thunderbird, evolution, etc,etc.


Some people like non-graphical applications. :)

mutt is another text-based email client and it's in the repositories. alpine is there too, but it's alpha.

---

### Post by kevinbenko on 2007-05-14
Well,

First things first.

I realize that I am a Linux zealot, that I do tend to be pushy, but I was practically doing cartwheels when he asked me about Linux. I figure that if I don't change too much on him at once, that he may come around and ask me about other email clients.

However...

He's had the opportunity to use a GUI email client since before I knew him, but he has stuck with PINE for some reason.  I would guess that it was the first email client he used.
[sort of analogous to the perpetual emacs/xemacs/vi or the KDE/GNOME debates, most people stick with what they're most comfortable with]

---

### Post by christhemonkey on 2007-05-14
From the pine website:
> Debian / Ubuntu Linux pine installation instructions

Grab pine .deb file from official FTP site:
$ wget [ftp://ftp.cac.washington.edu/pine/pine_4.64_i386.deb](ftp://ftp.cac.washington.edu/pine/pine_4.64_i386.deb)
Next, install .deb file:
$ sudo dpkg -i pine_4.64_i386.deb

And tetex is just a:
```
sudo apt-get install tetex-bin 
```

So it should be no problem to install pine or tetex.

---

### Post by kevinbenko on 2007-05-14
Yeah, I know that's going to be a minor hassle, but not too much of a problem for me since messing with Linux is what I do for recreation.  And since his office is about a 15 second walk from my office, it's within epsilon of being a non-issue for me.

I'll probably install one or two other email clients [aside from the GNOME-default] for him and he'll stumble across them on his own.

---

