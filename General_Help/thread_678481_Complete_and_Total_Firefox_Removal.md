---
title: "Complete and Total Firefox Removal"
date: 2008-01-25
forum: General Help
---

### Post by TimMcE on 2008-01-25
I've been using the version of Firefox that was installed with Ubuntu 7.10 for a while now, and all was well up until a couple days ago.  Then I stopped being able to log in to many of the sites/forums I visit.  Digg, Facebook, and (most annoyingly), my internet banking just refuse to log in.

There were no error messages, nothing to indicate there was a problem, aside from the fact that the page would just reload without actually logging me in.  I figured it might be a problem with Adblock or NoScript (the only addons I use), so I tried disabling, and eventually completely uninstalling them, all to no avail.

I tried deleting all cookies, history, cache, the whole bit, and it still had no effect, despite restarting Firefox several times.  I've clicked on every Restore Defaults button I could find, trying to get Firefox back as close to it's original settings as I can, and still no luck.

I then tried logging into these sites with different browsers, to see if maybe the problem lay with the websites themselves.  Opera, Epiphany and Konqueror all worked perfectly fine, so I'm now sure the problem lies with Firefox.

So, I decided more drastic measures were required.  I went into Synaptic and marked Firefox for Complete Removal.  I saw a bunch of other stuff was going to go with it, but I couldn't be bothered doing more than screenshot them so I'd know what I had to put back.  After I removed Firefox, I rebooted, went back into Synaptic and re-installed Firefox.

When I started Firefox again, everything was exactly as it was.  My default homepage was still set, my bookmarks were there, as were my addons and so was Firefox's inability to log me in.

So, after all that, I have but one simple question.  How do I totally, completely and utterly erase any trace that Firefox ever graced my hard drive?  I want Firefox, and everything remotely associated with it gone, so I can do a clean re-install and, God willing, have a properly functioning version of Firefox again.

---

### Post by LaRoza on 2008-01-25
Open your home directory, press Ctrl + h. Find the .mozilla directory. Delete it. Restart firefox.

Firefox should act like it never knew you or the computer.

---

### Post by jpeddicord on 2008-01-25
Make sure Firefox is closed. Open your home folder, and delete the .mozilla folder inside it. You may have to show it from View > Show Hidden Files. Once you remove the folder, load up Firefox again to enjoy a clean profile. [edit] ack, you beat me LaRoza!

Also, you may want to reinstall the ubuntu-desktop package in Synaptic, as removing Firefox probably removed that as well. It's there to ensure compatibility between system upgrades.

Jacob

---

### Post by LaRoza on 2008-01-25
> **jacobmp92 said:**
> Make sure Firefox is closed. Open your home folder, and delete the .mozilla folder inside it. You may have to show it from View > Show Hidden Files. Once you remove the folder, load up Firefox again to enjoy a clean profile. [edit] ack, you beat me LaRoza!

Also, you may want to reinstall the ubuntu-desktop package in Synaptic, as removing Firefox probably removed that as well. It's there to ensure compatibility between system upgrades.

Jacob

It was unanswered, I answered :)

Congrats on your new position, I hope to join y'all soon.

---

### Post by linux phreak on 2008-01-28
Does epiphany require firefox to be installed to work,since it uses the Gecko engine?

---

### Post by sports fan Matt on 2008-01-28
I convur and bring another set of chips to the table..Since Epiphany is based off the gecko engine why would only firefox behave this way, Wouldnt epiphany also since it has the same rendering engine (im not sure what engine konqueror uses)

---

### Post by TimMcE on 2008-01-29
Thanks folks.  I deleted the Firefox settings, and I'm now able to log in to every site except Digg.  I tried logging in to Digg on my laptop which is also running Ubuntu, and Digg didn't work there either, which makes me think it's a problem between Digg & Firefox.  But given that the majority of Digg users seem to use Firefox, I would think something would have been mentioned if none of them could log in anymore.  Which just confuses me further.

Especially if Epiphany uses the same engine as Firefox, since I have no problem logging into Digg with Epiphany on either computer.

---

