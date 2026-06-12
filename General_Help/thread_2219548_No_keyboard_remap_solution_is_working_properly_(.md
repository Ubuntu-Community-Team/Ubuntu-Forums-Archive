---
title: "No keyboard remap solution is working properly :("
date: 2014-04-24
forum: General Help
---

### Post by melarish on 2014-04-24
I'm trying to remap my left Ctrl and Shift to Home and End, because on this keyboard, they normally require the Fn button but I use these keys a lot. So I tried the solution given here: [http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys](http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys)

It works for the same session, as it promises. However, when I created the xinit file, it did not apply this on startup. I looked around the forums and someone suggested making the script executable and putting it in Startup Applications. Now it works some of the time but not always. And sometimes it seems to "expire" with time (not because of Suspend or anything - just after computer's been running for a while).

The code in the xinit file is simply "xmodmap .Xmodmap" and the contents of .Xmodmap are:
```
keycode  62 = End NoSymbol End
keycode 105 = Home NoSymbol Home
```

I also installed AutoKeys but it seems it can only remap a key (combination) to a command but not another key.

Does anyone know why the xmodmap script is not working all the time or can suggest an easier solution that does what I need it to do? Aside from getting a keyboard with an actual Home and End key :P

---

