---
title: "Want to use Compose key, not Dead keys"
date: 2014-02-25
forum: General Help
---

### Post by Keith_Beef on 2014-02-25
I've just switched to lxde from Unity on one of my computers (a little Sony Vaio portable) and I'm having a bit of trouble with the keyboard.

I need to be able to type in French and German, and would like to be able to type in the Scandinavian languages, the Slavic languages and Spanish as well, in addition to English (which is also the system language).

So far, I've got French language support installed, and can type most of the required letters, but the cedilla below the letter "c" is not from the comma, but from the apostrophe. This means that apostrophe followed by c gives me ç for French, where it should give me &#263; for Polish, Croatian and latin Serbian.

I'm more used to using the US layout with the left "Windows" key as "Compose", but for now I'm using the layout "US with dead keys", but haven found a way to do this with lxkeymap. Lxkeymap proposes a layout called "English (international AltGr dead keys), but I've not found a way to make that work.

Can anybody help me out?

---

### Post by Keith_Beef on 2014-02-26
Well, I've found a way of doing this, thanks to information in [this thread](http://forums.linuxmint.com/viewtopic.php?f=175&t=94248) and [this thread](http://forums.linuxmint.com/viewtopic.php?f=175&t=80965) .

In lxkeymap I set the layout to English (US) and then in a terminal I issued the following command.
```
setxkbmap -option compose:lwin
```

I put this in my /etc/xdg/lxsession/LXDE/autostart config file, so that the file now looks like this.
```
@xscreensaver -no-splash
@lxpanel --profile LXDE
@pcmanfm --desktop --profile LXDE
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
@setxkbmap -option compose:lwin
```

If I find that this works well, I'll mark the thread solved in a day or two.

---

