---
title: "Evolution Address Book is not cleanly deleted by Thunderbird"
date: 2013-05-31
forum: General Help
---

### Post by col48 on 2013-05-31
On switching from Lucid to Precise, I thought I'd try Evolution for email instead of Thunderbird.  This was not satisfactory, so I switched back.  I ended up with two copies of my Address Books, one set up for Evolution and one imported into Thunderbird (manually, if I remember correctly).  They are distinct and can be edited independently even though the books have duplicate names.

When I noticed this duplication and tried (in Thunderbird) to delete one of the the no-longer required Evolution books, this message appeared:
"Sorry - this version of EDS Contacts Integration does not support deleting Evolution address books. Due to the way that Thunderbird tries to delete address books, all of your EDS address books will appear to be removed from the address book manager. Simply restart Thunderbird in order to have them return."

Sure enough, all the Evolution books disappeared from the list, but reappeared as soon as I restarted Thunderbird.

The following closed thread gives the solution, which is to disable the "EDS Contact Integration" add-on. I did not need to install or uninstall anything else.  The Thunderbird books were unaffected.

[http://ubuntuforums.org/showthread.php?t=1844827]("http://ubuntuforums.org/showthread.php?t=1844827")

New thread added to record that this solution works for Thunderbird 17.0.6 in Ubuntu 12.04 (64-bit) as well as in the older context.

---

