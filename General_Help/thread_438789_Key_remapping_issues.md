---
title: "Key remapping issues"
date: 2007-05-10
forum: General Help
---

### Post by noctis_vulpes on 2007-05-10
Okay, few days ago I finally decided to give this Linux thing a try and installed Ubuntu. The entire ordeal was surprisingly painless - heck, I was more confused with Windows installation than I was with this.. So I messed with it for a bit... Tripped a few times here and there... and finally ended up breaking X.

So...Clean install!!

Now, the actual point of this post... I come from a Macintosh background, and I want to remap my control, alt and windows keys to better suit the way that I am used to using computers. That is, I want

control key (L) to be Meta_L (what does this do, anyway?)
alt key (L) to be Control_L  and
windows key (L) to be Alt_L.

I used xev to get the key codes and created .Xmodmap to reflect this...

```
keycode 37 = Meta_L
keycode 64 = Control_L
keycode 115 = Alt_L Meta_L
```

..in my home dir. But for some reason, this only works like, 20% of the time... other 80%, it still wants to be its old self. I never got this to work in any text editor... Well, as a matter of fact, firefox is the only one that I got this to work properly, but even then, it sometimes refuses to work ( I have NO idea what's causing this... When it works and when it doesn't seems to be completely random)

...as near as I can search,  I can't find anyone else with this problem, nor can I find a way to make this permanent. Can anyone help?

Thanks in advance for any help.

---

### Post by rai4shu2 on 2007-05-10
I'm not sure how to do that with Xmodmap, but there are a number of options in the System > Preferences > Keyboard in Layout Options (assuming you're using Gnome).

---

### Post by noctis_vulpes on 2007-05-10
Thanks for the help, but I already tried that... But none of those options lets me to what I want to do (outlined above) 

...and an off-topic question... Why is it that every time I search for key remapping, I invariably come across ways to remap caps lock to control? I even came across a discussion where people were fighting over having control key next to the 'A' key. Any specific reason why they feel so strongly about it?

Anyhoo, it doesn't even needs to be done through xmodmap... I just used the only method that I knew how. Any method that allows me to permanently and globally remap those keys will be GREATLY appreciated.

---

### Post by rai4shu2 on 2007-05-10
The caps lock remappers are probably designed with portables in mind. They generally have limited space, so you'll only see one Ctrl on the right side, etc.

---

### Post by ivesjd on 2007-05-23
You may want to try it like this 
```
xmodmap 'keycode 37 = Meta_L'
xmodmap 'keycode 64 = Control_L'
xmodmap 'keycode 115 = Alt_L Meta_L'
```

Thats how my xmods are written.

---

