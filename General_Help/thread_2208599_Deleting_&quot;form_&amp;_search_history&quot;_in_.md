---
title: "Deleting &quot;form &amp; search history&quot; in Firefox"
date: 2014-03-01
forum: General Help
---

### Post by mmf2 on 2014-03-01
Hey there,  I'm using xubuntu 13.10 and Firefox 27.0.1.

 For some reason, I'm unable to delete history, kind of.   My "Form & Search History" is greyed out, for some reason.. I already reset(ed?) my firefox, used bleachbit,  deleting history with and without an addon.. Whenever I write "test" on the search bar, it gives me "testing.test" as a suggestion.  

What the hell is going on and how do I completely delete history?

---

### Post by maglin2 on 2014-03-01
Do you already have 'Clear history when I close Firefox' checked under preferences- privacy? If so try unchecking it, and try deleting history again.

---

### Post by mmf2 on 2014-03-01
> **maglin2 said:**
> Do you already have 'Clear history when I close Firefox' checked under preferences- privacy? If so try unchecking it, and try deleting history again.

I did that.. Sadly, didn't help.

I noticed that my "Form & Search History" is not greyed out when there's something to delete. However, I still see the suggestions in my search bar, even when there's no apparent history (which I check by going to "history" -> "Show all history").


EDIT: I also noticed that the suggestions in the search bar are only working for sites which I visited 2+ or so hours ago. If I go to "whatever123.com", then delete history, "whatever123.com" won't show up in the search bar. The same is not happening for sites that I visited 2+ hours ago.

---

### Post by maglin2 on 2014-03-01
Do you have 'Show search suggestions' ticked unde rManage search engines (a drop down menu from the search panel to the top right)?

---

### Post by mmf2 on 2014-03-01
@maglin2, yes I do. Disabling that will disable the Search Suggestions, but that's not really a fix. How does firefox know I visited "testing.test" if there's no mention of it in the history? I want to completely eradicate my history.


EDIT: Actually, disabling that doesn't help at all.. My search suggestions still show. Btw, by "Search suggestions" I mean the suggestions in the address bar.

---

### Post by maglin2 on 2014-03-01
If you are determined you could I suppose delete the hidden folder '.mozilla' from Home. You may also have to delete '.cache/mozilla' from Home. These will probably get rid of all your bookmarks and extensions too though so it's a bit extreme.

Might be better to wait and see if anyone else knows exaclty what to delete to remove history only.

---

### Post by mmf2 on 2014-03-01
I fixed the problem by deleting the .mozilla folder, from home, as you suggested. I did lose all my bookmarks and addons, but oh well...

---

### Post by ibjsb4 on 2014-03-01
Next time just rename that folder and transfer your bookmarks.

---

### Post by ajgreeny on 2014-03-01
You should also have checked that the hidden folder .mozilla, and that thefiles in it all belonged to you and not root.

---

### Post by maglin2 on 2014-03-01
I think the file to delete from the profile to just get rid of history is probably places.sqlite. This also contains bookmarks, but they will be automatically recreated from the bookmarksbackup json it seems, whereas history won't.

@ajgreeny - if any files in home/.mozilla belonged to root, would there be prompt for enhanced authorisation to proceed with any attempt to rename/remove?

---

