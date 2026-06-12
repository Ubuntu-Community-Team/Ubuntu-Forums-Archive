---
title: "An easy guide to navigate Terminal for Beginners-Intermediate users"
date: 2012-11-24
forum: General Help
---

### Post by shantiq on 2012-11-24
An easy guide to navigate Terminal for Beginners-Intermediate users

in the words of Gandhi; Donald Duck and Joseph Stalin [alledgedly]

**"...if navigation is smooth you will have much more fun"**



Many of you will know this; clearly this is for the ones who do not yet:KS
If you have additional useful adjuncts please feel free to comment...

**navigate terminal**

> 
ctrl+a   to the start of writing
ctrl+e   to the end of writing
alt+b    goes back one word at a time
alt+f     moves forward one word at a time.
ctrl+b   goes back one letter at a time
ctrl+f    goes forward one letter at a time
ctrl+u   removes command left of cursor
ctrl+k   removes command right of cursor 

ctrl+w deletes the word before the cursor.
alt+c    capitalizes letter where cursor is and moves to end of word


ctrl+l  clears the terminal output
when a page is too busy   and you want a clean slate ctrl+l followed with ctrl+u clears everything


Shift + Ctrl + C = copy the highlighted command to the clipboard.
Shift + Ctrl + V (or Shift + Insert) = pastes the contents of the clipboard.




"**history**"   shows you your most recent commands


say you want to use 1951 command   enter    > !1951


very handy   see > man history for full info




_**incremental history searching**  _


[**from**]("http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/") 

in terminal enter:



```
gksudo gedit  ~/.inputrc
```


then copy paste and save


```
"\e[A": history-search-backward
"\e[B": history-search-forward
"\e[C": forward-char
"\e[D": backward-char
```


FROM now on [and many agree this is **[FONT="Century Gothic"]the most useful terminal tool[/FONT]**] save you a lot of writing/memorizing...

all you need to do to find a previous command is to enter say the first 2 or 3 letters and upward arrow will take you there quickly


say i want:

```
for f in *.mid ; do timidity "$f"; done 
```

all i need to do is enter ```
fo
``` and hit upward arrow command will soon appear

---

### Post by coffeecat on 2012-11-24
> **shantiq said:**
> 
in terminal enter:

```
sudo gedit  ~/.inputrc
```

Ahem! Cough, cough. 

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

> You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs.

I'll leave you to edit your post. :wink:

**Afterthought:** we are encouraging people to put howtos on the community wiki - the forum is not the best place for this. You have some information which I believe is not on this wiki page:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Have you considered getting involved in wiki work?

---

### Post by shantiq on 2012-11-24
thanx cat

changed to gksudo


more than happy to put it in wiki; will get on the case...

edit: relevant bits [**added**]("https://help.ubuntu.com/community/UsingTheTerminal#Change_the_text")

---

### Post by coffeecat on 2012-11-24
> **shantiq said:**
> edit: relevant bits [**added**]("https://help.ubuntu.com/community/UsingTheTerminal#Change_the_text")

Thanks! :)

---

