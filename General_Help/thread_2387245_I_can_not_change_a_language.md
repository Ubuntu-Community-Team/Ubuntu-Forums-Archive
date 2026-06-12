---
title: "I can not change a language"
date: 2018-03-16
forum: General Help
---

### Post by offir on 2018-03-16
I installed Ubuntu 16.04.04
In Hebrew
At first everything worked
I pressed the key combination to switch languages and wrote in Hebrew

For some reason it stopped
I can not change a language

---

### Post by #&amp;thj^% on 2018-03-16
From terminal:

English to Hebrew and vise versa with Alt + Shift
```

setxkbmap -option grp:alt_shift_toggle us,il
```

You can see all locale alias with this command
```

cat /etc/locale.alias
```

More info about setxkbmap in manual
```

man setxkbmap
```

To make these changes system wide, assuming you&#8217;re using **"Ubuntu"**, you can use the following:
```

sudo dpkg-reconfigure console-setup
```

---

### Post by offir on 2018-03-17
It works but it is not saved

After the first command it worked

When I typed the last command
I got something I guess I should pick something out there
But I do not know what because it's listed in a type of gibberish

This is indeed written in Hebrew letters
But it's written from the end to the beginning as if looking at a mirror

How do I make this Permanent ?



And why did this problem happen?
I've come across this by installing three computers already
All with Ubuntu 16.04

---

### Post by offir on 2018-03-17
In the last command I clicked OK
Every screen that appeared to me

But again it was not saved
Every time I do restart the computer
It is reset and I can no longer change language


How can you make it permanent

I installed Ubuntu 16.04.4 in Hebrew

---

### Post by #&amp;thj^% on 2018-03-17
> **offir said:**
> In the last command I clicked OK
Every screen that appeared to me

But again it was not saved
Every time I do restart the computer
It is reset and I can no longer change language


How can you make it permanent

I installed Ubuntu 16.04.4 in Hebrew
You may not have "**console-common**" installed.
```
sudo apt install console-common
```
Now we can set it to Hebrew with:
```
sudo dpkg-reconfigure keyboard-configuration
```
You will need to choose the keyboard you are using eg; **make** and **model**.
Tab to set it then set "OK"
Now go on to find the Hebrew lay out:
Screen shot included.
Now is that working with a reboot?

---

