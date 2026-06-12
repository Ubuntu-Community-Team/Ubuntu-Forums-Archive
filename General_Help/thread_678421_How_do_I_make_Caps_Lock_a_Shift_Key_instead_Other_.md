---
title: "How do I make Caps Lock a Shift Key instead? Other posts don't work"
date: 2008-01-25
forum: General Help
---

### Post by videodrome on 2008-01-25
Hi. How do I make my Caps Lock key and they left Shift key act the same? So I would have 3 total shift keys (caps lock, left shift , and right shift all acting like shift keys)? 

Threads like this one don't work for me. One key always becomes a Caps Lock no matter what I do.

[http://ubuntuforums.org/showthread.php?t=490402&highlight=caps+lock]("http://ubuntuforums.org/showthread.php?t=490402&highlight=caps+lock")

Thanks

---

### Post by accatagon on 2008-01-25
The following should work (and by that I mean it worked for me).

```
xmodmap -e "remove lock = Caps_Lock"
xmodmap -e "add shift = Caps_Lock"

```

If that works, then put the following in ~/.xmodmap
```
remove lock = Caps_Lock
add shift = Caps_Lock

```

---

### Post by videodrome on 2008-01-26
Ok that worked. Here's how for others:

So I then put the 2nd set of commands in a file called .xmodmap in my home directory.

Then I made a created a text file with the following inside of it:

```
#!/bin/bash

xmodmap ~/.xmodmap
```

Then I saved this text file in my home directory as keyboard.sh. I made it executable as well.

Then I added ~/keyboard.sh to my startup programs. 

Works great. No more caps lock. 

Thanks

---

