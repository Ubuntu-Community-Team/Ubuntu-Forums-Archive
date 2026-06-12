---
title: "keyboard problem! key mapping?"
date: 2008-06-11
forum: General Help
---

### Post by timklab on 2008-06-11
Hi,

I'm running Gutsy and have had no problems until today when I turned on my laptop to find that some of the keys had mysteriously acquired new mappings.

The following ones are occurring:

pressing 'b' gives me '5b'
pressing '5' also gives me '5b'

6 = 6n
n = 6n

/ = -/
- = -/

? = _?
_ = _?)

% = %B
B = %B

^ = ^N
N = ^N

These seem to be all the ones I can find, as you can see they appear to be "paired up" so it's most likely not a hardware problem.

I've tried to remap with xmodmap using "xmodmap -e 'keycode 56=b'" (for example) but nothing changes.

Any help would be amazingly appreciated!

Thanks

---

### Post by sdennie on 2008-06-11
Do you have your numlock key on?  Sometimes laptops will map the keyboard to different values when the numlock key is on.

---

### Post by timklab on 2008-06-11
Oh yeah, I forgot to say I'd tried that as well but still no joy :(

Cheers for the quick response tho

---

### Post by drs305 on 2008-06-11
Here are a few commands that you can run to see what is going on. I don't use Gutsy but don't think things have changed. DId Gutsy allow you to go to System, Preferences and select/reselect a keyboard?

To see current key assignments:
```
xmodmap -pke
```

To view current keyboard:
```
cat /etc/X11/xorg.conf | less
```

The available xmodmap keyboard layouts are in /usr/share/xmodmap/

In hardy, the current keyboard setting can be viewed in:
/home/**username**/.gconf/desktop/gnome/peripherals/keyboard/kbd

---

### Post by timklab on 2008-06-11
Hi again,

Still no luck i'm afraid. 

I checked xmodmap -pke and all the mappings were in order.

I then changed the layouts via System>Preferences... to different alphabets and keyboard combnations and i also tried doing the same through the terminal.

It's the same keyboard layout I've always used - Generic 105-key (Intl) PC (United Kingdom). Though it doesn't seem to be the layout or the mapping causing the problem...

I'm stumped. And having to correct these posts for about 5 minutes after writing them is driving me mental! lol

---

### Post by drs305 on 2008-06-11
> **timklab said:**
> 
I'm stumped. And having to correct these posts for about 5 minutes after writing them is driving me mental! lol

I feel your pain. I was researching some xmodmap problems for someone a few nights ago and had problems restoring my original settings for about 10 mintues - or should I say " for a4ou* 1R minutbs". I found I could cut and paste the letters I couldn't type into the messages!

Have you tried unplugging your keyboard?

---

### Post by timklab on 2008-06-11
Well, it's a laptop but is there a way to disconnect it and let Ubuntu redetect it?

I even reinstalled gutsy to try and fix this problem. 

I hope I'm being blissfully ignorant here, but I'm starting to think it might be the keyboard itself as maybe the keys that are "paired up" (5 and b, 6 and n) are physically connected.

---

### Post by hal8000 on 2008-06-11
If you boot from the live Gutsy CD does the keyboard still give incorrect keymappings?
It could be a faulty keyboard, just make sure you have no stuck keys.

---

### Post by drs305 on 2008-06-11
> **timklab said:**
> 
I hope I'm being blissfully ignorant here, but I'm starting to think it might be the keyboard itself as maybe the keys that are "paired up" (5 and b, 6 and n) are physically connected.

can you hook up an external keyboard (usb) to see what happens?  i don't know if it would override the internal keyboard or not. you can run '**xev**' in terminal to see what signal is being sent when you press a key but from what you've said it sounds like it is going to return "b" for "b" (and not  5b).

there are also key combinations on some computers that switch the keyboard to an alternate setting (Fn + some key, for instance). I've inadvertently pressed those before but the results made *some* sort of sense even though it wasn't what I wanted.

Here is another command you can try to reset things. It's just a command line way of installing the keyboard but who knows...
```
sudo dpkg-reconfigure -plow console-setup
```

bumping your post but probably not much else.... :(

---

### Post by Evamgeline on 2010-09-13
i am facing the same problem with my keyboard all of a sudden. It was working fine till last nite..
please help :(

---

### Post by Evamgeline on 2010-09-13
somehow it is fine again..!!

---

