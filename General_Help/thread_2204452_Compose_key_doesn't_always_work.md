---
title: "Compose key doesn't always work"
date: 2014-02-08
forum: General Help
---

### Post by John Jason Jordan on 2014-02-08
Xubuntu 13.10, up to date, System76 Bonobo Extreme, US English keyboard.

I have enabled the compose key and set it to the Ubuntu key ("leftwin," same as the Windows key on other computers). It works, but erratically. I hold down the Ubuntu key and then the ' key, and nothing is supposed to happen until I type a letter, at which point the letter will appear with an acute accent over it (á). Sometimes it works, other times I get just a '. Thinking that it might be a physical defect with the Ubuntu key I switched it to other keys, but I get the same behavior. And it's not like "every other time" - sometimes it works several times in a row, other times it fails several times; there is no pattern to when it will work and when it will fail. And it happens in all applications, even here typing in the forum.

The computer was brand new on December 8. 2013, at which time I installed Xubuntu 13.10. There are no other operating systems. I had this working fine on my old Thinkpad with Xubuntu 12.04. As far as I can tell all the keyboard settings are the same.

I am out of ideas. Need suggestions!

---

### Post by fiona3 on 2014-02-09
Have you tried [AltGr]+[;]  then press a letter? 

I was looking for the quickest way to enter acute accents.
That worked for me on Ubuntu 12.04 with a UK English keyboard, when the compose key didn't.

 [AltGr] + [;]  then [A] produces á. 
 [AltGr] + [;]  then [E] produces é.
 [AltGr] + [;]  then [I] produces í.
 [AltGr] + [;]  then [O] produces ó. 
 [AltGr] + [;]  then [U] produces ú.

---

### Post by John Jason Jordan on 2014-02-09
> **fiona3 said:**
> Have you tried [AltGr]+[;]  then press a letter? 

I have a US keyboard; no AltGr key. 

On the bottom row I have Ctrl, Ubuntu (lwin), Alt, Spacebar, pipe/left slash, Alt, Fn, and Ctrl. I have tried setting the compose key to several of those possibilities, but the compose function is still erratic regardless of which key I assign it to. (Hence I conclude it is not a defective key.) Sometimes it works, more often than not it does not work. To type a letter with a diacritic I have to keep trying until finally it "takes."

It's the erratic part that is driving me nuts. Things should either work or not work.

---

### Post by John Jason Jordan on 2014-02-16
Úpdate:

A friend who knows more about hardware and Linux than I do fixed using xev (key even viewer). With xev running we could see that the compose key was repeating. Sure enough, the repeat key function was enabled. After disabling the repeat key function my compose key now works perfectly.

---

### Post by Impavidus on 2014-02-17
Interesting...

My keys are repeating, but not my compose key (and neither my shift, control, alt, caps lock and num lock keys). This is what xev tells me. I use my Windows key as compose key. Even with repeating keys it may work if you just hit the compose key, not hold it but release at once, and then hit the composing characters. So not compose+{a, '} but {compose, a, '}.

---

