---
title: "Trash Can Funny ACT!"
date: 2008-05-20
forum: General Help
---

### Post by Ioky on 2008-05-20
hey it is our Lovely Trash Can again. This time it try to act funny.

I put a Trash Can Icon on my Desktop, so AS it's name say TRASH, I put Trash into it. However, After I put the Trash into the Trash Can, The icon doesn't change to full Trash Can, and when I try to empty it, I can't even click the button. 

And the Same time, the little icon on the Panel, work. ONLY the Trash Can on the Desktop doesn't work, So I logic out, and try it again. and It works again. But the icon change slightly slower than the on on the Panel. 

I don't know is it a bug, or just something I did wrong. I don't know. I just wonder has some one experience similar problem. It would be great if there is a way to fix it. 

Thanks

---

### Post by 3rdalbum on 2008-05-20
If you are dragging files from a root file browser to the trash icon, it will go into root's trash, not your user account's trash. I'm not sure whether this could be classed as a bug or not.  If you are dragging files from an ordinary Nautilus window to the trash, and the trash icon doesn't update, then it's a bug of some sort.

---

### Post by Ioky on 2008-05-21
I don't know why this happen but, whenever, I need to enter my root password, for saying update, or install new package. after I enter my password. The Trash can at the Desktop start to act like this. even when I just trash so file in the Desktop to the trash can.

I feels like this is a bug,maybe?

---

### Post by ibuclaw on 2008-05-21
To put a Trash Icon on your Desktop the "**proper**" way.

Press "Alt+F2", then type in **gconf-editor** in the run application applet.

In the new window, go down into "apps>nautilus>desktop" in the registry and enable the key named **trash_icon_visible**.

Or, there is also the user-friendly way. That is to download and install [Ubuntu-Tweak]("http://ubuntu-tweak.com/").
For new users to Linux, this is priceless gold!

Regards
Iain

---

### Post by Ioky on 2008-05-21
I did put down the Trash icon under gconf-editor.

by the way there is one more thing, as the icon on the panel is working, however, when you open Trash Windows with that icon, the Empty Trash button on the corner is not working. So the only way, I can empty my Trash is by right clicking on the trash icon on the panel, and hit empty Trash there.

There is no way to empty trash from the icon on the Desktop nor opening a Trash Window.

---

### Post by Ioky on 2008-05-21
So I set a range of Tests to test what is actually happen. and here is what I get.

There is no signal tell when will the Trash Bin doesn't work
(So time it doesn't work when the system just boot up and nothing have been done, and no app has lunch, And some time it works.) (Kill X sometime can make it work again, and something it make it doesn't work while it is working right before X got Kill).

When the Trash Bin doesn't work, The Trash Bin in the Desktop stop working, I can put in Trash to the Trash Bin however, when you open the trash window, it wouldn't recognize Trash is in the file, so you can't really hit the empty trash key at the top corner. No matter where you get the Trash windows open, neither the one on Desktop or the on the Panel. 

When Trash Bin Doesn't work happen, you can only empty Trash by right clicking on the Trash icon. and the on Desktop wouldn't even change the icon to the full trash icon. it will just appear with the empty icon. However the one on the panel works fine. 

I will report some more if more happen.

---

### Post by Ioky on 2008-05-21
[http://ubuntuforums.org/showthread.php?t=758617&highlight=Trash+icon+shows+empty+full+trash+button+grayed](http://ubuntuforums.org/showthread.php?t=758617&highlight=Trash+icon+shows+empty+full+trash+button+grayed)

I think this person are experience the same thing like me. however the post is close

---

