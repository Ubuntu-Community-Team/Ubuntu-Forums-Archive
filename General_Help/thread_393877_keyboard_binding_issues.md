---
title: "keyboard binding issues"
date: 2007-03-26
forum: General Help
---

### Post by stavpal on 2007-03-26
I have a Ms Multimedia keyboard and would like to use the "extra keys" (Help, Undo, Redo, New....) and "MyDocuments, Mypictures etc)
Some of the keys (mydocuments, mute, volume, play/pause, stop, next/previous track, player, mail, webhome) work. The other ones though don't produce output.
I've found out with xev and /var/log/messages to find out the keycodes for the keys and have written a script. I've stumbled to a point though:
1)After I use "setkeycodes exxx yyy) (xxx & yyy are numbers) when I use xev I get a different keycode for that key. wtf?
2)I don't know how to bind the keys to do something (for example undo, redo, new, open, close...)
3) where do I have to put the script so it runs as root (it needs sudo because It has the command setkeycodes exxx xxx)
4)even after I run the script manually in terminal, the "getkeycodes" show the keycodes I;ve set, yet nothing happens
Can anyone help?
Thanks in advance

---

### Post by Moordrik on 2007-03-26
Depending on your keyboard, the solution to your problems may be much simpler than using xev/setkeycode/xbindkeys or whatever your choice.  You should take a look at [http://keytouch.sourceforge.net](http://keytouch.sourceforge.net) and see if they have your keyboard listed.  If they do just grab that and your set =)

---

### Post by stavpal on 2007-03-27
I like to do it the hard way. Anyway, I've figured out almost everything - I just need to know what commands do I need to input in xbindkeys (I mean for "new",  "open" etc....) I can do for bindings to open folders or run programs

edit: it worked with keytype, although I would still like to know the "scripts" for new, open, undo, redo etc

---

### Post by shakma on 2007-03-30
Wow!  Thank you Moordrik!  I have been fooling with this keyboard binding "the hard way" for far too long.  Swallow your pride, stavpal.  keytouch is the future.  I'd love to see this integrated right into ubuntu.

Peace.

---

### Post by hackerssidekick on 2007-04-13
If you've got a keycode in X (ie xev prints out a keycode for the key), then you can assign commands to that key.

This gives a good idea on how to do it: [http://www.qte.dk/articles/linux/logitechnavigatorkeyboard/](http://www.qte.dk/articles/linux/logitechnavigatorkeyboard/)

---

