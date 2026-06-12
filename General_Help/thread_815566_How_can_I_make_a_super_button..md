---
title: "How can I make a super button."
date: 2008-06-01
forum: General Help
---

### Post by Lord Xeb on 2008-06-01
I have Ubuntu 7.10 on a T43. There is not Windows button. I want to make one of my extra buttons I do not use as the super button. I want make the Pause button my super button.

---

### Post by Rocket2DMn on 2008-06-01
I haven't done this myself, but try going to System->Preferences->Keyboard, hitting the Layouts tab and going to the Layout Options button.  You can customize some keyboard functionality from there.

---

### Post by drs305 on 2008-06-01
In my Sessions startup I have the following key to change my 'divide' key into a tab key. The command at startup is:
```
xmodmap -e "keycode 112 = Tab"
```

To find out the codes for the keys you are interested in, you can run this command. It will open in a small window and will display the key code with each key you press in a terminal window. 
```
xev
```

On my machine, the keycode for the pause button is: 110. The Windows Super_L key on my keboard is 115. You can play with xev to suit your preferences. The two names appear to be 'Pause' and 'Super_L'.

---

### Post by Confazed on 2008-06-01
The way I got it to work was on my T41 was:

Preference>Keyboard>Layout>Layout Options

Then Alt/Win key behavior

Then Left Alt is swapped with left win-key.

That allowed me to do all the super key required stuff in compiz.

---

