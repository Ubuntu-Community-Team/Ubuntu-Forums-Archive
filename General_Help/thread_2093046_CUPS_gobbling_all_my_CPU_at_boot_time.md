---
title: "CUPS gobbling all my CPU at boot time"
date: 2012-12-09
forum: General Help
---

### Post by frisket on 2012-12-09
I recently upgraded my older machines to Xubuntu 12.10 and everything has been working fine for a week or more. My printer is on one of these machines, and has been working perfectly since the upgrade, printing from all the other house systems without problems.

This afternoon, I submitted a 1-page web page document from my laptop to print, without the printer server running. Normally this is no problem, it just gets printed the next time the printer machine is fired up.

Then this evening I submitted a 2-page PDF, again without the printer server running, and went into the other room to fire up the machine which has the printer attached. Once booted, I expected the queued documents to start printing, but nothing appeared.

Back on the laptop there were two small pop-ups, asking for authentication to print the queued documents, something I have never been asked for before. They identified the documents, but did not identify where they came from, nor why they were suddenly asking for authentication for a printer which is configured to print anything from any system on my network.

As there was no indication of what kind of authentication they wanted (in small letters beside the text entry box it said 'none'), I used my login password, and tried to click OK. By that time I noticed the disk activity light was on solid, and the system hung completely: no response from any mouse click or keypress. I resorted to a hard power-off to recover.

When I fired up the laptop again, it ran at a snail's pace, with the disk activity light on solid, and 'top' revealed that cupsd was using between 60 and 95% of CPU. 

What might be causing this? The requests for authentication did not reappear, the documents were printed, and the high activity died down and the system was usable again.

Later on, I rebooted the laptop to see what would happen, and again cupds was taking over the whole system, so I managed to screenshot it:
[http://silmaril.ie/screenshots/Screenshot20120912211648.png](http://silmaril.ie/screenshots/Screenshot20120912211648.png)

As the queue was empty, I don't know why it would suddenly do this. All patches for Xubuntu 12.10 have been applied promptly, so it's running the supplied cups 1.6.1. I haven't been able to find any comment on the web about this, and all the CUPS newsgroups at news.easysw.com are only available intermittently.

All suggestions gratefully received.

PS [edit]

The size of the error_log suddenly jumped, and it now contains entries like:

E [09/Dec/2012:21:13:54 +0000] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [09/Dec/2012:21:40:35 +0000] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_Betty

Lines 15-16 of /etc/cups/cupsd.conf say:

15:# Administrator user group...
16:SystemGroup lpadmin

The second (Warning) line is repeated dozens of times, once for each installed printer, again and again and again (Betty in the example above is the name of my default printer). Quite why CUPS or FreeDeskTop would be shipped with bits missing is beyond me. Has something CUPS-related just been updated that I missed seeing?

[edit: much later]
Just tried to print another file: the authentication dialog pops up, along with another one from the first document mentioned above, which was long since printed. Does anyone know what causes the bogus authentication dialog? And why it won't accept any input, and why it hangs when you click OK?...

---

### Post by frisket on 2012-12-10
> **frisket said:**
> Does anyone know what causes the bogus authentication dialog? And why it won't accept any input, and why it hangs when you click OK?...

Fixed. Apparently I had clicked on "replace" when performing the upgrade and it asked if I wanted to keep the current cupsd.conf or replace it with a new one. Not having consciously modified the file, I accepted the upgrade.

Bad mistake. The new one has an entire section which appears to set the default print action to require authentication, without saying what password to use (my regular user password clearly didn't work).

Worse, the authentication pop-up does not obscure the password you type with *****, so anyone behind you could see it. And it doesn't work anyway: no matter what you enter, it hangs, and the file prints anyway.

The final symptom was that the root partition filled up as the response file in /var/spool/cups collected the auth err messages.

SOLUTION: 

sudo service cups stop
cd /etc/cups
sudo mv cupsd.conf cupsd.conf.dpkg-new
sudo cp cupsd.conf.dpkg-old cupsd.conf
sudo service cups start

Sanity is now restored. Moral: NEVER allow an upgrade to overwrite config files, even if you believe they need it.

---

### Post by izzaboo on 2013-03-02
> **frisket said:**
> 

The final symptom was that the root partition filled up as the response file in /var/spool/cups collected the auth err messages.

SOLUTION: 

sudo service cups stop
cd /etc/cups
sudo mv cupsd.conf cupsd.conf.dpkg-new
sudo cp cupsd.conf.dpkg-old cupsd.conf
sudo service cups start

Sanity is now restored. Moral: NEVER allow an upgrade to overwrite config files, even if you believe they need it.

I've lost some hair (and maybe even days of my life) to this problem! Very interesting that you were given a choice to keep/replace the .conf file. I don't recall having that choice. Nor do I have a cupsd.conf.dpkg-old file anywhere. I'm trying to get this working looking at how earlier versions of cupsd.conf were set up.

Do you have any ideas about what, specifically, in the default policy part of the the new .conf file were the problem?

thanks!

g

---

### Post by dodo_ur on 2013-07-17
> **izzaboo said:**
> I've lost some hair (and maybe even days of my life) to this problem! Very interesting that you were given a choice to keep/replace the .conf file. I don't recall having that choice. Nor do I have a cupsd.conf.dpkg-old file anywhere. I'm trying to get this working looking at how earlier versions of cupsd.conf were set up.

Do you have any ideas about what, specifically, in the default policy part of the the new .conf file were the problem?

thanks!

g



please commit out this line 

#SystemGroup lpadmin

---

