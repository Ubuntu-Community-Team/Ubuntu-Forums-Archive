---
title: "Evolution Email locks up asking for password!"
date: 2006-10-26
forum: General Help
---

### Post by wkulecz on 2006-10-26
I tried setting up evolution to connect ot an exchange server.  Not sure I setup the account correctly but the "authenticate" button did its thing and let me proceed.  Problem is as soon as the  main windows came up the program locked up when I entered my password.

After killing it, when I restart first thing it does is prompt for password with a dialog box which I can't type into or dismiss which has effectively locked up the program.

Definitely a bug if my account setup being incorrect causes this, question is how do I delete the existing account so I can get by this and try again.

If I try to uninstall evolution, it also wants to uninstall "ubuntu-desktop"  I hesitate to do this as other than my attempt to try evolution, I'm happy with the way everything else is working.

Anyone using Ubunto 6.06 evolution with MS exchange server successfully?

--wally.

---

### Post by Hmarroqu on 2006-10-26
try thunderbird?

---

### Post by wkulecz on 2006-10-26
I guess you missed the part about needing to connect to MS exchange server.  If it supported pop or imap I'd not be messing with evolution.

--wally.

---

### Post by wkulecz on 2006-10-26
I got it to work, sorta of.  Mistakes in setting up the account seem to lock it up easily, it other places its so slow it appears to have locked up.

Its such a great "clone" of MS Outlook it sucks every bit as much!  Everything I hate about Outlook seems to be there :(

My advice would be to forget about it if you've any other alternative, unfortunately if you are stuck like me where I'm forced to use MS Exchange *and* external pop, imap, webmail are blocked, there are few options.

I'd been using the webmail interface to MS Exchange and its worked well enough, but the powers that be decided it needs to log me off automatically after a few minutes making it pretty worthless!

Edit:
I overcame the password lockup problem by deleting the $HOME/.evolution folder and starting from scratch.  Got it correct enough on the third try to proceed.

--wally.

---

### Post by wkulecz on 2006-10-27
The performance of Evolution increased dramatically when I removed the ldap server entry for the "global address book".  Its at least as usable as Outlook is for me (minus the global address book which I rarely use), but that's not an endorcement.  As I said, Evolution has cloned all the things I hate about Outlook with no apparent way to change the behaviour, same as Outlook :(

--wally.

---

