---
title: "Evolution cache gone crazy?"
date: 2008-04-27
forum: General Help
---

### Post by dallas7 on 2008-04-27
Although using Linux for several years and Ubuntu since 6, I've only been using Evolution for about three months.

I have 90 emails stored in several "On This Computer" folders, 25 contacts and 45 calendar events. 

I began looking into the .evolution folder and image my surprise to find it holding 7863 files worth 422 MB.  Compare that to my Outlook PST environment of 12+ years with thousands of email, hundreds of contacts and calendar events at 860 MB.

Upon further analysis, I find three cache folders, one under .evolution's root and two more under mail, one each for my two POP accounts.  These hold a records of [B]every[B] message and every HTML tag of the emails I've received since day one!

I cleared these out and now .evolution is 366 files at 2.7 MB.  Still a bit high, but OK by me.

Is there some way to stop or put a cap on this insanity?  Or an easier way to purge this bloat?

I have a feeling only my system is affected as I can't find anything about   this here or in google searches or over at gnome.org. 

Thank you.

---

### Post by rbmorse on 2008-04-27
Evolution doesn't delete files when you tell it to delete files. It merely marks them as deleted, and hides then from view. To really delete deleted files in a folder, you need to highlight the folder in the folder list and use the folder > expunge command from the menu bar or <ctrl><e> from the keyboard.  You have to do this for each folder that may be holding deleted but not yet expunged deleted files (i.e., inbox, trash, junk, outbox, sent, drafts, etc.) 

Yes, it's stupid. No, I do not need to be reminded this is a feature designed to protect myself against accidental or inadvertent deletion of important stuff.

---

### Post by Ian Sinclair on 2010-11-23
I select the Junk folder and use Ctrl-E. The junk stays in place, but the Deleted Files folder is empty. Does'nt sound logical to me!

---

