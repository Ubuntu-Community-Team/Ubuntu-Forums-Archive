---
title: "How does whiptail hide the dialog box from the terminal window?"
date: 2015-05-13
forum: General Help
---

### Post by kevin_vanryck on 2015-05-13
This is not really a support question, it's more out of curiosity.

I noticed using "dialog" leaves the dialog in the terminal window, when scrolling up. This makes pretty much sense to me.
What I'm wondering about is-- "whiptail" does not leave the dialog in the terminal window once the dialog is closed. How does whiptail do this?

Thanks for the info! :)

---

### Post by QDR06VV9 on 2015-05-13
Hi kevin_vanryck I'm not sure if this is what you mean.
>  Whiptail is a "dialog" replacement using newt instead of ncurses. It provides a method of displaying several different types of dialog boxes from shell scripts. This allows a developer of a script to interact with the user in a much friendlier manner.
See here
[http://packages.ubuntu.com/lucid/whiptail](http://packages.ubuntu.com/lucid/whiptail)

---

### Post by kevin_vanryck on 2015-05-13
I just assumed in order to show a dialog box on the terminal window, it should be printed out. The "dialog" program does this -- if you scroll up you can see old dialogs. But with whiptail - if you scroll up you can not see anything. Is this because of newt? I thought displaying something on the terminal screen without printing it in the terminal isn't possible.

Maybe this is more clear:
Try out dialog -- scroll up: the old dialogs will be there!
Try out whiptail -- scroll up: the old whiptails won't be anywhere visible

---

### Post by QDR06VV9 on 2015-05-13
> **kevin_vanryck said:**
>  _[COLOR=#0000cd]Is this because of newt?[/COLOR]_ I thought displaying something on the terminal screen without printing it in the terminal isn't possible.

Maybe this is more clear:
Try out dialog -- scroll up: the old dialogs will be there!
Try out whiptail -- scroll up: the old whiptails won't be anywhere visible
Basic answer yes. 
Whiptail Manual [http://manpages.ubuntu.com/manpages/lucid/man1/whiptail.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/whiptail.1.html)
More info here [http://www.opensourceforu.com/2011/11/spicing-up-console-for-fun-profit-2/](http://www.opensourceforu.com/2011/11/spicing-up-console-for-fun-profit-2/)
and here [http://www.freebsd.org/cgi/man.cgi?format=html&query=dialog%281%29](http://www.freebsd.org/cgi/man.cgi?format=html&query=dialog%281%29)
A Good YouTube Reference [https://www.youtube.com/watch?v=gFHHvUcna6g](https://www.youtube.com/watch?v=gFHHvUcna6g)
Have not got my head around it yet so I do not have a clear answer.
Regards

---

