---
title: "A lot of things I need help with.."
date: 2008-05-05
forum: General Help
---

### Post by miickEe on 2008-05-05
Hey

I just upgraded to ubuntu 8.04.

I´m having some difficulty with a few things.

The keyboard layouts do not support my keyboard, which I find sometimes to be a little annoying. Many of the keys I need for writing are not included, which makes assignment-writing impossible. How can I resolve this?

Also, sound works well with everything apart from say youtube, myspace etc, anything in the browser pretty much. Solution?

And dvd playback, Ive installed xine, mplayer etc and yet no it plays the dvd (choppily) with no sound. I read somewhere it&#347; because linux has to check the media packets or something, and I tried the command to do that and it didnt work.

Thanks in advance

miickEe

---

### Post by pbpersson on 2008-05-05
> **miickEe said:**
> Hey

I just upgraded to ubuntu 8.04.

I´m having some difficulty with a few things.

The keyboard layouts do not support my keyboard, which I find sometimes to be a little annoying. Many of the keys I need for writing are not included, which makes assignment-writing impossible. How can I resolve this?

What country are you in?  What sort of keyboard do you have?  What characters are missing?  If you need them not very frequently you can insert them using a character map applet.  If you are looking for specific language, have you searched the forum for answers on that language?

---

### Post by miickEe on 2008-05-05
Australia, English. I figured maybe UK English would suffice but it wasnt much help. Um, the squiggle (the technical term escapes me) thats usually on the left-hand side directly under the Esc key. Double quotation marks, quotation marks, apostrophe, at symbol, hash (its actually on another key, but then the key that hash is on loses functionality, which is the backslash), and yeah those are the keys that I have gripes with atm.

Its an Omni keyboard, although apart from that I have no idea what model it is. Its a cheapie.

---

### Post by pbpersson on 2008-05-07
> **miickEe said:**
> Australia, English. I figured maybe UK English would suffice but it wasnt much help. Um, the squiggle (the technical term escapes me) thats usually on the left-hand side directly under the Esc key. Double quotation marks, quotation marks, apostrophe, at symbol, hash (its actually on another key, but then the key that hash is on loses functionality, which is the backslash), and yeah those are the keys that I have gripes with atm.

Its an Omni keyboard, although apart from that I have no idea what model it is. Its a cheapie.

SO.....you are saying on your keyboard you cannot type:

~~~ """  '''  @@@   ###  ????

That's crazy!  Have you tried another keyboard?  I am using an ancient IBM  Model M from the old PS/2 days when a 10MHz computer was blazingly fast and it works great.  I am leaning in the direction of a hardware problem with the keyboard or the port you are using on the computer.  :confused:

Oh....the little squiggly thing under the escape key is the tilde

When you installed Ubuntu, did you tell it you had a standard keyboard?

If you look in your /etc/X11/xorg.conf file, does the keyboard section look like this?

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection
```

---

### Post by asrai on 2008-05-07
What happens when you try to type those keys? Do you get different symbols coming up instead or is nothing happening at all?

Oh - and with your sound problem - do you have libflashsupport installed?

---

### Post by miickEe on 2008-05-07
Thanks for all the help guys.

Please note because I'm dual-booting with XP, XP has decided to **** up my master boot record and as such I'm not able to access my linux partition without much hassle, seeing as I have a lot to do atm. Hence why I can use these other keys in this message, I'm on XP as I speak.

"SO.....you are saying on your keyboard you cannot type:

~~~ """ ''' @@@ ### ????"

Yep, and when I push those keys I get other results.

I set it up how I usually do when I install linux, and tried all english variations (canada, UK, USA, South Africa etc).

I bought a new keyboard and yet it doesn't make a difference, even changing the "keyboard model".

I won't be able to check my /etc/X11/xorg.conf file for a while but if it does look like that, or doesn't, what does that mean?

To answer your question asrai, I installed a lot of different libraries and I don't think I downloaded that one. Thanks man.

When I get my other system up and running I'll let you know, but here's another conundrum for you:
When I install ubuntu alongside an existing xp installation, on different hdds, my xp decided to crack the shits. Then, when I delete my xp partition and intall linux fresh, then install xp afterwards, xp modifies the mbr and thus I cannot access grub bootloader. :S

Thanks guys for all the help.

---

### Post by pbpersson on 2008-05-07
> **miickEe said:**
> Thanks for all the help guys.

Please note because I'm dual-booting with XP, XP has decided to **** up my master boot record and as such I'm not able to access my linux partition without much hassle, seeing as I have a lot to do atm. Hence why I can use these other keys in this message, I'm on XP as I speak.

"SO.....you are saying on your keyboard you cannot type:

~~~ """ ''' @@@ ### ????"

Yep, and when I push those keys I get other results.

I set it up how I usually do when I install linux, and tried all english variations (canada, UK, USA, South Africa etc).

I bought a new keyboard and yet it doesn't make a difference, even changing the "keyboard model".

I won't be able to check my /etc/X11/xorg.conf file for a while but if it does look like that, or doesn't, what does that mean?

To answer your question asrai, I installed a lot of different libraries and I don't think I downloaded that one. Thanks man.

When I get my other system up and running I'll let you know, but here's another conundrum for you:
When I install ubuntu alongside an existing xp installation, on different hdds, my xp decided to crack the shits. Then, when I delete my xp partition and intall linux fresh, then install xp afterwards, xp modifies the mbr and thus I cannot access grub bootloader. :S

Thanks guys for all the help.

I just included that xorg.conf entry to show how a "standard" keyboard appears in the configuration file.  Although.....that is from Kubuntu version 7.10 - on my 8.04 machine the "corekeyboard" line was missing.

If the configuration says you have a standard keyboard and it works fine on Windows but in Linux you get totally different keys then you have a true mystery on your hands.

---

### Post by pbpersson on 2008-05-07
By the way, I had a Northgate Omnikey many years ago and there was a little door you could open where you could program it to emulate different keyboards.  I just remembered that today.

---

### Post by Lord Xeb on 2008-05-07
I believe this should help: [Dual boot xp (linux installed first)]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

You have Linux installed first right? Then this should help. There is a link their for if you have xp installed first. 

Have you looked for Australia in the list?

---

### Post by miickEe on 2008-05-08
> **Lord Xeb said:**
> I believe this should help: [Dual boot xp (linux installed first)]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

You have Linux installed first right? Then this should help. There is a link their for if you have xp installed first. 

Have you looked for Australia in the list?

That would have been the first thing I looked for lol, seems like us Australians aren't supported by the open source community haha.

---

### Post by asrai on 2008-05-08
Australian keyboards are the same as US keyboards - UK ones have the ~ etc in different places, so if you have it set up as a UK keyboard that would be why.  However if it also isn't working when it is set up as a US keyboard then that is very puzzling indeed :(

---

### Post by ShodanjoDM on 2008-05-08
Try this:

```
sudo dpkg-reconfigure console-setup
```

Here are the first three options:

[ATTACH]69225[/ATTACH] [ATTACH]69226[/ATTACH] [ATTACH]69227[/ATTACH]

There are other options after those above including Compose Key, Encoding, Character sets etc... 

I've got my ", | and ~ working after last year's upgrade (from 6.10 to 7.04) changed my keyboard layout somehow. 

Hope that helps.

---

