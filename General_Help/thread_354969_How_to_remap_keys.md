---
title: "How to remap keys"
date: 2007-02-06
forum: General Help
---

### Post by Snigel on 2007-02-06
Hello,

I am currently in the process of installing Ubuntu, my goal being to check if it is a workable alternative for Windows for me. Most things seem to be all right, except one thing. I have been using a Swedish version of Dvorak (called svdvorak) for the past two years and it is not the one most commonly used (there is another one supported right from the start, but that is not the one I am interested in). I have been unable to find drivers for this keyboard layout. Here is what I am asking for:

1) How I can remap the keys myself so they match the keyboard layout I am used to
2) If anyone happens to know where I can get hold of the drivers

It would be a pity if my first Linux adventure should fail because of something like this, so I will be glad for any help I can get.

Regards,

Snigel

---

### Post by kebes on 2007-02-06
Well it's tedious, but you can remap keycodes however you want. Here's how:

To determine the keycodes for keys on your keyboard, you can run a program called "xev". When running, you just press keys and you'll see the codes appear in the program. By keeping track of these you can make changes to the keys that need updating.


Then, you use a commandline program called "[xmodmap]("http://cf.ccmr.cornell.edu/cgi-bin/w3mman2html.cgi?xmodmap(1)")" to remap a keystroke. So for instance:

xmodmap -e 'keycode 234=F2'

This would remap the key on the keyboard that generates keycode signal 234 to now be treated as the "F2" key. You can read the xmodmap documentation online to determine how to refer to various keystrokes.


So then you can build up a list of xmodmap lines, and put them all in a script that gets executed at login time, so that your keyboard is mapped the way you like.


This is somewhat tedious, and there may be a better way. Perhaps you can find your desired keyboard layout file somewhere on the net, and add it to gnome?

---

### Post by Snigel on 2007-02-06
Uhm, okay, thanks. Now I have at least got one way of doing it, which is much better than none at all :) The only thing I have been able to find so far is the site where I got the Swedish drivers, but it says "coming soon" on the Linux ones. The site was last updated four years agon, but I have e-mailed the owner and hopefully he can help me.

---

### Post by Snigel on 2007-02-08
I just wanted to say that I have been able to solve the problem by following your instructions. The only problem for me was that I knew too little about basic stuff, but with help I managed. Thank you very much!

---

### Post by kebes on 2007-02-08
You're welcome! I'm glad it worked.

---

### Post by bran on 2007-04-13
> **kebes said:**
> You're welcome! I'm glad it worked.

What if I just wanted to make the capslock void or extend the shift key?   xmodmap -e 'keycode 66=50' turns the capslock into a spare 2 though 50 is shift.  

Bran who has no use for capslock.

---

### Post by Goodson1974 on 2007-04-13
Hi all
 
Just wondered if anyone knew how to use xmodmap to remap a key to open the panel menu?

---

### Post by garbage792 on 2007-04-17
Hi,
I tried xmodmap and xev but cannot remap my keys.
Basically I want to map my "ctrl + down" to act as "page down" and "ctrl + up" to act as page up.

I cannot get my keycode for "ctrl + down" using xev. It gives my the same keycode as pressing the down key without the ctrl modifier.

Secondly for example "xmodmap -e "104=page down"" gives me the error that " bad keysym name 'page down' in keysym list". 

Please help. In windows I used a simple program to do this and never had a problem :(

---

### Post by kebes on 2007-04-19
> **Goodson1974 said:**
> 
Just wondered if anyone knew how to use xmodmap to remap a key to open the panel menu?

In xmodmap you can map to keys beyond what's on your keyboard, by using the function keys beyond F12. Basically you can map to the keys F12-F30, so something like:
xmodmap -e 'keycode 223=F27'

Then in your menu editor, set the key F27 to be a shortcut for whatever item it is you want to access.

Obviously this only works if your GUI (Gnome or KDE) allows you to bind a shortcut to the action you're interested in. I'm not sure what you meant by "open the panel menu" but there's probably somewhere in the UI preferences where you can set the shortcut key for it...

Hope that helps.

---

### Post by garbage792 on 2007-04-20
> **garbage792 said:**
> Hi,
I tried xmodmap and xev but cannot remap my keys.
Basically I want to map my "ctrl + down" to act as "page down" and "ctrl + up" to act as page up.

I cannot get my keycode for "ctrl + down" using xev. It gives my the same keycode as pressing the down key without the ctrl modifier.

Secondly for example "xmodmap -e "104=page down"" gives me the error that " bad keysym name 'page down' in keysym list". 

Please help. In windows I used a simple program to do this and never had a problem :(

*bump*

---

### Post by garbage792 on 2007-04-22
> **garbage792 said:**
> *bump*

Noone has a solution? :cry:

---

### Post by Snigel on 2007-11-27
Hello,

As I said, I managed to fix this, but I forgot how to do it. This time I have therefore written down how to do it. I modifies a Swedish standard layout to a Dvorak version. You can see how I did [here]("http://www.snigel.nu/?p=779").

Regards,

Snigel

---

### Post by Alan Stancliff on 2007-11-27
> **Snigel said:**
> Hello,

As I said, I managed to fix this, but I forgot how to do it. This time I have therefore written down how to do it. I modifies a Swedish standard layout to a Dvorak version. You can see how I did [here]("http://www.snigel.nu/?p=779").

Regards,

Snigel

Thanks, Snigel,

This  will come in handy. 

How does the Dvorak layout work in Swedish? I have an American English Dvorak keyboard, hardwired that way. I was hoping to be able to adapt it to Latin American Spanish by remapping just a few keys.

---

### Post by Snigel on 2007-11-28
it works alright. Swedish and English are similar enough to allow for some of the advantages. I made an analysis of key positions on the dvorak keyboard and compared to letter frequency in the Swedish language. The difference is not as great as it is between Qwerty and Dvorak in English, but it still is a big difference (I am now talking on percentage of keystrokes on the home row, for instance, which is much, much higher for Dvorak). I do not want to customise further, because I write pretty much in both language, so therefore I keep all special characters (those on the number row) from the Swedish keyboard (otherwise I would be severely handicapped when not using my own computer) and then mix that with American Dvorak. Works exceedingly well!

---

### Post by loyeyoung on 2008-01-31
Be very careful when remapping your keyboard. If you don't know what you are doing, you can leave your computer in a FUBAR state that will be very tedious and frustrating to un-Foo. 

Comfortable user interfaces exist to do minor changes such as remapping your Caps Lock or Ctrl-Down. If you are going to remap various function keys to trigger an event, use:

[LIST]
[*]In Kubuntu: System Settings > Regional & Language > Keyboard Layout.
[*]In Ubuntu: System > Preferences > Keyboard, and System > Preferences > Keyboard
[/LIST]

The use of xmodmap and xev, as stated in the posts, should be reserved for cases when you have no other alternative and it's important enough that you'd be willing to reinstall your operating system if things go wrong. 

The original post is an occasion where one is left no other alternative than to do rather major surgery to the system, and it is important to the owner of the system. 

"With open source, if you break your system you get to keep both halves."

Happy Trails,

Loye Young
Isaac & Young Computer Company
Laredo, Texas
[http://www.iycc.net]("http://www.iycc.net")

---

### Post by oscarc on 2008-02-08
Hi,

I I was reading this post and was hoping that it might help my problem I have. SInce quite some time my pipe-key has been broken, and therfore I want to remap it to another key. My problem is that as it is broken, I cannot se what name it goes under. For example pressing left shift outputs "SHIFT_L" in xmodmap, and A outputs "a".

If anyone with a working pipe key can tell me what the key is called I would be happy. Btw, I am using a swedish keyboard.

Greetings,
Oscar

---

### Post by kebes on 2008-02-09
> **oscarc said:**
> my pipe-key has been broken, and therfore I want to remap it to another key. I cannot se what name it goes under. For example pressing left shift outputs "SHIFT_L" in xmodmap, and A outputs "a".


When I run "xev", this is what I get for the pipe key (which is SHIFT + \ on my keyboard):
```
KeyPress event, serial 32, synthetic NO, window 0x7c00001,
    root 0x135, subw 0x0, time 15117699, (77,114), root:(1495,139),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x7c00001,
    root 0x135, subw 0x0, time 15118204, (77,114), root:(1495,139),
    state 0x11, keycode 51 (keysym 0x7c, bar), same_screen YES,
    XLookupString gives 1 bytes: (7c) "|"
    XmbLookupString gives 1 bytes: (7c) "|"
    XFilterEvent returns: False

```

So the key seems to be called "bar". Hope that helps.

---

