---
title: "keyboard remapping to half-qwerty"
date: 2007-12-28
forum: General Help
---

### Post by akimatsu123 on 2007-12-28
im not sure if you've heard about the half-qwerty typing method. 

it basically maps reflects the keyboard over the gh keys when you hold space, allowing you to type with one hand. also, it's still the qwerty layout, so you wont have the problem of not being used to other computers' keyboards. 

i would like to be able to use my mouse and type at the same time. 

there are hardware for this (actually ONE company makes them i believe?) but i'd rather not spend the money, and even if i wanted to, i live in a place where this kind of uncommon tech isnt really sold. 

i heard there are ways to do this with software, through a script. is that true? do you know any free ways of doing this? 

thanks in advance

---

### Post by SOULRiDER on 2007-12-28
Youve already started a thread in the Absolute Beginner section, please dont double post, it will get you nowhere.

[http://ubuntuforums.org/showthread.php?t=652051](http://ubuntuforums.org/showthread.php?t=652051)

---

### Post by bingoUV on 2007-12-28
How do you type space then? Or did I understand you incorrectly?

Anyway, you need to modify the keymapping. Space needs to become a modifier. To figure out the internal codes of keys, use xev. 
```

man xev

```To change the mapping, and to change modifiers,  use xmodmap. 
```

man xmodmap

```Post here if you have any questions.

---

### Post by akimatsu123 on 2007-12-28
you type space by just pressing space. 

As in SPACE --> a space but (f + SPACE) --> j since j is in the same position as f on the other side of the keyboard.

edit:

hmm ive looked at those two commands. do you have a tutorial of some sort that i can read from? i'm quite a beginner and i dont really know what to do with them (even after reading the manual)

thanks a lot

---

### Post by akimatsu123 on 2007-12-28
how do i define space as a modifier key? 

can someone give an example of one key?

for example the code for making <space + f> be <j>. i can do the rest of the tedious work but i just need an example.

---

### Post by bingoUV on 2007-12-29
As far as I know, if a key is a modifier, it is a modifier only. Like ctrl. It does not have any effect of its own. So if you want to make space a modifier, it will not be able to type space; but you can type your own thing by space+any_other_key. 

If you pick some useless key(say with keycode XYZ) and want to switch using that key instead of space, you have to do something like the following. 
```

xmodmap -e "keycode XYZ = Mode_switch"
xmodmap -e "keysym f = f F j J"

```

Now if you press your useless key whose keycode is XYZ, and press f along with it, j will be sent to the application. shift+XYZ+f will send capital J.

---

### Post by akimatsu123 on 2007-12-29
thank you very much. and how would i go back to the original config? if i somehow screw it up i'd like to know i can go back before i start. haha.

edit: i also read that the space can be functional if it is defined as a "third-level modifier". just something i have read i have no idea what it means is this easy? or is it too complicated for a newbie like me to do.

---

### Post by bingoUV on 2007-12-30
Whatever  you do this way is not permanent. A ctrl-alt-backspace will get you back to your default configuration. You need to add these commands to your ~/.xsession file for them to run everytime you start a X session.

---

