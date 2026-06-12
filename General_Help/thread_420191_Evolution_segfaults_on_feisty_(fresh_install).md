---
title: "Evolution segfaults on feisty (fresh install)"
date: 2007-04-23
forum: General Help
---

### Post by cdheer on 2007-04-23
Apologies in advance, as I am a bit of a linux newb.

Just installed 7.04 Desktop on a Toshiba Satellite P25-S526 laptop (P4 3.2, GoFX5200, 2GB RAM, 80GB HD).  Evolution never loads.  If I click the icon in GNOME, I see "Starting Evolution Mail" in the bottom bar for a while as the cursor clocks, but that eventually disappears and Evo never fully loads.

So.  I deleted and re-created the ext3 and swap partitions (there's an NTFS partition present for WinXP).  Re-installed from scratch.  Did not enable any restricted drivers, or install any updates at all.  Same problem.

If I try evolution from bash, it segfaults almost immediately.  evolution --debug <file> produces no output in the file (just a segfault msg to the term window).  evolution --disable-eplugin (which I saw others mention, though it looks like that was to solve a different problem) also segfaults.

I tried doing a "sudo aptitude reinstall evolution" but that didn't fix anything.  Looked in /var/crash and saw a _usr_bin_evolution-2.10.1000.crash file.  I don't really know what any of it means, but it's a big file; if posting part/all of it would be helpful, let me know.

Any hints would be most appreciated!

--chris

---

### Post by campbr2 on 2007-04-23
I'm having similar problems, it just displays in the toolbar as starting and then disappears.  I've reinstalled several times, but it doesn't help.  I'm using a Gateway laptop with an AMD Turion and ATI graphics if narrows potential problems.

---

### Post by freewind on 2007-04-24
Hi
I have this BUG
Try with  key --disable-eplugin

---

### Post by Volgovod on 2007-04-25
I solved this problem. It is in missing account.

1. Start Evolution with 'evolution --disable-eplugin'.
2. Add your account with 'Edit -> Preferences -> Mail Accounts -> Add'.
3. Subsequently you can start Evolution as usually (without --disable-eplugin).

---

### Post by cdheer on 2007-04-25
No, that doesn't work -- as I posted in my original message, I tried --disable-eplugin but that also segfaults.

Any other ideas?

---

### Post by cdheer on 2007-04-30
Gave up and rolled back to Edgy.  Doesn't look like there's an answer for this at the moment.  Am I the only one having this issue?

---

### Post by kenrmcl on 2008-02-20
> **cdheer said:**
> Gave up and rolled back to Edgy.  Doesn't look like there's an answer for this at the moment.  Am I the only one having this issue?

It's a bit late for another reply, I know. However if someone still has the problem they may find this thread via a search (as I did).

I found that I had the same symptoms even down to the segfault after using the suggested startup switches. I don't know how or why, but what worked for me was:

Step 1) delete the ~/.gconf/apps/evolution/ folder
Step 2) from a console run evolution --disable-eplugin
Step 3) still get a segfault - swear & curse loudly
Step 4) run ls ~/.gconf/apps to make sure the evolution folder was gone (dunno if that has anything to do with it, but that's what I did)
Step 5) run evolution --disable-eplugin again. All works fine so add the new account and everything is up and running.

I have no idea whether the ls command had any effect, somehow I doubt it very much, but that's the sequence I used and it worked. I think that step 5 would have worked anyway, but without doing the  ls command it would have been step 4 :)

I think that just running the evolution command twice was the key but I have no idea why.

Hope that helps someone.

See ya
Ken McLennan
Qld, Australia

---

### Post by fowie on 2008-02-24
If you've tried all of the above, try deleting ~/.evolution
That will remove all of your mail (I believe) but if you're using IMAP like me you don't really care, and it'll get evolution working again.

---

