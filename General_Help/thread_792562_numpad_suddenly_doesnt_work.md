---
title: "numpad suddenly doesnt work"
date: 2008-05-13
forum: General Help
---

### Post by jorik42 on 2008-05-13
so, this evening (at some point, unnoticed), my numpad ceased working in linux.  i booted into vista, and the numpad works there.    so, does anyone have any ideas as to whats going on??

jorik

---

### Post by zenwalker on 2008-05-13
When u got back to ubuntu, still the state was same??  Seems to me like a problem with Xorg. See if u r keyboard layout is set correctly.

---

### Post by jorik42 on 2008-05-13
yeah; it still doesnt work. it doesnt matter which window manager i use, it doesnt type.  i checked the keyboard layout; its still set to the default us english.  

i installed the xorg-dev files tonight, i think before this began.    might that have anything to do with it?

---

### Post by chrisrico on 2008-05-14
I was having this problem as well. I found the solution here:

[http://www.uzbmaster.com/shingil/2008/05/13/ubuntu-804-hardy-heron-numpad-is-not-working/](http://www.uzbmaster.com/shingil/2008/05/13/ubuntu-804-hardy-heron-numpad-is-not-working/)

Solution
Go to:
1) System
2) Preferences
3) Keyboard
4) Switch to tab “Mouse Keys”
5) Uncheck “Allow to control the pointer using the keyboard”
6) Done.

---

### Post by amidaniel on 2009-03-05
Thanks, this solution worked for me. Very frustrating, though; I installed some assorted security patches, and then the numpad stopped working. This is not the first time that installing such patches has mysteriously enabled or disabled completely unrelated settings--I wish the Ubuntu devs would display a little more caution when releasing patches.

---

### Post by batasrki on 2009-03-08
This solution worked for me as well. It got screwy after the latest update, which was updating the libpng library.

WTF does the libpng library have to do with keyboard keys controlling mouse movements ?!?

---

### Post by edam on 2009-03-26
worked for me too!  :)  Thanks!

---

### Post by ikester8 on 2009-04-24
It worked for me as well, thank you!

---

### Post by semargl on 2009-05-08
I have some different problem - numpad doesn't work only in console.
For example I can't navigate by numpad arrows in Midnight Commander (in GNOME Commander too). Only by standard arrows between main keys pad and num pad.

PS: Control pointer using keyboard in Mouse keys setup is already unchecked.

---

### Post by Gimpy_Rob on 2009-05-14
Worked for me! 

Thanks!

---

### Post by mikeytag on 2009-06-24
Thanks so much. Worked for me too!

---

### Post by Heinzzz on 2009-07-03
Thanks for the proposed solution, works like a charm!

---

### Post by Martijn van Es on 2009-08-17
Thanx! It worked for me. Strange the settings changed without notice to the user.

---

### Post by knifesk on 2009-11-11
don't know why it got activated.. suddenly from one moment to the other on a cube rotate the numpad gone dead...

 tkz for the solution!

---

### Post by OpenTS on 2010-02-16
It work!!! Thanks a LoT :popcorn:

---

### Post by mrkazoodle on 2010-05-03
> **chrisrico said:**
> I was having this problem as well. I found the solution here:

[http://www.uzbmaster.com/shingil/2008/05/13/ubuntu-804-hardy-heron-numpad-is-not-working/](http://www.uzbmaster.com/shingil/2008/05/13/ubuntu-804-hardy-heron-numpad-is-not-working/)

Solution
Go to:
1) System
2) Preferences
3) Keyboard
4) Switch to tab “Mouse Keys”
5) Uncheck “Allow to control the pointer using the keyboard”
6) Done.

Thank you very much, you saved me at least half an hour of searching

---

### Post by ipatfrmww on 2010-05-10
The exact same thing was happening to me aswell. I thought it was a problem with lucid(i just upgraded). Apparently it isn't, this is an disturbingly common issue (see [http://ubuntuforums.org/showthread.php?t=1077301](http://ubuntuforums.org/showthread.php?t=1077301) aswell) with everybody having exactly the same fix.
I don't even know what i did to turn that turned that setting on but i think it was after installing a package like other people said happened to them.

Somebody needs to file a bug report so that people who know about this sort of thing can look into it, this bug seems to have been around for a while(in multiple releases).:confused:

I'm fairly new to Linux, can anybody suggest the best place to post a bug of this sort.

---

### Post by RottNKorpse on 2010-05-13
There is actually a simplier way to get the numpad control back.

Hold SHIFT and press "Num Lock"

that will toggle the Mousekeys feature on and off.

---

### Post by ipatfrmww on 2010-05-15
That must be what I did by accident to turn it on in the first place.
ooops :lolflag:  That was very very annoying when I had no idea what I had done. 

My personal opinion is that that key combination should gotten rid of, given the trouble it is causing people. If that is the the cause that is.
It would explain why so many people have this turned on without knowing what caused it.
I agree that it could be useful for some people having this key combination, but it is also extremely annoying for others who don't actually know about it.

---

### Post by svenskmand on 2010-08-26
I am pretty sure that it is not the shift+numlock key combo that is the cause why so many people get this enabled. I say this because this often happens on my system, and it is really annoying. I have it happened more than seven times, and I never use the numlock key. But it is definitely something that should be fixed in future patches/releases. By the way is there a bug report for this?

---

### Post by s7anley on 2011-10-25
> **RottNKorpse said:**
> There is actually a simplier way to get the numpad control back.

Hold SHIFT and press "Num Lock"

that will toggle the Mousekeys feature on and off.

Thanks a lot for this tip.

---

### Post by Parama on 2012-01-26
> **RottNKorpse said:**
> There is actually a simplier way to get the numpad control back.

Hold SHIFT and press "Num Lock"

that will toggle the Mousekeys feature on and off.

Yes! :KS That's what I'm talking about. It event works with Unity on Oneiric. Thank you very much!

---

### Post by oldos2er on 2012-01-26
And we'll let this one go back to sleep. Closed.

---

