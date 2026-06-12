---
title: "keyboard error"
date: 2008-05-17
forum: General Help
---

### Post by mastermind123 on 2008-05-17
Hi there,

I recently installed linux ubuntu on my desktop.  Evertything works fine but I am having a problem with my keyboard.  When I click some of the keyboard keys I get a different keystroke...for example when I click on shift - 2, I get a quotation mark (").  I tried changing my keyboard settings to the correct settings, but still have the same probblem...please let me know how to fix this, thanks

I am using a logitech Internet Navigator keyboard

Thanks

---

### Post by danwood76 on 2008-05-17
You need to make sure you are using the correct keyboard layout.
System -> Preferences -> Keyboard

Choose layout and select the correct layout for your keyboard, it sounds like you may be using a UK style keyboard layout.

---

### Post by Vincenso Andolini on 2008-11-22
I've also been trying to fix this error. It's not just the "@" symbol, there are a whole lot more shift-errors. 

I chose the "Canada" keyboard option during installation; maybe the "UK" and "Canada" options are similar, I don't know; but it sure is frustrating copying and pasting the "@" for email messages.

Anybody have any ideas about what to do?
Is there a way to rechoose the keyboard (layout?) option?


All help is appreciated!

Vincenso

---

### Post by danwood76 on 2008-11-22
You need to identify your keyboard type and make sure you set it correctly in the keyboard control panel.

The way to change it is identified in my previous post, they are just the names of the menus you choose, this is of course in GNOME as opposed to KDE.

---

### Post by Vincenso Andolini on 2008-11-22
Actually, I did in fact do that. I did go into the keyboard menu and identify the make. It did nothing. There must be some feature buried in the system somewhere to do something about this issue.

Thanks,

Vincenso

---

### Post by danwood76 on 2008-11-22
The other place it is stored is in the xorg configuration file.
Though this is depreciated and so shouldnt be in use.

To check this can you post the output of this from the terminal:
```

cat /etc/X11/xorg.conf

```

It might be that you are choosing the wrong keyboard type, each keyboard standard does have several types depending on the number of keys they have.

regards,
Danny

---

### Post by Vincenso Andolini on 2008-11-22
I'm not really sure what to do with this, I input it into Terminal, but it said nothing about keyboards.

I use a Toshiba satellite laptop. I chose Toshiba keyboard in the keyboard settings, and I tried 'US' keyboard type, but still the errors persist.

Does anybody have an idea why I am getting keyboard malfunctions?

Any help is appreciated,

Thanks,

Vincenso

---

### Post by Vincenso Andolini on 2008-11-22
I figured it out. I had to reboot for effects to take place...lol

Thanks,

Vincenso

---

