---
title: "Jedit keyboard problem: no tilde!"
date: 2007-04-20
forum: General Help
---

### Post by wgw on 2007-04-20
I can't get Jedit to output a tilde. I shuffled through various forum messages and this seems to be a perennial problem, more so with linux than Windows 

The problem(s):
Minor: with the standard us keyboard, no tilde
Major: with the us international keyboard, most dead keys can't be typed as themselves: ' " ~ ` ^

Under Ubuntu 6.10 (Edgy) I can switch keyboards to the US standard to resolve the Major problem (annoying, but an acceptable workaround: the US international keyboard works fine everywhere else except Jedit). However, I still can't get the tilde even under the US standard keyboard.

Is this a Linux problem? Jedit works fine in Windows.

Here is some data:

Jedit 4.3pre9 Java: 1.5.0_11
Ubuntu 6.10 (Edgy)
Compaq presario R3000

Keyboard troubleshooter message: filters the character.Here is the output under the standard keyboard (shift to get tilde):

Event KEY_PRESSED,keyCode=0x10,keyChar=0xffff,modifiers=0x1,consumed=0 filtered (shift down)
Event KEY_PRESSED,keyCode=0x80,keyChar=0xffff,modifiers=0x1,consumed=0 filtered
Event KEY_RELEASED,keyCode=0x80,keyChar=0xffff,modifiers=0x1,consumed=0 filtered
Event KEY_RELEASED,keyCode=0x10,keyChar=0xffff,modifiers=0x0,consumed=0 filtered (shift up)

Under the standard keyboard again, this is what I get for backtick: 

Event KEY_PRESSED,keyCode=0x80,keyChar=0xffff,modifiers=0x0,consumed=0 filtered
Event KEY_TYPED,keyCode=0x0,keyChar=0x60,modifiers=0x0,consumed=0 passed
==> Translated to <0,60>
Event KEY_RELEASED,keyCode=0x80,keyChar=0xffff,modifiers=0x0,consumed=0 filtered

Not sure why the 0x80 is there....

One more thing, to cap this key mess off: here one slightly promising message that seems to suggest it is possible to resolve, though I'm not sure how to implement this in Ubuntu, and especially how to switch options on the fly (though I am now using two keyboards): 

> 
I'm running RedHat 9 and jEdit 4.2final. I found myself unable to type ^, | and ~ (and maybe some others) on my danish keyboard where these are AltGr characters (but some other AltGr charaters worked). I then discovered that adding:

Option "XkbVariant" "nodeadkeys"

to the "keyboard" section in my /etc/X11/XF86Config solved the problem. I can now write the aforementioned characters by typing AltGr plus the character (no space needed). Maybe someone can use this information? 

Thanks for any ideas!

---

