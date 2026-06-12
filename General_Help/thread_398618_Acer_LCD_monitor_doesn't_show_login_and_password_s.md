---
title: "Acer LCD monitor doesn't show login and password screens"
date: 2007-04-01
forum: General Help
---

### Post by JimS on 2007-04-01
...
This is a Breezy issue.
It might become a Dapper, Edgy, Feisty issue too
if I upgrade this 6 1/2 year old Dell box.

I bought 2 new Acer LCD monitors
and this issue happens with both.
Both are wide screen.  One 19" and one 22".
Models AL1917W and AL2216W respectively.
When start (or restart) my login and password screens don't appear.
Just a small box flooting around - I forgot what it reads.
I hear the login drum roll, so I know it is time to login.
I can login and password in the blind OK.
But it is a bother.

Needless to say, this wasn't an issue with my old hernia maker 20" CRT monitor.
I'm using the 22" with my old Dell and Breezy.  The 19" is on the Windoz box.
Some of the letters are faded, but I can live with that.  
I've seen that complaint often here.

Any suggestions?

JimS
[email]workfromhome@pobox.com[/email]
...

---

### Post by teaker1s on 2007-04-02
sounds like an xorg config issue you want to put in current monitor spec
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dcstar on 2007-04-03
> **JimS said:**
> ...
.........
Needless to say, this wasn't an issue with my old hernia maker 20" CRT monitor.
I'm using the 22" with my old Dell and Breezy.  The 19" is on the Windoz box.
Some of the letters are faded, but I can live with that.  
I've seen that complaint often here.

Any suggestions?


It is most likely a Refresh Rate issue, you can either plug in your old monitor, go into Preferences-Screen Resolution and select the lowest res/refresh rate setting you can find (and then plug in your new monitor), and then do what was suggested in the other post.

You will need to reset Ubuntu (with that command) to pick up the new capabilities of your new LCD monitor so it doesn't try to use incompatible settings.

---

### Post by JimS on 2007-04-14
...
Issue Resolved.

I made a seperate Home partition following Psychocats directions.
God Bless Psychocats.
Only issue popped up.
I couldn't log in at all.
Must have done something wrong.
But I could see, using Knoppix disc, that I had
successfully created and populated the home partition.

Next I successfully installed Edgy.
No more hidden log in screens and I can log in normally.
Edgy probably has an up-to-date driver for My Acer LCD monitor.
Bottom Line: My business PC is back in business.

All I need to do now is find and install my old bookmarks.
Still using Firefox.
Also need to find Thunderbird's address book. 
(I switched from Thunderbird to Evolution - needed PIM),
and install address book in Evolution.
And maybe a few other things yet to be discovered.

Computers are supposed to relieve our work load,
but I seem to be getting busier and busier with them!!
... 
Thanks,
JimS
[email]workfromhome@pobox.com[/email]
...

---

### Post by teaker1s on 2007-04-14
in the mozilla file and mozilla-thunderbird in home folder, your need to select show hidden files:KS

---

