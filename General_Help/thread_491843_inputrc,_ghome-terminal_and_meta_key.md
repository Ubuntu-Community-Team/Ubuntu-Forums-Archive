---
title: "inputrc, ghome-terminal and meta key"
date: 2007-07-04
forum: General Help
---

### Post by slackorama on 2007-07-04
Hi --

I've got my INPUTRC set to ~/.inputrc. I've got the following definition in my ~/.inputrc
```
"\M-o": "\C-p\C-a\M-f "
```

but when I press Alt-o nothing happens.  Is there something else I need to do to get these binding working properly?  Other commands I have in my .inputrc work fine (like 'Space: magic-space)  

I notice too that other Alt commands don't work (like M-f).  Is this becuase I'm running in gnome-terminal?  or something else? 

Thanks in advance for help.

---

### Post by jyba on 2007-07-05
I'd be interested too if someone can explain how to get Meta key working properly.

I've tried out the Readline stuff in the bash manual and none of the Meta stuff seems to work. The only way I can get your keybinding to work is to use an escape character "\e" instead of the meta prefix "\M-"

```
"\eo": "\C-p\C-a\ef"
```

---

### Post by stylishpants on 2007-07-06
The meta key has always worked perfectly for me by default.  This is in a Gnome environment, using gnome-terminal (but it also works in other terminal programs as well.)

A couple of things to check:

-Do you have a ~/.xmodmap file?  This could be used to remap the meta key.  ('man xmodmap' for more details)

-Have you checked your window manager / desktop environment's keyboard settings?  In Gnome (on Feisty Fawn), find them in the menu here: System->Preferences->Keyboard, "Layout Options" tab, "Alt/Win key behaviour" setting.

---

### Post by slackorama on 2007-07-07
Still no go for me.  

Everytime I press Alt-o nothing happens.   If I press Alt-f it opens the File menu when it should move forward a word.

Tried a bunch of different options under the Keyboard Layout Options involving the meta and win keys but nothing worked.  And I don't have an ~/.xmodmap file.

What are you keyboard alt/win settings.

---

### Post by slackorama on 2007-07-10
Hmm, the escape character syntax that jyba posted works.  

Now I'd like to know why too.

---

### Post by slackorama on 2007-07-10
Found this for those that are interested:

[https://bugs.launchpad.net/ubuntu/+source/readline5/+bug/56734](https://bugs.launchpad.net/ubuntu/+source/readline5/+bug/56734)

---

