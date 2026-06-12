---
title: "Japanese Kana input 13.10"
date: 2013-11-06
forum: General Help
---

### Post by Karolina.K on 2013-11-06
Konnichiwa

I have a japanese keyboard on my computer so I dont wat to use the japanese anthy ibus input. I want to use the ubuntu kana input.
However the Zenkaku Kanji key (§) does not respond. all the characters are katakana by deafult but with that key it would change to either hiragana
or kanji. 

Please help as I want to be able to write japanese asap :D 

Arigatou

---

### Post by Karolina.K on 2013-11-06
Hello

My computer has japanese kana input (japanese characters on the keyboard) and by default it types katakana characters. however this should easily be converted either to kanji or hiragana using the kanji zenkaku key (§) however this do not work.

I do not want to use the ibus anthy :/

Plz help

arigatou ^_^

---

### Post by howefield on 2013-11-06
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=2186177](http://ubuntuforums.org/showthread.php?t=2186177)

---

### Post by Bucky Ball on 2013-11-06
Oops. Sorry howefield. I merged them before reading your post. 

Anyhow, @miyamoto2: Please refrain from duplicate posting. Thanks. ;)

---

### Post by Karolina.K on 2013-11-07
ah hai, but I really need help in how to fix it ><

---

### Post by Bucky Ball on 2013-11-07
Duplicate posting will not increase your chances of support. Just the opposite. It dilutes community effort and confuses the issue. Much better if everyone is working on the same problem on the same thread rather than scattered thoughts scattered about the forums. Thanks.

Feel free to bump the thread once every twenty four hours. If no-one is responding it is because they can't help. Duplicate posting will not change this fact.

---

### Post by Karolina.K on 2013-11-07
ah okey ,  bump desu

---

### Post by Karolina.K on 2013-11-08
bump

---

### Post by Bucky Ball on 2013-11-08
> **Bucky Ball said:**
> Feel free to bump the thread once every *twenty four hours.* If no-one is responding it is because they can't help. 

Obviously not many users experienced with Japanese keyboards here that can help for now. Good luck and keep trying. Have you tried other forums and web searches?

---

### Post by Karolina.K on 2013-11-08
ah yes I have searched alot and there is a question from 2011 which adresses the same issue on askubuntu but noone has answer there either :/

---

### Post by Karolina.K on 2013-11-09
bumpu

---

### Post by jhodowany on 2013-11-09
Not sure if [COLOR=#000000]miyamoto2 has figured this out. My upgrade to 13.10 severely messed up (rendered useless) my ibus chinese input. Many others have posted of similar experiences. What solved the issue for me was to migrate to the fcitx input framework. The setup was easy (check out a good guide at [/COLOR][https://wiki.archlinux.org/index.php/Fcitx](https://wiki.archlinux.org/index.php/Fcitx)). I had it working in 5 minutes. There is a section for setting up Japanese input, and I see they have an fcitx-anthy module in the standard saucy/13.10 repositories.

---

### Post by jhodowany on 2013-11-09
I should have said, the above link is for archlinux, but the advice for setting up environmental variables is the same for ubuntu. Just remove all the ibus* packages, then install the fcitx package and your input method fcitx-anthy. Get your environment variables set (.profile, .bashrc and/or .xsessionrc) and re-login. Set up to autostart, then re-login.

---

### Post by Karolina.K on 2013-11-12
ah yes thanks, katakana input work ,however when I press the zenkaku(§) button it doesnt change to  hiragana or kanji,

---

### Post by Karolina.K on 2013-11-17
bump

---

### Post by Karolina.K on 2013-11-21
bump

---

