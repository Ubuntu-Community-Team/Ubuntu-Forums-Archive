---
title: "How do I export data/contacts from Thunderbird to Evolution? [Resolved]"
date: 2007-01-15
forum: General Help
---

### Post by raul_ on 2007-01-15
The title is self explanatory. I've been searching but all I can find is from Evolution to Thunderbird. I find Evolution much lighter. It seems that Thunderbird doesn't even have an "Export" feature. I searched from some add-ons but they are all deprecated =\ Any ideas for solutions/add-ons? 

Contacts aren't really important, i just wanted to keep the mails

---

### Post by aysiu on 2007-01-15
Thunderbird does have an **Export** feature. You actually have to be looking at the address book, though.

---

### Post by Ryba on 2007-01-15
> **raul_ said:**
> Contacts aren't really important, i just wanted to keep the mails
[quote=aysiu;2016742]Thunderbird does have an **Export** feature. You actually have to be looking at the address book, though.[/quote]
I think you misunderstood his question. He doesn't care about the contacts. Just the emails.

Raul, I found I had the same problem. However, I *cheated* to solve that problem. What I did was setup an IMAP server (or use an existing one if you have access to one), and just copied all my thunderbird emails to the imap server and then pulled them down into evolution.

---

### Post by raul_ on 2007-01-15
I ended up using this add-on:

[https://addons.mozilla.org/thunderbird/2887/]("https://addons.mozilla.org/thunderbird/2887/")

If anyone bumps into this later:

Export the Messages from Thunderbird using the add-on. This will create a file for every message (a pain in the rear if you have a lot of them) then you can use the Import feature in Evolution, choosing "Single File". Instead of doing "Import" for every single one, just drag and drop them to the folder you want. You cant select multiple messages though.

I don't think this is worth a How-To

---

### Post by AndyCooll on 2007-01-15
I've done this a few times (though it's a while since I last did it) and IIRC it's a bit of a pain in the neck.

However, essentially you unhide the .mozilla-thunderbird (you can do this by either temporarily renaming it or copying it to a folder that isn't hidden by default). Then you use the "import" tool in Evolution. You select "import a single file", then navigate to the "Mail" folder and select an e-mail folder to import. You need to do this process for each of your folders (inbox, drafts, sent etc.)

:cool:

---

### Post by aysiu on 2007-01-15
Or use IMAP, as Ryba suggested.

---

### Post by tropicflite on 2007-02-08
I used the above-mentioned Thunderbird extension, and was able to open the folder it created containing all my inbox messages with nautilus and drag them all at once into Evolution.

---

