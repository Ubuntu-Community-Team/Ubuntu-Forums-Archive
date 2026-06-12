---
title: "How to migrate my Firefox"
date: 2007-04-29
forum: General Help
---

### Post by vicsnipe on 2007-04-29
OK SO i have winxp with firefox. How can i take all the stuff from my firefox (passwords, history, bookmars,etc, ) and put them on my ubuntu??

---

### Post by Flashgordon20 on 2007-04-29
Google makes a neat extension called google browser sync that will migrate most of that stuff. Install on your win xp firefox first. Then install on your ubuntu firefox. Everything should be as you had it on win xp. Sorry for not providing a link, I am at work and the urls are blocked. You can also try foxmarks . I've never used it but I have heard good things about it for accessing your bookmarks.Foxmarks can be found here:
[https://addons.mozilla.org/en-US/firefox/addon/2410]("https://addons.mozilla.org/en-US/firefox/addon/2410") Good Luck!

---

### Post by fwojciec on 2007-04-29
If you're dual-booting then use something like ntfs-3g (and ntfs-config), make your windows partition writable from ubuntu and then run "firefox --ProfileManager", create new user, set the user as default, choose the windows Firefox profile directory and voila - all you settings from Firefox in Windows are available in Ubuntu.  That way you can actually share the same Firefox profile between your Windows and Ubuntu - which means that if you add some bookmarks in Firefox in Windows they will appear in Ubuntu when you next run Firefox there (and vice versa).

If you're getting rid of the Windows partition altogether you can just backup and copy the Firefox profile directory to your Ubuntu partition, or wherever you want to keep it, and, like above, create a new Firefox profile in Ubuntu pointing Firefox to where you saved the profile files from Windows.

The same can be done with Thunderbird, of course, and like with Firefox, Thunderbird profile can be shared by Windows and Ubuntu versions of the program (so you can check your email from both Windows and Ubuntu).  The command to set up a new profile for Thunderbird in Ubuntu is "mozilla-thunderbird --ProfileManager"

If you google around I'm sure you can find a more detailed guide on how to set it all up.

Good luck!

---

