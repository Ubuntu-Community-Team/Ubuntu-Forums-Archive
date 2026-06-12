---
title: "Bottom of part of Chinese characters doesn't change in ibus"
date: 2014-03-14
forum: General Help
---

### Post by chickendude2 on 2014-03-14
I'm not really sure what the best way to describe this, so i'll share some pictures.
1. Start typing a character. Notice the gray line in the middle.
[ATTACH=CONFIG]251150[/ATTACH]
2. Type the next letter of the character. The list of possible characters changes, but the bottom part (underneath the gray line) still shows the previous characters. So it's half one character, half another.
[ATTACH=CONFIG]251149[/ATTACH]
3. Adding another character or doing something so that the size of the box changes will refresh the whole box and the characters will display normally from now on. (Here the &#20102; character makes the ibus box one character larger)
[ATTACH=CONFIG]251148[/ATTACH]

So if i want to type/change just one character, i can't see what the character is. It's not a huge issue when typing sentences or phrases, since once the ibus box changes size everything updates normally, i just won't be able to see what the first character is until i've added another.

I'm on Ubuntu 13.04, but i don't think this is an Ubuntu-specific bug as i remember having it on Fedora, too. I don't remember having it on older (pre-Unity) versions of Ubuntu, though.

Thanks in advance :)

---

### Post by chickendude2 on 2014-03-18
Does anyone have any ideas or perhaps suggestions where else i can ask to try to figure this out? Thanks :)

---

### Post by chickendude2 on 2014-03-30
Alright, well i switched back over to Fedora and it seems to have a different ibus system. I'm not sure. But either way, i don't have the problem anymore and can type Chinese characters just fine now. Sorry i couldn't find a solution to this issue, if someone comes up with something i'd still be glad to hear.

Anyway, thanks to anyone who may've put an effort into trying to figure this sucker out, i do appreciate it even if nothing really came of it in the end.

---

### Post by monkeybrain20122 on 2014-03-31
13.04 has reached end of life in Jan. You should install 13.10. 

As for your problem about ibus, I am not going to be of much help since I don't use it and know nothing about pinyin.
However, I have just set up Chinese support for someone on Ubuntu 13.10, based on my web research ibus is apparently quite broken in 13.10. You may want to take a look at these links:

[http://askubuntu.com/questions/360774/how-do-reactivate-ibus-after-upgrading-to-ubuntu-13-10](http://askubuntu.com/questions/360774/how-do-reactivate-ibus-after-upgrading-to-ubuntu-13-10)
[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1241309](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1241309)

Then I read about fctix, it is highly recommended by many people and is the default for kylin-ubuntu. So in the end I didn't bother with ibus, I installed fctix and set it as default. But I have no idea how well it work, I will get my friend's feedback when I give him the computer next week.

---

### Post by chickendude2 on 2014-03-31
Thanks for the links, the next time i'm on Ubuntu (if the ibus issues aren't fixed by then, at least), i'll definitely give fctix a shot. For now, pinyin input is working great with Fedora. :)

---

### Post by Pedroski55 on 2014-03-31
ibus works fine for me in 12.04, I use it every day. I suggest a reinstall.

---

