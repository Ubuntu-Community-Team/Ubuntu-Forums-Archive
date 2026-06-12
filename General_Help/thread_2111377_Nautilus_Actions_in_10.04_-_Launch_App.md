---
title: "Nautilus Actions in 10.04 - Launch App?"
date: 2013-02-01
forum: General Help
---

### Post by Alaksandu on 2013-02-01
Hello,

I installed Nautilus Actions in my Lucid Lynx. Not surprisingly I'm having trouble setting it up.

What I want to do:
Right-click on .JPGs or .jpgs. Get 'Exiftran' in the menu. Have it run exiftran -i -a on the selected file(s) when activated. 

What I've managed:
The right-click menu has Exiftran when and only when a JPG or jpg is selected. It does nothing.

I've fed the following into the Command GUI section. I suspect the problem is here:
Path: /usr/bin/exiftran
Parameters: -i -a

Thank you for any help.

---

### Post by mc4man on 2013-02-02
Haven't used that old a version of N-A for quite some some time. You'll need to add a %<something> to your parameters, click on the "Legend" box to see available.
I guess I'd try %M first, like
```
-i -a %M
```

---

### Post by Alaksandu on 2013-02-04
Thank you! %M seems to have solved it. I did try to read the Legend thing but it was cryptic. Too bad since the authors had obviously tried hard to make it all easy to use: it came just a little bit short.

I doubt this will help anyone this late in the game, but some things I learned about the process:
[LIST]
[*]use 'which' or 'locate' to find the application you want
[*]Be careful with the filename wildcards: the box for them appears to be buggy, and spaces will break things.
[*]Apparently you should add an empty scheme and enable it in the advanced options if you want things to work universally.
[/LIST]

---

