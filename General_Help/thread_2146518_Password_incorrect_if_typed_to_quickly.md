---
title: "Password incorrect if typed to quickly"
date: 2013-05-18
forum: General Help
---

### Post by cpu2007 on 2013-05-18
I don't know if this is something that happens to me only but when I type my password quickly in the login screen, terminal or any other panel asking to input my password, it throughs an error saying the password is incorrect. If I type it slowly then it doesn't give that problem.

I'm pretty sure it's not me typing the password incorrectly because I have been using the same password in win7 and I don't get any error even if I type it quickly.

I've noticed this problem even when using ubuntu on a different computer on a virtual machine.

My passwords contains upper/lower case and numbers.

---

### Post by pqwoerituytrueiwoq on 2013-05-18
once you type it count the number of dots on the screen, see if you typed the same number of letters tat your password is, type it in a text editor fast and see what happens

---

### Post by cpu2007 on 2013-05-19
Thank you 
That was a great tip, I should have thought of it before.
Typed it in the text editor and if I type quickly, even if I press caps lock again to type lower case, the letters are printed in upper case. It seems like there's a delay when the caps lock is pressed and that i have to slow down so that lower case is activated.
This is not an issue if I type equally or faster in win7 so I assume it has to do something with ubuntu?
any thought?

---

### Post by Jonathan Andrew Upton on 2013-05-19
This is a security precaution taken by Ubuntu to ensure that the operating system's user is a person and not a droid.

---

### Post by miegiel on 2013-05-19
> **Jonathan Andrew Upton said:**
> This is a security precaution taken by Ubuntu to ensure that the operating system's user is a person and not a droid.

Are you serious or being funny ?

---

### Post by richierich1986 on 2013-05-19
It might sound funny, but when you think about it, what Jonathan Andrew says sounds very logical actually.
I have noticed the same lag, but only since I installed 13.04. Maybe this is a new precaution indeed,
but I never had any lag before 13.04.

Android is a strange term, but a precaution against bots would make sense.

---

### Post by cpu2007 on 2013-05-19
i have 12.10 installed and noticed this problem on previous versions as well. Not a good precaution btw :/

---

### Post by cpu2007 on 2013-06-05
If this is a feature that they have added in Ubuntu, wouldn't be possible to remove it?
Does anyone know what file controls this feature?

---

### Post by SangeetKhatri on 2013-06-05
I type my passwords crazy fast in lubuntu 13.04. I never had any such problems.

---

### Post by Jonathan Andrew Upton on 2013-06-05
> **miegiel said:**
> Are you serious or being funny ?

No, I am being deadly serious. It is a security precaution, because a lot of bots are used nowadays to enter and configure code at speeds faster than the average human being. The computers at Canonical Ltd. can (probably) detect who is human and who is not by how fast the codes are entered. It is like the GUFW disabling to prevent hackers from getting onto the computer and altering the firewall settings.

---

### Post by 3rdalbum on 2013-06-05
It's not a security feature, that's ridiculous.

Either don't use caps lock to capitalise individual letters when touch-typing, or file a bug report with Xorg to maybe have the problem fixed in later versions of X.

---

### Post by CharlesA on 2013-06-05
> **Jonathan Andrew Upton said:**
> No, I am being deadly serious. It is a security precaution, because a lot of bots are used nowadays to enter and configure code at speeds faster than the average human being. The computers at Canonical Ltd. can (probably) detect who is human and who is not by how fast the codes are entered. It is like the GUFW disabling to prevent hackers from getting onto the computer and altering the firewall settings.

Source please. That doesn't sound very likely.

---

### Post by lisati on 2013-06-05
Why are you using Caps Lock instead of SHIFT?

---

### Post by houseworkshy on 2013-06-05
You could try opening a terminal and using sudo for something trivial, then sudo -k, then sudo something trivial etc etc.  If you recorded your desktop whilst doing this repeatedly you'd end up with a video and timeline.  Perhaps change your password before posting it.  Be worth seeing.   If it's not a feature maybe look at your short cut keys, could be that when typed slowly the keys are seen individually but when fast you are unwittingly using a key combination ( more than one being held down at the same time ) which your system is set to recognise.

---

### Post by coffeecat on 2013-06-06
> **cpu2007 said:**
> 
Typed it in the text editor and if I type quickly, even if I press caps lock again to type lower case, the letters are printed in upper case. It seems like there's a delay when the caps lock is pressed and that i have to slow down so that lower case is activated.

This is your problem. It has been known about for years and is a "problem" with xorg. Nothing to do with Ubuntu and certainly not a security feature.

You've correctly identified the delay - when you press caps lock the second time, the character typed immediately after will render as a capital if you are typing too fast. I've seen people describe this as a bug, but I don't know whether there has been a bug report raised with xorg. I've also seen debates about whether it is appropriate to use caps-lock in situations like this, some fast touch typists saying it is more efficient than using shift, and others disagreeing. I have no view since I am not a touch typist, and have no view whether this is a bug or not, but I have a pragmatic suggestion. Since the bug/feature is unlikely to go away soon, and since it is entirely out of Canonical's control, use the shift key for caps when typing in your password.

---

### Post by 3rdalbum on 2013-06-06
Bug was reported a while ago and there is a workaround : [https://bugs.freedesktop.org/show_bug.cgi?id=27903](https://bugs.freedesktop.org/show_bug.cgi?id=27903)

Basically, Xorg turns off Caps Lock when Caps Lock no longer registers as being "down" after being pressed the second time. Windows turns off Caps Lock when it registers the second press of the Caps Lock key.

---

### Post by tubbygweilo on 2013-06-06
Noticed this a while ago, good for stopping someone from attempting to use my long, strong & hard pass phrase but every now and again I have to slow down and move my lips as I type. 

Just remember to keep your keyboard crud free as just a little something caught under a key can give the impression of a fully depressed key when the reverse may well be true often causing all sorts of pass phrase problems.

---

