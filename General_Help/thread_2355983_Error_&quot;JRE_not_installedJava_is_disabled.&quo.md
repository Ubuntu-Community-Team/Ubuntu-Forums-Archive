---
title: "Error &quot;JRE not installed/Java is disabled.&quot; after recent Firefox update"
date: 2017-03-18
forum: General Help
---

### Post by rg4w on 2017-03-18
Setup:
Ubuntu 14.04 (64-bit)
Firefox 52.0 (32-bit)

I have a client that uses Juniper Connect for their VPN, and after much trial-and-error a couple years ago I finally got it set up well with the icedtea plugin in a 32-bit version of Firefox.  It's been working reliably for a long time, but - 

Last time I successfully used Juniper Connect to log into the VPN was about a week ago, and IIRC since then Ubuntu 14.04 has updated Firefox.  I'm not sure about that update or if that's even the source of the problem, all I know is that when I go to the URL where icedtea had successfully run Java before I now get:

"JRE not installed/Java is disabled."

Nothing Java-related appears in my Firefox Plugins settings, not even Iced Tea.

Any clues as to how I might resolve this?

Thanks in advance -

---

### Post by &amp;KyT$0P# on 2017-03-18
Yes, the Firefox update is the source of the problem.  There are a few possibilities -

1) Downgrade Firefox to [version 51]("https://ftp.mozilla.org/pub/firefox/releases/51.0.1/") or the latest [45 ESR]("https://ftp.mozilla.org/pub/firefox/releases/45.8.0esr/")

2) Switch over to [Firefox 52 ESR]("https://www.mozilla.org/firefox/organizations/all/") and enable loading plugins other than Flash -
about:config > set [FONT=Courier New]plugin.load_flash_only[/FONT] to [FONT=Courier New]false[/FONT]

3) Use another browser that still supports plugins other than Flash, such as [SeaMonkey]("http://www.seamonkey-project.org/") or [Pale Moon]("https://linux.palemoon.org/").

---

### Post by Geoffrey_Arndt on 2017-03-18
Or try the "Chromiium" browser.   FF is going thru a crazy lot of changes between now and end of the year.

---

### Post by rg4w on 2017-03-20
Thanks to both of you for the quick replies. Halogen2, I'd not heard of Firefox ESR before but tried it and it was a quick and easy solution - thank you!  Marking "solved"....

---

### Post by &amp;KyT$0P# on 2017-03-20
You're welcome! :KS

Oh, and you'll need to make sure Firefox ESR does **not** update to any version > 52.x, if it does you'll be back to where you started.

---

### Post by rg4w on 2017-03-20
> **halogen2 said:**
> ...you'll need to make sure Firefox ESR does **not** update to any version > 52.x, if it does you'll be back to where you started.
Good thought.  I'll keep an eye on that.  Thanks!

---

