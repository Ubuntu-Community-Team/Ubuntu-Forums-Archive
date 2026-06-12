---
title: "Firefox and copy link location"
date: 2008-05-23
forum: General Help
---

### Post by frogitts on 2008-05-23
I'm still holding on to Firefox 2 at the moment, and I've realized that the right click -> Copy Link Location doesn't actually do anything. Does anyone know why this would be?

---

### Post by bingoUV on 2008-05-23
Can you give exact steps to reproduce? Which application do you try to paste into? Do you try to paste after closing firefox? How do you try to paste , keybinding /mouse / context menu?

---

### Post by reza81 on 2008-05-23
Did you try to past it to an empty document or field?

I dont know if you know that there are two kind of copy pastes in linux by default. (This by selecting/ high lighting things.) & by keyboard short keys

I am at work can't test this on I.E. 7...

---

### Post by frogitts on 2008-05-23
The exact steps to reproduce are simply:

1)right click on any hypertext link in Firefox and select "Copy Link Location"
2)paste into the address bar or text document, with either Ctrl+V or the right click menu.

It didn't actually copy to the clipboard as far as I can tell, because if nothing was in the clipboard, nothing would paste, and if something was, whatever was there before would paste. I did not, however, try to paste after closing Firefox - I figured if it wasn't there when Firefox was running, it wouldn't magically appear after it closed, but I wouldn't mind being wrong here.

I did try to this in Firefox 3, and it works, so maybe it's not worth fixing, since Firefox 3 will be final in a while. Maybe this will push me over the edge to trying to get each of my extensions to maybe work with Firefox 3 using the version non-detection stuff.

---

### Post by jellylogix on 2008-05-23
sounds like a bug in FF2... I noticed that if I closed FF then it would delete/corrupt the data that I had copied on the "clipboard" that wasn't really a helpful clipboard... I fixed this problem though installing a little program called glipper to handle these "copies/cuts"  in an ACTUAL clipboard. 

to get glipper: 

sudo apt-get install glipper

---

