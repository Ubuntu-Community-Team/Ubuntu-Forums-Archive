---
title: "[SOLVED] Caps lock light reversed"
date: 2008-05-06
forum: General Help
---

### Post by Goombie on 2008-05-06
I was working on my computer, and I hit some key combination (not sure which one, sorry) and now my Caps Lock light on my keyboard is wonky. If caps lock is OFF, the light is ON, and when caps lock is ON, the light is OFF. This is already driving my crazy, and it only happened 15 minutes ago! Any ideas how to fix it? Thanks!

---

### Post by Daniel15 on 2008-05-06
This might not be a "proper" fix, but have you tried rebooting? Maybe it's just a glitch of some kind?

---

### Post by Goombie on 2008-05-07
I did try logging off and back on, which fixed it. :) Odd little glitch, though. I don't even know what I did to trigger it in the first place.

---

### Post by rohan.modi on 2008-05-07
hey
can any one help me for this
mine problem is some wat diffrent 
the led's r not glowing when i prss caps lock or num lock or scroll lock
on is it related to ati graphics driver  ???????

---

### Post by rohan.modi on 2008-05-07
heyyyyy
i got the sol of the problem 
just run the folloing in the terminal
sudo apt-get remove mouseemu
the problem of keyboard light not working will be removed

---

### Post by Goombie on 2008-06-01
I'm glad you found the answer to that. I don't have mouseemu installed, so I can't try it. I'll mark this thread as solved for posterity, though. That, and the problem hasn't come back for me. :)

---

### Post by spatterlight on 2008-06-05
I'm having the same issue with my caps lock spontaneously inverting. Removing the mouseemu package, though, doesn't affect the problem, because it's not installed to begin with.
Can we mark this unsolved? Anybody else seen this problem?

---

### Post by Flying caveman on 2008-06-05
ooooooh ohhhhhh, press and release the caps lock key really really fast, that will fix it.

---

### Post by avl555 on 2010-07-05
Or you could try plugging the keyboard out and in your computer

---

### Post by ierpe on 2010-07-13
i HAVE THE SAME PROBLEM AS YOU CAN READ...

BUT IT'S ONLY FOR CHARACTERS, ALL MY PUNCTUATION WORKS NORMALLY!!! ", . : '"

REMOVE THE SOLVED TAG....

---

### Post by DrMelon on 2010-07-13
> **ierpe said:**
> i HAVE THE SAME PROBLEM AS YOU CAN READ...

BUT IT'S ONLY FOR CHARACTERS, ALL MY PUNCTUATION WORKS NORMALLY!!! ", . : '"

REMOVE THE SOLVED TAG....

Punctuation always works normally with capslock. Just push the capslock key to turn it off (although the light will show as on). You don't need to show us by typing in all-caps.

---

### Post by All Good on 2010-08-03
Turn caps on (light off)
Open OpenOffice Writer, blank document
Hold right shift key, type letter "f" (the letter will appear in small caps: f)
Let go of right shift key, type letter "a" (the letter will appear in caps: A)
Hit the space key...

If you have autocorrect turned on in OpenOffice, as soon as you hit space,
aF will change to Af. The keyboard will change to small caps while the caps
light will stay off. The caps light and keyboard caps are back in sync.

---

### Post by trennor on 2010-08-03
> **All Good said:**
> Turn caps on (light off)
Open OpenOffice Writer, blank document
Hold right shift key, type letter "f" (the letter will appear in small caps: f)
Let go of right shift key, type letter "a" (the letter will appear in caps: A)
Hit the space key...

If you have autocorrect turned on in OpenOffice, as soon as you hit space,
aF will change to Af. The keyboard will change to small caps while the caps
light will stay off. The caps light and keyboard caps are back in sync.


WRONG!! I have the same problem: reversed caps lock, when the light is on, lower case, light off, upper case. The above fix did NOT work for me. 

kubuntu 9.04 -- but I'm switching to PCLINUXOS

This issue is NOT solved. There has to be some command we can issue in terminal which will restore things; why has this not been yet posted?

---

### Post by Goatrancer on 2010-09-14
> **All Good said:**
> Turn caps on (light off)
Open OpenOffice Writer, blank document
Hold right shift key, type letter "f" (the letter will appear in small caps: f)
Let go of right shift key, type letter "a" (the letter will appear in caps: A)
Hit the space key...

If you have autocorrect turned on in OpenOffice, as soon as you hit space,
aF will change to Af. The keyboard will change to small caps while the caps
light will stay off. The caps light and keyboard caps are back in sync.


This worked for me.. but I'm still at a loss as to how the hell it happened in the first place? Does OpenOffice autocorrect somehow screw up my keyboard?? I was using OO before the issue started.

---

### Post by rcorlett on 2010-09-15
Brilliant! That worked for me. 

I just plugged in a new logitech dinovo wireless keyboard (amazing btw) and had the same problem. Was NOT using openoffice at the time. I recommend trying that fix.

Robert

---

### Post by JackOfBlades on 2010-10-07
> **All Good said:**
> Turn caps on (light off)
Open OpenOffice Writer, blank document
Hold right shift key, type letter "f" (the letter will appear in small caps: f)
Let go of right shift key, type letter "a" (the letter will appear in caps: A)
Hit the space key...

If you have autocorrect turned on in OpenOffice, as soon as you hit space,
aF will change to Af. The keyboard will change to small caps while the caps
light will stay off. The caps light and keyboard caps are back in sync.

This worked for me. It seems OpenOffice has to do something about it. Someone should take a look into this.

---

### Post by zerocc on 2010-11-05
Unplugging the keyboard worked for me - was not using OO at the time. There appears to be at least two, possibly more, separate issues resulting in the same problem.

---

### Post by FormerSlacker on 2010-12-21
Is there any progress with this bug? I'm on 10.04 and the CAPSLOCK will randomly be reversed, and whats weird is that even punctuation is reversed as well.

For example, when CAPSLOCK is reversed it's impossible for me to type "," as only "<" will display. Very annoying behavior that's driving me nuts. It seems completely random.

---

### Post by vtk_90 on 2011-01-04
> **All Good said:**
> Turn caps on (light off)
Open OpenOffice Writer, blank document
Hold right shift key, type letter "f" (the letter will appear in small caps: f)
Let go of right shift key, type letter "a" (the letter will appear in caps: A)
Hit the space key...

If you have autocorrect turned on in OpenOffice, as soon as you hit space,
aF will change to Af. The keyboard will change to small caps while the caps
light will stay off. The caps light and keyboard caps are back in sync.

Heh, worked for me too. Open Office is really funny...

---

### Post by loganphyve on 2011-04-08
I fixed this by doing the following: turn caps lock off (so the light is now illuminated as though caps lock is on). Then, just unplug your keyboard and plug it back in. The keyboard should default to showing "caps off" while caps are now toggled off in the system.

---

### Post by negora on 2011-04-20
I'm using Ubuntu 10.10 and still suffering from this "bug" (if it's one). I'm not sure about its origin, but seems to be related to a quick and accidental pushing of certain keys.

When this error happens, I get into Preferences > Keyboard > Layouts and push "Reset to defaults". This sets the option "Caps lock key behavior" to "Caps lock acts as Shift with locking. Shift 'pauses' CapsLock". Now that I know its default value, I might choose this option directly, of course.

Maybe I'm mistaken, but I believe that option was set to "Default" by default in older versions.

---

### Post by byStanderone on 2011-04-20
...seems like an external hardware issue, there are devices that are hard headed and insist on using a preset IRQ, which generates conflicts when two devices are plugged in at the same time and are using the same 'irq's'. try using different ports, i.e. keyboard in ps2...mouse in usb.

---

### Post by bluesceada on 2011-08-11
How would you unplug and replug a notebook keyboard?

The following happened to me:

Thinkpad X61 is in sleep
Resume from suspend and the KDE unlock screen said that caps lock is on, even if the light didn't light up of the X61
Pressing capslock removed capslock but light was on...

Openoffice did also fix it for me, but I dont really believe in glitchy hardware in my case, rather something related with suspend/resume and thinkpad_acpi or something...

---

### Post by davec_48 on 2011-08-16
I had been using the same hardware for some time before this problem started, so I don't think this is necessarily hardware related.  What worked for me was a restart followed by unchecking the OO AutoCorrect option "Correct accidental use of cAPS LOCK key".  See [http://www.barregren.se/blog/openoffice-reverse-caps-lock](http://www.barregren.se/blog/openoffice-reverse-caps-lock).

---

### Post by daspliff12345 on 2011-09-19
> **All Good said:**
> Turn caps on (light off)
Open OpenOffice Writer, blank document
Hold right shift key, type letter "f" (the letter will appear in small caps: f)
Let go of right shift key, type letter "a" (the letter will appear in caps: A)
Hit the space key...

If you have autocorrect turned on in OpenOffice, as soon as you hit space,
aF will change to Af. The keyboard will change to small caps while the caps
light will stay off. The caps light and keyboard caps are back in sync.


Genius....how the heck did u figure this out??....worked for me

---

### Post by AntonJ on 2012-01-17
> **All Good said:**
> Turn caps on (light off)
Open OpenOffice Writer, blank document
Hold right shift key, type letter "f" (the letter will appear in small caps: f)
Let go of right shift key, type letter "a" (the letter will appear in caps: A)
Hit the space key...

If you have autocorrect turned on in OpenOffice, as soon as you hit space,
aF will change to Af. The keyboard will change to small caps while the caps
light will stay off. The caps light and keyboard caps are back in sync.

Thanks! Worked for me!

---

### Post by Rebelli0us on 2012-01-20
> **All Good said:**
> Turn caps on (light off)
Open OpenOffice Writer, blank document
Hold right shift key, type letter "f" (the letter will appear in small caps: f)
Let go of right shift key, type letter "a" (the letter will appear in caps: A)
Hit the space key...

If you have autocorrect turned on in OpenOffice, as soon as you hit space,
aF will change to Af. The keyboard will change to small caps while the caps
light will stay off. The caps light and keyboard caps are back in sync.

Same probem here and this worked, wtf, I don't even use Open Office , using MSWord in VM.

BTW, some keyboards' CapsLock LED doesn't work properly in Linux, that includes some very expensive Ducky /w Cherry MX switches.

---

### Post by pleurastic on 2012-03-17
5:30am, important deadline, Noooooo.  Caps lock reversed and ocd me cannot continue until corrected.  Thanks All Good!

---

### Post by coilwinder on 2012-12-03
> **loganphyve said:**
> I fixed this by doing the following: turn caps lock off (so the light is now illuminated as though caps lock is on). Then, just unplug your keyboard and plug it back in. The keyboard should default to showing "caps off" while caps are now toggled off in the system.

Thanks! This worked for me (I didn't use Open Office).

I've been using Ubuntu 10.04 LTS on this computer for some 2.5 years, and this is the first time this inverted caps lock bug happened to me. At login (luckily the login have a caps-lock warning). Well, that's computers for you :P

---

