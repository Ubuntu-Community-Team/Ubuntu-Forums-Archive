---
title: "Open a saved email in Thunderbird?"
date: 2006-08-17
forum: General Help
---

### Post by mannheim on 2006-08-17
I have some individual emails stored in text files. I can open these with Thunderbird using the menu item "File --> Open Saved Message ... ". But I would like to open these from Nautilus (for example) by just double-clicking the file, and have Thunderbird open them up in a message window.

Nautilus recognizes the files as email messages (mime type: message/rfc822), but opens them with a text editor. I can change the mime type preferences to ask Nautilus to open the message using Thunderbird, but Thunderbird does not respond.

From the command line, I also tried  "mozilla-thunderbird "file:///path/to/file" but that did not work: I got an error message saying that thunderbird was unable to find the file "/path/to/file&number=0"

I believe this feature was added to the Windows version of Thunderbird. Does anybody know if I can do it in linux/gnome?

---

### Post by yopnono on 2006-08-18
Are they saved as .EML? Anyhow just select properties (rightclick) then "Open With" then select your mail client, if it's not in the list just use browse.

Also you can select it in the open with tab to open the mail client as first choice.

---

### Post by mannheim on 2006-08-18
Thanks for the reply. Yes, they are saved as .eml. I had already tried "Open with ... " and selecting Thunderbird. I think the problem is with Thunderbird itself. It simply does not open the file. Thunderbird **will** open .eml files (type message/rfc822) using its menu item under the File menu, but seems unable to open them otherwise.

---

### Post by yopnono on 2006-08-18
Ok. The "open with" works for me. But I use thunderbird from mozilla, not the ubuntu thunderbird. It might be some different there.

---

### Post by mannheim on 2006-08-18
Hmm ... and now it works for me too :oops:

From the command line, this does not work:
```
mozilla-thunderbird file.eml       [COLOR="Red"]# Fails[/COLOR]
```
But this does work:
```
mozilla-thunderbird /full/path/to/file.eml       [COLOR="Blue"]# Works[/COLOR]
```
It also seems that having the extension ".eml" is necessary: a text file with the right mime type but no extension won't open. Thanks again.

---

### Post by yopnono on 2006-08-18
Yes, you need to provide the path aswell, if not the application will not know where to look for the file, unless the file you are trying to open is in the same dir/folder as the application.

---

