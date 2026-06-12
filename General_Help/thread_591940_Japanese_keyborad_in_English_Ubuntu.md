---
title: "Japanese keyborad in English Ubuntu?"
date: 2007-10-25
forum: General Help
---

### Post by osiris2258 on 2007-10-25
I would like to be able to type in Japanese in ubuntu. I have gotten SCIM to work, so I can input using romaji and have it convert. 
The thing is, I break out my Japanese keyboard when I want to type in Japanese, and I type based on the printed kana, rather than romaji (slightly ironic, since the most common input method in Japan is actually in romaji).

This means that I need to do 3 things:

1) have the computer recognize the Japanese board, with its associated extra keys. I have a manual way to do this but it still only takes the English input. Is there an automatic way?

2) have the computer use the extra keys normally. Thus far it ignores them.

3) have the computer accept input in Japanese mode based on the Japanese layout kana, not the English letters.

Anyone know how to do this?

---

### Post by jenhsun on 2007-10-26
I think computer is nothing to do with complex characters input. All it knows is 0 and 1.
And all you have to do is depended on your language plugin into your system, then your SCIM use your special-language table for doing the input and the link in between. 
Anyway, if you know SCIM's howto, that's good enough at least you know how to input japanese words.

---

### Post by osiris2258 on 2007-10-26
That is like telling someone who is used to Dvorak to suck it up and use qwerty. Yes, they can do it, but they have to look at there hands all the time and they make a ton of errors. If I am going to get any kind of speed or accuracy, I need to get Ubuntu to let me input based on the Kana, not romanization.

---

### Post by jenhsun on 2007-10-28
Problem solved.

Please take a look at this bug report
[https://bugs.launchpad.net/ubuntu/+s...cim/+bug/34282](https://bugs.launchpad.net/ubuntu/+s...cim/+bug/34282)

And the most important is the document in your
/usr/share/doc/scim/README.Debian.gz

---

### Post by osiris2258 on 2007-10-28
The link to the page about the bug leads to a 'page not found' error :rolleyes:

---

### Post by jenhsun on 2007-10-28
> **osiris2258 said:**
> The link to the page about the bug leads to a 'page not found' error :rolleyes:

Sorry, right here
[https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)

---

### Post by osiris2258 on 2007-10-28
This isn't quite what the problem is, although I will probably run into it later. If you look at an image of a Japanese keyboard, you will see that it has both a near qwerty English set and a Japanese language set. The problem is that when I am on the Japanese keyboard, it will only let me input with the English keys, whereas I type in Japanese based on the Japanese keys.

When typing in Japanese, there is actually a dedicated key (next to right control) that switches between English letters and Japanese kana. This dosen't work in ubuntu, so I am stuck in English input mode. I can still get Japanese to appear, since there is a method to accommodate English keyboards by taking the English phonetic sound and transliterating, but this is not the way I type in Japanese. I need to get the full keyboard working.

---

### Post by jenhsun on 2007-10-28
> **osiris2258 said:**
> This isn't quite what the problem is, although I will probably run into it later. If you look at an image of a Japanese keyboard, you will see that it has both a near qwerty English set and a Japanese language set. The problem is that when I am on the Japanese keyboard, it will only let me input with the English keys, whereas I type in Japanese based on the Japanese keys.

When typing in Japanese, there is actually a dedicated key (next to right control) that switches between English letters and Japanese kana. This dosen't work in ubuntu, so I am stuck in English input mode. I can still get Japanese to appear, since there is a method to accommodate English keyboards by taking the English phonetic sound and transliterating, but this is not the way I type in Japanese. I need to get the full keyboard working.

Sound like the Jap character table is mismatch.
Could you check the SCIM document about it? And before that please setup your keyboard correctly. That's very important. Look at my diagram

Keyboard <-> OS input handle <-> Application table converting (SCIM) <-> Your Screen

---

### Post by osiris2258 on 2007-10-28
Um...

I don't understand your diagram :confused:   What are you trying to tell me?

---

### Post by jenhsun on 2007-10-28
> **osiris2258 said:**
> Um...

I don't understand your diagram :confused:   What are you trying to tell me?

Forget about it. You just to make sure.

1. Your system's keyboard layout is correct. It has to match your physical layout.
2. Check your supported table in your SCIM.
3. Read the SCIM documents.

Sorry for not being helpful information for you.

---

### Post by serador on 2007-11-04
> **osiris2258 said:**
> 

3) have the computer accept input in Japanese mode based on the Japanese layout kana, not the English letters.

Anyone know how to do this?

UIM works but the extra keys doesn't.

 ```
sudo apt-get install uim-applet-gnome uim-xim uim-anthy uim-gtk2.0
```

Go to System>Preferences and right click on Input Method (uim) and add it to panel and choose Anthy, Hiragana and Kana

[https://help.ubuntu.com/community/JapaneseInput](https://help.ubuntu.com/community/JapaneseInput)

---

