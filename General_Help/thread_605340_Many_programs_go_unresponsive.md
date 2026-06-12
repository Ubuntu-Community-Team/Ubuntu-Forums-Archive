---
title: "Many programs go unresponsive"
date: 2007-11-06
forum: General Help
---

### Post by chris0 on 2007-11-06
OK, this one is just plain weird....

I'm running Gutsy on a ThinkPad t61, with Gnome and Compiz. 

Earlier today (2007.11.06, ~4pm CST), I booted up and got into Gnome just fine (as usual). I went to work on a spreadsheet in OpenOffice. I selected a bunch of cells, right clicked, and hit "Format Cells..." And Openoffice went unresponsive.  And when I restarted Open Office and recovered the file, it couldn't recover any changes that I made since the previous save. 

I figured it might be an issue with the XLS file I was editing, so I saved it as ODS and tried again...same thing. 

I opened up Firefox to see if some Googlery would help, and Firefox segfaulted. I rebooted. 

I opened up Thunderbird to check my email and that segfaulted. I tried Firefox again and it segfaulted again. 

I tried editing a Word file. It went fine until I tried to change some formatting. It went unresponsive. 

Right now I'm in the failsafe terminal session posting this on a copy of Opera that I apt-get installed because Firefox still doesn't work in the terminal session. 

The only other thing of note that I could mention is that while I was using Open Office, some Ubuntu updates installed. 

Anyone else having this problem? Any ideas what it could be coming from?

---

### Post by chris0 on 2007-11-07
It appears that the problem was that I had copied a bunch of TrueType fonts over from my Vista partition into /usr/share/fonts/truetype/win-fonts. Somehow, my computer really didn't like that and it made most programs puke. 

-problem solved-ish.

---

