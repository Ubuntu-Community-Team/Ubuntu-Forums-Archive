---
title: "Mutt--character probs on tty"
date: 2005-04-10
forum: General Help
---

### Post by dontodd on 2005-04-10
I'm a convert from Mandrake (now Mandriva  :wink: ) ; I just installed Hoary leaving my /home partition intact from my mdk install. I built mutt 1.5.9i from source to include the trash folder patch.

At first I had problems with the characters that displayed threading inside gnome terminal. Setting encoding to utf-8 in my muttrc and adding 

source /usr/doc/mutt/samples/iconv/iconv.osf1-4.0d.rc

to the system-wide Muttrc took care of that problem.

However, when I use mutt from say tty1 I have the problem with the characters for threading--these are basically pipes and lines/arrows to denote who replied to whom. I'm getting output like

wq>
x mq>
x     mqmq>

instead of 

|
|->
|--->

Any ideas on how to fix this, or is it strictly a mutt issue?

Todd

---

