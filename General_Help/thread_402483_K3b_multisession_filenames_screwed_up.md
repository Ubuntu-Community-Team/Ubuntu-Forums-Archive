---
title: "K3b multisession filenames screwed up"
date: 2007-04-05
forum: General Help
---

### Post by mageus on 2007-04-05
K3b always renames files to a primitive charset when I add to a multisession CD/DVD.

- I create a new CD/DVD and import the prior session from the disc.
- K3b displays the correct filenames in the file listing window.
- I add files from my hard drive.
- Rock Ridge, Joliet, and UDF file systems are enabled.
- 'Allow untranslated ISO9660 filenames' is checked.
- Tried at ISO levels 1 through 3.
- Tried every combination of settings in the Burn dialog as possible.
- The same system/burner works flawlessly under WXP using Nero.

The Problems
- The burnt CD/DVD shows files from the original session with a different name than what was shown in K3b.  Specifically, all spaces are converted to underscore, and everything is lowercase.  Sometimes, extra characters are added.
- Files that I added to the disc on top of the old session are displayed with the correct filename (mixed case, spaces intact, etc).
- When importing a session, K3b only displays the first session on the original disc (even if there were multiple to begin with).  However, sometimes it will add all of the files from _all_ the prior sessions, even if those files aren't displayed in the K3b file listing window.
- K3b keeps resetting my Filesystem settings in the Burn dialog, even though I've saved the user defaults and chosen Save from the Burn dialog.


Any ideas?

Multisession is the last thing keeping me from ditching Windows completely (aside from games), so I'd like to get this worked out.


My setup:
- Ubuntu 6.10 Edgy
- NEC ND-3550A
- Latest updates to everything applied from repository.

---

