---
title: "Keyboard and tvout(ati) problem"
date: 2006-12-17
forum: General Help
---

### Post by tuskal on 2006-12-17
Hello!

_My first problem is this:_ [COLOR="SeaGreen"]fixed[/COLOR]

I have a problem with my keyboard(s) and logging in to ubuntu. (i've got a micro$oft wireless keyboard and a logitech wired one)

When entering my username, all keys from a-z doesn't work. But here's the wierd part; the keys 0-9, ä and ö (swedish letters) works, but not å for some reason! 
This means that I can't login at all... :mad: 

I have a swedish keyboard and i've selected swedish as my system language.

Something that can be noted is that i have messed around in my xorg file trying to get my tvout to work. I have run the command $ sudo dpkg-reconfigure x server (dunno if it looks like that but it worked) and I guess it messed up stuff... I dunno, I'm still a nOOb when it comes to stuff like this...

_My second problem is this:_

With the risk of being repetitive, my tvout isn't working properly. 
I've got my drivers up and running but i ran this controlpanel thingy(can't remember the name, firegl?) and selected that it should clone my desktop, it did, but now I can't turn it off! And I didn't want to clone it becauseI want to play movies from my computer and that dosen't work in cloned mode... I don't know how to turn it off and get it right.. Help please? ](*,)

And due to my first problem, the second problem kinda have to wait lol :D help please?

---

### Post by jocko on 2006-12-17
For your first problem:
Can you get to a command line? Try hitting ctrl-alt-F1 (or F2-F6). Otherwise you can boot into recovery mode (hit Esc when grub is loading to get the boot menu).

When you have a command line interface, your keyboard should work. To fix the x.org keyboard settings try this:
```
sudo nano /etc/X11/xorg.conf
```
Find the keyboard section and make sure it looks like this:
```
Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "se"
    Option        "XkbOptions" "lv3:ralt_switch"
EndSection
```

---

### Post by tuskal on 2006-12-18
ok, thanx! I'll try it right away... brb :cool:

Edit: lol, it seems like my xorg.conf file is completely empty! what on earth have I done? :D lol

anyway, I used the recovery option in boot menu which seemed to work ok anyhow, so I can use the terminal to do stuff atleast.

There's a command I can run to reconfigure xorg.conf file right? I think I've made a backup of it before aswell, maby I can recover that one? Or make a new one... hehe

---

### Post by tuskal on 2006-12-18
anyone? :-?

---

### Post by jocko on 2006-12-18
> **tuskal said:**
> anyone? :-?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tuskal on 2006-12-20
> **jocko said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```

ok, so I tried that one, twice, but it still won't work! ](*,) 

I don't understand this, the reconfiguration was kinda hard, maby I got something wrong, I dunno.. Anyway, I still got the same problem, now what?? Why isn't it typing in anything into my xorg file? Do I have to type it myself?? 

Maby it's best that I do a reinstall again... bah #-o

---

### Post by jocko on 2006-12-20
Are you sure you don't have an /etc/X11/xorg.conf? Make sure you type the path correctly (it has to be capital "X" in "X11").

Check the output of ```
ls /etc/X11
```
Do you see xorg.conf? Maybe you even see an old backup from before you messed it up?

---

### Post by tuskal on 2006-12-20
> **jocko said:**
> Are you sure you don't have an /etc/X11/xorg.conf? Make sure you type the path correctly (it has to be capital "X" in "X11").

Check the output of ```
ls /etc/X11
```
Do you see xorg.conf? Maybe you even see an old backup from before you messed it up?

ok, so there we had one of the problems, my xorg file isn't gone, it me who messed up that darned X! ](*,) 

anyhow, now that I can access my xorg file, this is what I see(parts of it anyhow) and since I'm to lazy to type it down, here you have some pictures :) :

$ ls /etc/X11 gives (not really important now though):
[[IMG]http://img158.imageshack.us/img158/4483/img8836gl3.th.jpg[/IMG]](http://img158.imageshack.us/my.php?image=img8836gl3.jpg)
keyboard and mouse section:
[[IMG]http://img158.imageshack.us/img158/5405/img8839du2.th.jpg[/IMG]](http://img158.imageshack.us/my.php?image=img8839du2.jpg)
graphic card and monitor section:
[[IMG]http://img158.imageshack.us/img158/7775/img8841rq3.th.jpg[/IMG]](http://img158.imageshack.us/my.php?image=img8841rq3.jpg)
serverlayout section:
[[IMG]http://img158.imageshack.us/img158/4904/img8842lq3.th.jpg[/IMG]](http://img158.imageshack.us/my.php?image=img8842lq3.jpg)

Ok, so in the keyboard area there's gotta be something wrong right? 
The only thing I see is that it says " "Xkbmodel" "pc104" ", while my keyboard has 105 keys?
But is that the only reason why some of my keys work and the rest won't? Sounds odd to me... any thoughts?

This is quite instructive btw, I'm learning alot! :KS

---

### Post by jocko on 2006-12-21
One way to fix it would be to go back to one of your backup copies:
```
sudo cp /etc/X11/xorg.conf.fglrx-0 /etc/X11/xorg.conf
```

Another way is to change the keyboard section in your current xorg.conf so that it looks like it does in one of your working backups or the one in my previous post.

To be able to read and scroll through the contents of a file in a terminal:
```
cat /etc/X11/xorg.conf.fglrx-0 | less
``` (exit by pressing "q")

---

### Post by tuskal on 2006-12-21
**Wohooo!!!** Ok, so now it's working, I can now login! :D 

I was missing this little line of text:
> **jocko said:**
> 
```
    Option        "XkbOptions" "lv3:ralt_switch"

```
Btw, what does it mean? Like "make so user can type with letters"? lol :p 

But now 2 more problems has appeared:

[COLOR="Silver"]1.The freezings seems to be back, but perhaps I have to do that ati process which fixed it last time once more now that my xorg file is all new and shiny... I'll fix that later (no time now)[/COLOR] [COLOR="Green"]Done[/COLOR](did [[COLOR="YellowGreen"]this[/COLOR])]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

[COLOR="Silver"]2. I've recently bought a router, It should work if I apply the same settings as I have in windows, couldn't get an idea about it before it froze though.. (it's a Netgear WGT624)[/COLOR] [COLOR="Green"]Done[/COLOR]

and then the tvout problem...

Now then, where do I start? :)

Edit:

Ok, so I googled around a little, and found a command:

```
$ aticonfig --enable-monitor=tv
```

With this, my monitor went black and I get picture on my tv! Playing movies worked, which I see as a good sign :D

But I want to have an extended desktop, where I drag the movieplayerwindow(vlc) over to the extended area, or, clone the desktop and then playing the movie in fullscreen on the tv (now I get the fullscreen on my monitor) and It would be wonderful to make, like, a button which I can press and then get the extended area easypeasy just like that...
I'll try some more now.. any ideas?

Edit 2:
Ok... hm, so now I changed back to cloned desktop, and playing movies works, but the resolution is all messed up. I changed to 800x600, which looks fine when just using the desktop, but when playing movies, the picture is all wrong, either 1/4 of the original picture is covering the screen or it's misplaced..

---

### Post by tuskal on 2006-12-22
bump

---

