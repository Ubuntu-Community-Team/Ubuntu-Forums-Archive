---
title: "problems opening attachments with evolution"
date: 2006-10-25
forum: General Help
---

### Post by thomasaaron on 2006-10-25
Hey, fellow Ubuntu-ers.

I use evolution for my email client, and I'm having difficulty opening attachments sent to me.

I researched the forum and found another post with asking for help in the exact same scenario, but the fellow that posted the question had never been given any help. So, I guess I'm kind of duplicating the post.

When I click on an attachment, here is what happens. I get an error message that says:

File /home/thomasaaron/file:/home/thomasaaron/.evolution/cache/tmp/evolutions-tmp-ndZdbG/ROI_excel_dpc.xls

The file is actually in the folder. The problem is that for some reason, evolution is tacking /home/thomasaaron/file: to the beginning of the path.

It does it with ALL file types, regardless of what email client they are sent from.

Any idea where things are going amok?

Best,
Tom

---

### Post by JShadow on 2006-10-25
Are you using Gnome or KDE?

---

### Post by thomasaaron on 2006-10-25
I'm using gnome.

Incidentally, I use evolution to pull mail from two online accounts: yahoo and icmail.

I get the same result, regardless of which account I'm downloading from.
So, the problem is definitely a local one.

I've also tried to think of anything I might have done that could have resulted in this breakage. Nothing's coming to mind.

Best,
Tom

---

### Post by thomasaaron on 2006-10-29
So, nobody has any clue on this one?

---

### Post by Jorge on 2006-10-30
I assume you are running Dapper, and the 2.6 version of Evolution. It is a bug of that version, corrected in the 2.8 version (in Edgy). The workaround is this:
1. Instead or double clicking the attachment, right-click it, and select "open with... (the appropriate program)"; or 
2. Scroll to the bottom end of the email, then select the pull down arrow, and select "open with... (the appropriate program)".

---

### Post by thomasaaron on 2006-10-30
Thank you.

It's interesting though. It used to work just find.

Is it possible to upgrade dapper with the 2.8 version -- without loosing all my data?

Best,
Tom

---

