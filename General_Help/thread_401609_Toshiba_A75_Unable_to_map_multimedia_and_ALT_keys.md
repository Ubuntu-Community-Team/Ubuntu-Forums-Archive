---
title: "Toshiba A75: Unable to map multimedia and ALT keys"
date: 2007-04-04
forum: General Help
---

### Post by se2131 on 2007-04-04
I have a Toshiba Satellite A75 series, and it has multimedia keys (play/pause, stop, ffwd, rewind, start) which do not register at all in the "xev" program (everything else does). Is there any way that I can get them to do something useful?

Also, I can't seem to map the right Alt key to perform as it should. When I run xmodmap -pke, I get...

...
keycode 64 = Alt_L Meta_L
...
keycode 113 = ISO_Level3_Shift
...

So then I tried remapping it using the following commands (one-by-one). None of them worked:

xmodmap -e "keycode 113 = Alt_R Meta_R"
xmodmap -e "keycode 113 = Alt_R"
xmodmap -e "keycode 113 = Alt_L Meta_L"
xmodmap -e "keycode 113 = Alt_L"

However, if I do the following:

xmodmap -e "keycode 113 = a A"

then it acts like the "a" key properly. My other Alt key works fine, so why can't I get this one to work?

Thanks in advance.

---

### Post by se2131 on 2007-05-02
bump

---

### Post by se2131 on 2007-05-04
bump again

---

### Post by se2131 on 2007-05-06
anyone have any ideas?

---

### Post by se2131 on 2007-05-27
trying one more time

---

### Post by lkakol on 2007-10-08
bump...it would be cool if someone could figure out a way to get this working

---

### Post by se2131 on 2007-10-15
Update: ALT key magically works for me in Gutsy, multimedia keys still not working.

---

### Post by fregl on 2007-10-23
For multimedia keys that do not show up in xev:
Press the key you would like to make known
```
$ dmesg
```
gives output like this:
```
[ 3959.360000] atkbd.c: Unknown key pressed (translated set 2, code 0x9e on isa0060/serio0).
[ 3959.360000] atkbd.c: Use 'setkeycodes e01e <keycode>' to make it known.
[ 3959.576000] atkbd.c: Unknown key released (translated set 2, code 0x9e on isa0060/serio0).
[ 3959.576000] atkbd.c: Use 'setkeycodes e01e <keycode>' to make it known.
```
Do what it tells you:
in /etc/init.d/rc.local add a line like this
setkeycodes e01e 158

Where the e01e comes from dmesg and 158 is any keycode that is high enough.
Now the key should be working in xev and you can map it to a key symbol.

---

### Post by se2131 on 2007-11-05
Sorry for the delay in this response, didn't realize somebody replied to my post.

So I hit the buttons (I tried all my multimedia buttons), and typed in "dmesg" into my terminal. There's no mention of keypress errors. I scanned the entire log and also did "dmesg | grep Unknown", and came up w/ no results.

I guess that there's no way to get this to work for now?

---

