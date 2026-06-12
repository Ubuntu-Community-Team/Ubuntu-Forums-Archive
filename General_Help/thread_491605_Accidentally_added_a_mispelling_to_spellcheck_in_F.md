---
title: "Accidentally added a mispelling to spellcheck in Firefox"
date: 2007-07-03
forum: General Help
---

### Post by sloggerkhan on 2007-07-03
I accidentally added a bad spelling to the spell check in firefox. How do I remove it from the dictionary?

---

### Post by Brucevdk on 2007-07-03
First hit for Google search query *remove entries from firefox dictionary* or *delete words firefox spell check*.
[LIST]
[*][remove entries from firefox dictionary - Google Search]("http://www.google.com/search?q=remove+entries+from+firefox+dictionary")
[/LIST]
> 
C:\Documents and Settings\<user>\Application Data\Mozilla\Profiles\<profile name>
persdict.dat holds the personal dictionary entries used by the spellchecker added by you. 

But if you make a mistake or accidentally add a wrong word to the dictionary, the only way to delete is by manually removing it from, you guessed it right, persdict.dat file.


So that would be *~/.mozilla/firefox/Profiles/<profile name>/persdict.dat* for us. Note however that this file is only created/updated once the Firefox process has been terminated.

---

### Post by sloggerkhan on 2007-07-03
Thanks.

---

