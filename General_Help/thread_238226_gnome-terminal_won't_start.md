---
title: "gnome-terminal won't start"
date: 2006-08-17
forum: General Help
---

### Post by compwiz18 on 2006-08-17
Well, the title pretty much says it all: I click the Terminal button and nothing happens.  If I watch the System Monitor when I click it, gnome-terminal appears briefly, and then immediately exits :frown: 

Any ideas? Thanks in advance.

[COLOR="Red"]UPDATE - PROBLEM SOLVED - SEE [http://ubuntuforums.org/showpost.php?p=1390817&postcount=13]("http://ubuntuforums.org/showpost.php?p=1390817&postcount=13") FOR INFORMATION.[/COLOR]

---

### Post by Ramses de Norre on 2006-08-17
Can you use something like xterm, aterm, eterm, konsole ... to start gnome-terminal from command line?

---

### Post by compwiz18 on 2006-08-17
[CODE]
Log of gnome-terminal 
Fri Aug 18 00:45:38 2006

gnome-terminal: symbol lookup error: gnome-terminal: undefined symbol: vte_terminal_set_opacity
gnome-terminal died with exit status 127

Fri Aug 18 00:45:40 2006
----------------
[\CODE]

That's what I get.  The funny thing is, it worked fine yesterday, and suddenly stopped working...

---

### Post by Griff on 2006-08-17
I'm in the same boat; worked yesterday, but now it doesn't.  All I've done since yesterday is install/use an icon pack and install some updates.

---

### Post by Ramses de Norre on 2006-08-17
Are you using XGL/Compiz with quinn's packages? They are updating packages to get real gnome terminal transparancy and the packages cause some problems.. (this is not the only issue with it..)

---

### Post by PingunZ on 2006-08-17
use xterm to upgrade.
( now gnome-term has true tansparancy )

---

### Post by Griff on 2006-08-17
> **Ramses de Norre said:**
> Are you using XGL/Compiz with quinn's packages? They are updating packages to get real gnome terminal transparancy and the packages cause some problems.. (this is not the only issue with it..)
Yep.
> **PingunZ said:**
> use xterm to upgrade.
( now gnome-term has true tansparancy )
Will do.

---

### Post by compwiz18 on 2006-08-17
How do I go about upgrading?

---

### Post by staakka on 2006-08-17
I'm having this problem, too. Can someone tell me what repositories I should have?

Thenks in advance!

---

### Post by sumadartson on 2006-08-17
Dito problem here. For some reason the beerorkid archives don't respond.

---

### Post by compwiz18 on 2006-08-17
> **sumadartson said:**
> Dito problem here. For some reason the beerorkid archives don't respond.
Yep, same beerorkid problem here.

---

### Post by sumadartson on 2006-08-17
Use the following repository in your sources.list:

deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

This seems to work.

And gnome terminal is back again.

(Ok, I just tried to submit an edit by typing :wq, must use less vim )

---

### Post by compwiz18 on 2006-08-17
FIXED.

Remove the beerorkid repo from Synaptic.

Add **deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main** to the repo list.

Reload the package lists.

Mark all upgrades.

Apply.

Use your Terminal.

---

### Post by staakka on 2006-08-17
Thanks a lot!
Update manager woke up and rest is history....

---

### Post by sumadartson on 2006-08-17
Ubuntuforums: We deliver solutions. Twice!

---

### Post by compwiz18 on 2006-08-17
> **sumadartson said:**
> Ubuntuforums: We deliver solutions. Twice!
lol, we both came up with it at the same time.  Well, actually you beat me by three minutes...

---

### Post by sumadartson on 2006-08-17
> lol, we both came up with it at the same time. Well, actually you beat me by three minutes...

And I lost a minute looking at a pretty, transparent, wobbly gnome-terminal... ;)

---

### Post by jackkerouac on 2006-08-17
> Use the following repository in your sources.list:

deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

This seems to work.

And gnome terminal is back again.

Actually, back better than before. Now transparencies work for me.

This SO illustrates why Ubuntu 'rocks the house.' Problem solved in under 10 minutes and awesome upgrade (admittedly Compiz) free.

---

### Post by sumadartson on 2006-08-17
> 
Actually, back better than before. Now transparencies work for me.

This SO illustrates why Ubuntu 'rocks the house.' Problem solved in under 10 minutes and awesome upgrade (admittedly Compiz) free.

And I absolutely love this update. I'm currently following a guide to set up CVS and loving it. You just place the terminal over the website, follow the instructions and modify the commands where necessary. I've never used my screen real-estate this effectively.

Next time anyone says Compiz is just eye-candy, I'll show them this trick.

---

### Post by compwiz18 on 2006-08-17
*sigh* now I wish that my terminal did that...compiz/XGL doesn't work on my laptop...

---

### Post by sumadartson on 2006-08-17
Check the attachment to get an idea why I love this so much.

Sidenote: I use two monitors, hence weird imagesize.

---

### Post by compwiz18 on 2006-08-17
Awesome :D

I wish I had two monitors too....and transparent terminals... :P

---

### Post by MikeMLP on 2006-08-17
quick question:  if this is solved by removing the beerorkid repo from Synaptic and adding deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main to the repo list, than does that mean that beerorkid is no longer the proper source for compiz updates?  what about the future? is this just a temporary lapse, or a permanent change in sources? anybody know?

edit: edit 2: nevermind I found my sources.list :roll:

---

