---
title: "Cannot Start Ubuntu"
date: 2007-03-15
forum: General Help
---

### Post by jexdawg13 on 2007-03-15
Last night I was messing around in theme manager changing window border styles and icons. As I was scrolling through various icons, I selected one and my computer froze. You'd think a frozen computer would work itself out after a restart, but that would be way too easy. My entire system died. Seriously lame.

So now when I restart, the Ubuntu loader comes up and the orange bar creeps across until its finally loaded. It gets me to a brown screen that always showed up even when ubuntu was working well, and it makes the cool startup noise. I have my mouse cursor load (and its the custom icon). I can wave the mouse around but I can't do anything useful with it.

It gets to that screen and refuses to budge. I plead with it, but it is steadfast in its stubborness.

After screwing up ubuntu before while doing things that warrant a potential meltdown (like screwing around with very important internal files), I went into terminal via ctrl + alt + f1 and pulled some tricks out of my (pathetically limited) linux-command bag.

Maybe it was a graphical problem? sudo dpkg-reconfigure -phigh xserver-xorg to reset xorg.conf did nothing. sudo /etc/init.d/gdm restart did nothing (though I didn't really expect it to). "work you pos" was not a recognized command. Throwing my keyboard was also ineffective.

No matter, I thought. I'll just boot from ubuntu cd and ask them a question on the forums... if my cd work. A friend wanted to try linux so I have him my cd, and he gave it back to me, scratched. When I try to boot from CD the last line is "Boot from CD" and then nothing happens. Sweet.

So I installed windowsXP (which barely worked since ubuntu takes up all my space and partioning drives on the fly is not my area of expertise... or even general know-how... or even any ideas whatsoever) so that I could get online and ask this. 

Anywho, here I am. I formally request the help of the wonderful ubuntu community. I need to somehow... uhh... change my icon set back to something that works so that my computer will load, and also figure out how to boot ubuntu again (edit boot.ini maybe? I'll wait for your responses). Please help. My computer is annoyingly bad right now. 

Thanks. I love you (potentially, if you help :)).

---

### Post by jexdawg13 on 2007-03-15
Bump. Please help. I have an english report due tomorrow and my current windows install doesn't actually have a c: drive, so I can't actually save or install anything (like word, or open office). Pity me. I kind of need Ubuntu to work, haha. Thanks.

---

### Post by jexdawg13 on 2007-03-15
Please?

All I want to know is how to reset my theme and all of its subcategories to the default of gnome from terminal. Surely this is possible? Surely I haven't lost my entire computer and everything on it just from changing an icon? 

Any help is greatly appreciated.

---

### Post by LuxVoodoo on 2007-03-15
I had a similar freeze up while changing themes once and the following commands put my desktop back to its defualt, but I have yet to have another freeze up when changing themes. So try the following:

rm .recently-used.xbel

rm -rf ~/.gnome* && rf -rf .gconf*

rm -rf ~/.gtkrc*

It's worth a shot, anyway.

---

