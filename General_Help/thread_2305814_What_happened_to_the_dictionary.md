---
title: "What happened to the dictionary?"
date: 2015-12-09
forum: General Help
---

### Post by VanillaMozilla on 2015-12-09
Ubuntu used to have a very nice, fairly comprehensive, locally installed English dictionary.  I believe it was American English, but I haven't seen it for many months, and I'm not sure.  I'm not talking about a spell checker.  I mean an actual dictionary.

It may have been gnome-dictionary.  The Ubuntu apps directory ( [https://apps.ubuntu.com/cat/applications/saucy/gnome-dictionary/](https://apps.ubuntu.com/cat/applications/saucy/gnome-dictionary/) ) lists it only for 13.10 and earler versions.  It may (or may not) have been part of gnome-utils.  Synaptic doesn't list gnome-utils.  The Ubuntu Software Center shows only a few apps.  One of them is actually a dead link, and others are poorly rated.  If there is a good choice, it's not obvious.  A search for "dictionary" in Synaptic gives possibly hundreds of inscrutable sources, most of which seem irrelevant.  A Google search for dictionary Ubuntu gives mostly very old, irrelevant links (from when Ubuntu actually *had* a dictionary right in the menu).  More recent links seem sort of nebulous and non-commital, which is to say, vague.  One link suggests a dictionary from a Deb source, but gives no details.

There has to be a simple, known answer, so I thought I would try again.  (1) What happened to the dictionary.  And (2) what do I do to get a good English dictionary in Ubuntu 14.04?  It needs to be rather complete, and not a pared-down, 5000-common-words type dictionary.  I would prefer something locally installed, but if I can't get it, I'll take the best alternative.

---

### Post by howefield on 2015-12-09
I don't have gnome-dictionary installed, however it is available via synaptic.

[http://packages.ubuntu.com/trusty/gnome-dictionary](http://packages.ubuntu.com/trusty/gnome-dictionary)

---

### Post by VanillaMozilla on 2015-12-09
OK, I have the answer.  There's a lot of broken stuff in Ubuntu.

The package is called gnome-dictionary.  I don't know how it got uninstalled, but if you try to find it, you have to know exactly what to look for.  Fortunately, I still had it on another computer.

**Here's the broken stuff:**
1. The Ubuntu Software Center does not show it if you search for dictionary -- or at least not by any name that I can recognize.
2. GNOME Desktop Utilties is a broken link in the Software Center.
3. If you search for "dictionary", Synaptic overwhelms you with hundreds of irrelevant dictionary-related entries.
4. Ubuntu apps directory does not show gnome-dictionary as current.

I think the command is
sudo apt-get install gnome-dictionary.
Synaptic also works, but you have to know exactly what you are looking for.

---

### Post by VanillaMozilla on 2015-12-09
Thanks for the reply, howefield.  Please note the reports of broken stuff.

I'm not going to report it further, because my bug reports never get fixed.

---

### Post by grahammechanical on 2015-12-09
I open Ubuntu Software Centre. I type "dictionary" in the search panel and there at the top of the list is Dictionary. Select and click and then clicking More Info and I see that it is gnome-dictionary 3.18.0-2. I am on Xenial Xerus (16.04 development version). I see nothing broken with Ubuntu Software Centre as far as finding Gnome Dictionary and listing other dictionaries.

It is the Ubuntu apps directory that is way out of date. In the old days when Dictionary was part of the set of default applications that were installed we could fit a Ubuntu ISO image on a CD ****. Now, we need a DVD disk and that is the case even with things like Gimp and Dictionary being dropped from the ISO image.

---

### Post by howefield on 2015-12-09
> **VanillaMozilla said:**
> ...  Please note the reports of broken stuff.

Err.. thanks but no thanks.

> I'm not going to report it further, because my bug reports never get fixed.

Further ? you haven't reported it at all yet. Besides, best not to report the stuff that isn't broken.

---

### Post by QIII on 2015-12-09
Have you reported bugs on Launchpad?  Talking about things here is not reporting bugs.  We are just common users like you, not Ubuntu developers or employees of Canonical.

Edit:  I had a look at your Launchpad.  I would say that most of your entries are questions, not reports.  Of those you reported as bugs, I didn't see any with logs or other files to complete the report.  I'm sure those get passed by because there is little the developers can do without that information.  I suggest that your bugs might get better attention if they were complete.

---

### Post by rewyllys on 2015-12-09
Vanilla, you might take a look at Artha.  It's an English dictionary plus thesaurus, and I find it very useful.

---

### Post by VanillaMozilla on 2016-01-01
OK, guys, I was really exasperated, but let's try this.  I've found that it's better to discuss bugs before reporting them, because sometimes they aren't really bugs.  So check these out for me, will you please?  I guarantee, these are not complicated problems.

1. Search the Ubuntu Software Center for **dictionary**.  Can you find it?  Now search for **Gnome dictionary**.  Can you find that?  I can't.  I'm running 14.04 LTS.  (It so happens that it's indexed under **gnome-dictionary**, but if I had the exact package name, I wouldn't need the Software Center, would I?)

2. Now search for **Gnome dictionary** and click on GNOME desktop utilities.  (I think that's the wrong package, by the way, but it's the only plausible one.)  Tell me, is it or is it not a broken link?  (FYI, I'm running 14.04 LTS.)

4. (Taking these out of order.)  Search Google for **Gnome dictionary Ubuntu**.  First hit on my computer is this:  [https://apps.ubuntu.com/cat/applications/precise/gnome-dictionary/](https://apps.ubuntu.com/cat/applications/precise/gnome-dictionary/) .  Open that page.  Look on the left under "Available versions".  Does it look like the app is current?

3. If you're still with me, try this.  Search Synaptic for **dictionary**.  Search under "Status" "All", because that's what you might do if you don't know what you are looking for.  Could you find the Gnome dictionary if you didn't know what you are looking for?  OK, technically, some might say it's not a bug, but do you consider it a usability issue?

---

