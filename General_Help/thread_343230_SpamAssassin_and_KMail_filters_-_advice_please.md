---
title: "SpamAssassin and KMail filters - advice please"
date: 2007-01-21
forum: General Help
---

### Post by martal on 2007-01-21
SpamAssassin on KMail appears to be correctly identifying spam, but the spam mails are just sitting in my inbox.

My filter list is:

1. People I want to receive mail from.

2. Spam AssassinCheck
Match all: Size <= 256000 bytes
Filter Actions:
  Pipe through spamassassin -L
If this filter matches, stop processing here: unchecked

3. Classify as Spam
Match all: Size >= 0 bytes
Filter Actions:
  Mark as Spam
  Execute Command: sa-learn -L --spam --no-sync
  Move Into Folder: Local Folders/XSpamKnown
  Mark As: Read
If this filter matches, stop processing here: checked

I select all the spam in the inbox as it comes in: click the button Filter Classify as Spam
Then I have to manually move it into XSpamKnown

Nothing is happening automatically. It's as though I have no spam filter at all.

I have run the command: sa-learn --spam --dir /home/martin/Mail/XspamKnown/cur  in the past. Didn't have any effect on future spam.

Where am I going wrong?

---

### Post by kuja on 2007-01-21
Looks like you're complicating things to me :s

After setting things up, make sure that the filter is set to mark the spam as read and move it to the trash. As per else, make sure to mark the goods as ham and manually mark anything that passed the filters as spam.

---

### Post by martal on 2007-01-23
Still no joy.

It doesn't matter whether I filter to trash or a custom folder, SA is not moving anything, even when recognized as spam.

Clicking the 'Filer classify as spam' button will move spam, but I want SA to filter without my intervention.

---

