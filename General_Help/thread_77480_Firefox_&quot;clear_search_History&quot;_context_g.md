---
title: "Firefox &quot;clear search History&quot; context gone from search field"
date: 2005-10-16
forum: General Help
---

### Post by holomorph on 2005-10-16
Not sure if this is something done for Breezy, or something the firefox people have done since whatever version was in Hoary but. . . there used to be this nifty "clear search history" menu item when you right clicked the search field in the upper right of the firefox browser.  Since upgrading to breezy, this option has dissapeared.  What I want is an easy way to clear the field so that I can enter a new search w/o ending up copying the search terms.  Something like the diggler extension does for the address bar would be ideal.  Anyone got a suggestion or know what happened to the "clear search history" context menu item?

---

### Post by not-a-bot on 2006-09-05
Sorry for bringing up this old thread.
I also found it quite annyoing that this nifty feature was missing from Ubuntu for no obvious reason. So I did some digging and came across this bug report:

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg148426.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg148426.html)

> As I describe here
 [https://bugzilla.mozilla.org/show_bug.cgi?id=308483](https://bugzilla.mozilla.org/show_bug.cgi?id=308483)

After you've invoked the `clear search history' option (on the context
menu in the search box), the normal browser history still contains the
URLs for the search results pages.  This completely defeats the
intended privacy effect unless the user knows to clear the browser
history.

This means that feature is a privacy risk, as it can lead to a false
sense of security.  This is quite hard to fix; the only correct
approach would be to clear all relevant entries from the browser
history or perhaps to ask the user whether to clear the browser
history too.

So in Ubuntu I have disabled this feature completely.  The only way
now to achieve this effect is
  Edit / Preferences ... /
  Privacy / Saved Forms / Clear Saved Form Data Now

Firefox 1.0 used to have a useful `clear everything' button outside
all of the tabs on the Privacy pane.  Unfortunately this has been
replaced by a reference to the Clear Private Data tool and a button
labelled, unhelpfully, `Settings ...'

I never really thought of the feature as a privacy feature, after all, that's what "Clear Private Data" is for. For me "Clear Search History" always simply helped me to keep track of my searches - kind of like resetting an odometer (I hope I found the right translation, not a native speaker here) in a car before a trip.

If somethinmg is "dangerously misleading" a slightly less radical solution would be, to simply make it less misleading. Why not rename it "Clear Searchbox History" (indicating that only the searchbox entries are deleted, exactly what is done) instead of removing it?

Would it be okay to maybe e-mail Ian Jackson, who seems to be responsible for the patch that removes an important feature to me?
Am I the only one who actually cares about this feature?

---

### Post by holomorph on 2006-09-05
Yes, I think it would be fine to email him with your suggestion.

I did find a good solution though, I installed the "Clear Fields" extension, which lets me place icons on the toolbar to clear the address field, search field, etc.

---

### Post by not-a-bot on 2006-09-05
The "Clear Fields" extension sounds like taking a sledgehammer to crack a nut. I do like my Toolbars simple and uncluttered (after all, isn't that part of Gnome's philosophy?) and I don't see the point in installing an extension for adding a button that re-adds a feature that was removed and that did the same thing more convinient in a more logical place for it. ](*,)

I'd personally loved to see this unnecessary patch removed from Ubuntu in the future but I doubt that's going to happen.
I guess I'll try to write an e-mail anyways.

Does anyone know if Debian followed Ian Jackson's advice to include his patch or was this a sole decision and only the Ubuntu crowd has to suffer the consequences?

---

