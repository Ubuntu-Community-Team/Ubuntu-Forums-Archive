---
title: "Keyboard language switching not working"
date: 2014-12-19
forum: General Help
---

### Post by DavidS on 2014-12-19
I am using Ubuntu 12.04.  I have Hebrew language support installed, and also the Hebrew (Biblical, Tiro) keyboard in addition to my standard English UK.

The two languages show up correctly in the icon at the top of the screen, and I can switch from 'en' to 'he' by using the mouse.  But although 'he' is now displayed next to the keyboard icon, I still get English typing.

Not only that, but I have tried setting various key combinations to switch layouts (e.g. Shift-CapsLock, RCtrl-RShift) and they simply don't do anything: they don't even change the 'en' to 'he' or vice versa.

So how can I get this actually to work as it is supposed to?

David

---

### Post by DavidS on 2014-12-20
Can nobody help with this problem?

I have tried adding the Hebrew (phonetic) keyboard, and also German and French keyboards.  I have done this with the Hebrew (Biblical, Tiro) still there, and with it removed.

Both Hebrew keyboards resolutely remain typing English.  Perhaps more astonishing is the fact the neither the French or the German keyboards will type anything at all!  I can move the cursor around in a document by using the arrow keys, but none of the letter keys produce anything.

Where might the problem be?

---

### Post by Bashing-om on 2014-12-20
DavidS; Hi !

Maybe pull something like this of :
```

cat /etc/default/keyboard

```
My default: ->
> 
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

&&
open file /etc/default/keyboard and edit it to add necessary options:
> 
XKBMODEL="pc105"
XKBLAYOUT="us,ua,il"
XKBVARIANT=","
XKBOPTIONS="grp:ctrl_shift_toggle,grp_led:scroll"

Then restart X session

Read the documentation, for how you want the keys set:
```

man setxkbmap

```

For an instance of what you might like:
issuing the following command switching English and Hebrew layouts worked:
```

setxkbmap -option grp:ctrl_shift_toggle "us,il"

```
( I show 'il' to be the code for "Hebrew")
 ->I used Ctrl_Shift and not Alt_Shift, because the latter was set too, and switched keyboard layouts on the host machine .

[INDENT]maybe Yes !
[/INDENT]

---

