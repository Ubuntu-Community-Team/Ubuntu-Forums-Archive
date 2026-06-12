---
title: "Terminal acting funny"
date: 2007-06-04
forum: General Help
---

### Post by heyilikeyoursweater on 2007-06-04
I need help with my terminal. I think I might have changed my group or something. When I start terminal it only shows a $ not username@computer$ or whatever. This is fine, but when I press any of the arrow keys to move back in the text I type or up to get what I just typed in I get these sorts of things:  $ ^[[A^[[B^[[D^[[C
Any help would be appreciated.

---

### Post by phidia on 2007-06-04
> **heyilikeyoursweater said:**
> I need help with my terminal. I think I might have changed my group or something. When I start terminal it only shows a $ not username@computer$ or whatever. This is fine, but when I press any of the arrow keys to move back in the text I type or up to get what I just typed in I get these sorts of things:  $ ^[[A^[[B^[[D^[[C
Any help would be appreciated.
You could check your path too > echo $PATH to check the groups you belong to type "groups" BTW both commands are typed in the terminal.

---

### Post by heyilikeyoursweater on 2007-06-04
ok, when I typed in echo $PATH this is what I got:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

and when I typed in groups I got:
root adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin ntfs

I have no idea what either of these mean. What do I do now?

---

### Post by phidia on 2007-06-04
It looks ok AFAIK. Have you tried logging out and back in again to see if the terminal behavior you're describing goes away or continues? There is a command in terminal to set things straight again but I forget..... is it sanity? No really it's something like that, but from what you've described it may be that you somehow selected a different default terminal. Sorry I don't know what else to suggest.

I thought of one other thing. You can use the "up" arrow key while in terminal to see the past commands you've issued. If you see anything there that you don't understand or that looks like it could have caused this behavior you could post it here and hopefully someone will know what to do.

---

### Post by heyilikeyoursweater on 2007-06-04
Well it keeps happening when I log out and in. Are you sure there is nothing else?

---

