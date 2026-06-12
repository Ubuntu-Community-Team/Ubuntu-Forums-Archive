---
title: "[ubuntu] 16.04 32bits xdotool"
date: 2019-05-04
forum: General Help
---

### Post by lchachay on 2019-05-04
Hello Folks,
I have a question about xdotool
I have been trying the command to save the active page on chromium: 
```
$ xdotool search --onlyvisible --class Chromium windowsfocus key Control_L+s
```
But this doesn't work, it only writes a "s" on the search bar.

This command worked on a 64 bits ubuntu machine but it doesnt work in 32 bits.
I hope you can all help me
Thanks!!

---

### Post by yetimon_64 on 2019-05-04
I am on ubuntu mate 18.04 (64 bit) and on trying your command as posted with a webpage open in chromium all I got was ...
```
yetiman:~ $  xdotool search --onlyvisible --class Chromium windowsfocus key Control_L+s
xdotool: Unknown command: windowsfocus
Run 'xdotool help' if you want a command list
```

On seeing that error I tried changing "windowsfocus" to "windowfocus" and the chromium save page dialog popped up and I could save the active page.

 It appears you have a typo error in the command. Try it again without the extra "s" like...
 ```
xdotool search --onlyvisible --class Chromium windowfocus key Control_L+s
```
... and see if that suits what you are trying to achieve. I suspect it should work the same on 32 bit.

Regards, yeti.

---

### Post by lchachay on 2019-05-05
> **yetimon_64 said:**
> I am on ubuntu mate 18.04 (64 bit) and on trying your command as posted with a webpage open in chromium all I got was ...
```
yetiman:~ $  xdotool search --onlyvisible --class Chromium windowsfocus key Control_L+s
xdotool: Unknown command: windowsfocus
Run 'xdotool help' if you want a command list
```

On seeing that error I tried changing "windowsfocus" to "windowfocus" and the chromium save page dialog popped up and I could save the active page.

It appears you have a typo error in the command. Try it again without the extra "s" like...
```
xdotool search --onlyvisible --class Chromium windowfocus key Control_L+s
```
... and see if that suits what you are trying to achieve. I suspect it should work the same on 32 bit.

Regards, yeti.

Hello yeti, thanks for your reply. It was a typo error when I was typing the question in the forum.
The command still doesn't work with 'windowsfocus' in ubuntu 32bits for some reason

Thank you!

---

### Post by yetimon_64 on 2019-05-05
> **lchachay said:**
> Hello yeti, thanks for your reply. It was a typo error when I was typing the question in the forum.
The command still doesn't work with 'window**s**focus' in ubuntu 32bits for some reason

Thank you!
You've put the extra **s** in again here ... ;)

But "ok, understood". I don't know what could be happening with the 32 bit install in that case. I haven't been on a 32 bit install for about 8 or 9 years now. Hopefully someone else with such an installation will come along and help you out soon. Good luck, yeti.

---

