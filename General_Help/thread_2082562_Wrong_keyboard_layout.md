---
title: "Wrong keyboard layout"
date: 2012-11-09
forum: General Help
---

### Post by antonum on 2012-11-09
Hi,

I have a UK qwerty keyboard, but Ubuntu doesn't seem to recognise the layout correctly. For example, the @ and " are switched round from how they should be.

The mysterious thing is that the keyboard layout in System Settings is absolutely correct. But in any application (chromium, terminal, nautilus) the keys come out wrong.

Any ideas?

Thanks very much

---

### Post by BertN45 on 2012-11-10
Did you compare the lay-out of the hardware keyboard with the lay-out presented, if you press the small keyboard icon. That small icon is found under the left box with "English (UK)" as presented by the system settings. 

Maybe you have an English UK, Macintosh keyboard. You can use the + icon to check all possible UK lay-outs.

---

### Post by antonum on 2012-11-12
Thanks for the reply.

Yes, when I press the small keyboard icon I get the correct keyboard layout. My keyboard is nothing special, it is just a perfectly standard UK layout. It's the Logitech Wireless K270: [http://www.logitech.com/en-gb/keyboards/keyboards/7990](http://www.logitech.com/en-gb/keyboards/keyboards/7990)

---

### Post by antonum on 2012-11-14
Anyone got any ideas?

---

### Post by antonum on 2012-11-17
Anyone?

---

### Post by zombifier25 on 2012-11-18
[This is a really dirty solution but it will work](http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys).

---

### Post by antonum on 2012-11-18
Thanks for the help. That should work but will take a while to implement since there's a lot of remapping to be done. I don't suppose you know what the actual root of the problem is? It seems very odd since everything appears to be set up correctly.

---

### Post by Peter Maunder on 2012-11-18
If the " and @ are switched on a QWERTY keyboard it can be caused by the differences between the English (UK) keyboard  and the English (USA). For example "£$% above the numerals and L:@ following the uppercase L. On my American keyboard they show as @#$% and L:"  
You don't have a missmatch between the Logon Language you are using and the Physical Keyboard Language as set in the keyboard settings?

---

### Post by antonum on 2012-11-18
Hi,

Yes, the differences I'm seeing are exactly UK vs USA keyboards.

In System Settings -> Language Support, it is set to English (United Kingdom), so that's OK. 

I don't suppose the "Keyboard method input system" option is relevant? It's currently set to none.

---

### Post by Peter Maunder on 2012-11-19
Well I use a K340 (Swiss French and Swiss German) wireless unifying keyboard  as well as my normal USB English keyboard. if I forget to change the keyboard selection as I change keyboards the system does not know. Hence my Logitech QWERTZ will appear to be QWERTY to the system. 

As a long shot you could try adding the UK keyboard again and deleting the old selection. Don't forget to use Layout Options to place the € onto the correct key. Sorry to not be more help.

---

### Post by antonum on 2012-11-19
Actually, that seems to have solved it! I added another keyboard, switched to it and removed the UK one, then switched back again and it seems to work now.

Thanks very much for your help.

---

### Post by scubascooby on 2012-11-24
I've just installed 12.04 with gnome on a new build with a UK keyboard plugged in via a PS2 - USB adapter.

The layout shown is correct but the backslash and pipe key does not respond at all, unlike the other keys which light up the correct part of the layout.

I tried xev but that does nothing when I type backslash.

I know that the keyboard works because it is from my Milan.

PS

Ignore this. I have discovered that some of these cheap PS2 - USB adapters do not recognise the backslash key so it will never work.

---

