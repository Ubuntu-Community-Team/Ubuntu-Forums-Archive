---
title: "Canadian Multilingual keyboard bug for one French character"
date: 2008-07-07
forum: General Help
---

### Post by Browser_ice on 2008-07-07
I have just noticed that the Canadian keyboard settings that I have just switched to has a bug when it comes to type one specific French character.

When I press the key to have the letter 'e' with a hat on top of it, all I get is the '^' hat only. If I try to type the 'e' before and then type the '^' hat, all I get is 'e^'. All other French accented characters are ok except this one.

Why isn't it working ?

Will I have to switch to another keyboard to have all the French accented characters work ?  I am used to work with the Canadian Multilangual one at the office.

This is with Ubuntu 7.10 by the way.

[added comments]
I thought there were different Canadian French version keyboard but there seams to be only one ???

---

### Post by Browser_ice on 2008-07-13
Anyone care to answer ?

---

### Post by lukjad on 2008-07-13
You need to hit the ^ key first. Taadaa: ê. If you do it the other way around all you get is the symbol all on it's own. By hitting the ^ key you are telling the word processor that the next character, (assuming it is one that needs and can use this accent) must have this accent. So the hitting ^ and then hitting "space" tell your computer to just leave it hanging in mid air. Here are a few examples: êâôû

---

### Post by Browser_ice on 2008-07-13
I know that. I have been using Canadian French keyboards for years.

It does not work if I press ¨ "hat" first or last.

The same things goes for ¨  "2 dots"

Both are on the same key.


Just tried to remove the Canadian Multilingual and add the Canadian French. Keyboard is about the same but the problem still remaines.

My keyboard is a Logitech Media Keyboard Elite which I cannot find in the list of available keyboards on my Ubuntu 7.10

---

### Post by lukjad on 2008-07-13
> **Browser_ice said:**
> I know that. I have been using Canadian French keyboards for years.

It does not work if I press ¨ "hat" first or last.

The same things goes for ¨  "2 dots"

Both are on the same key.


Just tried to remove the Canadian Multilingual and add the Canadian French. Keyboard is about the same but the problem still remains.

My keyboard is a Logitech Media Keyboard Elite which I cannot find in the list of available keyboards on my Ubuntu 7.10

Sorry if the answer last seemed overly simplistic but that answer usually solves this type of problem. The keyboard sounds reasonable. Can you try out another keyboard and see if that one works better? It could just be a jammed or broken key.

---

### Post by Browser_ice on 2008-07-13
Tried it with Canadian Multilingual and Canadian French. Both have the same problem.

If I switch to English keyboard, the key works fine. So that rules out any jammed or mal-functioning key.

Just tried removing my Canadian layout and added the France one. I have the same problem with that key again (^ hat on same key for that other keyboard profile).

I am pretty sure it is not related to any physical problems with the key but rather software (using keyboard profile P105 since no match found for my Logitech Media Keyboard Elite keyboard)

---

### Post by lukjad on 2008-07-13
[https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/46586](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/46586)
[http://ubuntuforums.org/showthread.php?t=858388](http://ubuntuforums.org/showthread.php?t=858388)
[https://help.ubuntu.com/community/KeyTouch](https://help.ubuntu.com/community/KeyTouch)
[http://ubuntuforums.org/showthread.php?t=202245](http://ubuntuforums.org/showthread.php?t=202245)
Read these. Somewhere there must be an answer. I'll keep looking. Tell me if this helps. The last one looks promising.

---

### Post by lukjad on 2008-07-13
[http://www.ubuntuforums.org/showthread.php?p=1336764#post1336764](http://www.ubuntuforums.org/showthread.php?p=1336764#post1336764)
May not be exactly what you are looking for mut may work anyway.

---

### Post by lukjad on 2008-07-14
Do any of those links help you?

---

