---
title: "Thunderbird won't open on Inbox"
date: 2019-07-13
forum: General Help
---

### Post by Olivares on 2019-07-13
I uninstalled & reinstalled Ubuntu 18.04 yesterday. Now Thunderbird won't display the inbox. I have seen a post under General Help from 2018 about this problem and the suggested solution was to install the manually-sort-folders add on. I have installed this add-on but I fail to see how this helps if the inbox is already first on the list of folders. 

When I attempt to start Thunderbird from a terminal this is what I see:
barry@barry-desktop:~$thunderbird
1562964112219	addons.xpi	WARN	Can'tget modified time of/usr/lib/thunderbird/features/wetransfer@extensions.thunderbird.net
JavaScript error:chrome://messenger/content/folderDisplay.js, line 498: SyntaxError:JSON.parse: unterminated string at line 1 column 197 of the JSON data


Does this mean anything to anybody?

Thanks.

---

### Post by walts48 on 2019-07-13
Not really.

Thunderbird always opens to the folder last selected when closing it. If you close it with the Inbox selected, it will open with the Inbox selected.

---

### Post by Olivares on 2019-07-13
I have uninstalled - reinstalled Thunderbird, and this has resolved the problem.

---

### Post by walts48 on 2019-07-14
> **Olivares said:**
> I have uninstalled - reinstalled Thunderbird, and this has resolved the problem.

What version of Thunderbird?

So if you select an email accounts Draft folder, quit Thunderbird, it opens to the Inbox on he next startup?

Lucky you :D

---

