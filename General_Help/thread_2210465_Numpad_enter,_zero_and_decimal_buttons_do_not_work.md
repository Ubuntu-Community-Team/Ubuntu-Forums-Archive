---
title: "Numpad enter, zero and decimal buttons do not work in xmonad"
date: 2014-03-10
forum: General Help
---

### Post by cgerrie on 2014-03-10
Hello. I have a very specific problem. The zero, enter and decimal keys on my numpad don't work. But they don't just not work; They work in unity, but I use xmonad. They even work in lightdm. However, once I login to xmond, they stop working. But the weirder part still is that they are still detected. They show up if I use xev or go into layout settings in gnome-control-center. But if I try to use them, they just don't work. I like to think that I am not a new linux user, as I have been using it for several years, but this problem has really stumped me.

my xmonad.hs is here: [http://pastebin.com/BRkkWb9F](http://pastebin.com/BRkkWb9F)

I can provide any more config details if you need. So please help :cry:

---

### Post by cgerrie on 2014-03-11
Sorry. I discovered the problem. It turned out that I had been fooling around with xmodmap a while ago, and a .Xmodmap that I had been fooling with found it's way into my home directory, but those buttons had been reasigned. I apologize for my stupidity. I am new to the forums, so could someone help me by telling me how to delete/remove a thread?

---

### Post by Impavidus on 2014-03-12
Glad you solved it yourself.

Threads are not deleted here, unless it's clearly spam or in violation with the code of conduct. You can mark your thread as solved. Click on "thread tools" (above your first post) and click "mark as solved".

---

### Post by cgerrie on 2014-03-12
Thank you for your help. :)

---

