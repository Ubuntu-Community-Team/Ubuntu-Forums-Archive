---
title: "Mac Keyboard Layout"
date: 2007-08-31
forum: General Help
---

### Post by GavMJM on 2007-08-31
Sorry if I sound like a bit of a cheese posting this, but I can't seem to find a solution to this problem.

The keys on my keyboard are arranged like this:

[IMG]http://www.freefileuploader.com/files/5s0doaiqhq7eaul5sm30.jpg[/IMG]

Its a UK Apple Keyboard. I've tried all the different 'United Kingdom' layouts, and they all seem to be wrong. The keys affected are | @ " ~ 

Anybody know what layout I should be using to get the above keyboard sorted?

Thanks,

Gav.

---

### Post by coffeecat on 2007-08-31
Two comments:

I've been trying to get one of my Linux boxes to use the UK Mac keyboard layout, so far without success. Apparently you need to edit /etc/X11/xorg.conf so that in the "Input Device" Section for the keyboard, the XkbModel value line is:

```
Option      "XkbModel"      "macintosh"
```Trouble is, if I have:

```
Option      "XkbLayout"      "gb"
```the @ and " keys work fine, but it won't respond to any of the letter keys which makes logging in a bit difficult. :wink: (Actually this is with Gentoo - Feisty is on another machine.) If I change the "gb" to "us", most of the keyboard works but, of course, it works as though it's a US keyboard which has yet another layout.

My Mac keyboard is connected to the Gentoo box and to a Mac Mini through a KVM switch, so it's just possible the KVM switch may be causing a problem - I haven't tried without yet. I'll be interested to hear what you get.

Second point: I was rather surprised to see the picture of your UK Mac keyboard, because mine has a difference. (I'm posting from my Mac Mini at the moment.) It's a white one just like yours, but the ~ ` key is next to the left shift key, and the \| key is nest to carriage return. I.e, they are swapped over from the positions of yours. Very odd. :?

---

### Post by GavMJM on 2007-08-31
> **coffeecat said:**
> Second point: I was rather surprised to see the picture of your UK Mac keyboard, because mine has a difference. (I'm posting from my Mac Mini at the moment.) It's a white one just like yours, but the ~ ` key is next to the left shift key, and the \| key is nest to carriage return. I.e, they are swapped over from the positions of yours. Very odd. :?

Actually, its probably just me - I took all the keys off and probably put them on wrong :P

Thanks for your help though :)

EDIT: Actually, I think you've got your keys wrong, not me. I'll Google it now :)

---

### Post by coffeecat on 2007-09-01
> **GavMJM said:**
> EDIT: Actually, I think you've got your keys wrong, not me. I'll Google it now :)

Well - if they're wrong, it's Apple that's got it wrong. :) The keys are exactly as they were when I lifted the keyboard out of the box about a year or so ago when I first bought it. Unless, that is, I've got a poltergeist in the house. :wink:

I'll be interested to hear what Google turns up, and I'll check to see what the layout is on some Mac-using friends' keyboards.

If you try that "XkbModel"      "macintosh" line, do please post what happens. I'll be interested to hear.

---

### Post by GavMJM on 2007-09-01
> **coffeecat said:**
> Well - if they're wrong, it's Apple that's got it wrong. :) The keys are exactly as they were when I lifted the keyboard out of the box about a year or so ago when I first bought it. Unless, that is, I've got a poltergeist in the house. :wink:

I'll be interested to hear what Google turns up, and I'll check to see what the layout is on some Mac-using friends' keyboards.

If you try that "XkbModel"      "macintosh" line, do please post what happens. I'll be interested to hear.

Well, that picture I posted was actually someone elses. I think we're right, and he was wrong. Not sure though.

I'm going to try that thing soon, but I've got one or two faults with authentication. It won't let me become a super user arghhh :P

Shouldn't be long though, then I'll let you know =]

EDIT: Okay. Right now I have it 'semi-working'. The @ " | \ are all correct. However, the key at the bottom left of the keyboard with the 'curly hyphen' on it produces < and > (with shift)...

Geesh. So close too :P

---

