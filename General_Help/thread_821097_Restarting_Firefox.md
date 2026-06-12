---
title: "Restarting Firefox"
date: 2008-06-06
forum: General Help
---

### Post by Exsecrabilus on 2008-06-06
**I am running Firefox 2.0.0.14**.

When I moved to Firefox 2 from Firefox 3, my add-ons were intact.
But for some reason they didn't work. So I decided to uninstall them and install them again.

I went *Tools >> Add-ons >> Extensions* and clicked *Uninstall*.
It said they would be uninstalled when Firefox was restarted.
So I quit Firefox 2, but when I opened it and went *Tools >> Add-ons >> Extensions*, the add-ons were still there, still saying they would be uninstalled when restarted.

How do I get Firefox to restart to uninstall these extensions/add-ons? Thanks so much.

---

### Post by ludicrous on 2008-06-06
Make sure that Firefox has quit completely- open up System Monitor, and end Firefox from the processes tab.
Or, in a terminal, type
```
killall firefox
```

---

### Post by Exsecrabilus on 2008-06-06
Thanks.

Also, when I try to install more Firefox add-ons, it won't let me.

For example:

[img]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Error.png[/img]

[https://addons.mozilla.org/firefox/](https://addons.mozilla.org/firefox/) (Without the en-US) doesn't seem to work either.

---

### Post by Tomone on 2008-06-07
An easier way to restart Firefox is to go to Tools >> Add-ons. There's a button in the bottom right of the window to restart.

---

### Post by Exsecrabilus on 2008-06-07
Nope, not for me.

I did with the System Monitor and th Terminal, but the add-ons are still ther e. :(
Except this time it says they're installed. I'm right back to where I started. :(

---

