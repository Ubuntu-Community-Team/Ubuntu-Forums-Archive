---
title: "Can't Type L in Terminal - Just Toggles"
date: 2008-01-14
forum: General Help
---

### Post by kmfdmk on 2008-01-14
This isn't the regular n00b problem of not being able to see the password entered.

I'm not sure what the heck I did, but anytime I press the letter L in the terminal window it merely Toggles the Show Menu Bar function.  

I have tried to turn off Editable Shortcut Keys under System, Appearance, however that didn't help a bit.

Please help!!  I'm crippled.

Yes I've restarted.

---

### Post by perixx on 2008-01-14
I can't guarantee, but maybe reconfiguring the X-server (including keyboard) helps:
```
sudo dpkg-reconfigure xserver-xorg
```
You may re-set your keyboard and language settings after that in the desktop settings-manager.

There's also a switch for high-level reconfiguring and low-level configuring (though I've no idea what the latter will do - so it's on your own risk!)
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
```
sudo dpkg-reconfigure -plow xserver-xorg
```

perixx

---

### Post by kmfdmk on 2008-01-14
I was able to fix this doing the following:

[LIST=1]
[*]Open a Terminal Window
[*]Edit >> Keyboard Shortcuts
[*]Remove the "L" from the "Show / Hide Menubar" shortcut
[/LIST]

Kind of simple, I'm not sure how it happened but I do sincerely appreciate your help!!

---

### Post by perixx on 2008-01-15
Glad you solved it :)
Do you mind marking your thread a 'solved'? This way, others can refer to it more easily...

perixx

---

