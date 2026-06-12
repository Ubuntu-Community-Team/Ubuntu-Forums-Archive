---
title: "Should I be concerned about this?"
date: 2014-08-30
forum: General Help
---

### Post by Lamin on 2014-08-30
O'k ... so I'm learning how to use the terminal in Ubuntu and I just learned about alias. 

I input 'alias' in terminal and get the following back:

   larinkaare@larinkaare-Inspiron-N4010:/usr$ alias 
 (1) alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"' 

 (2) alias egrep='egrep --color=auto' 

 (3) alias fgrep='fgrep --color=auto' 

 (4) alias grep='grep --color=auto' 

 (5) alias l='ls -CF' 

 (6) alias la='ls -A' 

 (7) alias ll='ls -alF' 

 (8) alias ls='ls --color=auto' 


I inserted the numerals for clarification but should I be concerned about (1)? 

Thank you for your help.

---

### Post by ian-weisser on 2014-08-30
No, you shouldn't be concerned.

When you types the command 'alias', the system lists all of it's aliases.
The 'alert' alias merely sends a notification.

Try the following example command to see the 'alert' alias in action.
```
alert "Example Text"
```

---

### Post by Lamin on 2014-08-30
Rotfl ... Thanks. I needed that : ) Good way to scare the 'ish out of a computer noob like me, lol. 

Imaginary prankster:  Lamin, what is this "Alert, you are being hacked" on your computer screen. 

Me: What! ********! (Sees screen) Omg, wtf!!!

---

### Post by CantankRus on 2014-08-31
Alert allows you to be notified when a long running command finishes.
eg
```
sleep 10; alert
```
or
```
sudo apt-get update; alert
```

---

