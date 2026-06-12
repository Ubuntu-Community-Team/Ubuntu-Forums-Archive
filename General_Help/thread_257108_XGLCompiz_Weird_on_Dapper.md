---
title: "XGL/Compiz Weird on Dapper"
date: 2006-09-14
forum: General Help
---

### Post by rowanparker on 2006-09-14
Hey,
I installed XGL/Compiz, and when I ran it for the first time. There was no gnome panel, so I had to create an executable text file which did "killall gnome-panel". Then I tried running Firefox, and there are no window borders, it just puts the window at the very top right, over the gnome panel. I tried to take a screenshot of this but ksnapshot forced me to log out each time of trying and the gnome screenshot didn't load.

Does anyone know why it's doing this, is there something I missed?

Thanks, Rowan.

---

### Post by turbojugend_gr on 2006-09-14
check these threads, it is a very common issue lately... hopefully the answer is there, it is thouroughly discussed.

1.[http://www.ubuntuforums.org/showthread.php?p=1462396](http://www.ubuntuforums.org/showthread.php?p=1462396)
2.[http://www.ubuntuforums.org/showthread.php?t=252796](http://www.ubuntuforums.org/showthread.php?t=252796)

---

### Post by rowanparker on 2006-09-15
I'll look at the links, thanks.

---

### Post by bulldog on 2006-09-15
Did you install cgwd and cgwd-themes and cgwd-themes-extra??

This give you the opportunity to use preconfigured borders,realy nice though.

---

### Post by rowanparker on 2006-09-15
I installed what you said, changed some options, still I don't have window borders.

I looked at the links, didn't seem to help much.

Any other ideas?

---

### Post by bulldog on 2006-09-16
Well it all depends on how and what you've installed.

Now I'm only guessing what could be wrong.

The latest compiz starts with '/usr/bin/compiz-start' in your sessions menu.
It works with csm as configuration-tool

I know it works very well with cgwd etc. for your window decoration.

You have to remove all other compiz-start commands from your session menu.

If you have no idea what I'm talkin about let me know.

{did you logout after installing cgwd etc.?}

---

### Post by JayTee on 2006-09-16
After trying to install XGL/Compiz on my system with an Nvidia Geforce 6200 using a very detailed how-to I found on this forum it totally b0rked my system. I had no gnome desktop at all. Every attempt I made to reverse the changes failed to restore gnome to the default except one, completely blowing away the install and installing fresh. Kinda reminded me of a corrupt Windows install. I'm sticking with the standard gnome setup until XGL/Compiz is more mature and there is a more concise and easy to follow installation available.

---

### Post by bulldog on 2006-09-16
Bad luck I think,I'm using Xgl/compiz from the beginning when I installed Dapper.
So it runs 4 month's or so.

There where some major changes in how compiz works.[gsetcompiz,gconf-editor and now csm]

It has been broken twice but was easely fixed.

So I can't complain about it.

[nVidia 6800Ultra and AMD64 X2 4600]

There are some good tutorials though but be sure they work with the latest changes.[csm,cgwd,and /usr/bin/compiz-start]

---

### Post by handy on 2006-09-16
> **JayTee said:**
> After trying to install XGL/Compiz on my system with an Nvidia Geforce 6200 using a very detailed how-to I found on this forum it totally b0rked my system. I had no gnome desktop at all. Every attempt I made to reverse the changes failed to restore gnome to the default except one, completely blowing away the install and installing fresh. Kinda reminded me of a corrupt Windows install. I'm sticking with the standard gnome setup until XGL/Compiz is more mature and there is a more concise and easy to follow installation available.

Similar for me, though not totally  borked, but I was happy to get it off my system, it had turned an otherwise wonderfuly reliable system into unpredictable rubbish, even when XGL/Compiz wasn't running!! :(

I will never install it until it is so well behaved that it is a part of the initial Ubuntu install... 

Compiz/XGL was a big waste of time for me.

---

