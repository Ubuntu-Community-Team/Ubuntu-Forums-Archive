---
title: "unable to disable crash recovery in epiphany"
date: 2007-07-18
forum: General Help
---

### Post by dreamersbrow on 2007-07-18
I am trying to use pessulus and epiphany on the computers at our library as public catalog kiosks.  The problem that I am having is that I have cron jobs set to automatically shutdown the computers when the library closes.  The next day when the computer starts up, epiphany brings up a crash recovery dialog.  

I have gone into about:config and set *browser.sessionstore.resume_from_crash* to **false** (this worked in firefox) but I still get the recovery screen in epiphany.  Is this a bug or am I doing something else wrong?

Thanks

Ron H.

---

### Post by ernz on 2008-02-18
Hi dreamersbrow,
                              I realise this is probably WAY to late to be of any use to you, but the same problem was driving me nuts. All you have to do it delete the ~/.gnome2/epiphany/session_crashed.xml file before loading Epiphany.

This example will clear the recovery info, load epiphany with a specified URL and then close it 1 minute later. You can adapt it to your own needs.

```
rm ~/.gnome2/epiphany/session_crashed.xml; epiphany-browser & sleep 60 ;  pkill epiphany*
```

To just clear the recovery data and then load Epiphany use:

```
rm ~/.gnome2/epiphany/session_crashed.xml; epiphany-browser
```

I suppose you could even get clever and change your shortcut to run this modified loader instead of just 'epiphany-browser'. I hope this helps you and anyone else facing this rather irritating bug.

Sidenote: *I forgot to mention that I think location of the XML file varies depending on your versions of Epiphany/Ubuntu*

Ernz

---

