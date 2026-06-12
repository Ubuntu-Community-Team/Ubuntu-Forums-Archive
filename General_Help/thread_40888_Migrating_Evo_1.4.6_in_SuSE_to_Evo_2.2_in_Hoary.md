---
title: "Migrating Evo 1.4.6 in SuSE to Evo 2.2 in Hoary"
date: 2005-06-10
forum: General Help
---

### Post by kjmorris on 2005-06-10
I thought that I had successfully migrated Evo 1.4.6 from my SuSE Pro 9.0 setup to Evo 2.2 on Ubuntu 5.10 Hoary. Here is what I have done so far and the resultant problem:

I killed the relevant backend tasks on SuSE and copied the following to a DVD-R:
/home/kelly/Evolution
/home/kelly/.gconf/apps/evolution

On Hoary, I did not run set-up for Evolution. I killed all relevant backend tasks and  deleted the following:
/home/kelly/Evolution
/home/kelly/.evolution
/home/kelly/.gconf/apps/eveolution

Next, I copied the following from the DVD-R to Hoary:
/home/kelly/Evolution
/home/kelly/.gconf/apps/evolution

Then, I ran Evolution and it proceded to accomplish the migration from Evo 1.4.6 to Evo 2.2 . Everything looked fine, but it wasn't fine.

Whenever I try to open a folder or file, I get the following error message (where "Widget" represents the folder or file name):

"Error while storing folder 'Inbox/Widgets'.
Cannot create folder on
/home/kelly/.evolution/mail/local/inbox.sbd/Widgets: Permission denied"

Even though everything is right in front of me, I can't open any folders or files.

What can I do to correct this? TIA kjmorris

---

