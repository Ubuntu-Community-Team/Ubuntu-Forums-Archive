---
title: "I don't have the English Dvorak keyb layout choice :("
date: 2018-09-04
forum: General Help
---

### Post by drpeppercan on 2018-09-04
I was following this [tutorial]("https://websiteforstudents.com/configure-ubuntu-18-04-lts-beta-keyboard-layout-for-native-languages/") to be able to do Spanish accents, but contrary to the tutorial I don't have the English Dvorak keyb layout choice. 
I also made more input sources available:

```
[COLOR=#333333][FONT=Menlo]gsettings set org.gnome.desktop.input-sources show-all-sources true[/FONT][/COLOR]
```

But to no avail.

Any ideas?

Thanks guys :)

---

### Post by hazalide on 2018-09-05
I have had the same problem, though it has also mysteriously shown up on the list. Not sure why. I did find this solution on superuser.com and it seems to work for me.

```
sudo dpkg-reconfigure keyboard-configuration
```

[https://superuser.com/questions/119018/changing-keyboard-layout-to-dvorak-in-ubuntu-server](https://superuser.com/questions/119018/changing-keyboard-layout-to-dvorak-in-ubuntu-server)

---

### Post by hazalide on 2018-09-05
Updated development to my post from an hour ago. While the dpkg-reconfigure keyboard-configuration worked for about an hour, it suddenly and without warning switched back to QWERTY! So I went back to the GNOME settings and was able to find Dvorak. Try the following and let me know if it works for you:

1. Open Region and Language settings.
2. Click the + button under Input Sources.
3. Click English (United States).
4. Scroll down and click English (Dvorak).
5. Click Add.

I think the step that I missed the first time was to select English (United States) first. I assumed that option was not correct since it was the layout I already had.

---

### Post by drpeppercan on 2018-09-05
Thank you hazalide.
I'll try asap

---

### Post by drpeppercan on 2018-09-05
It worked!
Except I had to choose:
[I]
English (intl., with AltGr dead keys)
[/I]
Otherwise with English (Dvorak) it would change all my keyb layout, so my keys would give me different letters.

Thanks

---

### Post by drpeppercan on 2018-09-06
Aaannnndddd.....
Today's gone again :(
I don't know how it happened. It's like I never did the modification yesterday.
I know it shouldn't mean much, but I know that for most people this settings are found under Region and Language. For me though, are found under Language and Region.

---

