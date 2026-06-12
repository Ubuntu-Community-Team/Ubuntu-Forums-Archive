---
title: "Firejail Icon"
date: 2016-12-15
forum: General Help
---

### Post by poorguy on 2016-12-15
Hey All,

Downloaded and installed firejail and it works great.:)

I can only open firefox in firejail from command terminal using "firejail firefox".
How can I create a desktop icon or panel icon for opening "firejail firefox".

I'm using Lubuntu 16.04 32bit.


In Ubuntu Mate 16.04 all I had to do was right click FF panel icon and go into properties then edit then copy and paste "firejail firefox %u" where "firefox %u" was.
This however doesn't work in Lubuntu 16.04.

Thanks

The PoorGuy

---

### Post by &amp;KyT$0P# on 2016-12-15
Here's how I'd do it -

1) Copy [FONT=Courier New]/usr/share/applications/firefox.desktop[/FONT] to [FONT=Courier New]~/.local/share/applications/firefox-firejail.desktop[/FONT].

2) Create a shell script somewhere.  Make it executable.  Fill it with this -
```
#!/bin/bash
firejail firefox $@
```

3) In the [FONT=Courier New]firefox-firejail.desktop[/FONT], edit the [FONT=Courier New]Name[/FONT] entries to something like "Firefox (sandboxed)".  And edit the [FONT=Courier New]Exec=[/FONT] entry to the full path to your shell script from (2).

4) Now remove the Firefox launcher, and add a launcher for "Firefox (sandboxed)"

---

### Post by #&amp;thj^% on 2016-12-15
There is also Firetools which will hold all short cuts and customs scripts you want.
Should be in the repos...if I remember correctly.
And it will minimize to tray to get out of the way...or lock to launcher.
More Info Here: [https://firejail.wordpress.com/](https://firejail.wordpress.com/)

---

### Post by &amp;KyT$0P# on 2016-12-15
> **1fallen said:**
> There is also Firetools which will hold all short cuts and customs scripts you want.
Should be in the repos...if I remember correctly.
Nope, not for 16.04 - [http://packages.ubuntu.com/search?keywords=firetools]("http://packages.ubuntu.com/search?keywords=firetools")

---

### Post by #&amp;thj^% on 2016-12-15
Right Then it is in the link in my previous post...and there is fix for both...
> [COLOR=red]This is a maintenance and security release for version 0.9.44. We strongly encourage you to update the software.[/COLOR]
Just Saying.
Right Now i'm using "firejail 0.9.44.2-1"

---

### Post by poorguy on 2016-12-15
> **1fallen said:**
> Right Then it is in the link in my previous post...and there is fix for both...

Just Saying.
Right Now i'm using "firejail 0.9.44.2-1"

Ok I'm using firejail 0.9.38-1 so are saying that I need to uninstall that version and install the new version firejail 0.9.44.2-1 .

---

### Post by #&amp;thj^% on 2016-12-15
I'm just passing the information from their site: [https://firejail.wordpress.com/](https://firejail.wordpress.com/)
> [h=2]News[/h] **December 2016** – released Firejail 0.9.44.2 ([Download]("https://sourceforge.net/projects/firejail/files/firejail/")). [COLOR=red]This is a maintenance and security release for version 0.9.44. We strongly encourage you to update the software.[/COLOR] [Release Notes]("https://firejail.wordpress.com/download-2/release-notes/").
 **October 2016** – released Firetools 0.9.44 ([download]("https://sourceforge.net/projects/firejail/files/firetools/")). This is a bugfix release.


Every time I add my opinion I'm met with resistance....so you decide.:)

---

### Post by poorguy on 2016-12-15
I guess I need to look into this and see what I find.
I appreciate the replies.

Thanks

---

### Post by poorguy on 2016-12-17
Ok went ahead and installed the new deb file and all went well. =d>

Thanks to all for your replies and opinions.

The PoorGuy ;)

---

