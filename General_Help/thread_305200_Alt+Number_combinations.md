---
title: "Alt+Number combinations"
date: 2006-11-22
forum: General Help
---

### Post by KedDeK on 2006-11-22
In Windows I often used Alt+Num combinations, such as Alt+64 for @, Alt+126 for ~, but since I've moved to Ubuntu Dapper and then to Edgy, these combinations don't work. I have to do all the symbols using AltGr.

I asked in IRC and nobody could give me an answer. It would be nice to make this keys work since I'm accustomed to using them.

Any ideas?

---

### Post by creaturex on 2006-11-23
I noticed that too, and I haven't found any other ways except the Character Map (Applications > Accessories > Character map) I'm sure there's a way to write a script to emulate this, but it would be a real pain to write.

---

### Post by grsing on 2006-11-23
It still works in Word running on CrossOver, so it's not an inherent inability with Linux.  Don't know how you'd make it work for other, native Linux programs, but it shouldn't be impossible.

---

### Post by SOULRiDER on 2006-11-23
I have exactly the same problem.

---

### Post by strabes on 2006-11-23
I'm just wondering but is there a specific reason you don't use shift+2 for @, etc? Is it faster?

---

### Post by KedDeK on 2006-11-24
Shift+2 doesn't work for me. It produces "

---

### Post by Gustav on 2006-11-24
I used to be able to hold down ctrl-shift and type a number to get those symbols, but now it doesn't work anymore. 

I don't know if it disappered when upgrading from breezy to dapper or from dapper to edgy.

(European (or at least Swedish) keyboards usually have @ at AltGr-2)

---

### Post by andyrobo60 on 2006-11-24
> **KedDeK said:**
> Shift+2 doesn't work for me. It produces "

Thats because you have your keyboard set to UK. On US keyboards the @ and " keys are swapped.

---

### Post by KedDeK on 2006-11-24
I have @ at AltGr+q, my keyboard is latin-american, not UK.

---

### Post by end3rkid on 2006-11-24
I would like a solution for this issue too. Any ideas?

---

### Post by CatKiller on 2006-11-24
I vaguely recall something about Ctrl-Shift-U and then Unicode numbers doing sometihng-or-other. Possibly that's similar enough to what you're after?

---

### Post by Gustav on 2006-11-25
> **CatKiller said:**
> I vaguely recall something about Ctrl-Shift-U and then Unicode numbers doing sometihng-or-other. Possibly that's similar enough to what you're after?

holding down ctrl-shift while typing u followed by the unicode number (in hexadecimals) is working. 

Great, thank you!

---

### Post by KedDeK on 2006-11-25
It doesn't work in my keyboard :(

---

### Post by Nephron on 2007-11-13
Wikipedia agrees wiht the Ctr+Shift+U combinations:
> In GTK+ applications, press Ctrl-Shift-U and then type the Unicode number (in hexadecimal) with Ctrl and Shift held down. Later versions do not require Ctrl and Shift to be held down while typing the number. GTK+ versions before version 2.10 require that you hold down Ctrl and Shift while entering the number (Ctrl-Shift-U does not exist in those versions). 

From the Wikipedia "[Alt codes]("http://http://en.wikipedia.org/wiki/Alt_codes")" aritical

---

### Post by shmengie on 2007-11-28
thx all. if i may question a bit further: while character map/ctrl+shft+u work for me, there's some characters i don't seem to be able to find. specifically, the degree symbol (alt-0126 in windows). i then noticed that stuff like copywrite and trademark don't seem to be in the latin set either. can anyone advise?

thx!

---

### Post by shirilover on 2007-11-28
Degree symbol -- °  > Ctrl+Shift+u + b0
copywrite -- © > Ctrl+Shift+u + a9 or Compose key+c+o
trade mark -- &#8482; > Ctrl+Shift+u + 2122

These can be found in the common section of the character map.

---

### Post by shmengie on 2007-11-28
> **shirilover said:**
> Degree symbol -- °  > Ctrl+Shift+u + b0
copywrite -- © > Ctrl+Shift+u + a9 or Compose key+c+o
trade mark -- ™ > Ctrl+Shift+u + 2122

These can be found in the common section of the character map.

d'oh! thx! (what's the 'compose' key?)

---

### Post by teryowen on 2007-11-28
Nice works

---

### Post by shmengie on 2007-11-29
> **shmengie said:**
> ...what's the 'compose' key?...
nvm. google is my friend.

---

### Post by MemoryDump on 2008-05-09
> **shirilover said:**
> Degree symbol -- °  > Ctrl+Shift+u + b0
copywrite -- © > Ctrl+Shift+u + a9 or Compose key+c+o
trade mark -- ™ > Ctrl+Shift+u + 2122

These can be found in the common section of the character map.

does this still work in Hardy? I'm trying to get this working and I haven't had any luck yet :(

---

