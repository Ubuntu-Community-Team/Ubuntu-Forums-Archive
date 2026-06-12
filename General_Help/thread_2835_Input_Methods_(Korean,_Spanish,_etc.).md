---
title: "Input Methods (Korean, Spanish, etc.)"
date: 2004-11-01
forum: General Help
---

### Post by moon2js on 2004-11-01
I'm wondering if anyone has had any luck with installing non-English input methods.

Most of the howtos I've read about localization aren't very helpful for me (or are awfully dated) and I've had some problems accidentally switching things I need like manpages into a language I'm not fluent in. I'd like to keep the system in English, but I want the option of being able to type in Korean or type in Spanish using my American keyboard.

Is there any easy way of doing this in Ubuntu? Has anyone any recomendations for input methods?

---

### Post by ynef on 2004-11-01
I'm from Sweden and use a Swedish keyboard, but have Gnome running in English. How I accomplished this is still a mystery to me because it was late at night and I had to dick around with settings for about an hour or so, but some of the things I tried was:

* Generate the Swedish locale (dpkg-reconfigure locales), not setting it default for the system
* Add the lines:
```
export LC_MESSAGES=sv_SE
export LANGUAGE=sv_SE
export LANG=sv_SE
```
to my .bash_profile
* Set the keymap in Gnome (Computer -> Settings -> Keyboard)
* Change font for use in terminals, because the one that was used by default for some reason didn't support our beloved åäö letters

I'd go with trying the third step first, but the others are possibly also needed. I'm sorry I don't know what I did to accomplish it. :(

---

### Post by macsaint on 2004-11-01
You can refer to my blog..

[http://kr.blog.yahoo.com/jungwukhong/1359850.html](http://kr.blog.yahoo.com/jungwukhong/1359850.html)

JW

---

### Post by moon2js on 2004-11-05
&#51652;&#51676; &#44256;&#47560;&#50892;&#50836;!

I installed nabi and as of now it seems to be working. But just now I noticed that it tends to suddenly switch to hangeul while I'm typing in English.

For example I&#12641;&#54672;&#49548; &#46272; &#49660;&#45936;&#12625;&#54980; --see? it just happened. Is this a bug?

And how do I&#49660;&#12628;-- how do I type hanja?

OK, I'm going to try using nabi in email and IM for a day or so and see if it works out. Wait, I'm also noticing that for some unknown reason, the typing cursor is suddenly repositioned to the top line of the text box randomly while typing and that's really annoying. Did I install something incorrectly?

---

### Post by moon2js on 2004-11-05
And another thing. Iis there a way to change the han/eng button to something less annoying than shift-space? I've traced the random language switching down to the fact that my typing habit is to press the shift key early when typing a capital letter after a space, which causes it to switch into Korean!

---

### Post by oseb on 2004-11-05
If you use usb-keyboard or 106 key, you must recompile kernel.
Edit 95 lines in (source path)/linux/drivers/input/input.c source file.

[From]
if (code > KEY_MAX || !test_bit(code, dev->keybit) || !!test_bit(code, dev->key) == value)
return;

[To]
if (code != KEY_HANGUEL && code != KEY_HANJA) {
if (code > KEY_MAX || !test_bit(code, dev->keybit) || !!test_bit(code, dev->key) == value)
return;
}


I use shift+space key in nabi. because kernel compile is uncomfortable.
Have a good luck. 

--
[http://joycode.net/ubuntu](http://joycode.net/ubuntu)

---

### Post by diebels on 2004-11-05
It's easy to set this in the keyboard thing in gnome-control-center.

---

### Post by oseb on 2004-11-05
Kernel dose not assist han/eng key in korean usb keyboard.
xev can not catch han/eng key event
therefore kernel compile is necessary.

---

### Post by diebels on 2004-11-05
Ok. Maybe you should make a bug report.

---

