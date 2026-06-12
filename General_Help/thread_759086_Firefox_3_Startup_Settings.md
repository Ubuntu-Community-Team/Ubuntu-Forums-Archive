---
title: "Firefox 3 Startup Settings"
date: 2008-04-18
forum: General Help
---

### Post by MattyGabe on 2008-04-18
As of right now, I am using Xubuntu to implement the PHPPOS software through LAMPP.  The entire installation is working fine and I have most of the large bugs worked out, however I've been working towards streamlining the process that the users of the PHPPOS system will have to go through.

Currently, I have it so that Firefox loads after login (maximized), and the homepage is the local server that PHPPOS is running on. I have basically abstracted away from the user what is going on, so the entire computer system seems like a dumbed-down terminal that they use to process sales (this abstraction is what I'm going for).

There is a slightly unwanted effect due in part to Xubuntu's settings, or perhaps Firefox's settings. When a user shuts down the machine, if a Firefox window was not closed first, it is re-loaded (or is considered "still running") when the user logs back in again. When the auto-started command for Firefox runs, it creates an error (it cannot create a second instance of a program already running).

While I understand why it does that and understand its no biggie in my eyes, it might confuse or annoy the regular user this system is intended for.  Was wondering if anyone knew of the particular setting in either Xubuntu or Firefox that I was looking for and how to go about changing that.

Note: I've scoured Firefox's settings and cannot for the life of me find what I'm looking for. I've briefly looked through Xubuntu's settings, but I'm not entirely sure I know what I'm looking for.

Any help is greatly appreciated!  Thanks again!

---

### Post by MattyGabe on 2008-04-20
...bump...

Also, if any moderators see the need to move this thread to another forum, please feel free to do so.  Wasnt sure which forum this needed to go into.


Edit: Discovered what was going on, yet never occurred to me.  On the "Quit" screen that offers the "Shut Down, Restart, Log Out" options, the box for "Save session for future logins" was checked.  I simply unchecked it and now it works as prescribed.

---

