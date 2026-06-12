---
title: "Want to uninstall then reinstall Thunderbird without losing emails or settings"
date: 2015-12-30
forum: General Help
---

### Post by Rocket J Squirrel on 2015-12-30
Thunderbird is up-to-date but it's gotten kind of hinky lately, freezing with unresponsive scripts and things like that. I've disabled all extensions and plugins but no joy.

Just for a lazy-person's approach, I wonder if I can apt-get remove thunderbird then apt-get install it, and have it retain my emails, mail filters, folders, and suchlike? Google has not come up with anything that directly addresses this. 

Anyone had any experience with this?

---

### Post by deadflowr on 2015-12-30
Thunderbird's settings which include your various email account settings, which thunderbird uses, are in the hidden folder ~/.thunderbird in your home folder.
Normally *apt-get remove* does not touch anything in your home folder, so that should stay intact as is.

If you want to be safe, simply copy that folder somewhere, and later move it back.
All your settings will be just as you left them.

---

### Post by Rocket J Squirrel on 2015-12-30
Thanks deadflowr, that worked.

---

### Post by ajgreeny on 2015-12-31
Has it actually solved your problem with TBird?

More often than not, any problems such as you were seeing are related to the user profile, ie, the configuration you have in that hidden ~/.thunderbird folder in your home.

If a reinstall has helped, that's great; if not you may need to look closer in your configuration.

---

### Post by Rocket J Squirrel on 2015-12-31
Solved the TB problem? Oh, gosh, no. That would have been too easy.

Three problems, all of which cropped up at the same time:

1. I have Master Password enabled. When TB loads, it now brings up two login windows, one behind the other. Typing in the password in the first window satisfies login, but I have to manually close the second window. Not a big deal but this behavior started at the same that as:

2. During composing (replying, new, whatever), the cursor frequently freezes and I can't do anything in TB until it unfreezes, a matter of a few dozen seconds or so but disruptive.

3. All by itself, possibly when checking for new messages, TB freezes with a windows stating that a script has stopped running Continue/Stop script. Selecting either doesn't bring about instant relief, but usually after a dozen seconds or so it does. 

I can think of nothing I've changed in TB (adding a plugin, or a new account, or a filter) that preceded this swell new behavior cluster. Disabling all plugins and extensions doesn't help.

---

### Post by SeijiSensei on 2015-12-31
Are you using POP with the "leave mail on server" option enabled or IMAP?  Do you have large mailboxes with thousands of messages?  Often these slowdowns happen when the client is syncing with the server.  Archiving older messages into separate folders can help.

---

### Post by Rocket J Squirrel on 2015-12-31
> **SeijiSensei said:**
> Are you using POP with the "leave mail on server" option enabled or IMAP?  Do you have large mailboxes with thousands of messages?  Often these slowdowns happen when the client is syncing with the server.  Archiving older messages into separate folders can help.

Thank you.

Half dozen or so IMAP accounts, one POP with about 6 messages in it. That one is set to leave on server for 14 days. 

Setting aside issue #1, above, for the time being,

Issue #3 (freezing out of the blue with a "Script is not responding" message throws off 

Script: chrome://messenger/content/folderPane.js:2123

Issue #2, freezing for while while composing, generally occurs when I've written about 1/2 of the first line of text. 

TB on my Win XP machine, pointed to the same accounts, does not hang.

---

