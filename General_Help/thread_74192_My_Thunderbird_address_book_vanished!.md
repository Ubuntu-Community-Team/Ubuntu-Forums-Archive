---
title: "My Thunderbird address book vanished!"
date: 2005-10-11
forum: General Help
---

### Post by twoseids on 2005-10-11
It doesn't really seem possible, does it? All of a sudden, all of my address book information is gone. I went to Konqueror and I don't even see a directory called /.thunderbird or /.mozilla-thunderbird. Isn't that where the profiles are?

I do still have all of my folders full of e-mails. Just no address book.

Any ideas?

**UPDATE:** Okay, I was wrong, my profile IS there, under /home/eric/.mozilla-thunderbird. And I see a file called *abook.mab*, which appears to have been last modified 5 days ago. So why can't I see my addresses?

---

### Post by darkmatter on 2005-10-11
Sound like it could be a corrupted profile.

Try backing up the directory and then deleting the profile. You will loose your settings, but as long as you backup first, you can always restore them.

Under the new profile, try to import your bookmarks from the backup profile.

Please inform me of the results.

---

### Post by twoseids on 2005-10-11
[QUOTE=darkmatter]Sound like it could be a corrupted profile.

Try backing up the directory and then deleting the profile. You will loose your settings, but as long as you backup first, you can always restore them.

Under the new profile, try to import your bookmarks from the backup profile.

Please inform me of the results.[/QUOTE]
You mean import my address book, right?  :)

I'll try that in the morning (I'm in Asia) and get back to you then. Thanks for the idea!

---

### Post by twoseids on 2005-10-12
[QUOTE=darkmatter]Sound like it could be a corrupted profile.

Try backing up the directory and then deleting the profile. You will loose your settings, but as long as you backup first, you can always restore them.

Under the new profile, try to import your bookmarks from the backup profile.

Please inform me of the results.[/QUOTE]

No dice. There really isn't a way to import an entire profile. You have to import Address Book, Mail and Settings in three steps, but I can't do it for the following reasons:

Address Book: Thunderbird wants a file format such as .ldif, .ldi, .tab, .txt or .csv. And yet my address book file is .mab. What gives?

Mail: Thunderbird seems only to want to import mail from Communicator 4.x.

Settings: No programs are listed for me to select settings import.

So I'm back to where I was, having restored the (corrupt?) profile folder. I still have all my e-mails, just no address book. It stinks.

---

### Post by stinger30au on 2007-09-14
yep... my version of thunderbird 2.0 had just up and done the same thing

---

### Post by praet on 2007-09-14
twoseids,

If you open your profile folder, open your abook.mab file in gedit are your contacts in there?
If so, check that your localstore.rdf file has a reference to the abook.mab file.
If you have multiple contact folders, you may have additional mab files that will be configured in prefs.js.

To search for the file that contains your contacts try this command in a terminal in that dir.
```
cd ~/.mozilla-thunderbird/(RandomChars).profile
```

To find files containing a contact by name:
```
grep -i 'NameToSearch' *
```

To find files referencing mab files:
```
grep -i '.mab' *
```

To stinger30au, If you installed thunderbird 2.0 without a repo, you may need to copy your profile to the new location ~/.thunderbird from the ubuntu configured default ~/.mozilla-thunderbird.

---

