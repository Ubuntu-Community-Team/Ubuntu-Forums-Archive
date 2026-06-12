---
title: "Want to make a simple script to change keyboard layout"
date: 2018-04-23
forum: General Help
---

### Post by Nazosan on 2018-04-23
So this should be really simple.  I just want to be able to quick change keyboard layouts via a simple script.  While I am aware of dpkg-reconfigure console-setup and the X equivalents, I don't want it to permanently change.  I just need to be able to change keyboard layouts only when I'm using an external keyboard and stick with QWERTY with the internal (it's for a device with a not so great built-in keyboard, so I basically can't go by touch.)  So I have the idea to just simply type "dvorak" to switch to Dvorak when I want that (and I guess while I'm at it I should throw in a "qwerty" to go back, though I doubt I'd need it.)  And yeah, in case it's not obvious I want to switch to the Dvorak layout (specifically the US variant, not the UK one.)

I of course googled around a bit first.  It seems loadkeys can do what I want.  Unfortunately you have to point it to an appropriate keymap file.  It seems these files (if they're even still there?) aren't in the same place in Ubuntu now.  Or maybe I must install some particular package first now?  I have no idea what to even look for to find them.

Also, I should probably do this with X too.  I think setxkbmap is supposed to be able to do this with it?  I don't entirely know how to use it either, but I take it I want to do something like [COLOR=#111111][FONT=Consolas]setxkbmap -layout "us,dv" [/FONT][/COLOR]?

---

### Post by kerry_s on 2018-04-23
settings-> region & languages
set your input sources

win+space switches input sources

---

### Post by Nazosan on 2018-04-23
And how does this work in a console?  This isn't quite what I want anyway.  A script would serve my purposes exactly and as far as I know it should actually be pretty easy to do -- I'm only thwarted by one of the simplest aspects of it.

---

### Post by kerry_s on 2018-04-24
you didn't say you wanted a console only option.
you already said you know the commands.

> dpkg-reconfigure console-setup
setxkbmap -layout "us,dv"

---

### Post by kerry_s on 2018-04-24
if the commands are to long to type you can use aliases
example:
alias dvk='setxkbmap -layout "us,dv"'

---

### Post by Nazosan on 2018-04-24
Or I can just make a script.  My plan is to be lazy and just put both commands in a single script and simply run that in a terminal or console as needed.  And yeah, I didn't explicitly say console, but I thought that was rather implied given that I was using console-setup (why would I do that for X?)  Actually, at the time I couldn't get the GUI to even work right on this device, but I think I actually got it working.  I still need to be able to do this in the console though.  In fact, I need it more there than in X.

dpkg-reconfigure console-setup is a permanent change.  I want to do a temporary change.  loadkeys is probably what I want, I just need to know where the file is to give it...

---

### Post by kerry_s on 2018-04-24
why would a single command require a script? i don't get it you seem to want to make it more complicated than it is.

if you'll feel better with a script:
```

#!/bin/sh
setxkbmap -layout "us,dv"

```

---

### Post by Nazosan on 2018-04-24
Nevermind.  Let's just simplify:  I need to change the keyboard layout in the console, not in X, and I need it to be a temporary change, not a permanent one.

---

### Post by again? on 2018-04-24
There is a script [HERE]("https://unix.stackexchange.com/questions/2884/toggle-between-dvorak-and-qwerty/2907#2907") that may get you going.
```
#!/bin/bash

if [ -n "$DISPLAY" ]; then
  if xmodmap -pke | awk '$3=="=" && $4=="q" {q=$2}
                         $3=="=" && $4=="w" {w=$2}
                         END {exit w-q==1}'; then
    setxkbmap us
  else
    setxkbmap dvorak
  fi
elif [ "$TERM" = "linux" ]; then
  if dumpkeys | awk '$3=="=" && $4=="q" {q=$2}
                     $3=="=" && $4=="w" {w=$2}
                     END {exit w-q==1}'; then
    loadkeys us
  else
    loadkeys dvorak
  fi
fi
```
I tested here by first making loadkeys executable without sudo.
```
sudo chmod +s /bin/loadkeys
```

Worked in X but not in console.
Don't really use different keyboard layouts.
Perhaps you can adapt with what you know.

---

### Post by Nazosan on 2018-04-24
Oh geez.  The googled solutions told me I had to point it to an actual layout file.  It never even occurred to me to just type the name of the layout.  *Sigh*  Thank you very much.  I tested that just now and it did indeed work.

---

### Post by ajgreeny on 2018-04-24
Great news! 

Please now mark as SOLVED from the Thread Tools menu up-top if this is solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by Nazosan on 2018-04-24
No problem.  It's now marked as solved.

BTW, I just kept things uber-simple.  I simply created two simple scripts.  One /usr/bin/dvorak and one /usr/bin/qwerty.  Each just does loadkeys followed by setxkbmap.  Rather than toggling, I just run whichever.  And it doesn't matter that the wrong one will fail (eg can't use setxkbmap in the console and loadkeys does nothing in X) because it just produces a minor error or does nothing.  This seems a little more intuitive and keeps it simpler for me.  Kind of strange that loadkeys wants higher permissions though...  I guess that's easily enough solved.

---

