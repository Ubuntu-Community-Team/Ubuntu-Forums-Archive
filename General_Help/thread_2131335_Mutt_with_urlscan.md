---
title: "Mutt with urlscan"
date: 2013-04-01
forum: General Help
---

### Post by GrouchyGaijin on 2013-04-01
Hi Folks,

I'm hoping someone can clarify an error message for me.
I'm using Mutt-patched from the Ubuntu repository and I like it a lot, except it has a problem with long urls.
When I click on one that stretches over multiple lines in the terminal, the url is cut and the browser gets a page not found error.

Fortunately, urlscan (also in the Ubuntu repository) integrates with Mutt to get around that problem.  Hitting ctrl+B in Mutt will open up a terminal window listing all of the urls in a given email.  It works pretty well, better than anything else I have found, but not perfectly.

When I hit enter to visit a url from the list urlscan has presented me with, I get this error:
```
 Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
```
**The browser does launch and go to the specified url**.

I don't understand what this means or how to fix it.  Can anyone give me a clue, please?  

I've also noticed that on occasion, after the browser launches, Mutt (or the urlscan terminal window) will lock up and the only way to get back to my list of messages is to close the terminal and relaunch Mutt.

---

