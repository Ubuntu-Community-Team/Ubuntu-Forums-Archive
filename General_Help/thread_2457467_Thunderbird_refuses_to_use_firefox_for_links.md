---
title: "Thunderbird refuses to use firefox for links"
date: 2021-02-02
forum: General Help
---

### Post by adrian-h on 2021-02-02
This is on my main PC which is still Ubuntu 18.04.  But is checked for updates daily and think I may have had some today as well.

For some reason I had major issues with Thunderbird mail today, thought I had lost everything as when I went into thunderbird I was required to start new accounts.  After much probing around I realised that thunderbird was not as per all the google searches told me but as installed from a snap was in a different location.

I was able to go into the profiles.ini, change from the new just opened profile and go back to the original profile.  Restart thunderbird and find all my emails and accounts are back as normal.  But I can not open a link from within an email.  Thunderbird refuses to let me set Firefox as the default action, no matter what, it stays as always ask, even when I try changing it manually to Firefox it does not recognise Firefox is there?

I am quite clueless on this, so I tried going through a few things including  Tools - Developer Tools - Debug add ons where I see this error message

[ATTACH=CONFIG]287893[/ATTACH]

Just checking the version number of Thunderbird I get 86.0b1 and notice that it has just come out recently, so perhaps it was installed today.  I seem to be on some beta channel if that makes a difference, not sure?

Firefox is 85.0, it is a 64 bit system, (although I believed that it all was now) just checked and no updates available, I seem fully up to date, but I am not sure if this is an update issue or a corrupt file issue so any help is appreciated.

Before I forget I also installed gnome web browser to see if Thunderbird gave me the option to open links in that, again without success.  After many hours of poke and hope,  before I go to sleep (02:00), I thought I would post here to get some ideas from more knowledgable people and I will try again in the morning.

If I have posted in the wrong area please move.

Cheers

Adrian

---

### Post by CelticWarrior on 2021-02-02
Yes, that Thunderbird is a beta version may have something to do with it all. How exactly have you obtained it? Certainly not from regular updates unless you added a PPA. Or it's a snap that you purposefully installed but either way you should know what you did??

---

### Post by adrian-h on 2021-02-03
It is a snap, I did mention that, for some reason when I installed some time ago I picked it from the Ubuntu software list, not realising it was beta.

On trying the install the normal version and run it it will not run with the beta profile.

I guess I either wait for an update to this version to see if things get fixed or I start afresh.

Adrian

---

### Post by CelticWarrior on 2021-02-03
Thunderbird (stable - non-snap) comes standard with Ubuntu. Why install another, I wonder?

But it being a snap the problem may stem from lack of permissions (snaps are sandboxed). You may want to check it directly in Ubuntu Software. Search for it, open the page and you should see the Permissions button.

---

### Post by adrian-h on 2021-02-03
I would have to remember some time back why I installed from a snap, both stable and beta are in the Ubuntu software list and I installed the wrong one.  I think I was using evolution originally as I migrated from Opensuse some time ago, but all a faint memory now.

I have had some success with a clear head and some poke and hope at this end.
From command line I installed thunderbird again ran it  and created a new profile.    I have always stored all sent, and saved emails in local folders rather than out on the the internet or other servers, and a bit more reading suggested I could add them to the stable version.  The settings did not give me as many options to change locations as the beta version, so relied on the file browser to move things around, but copying the snap local folders into the stable local folders gave me all my emails in the stable version.  Then create the rest of my email accounts and  change the settings to stick all in local folders and all looks OK.

With the stable version http and https links once again open with firefox.  I have changed favourites so that when I select open my email client, I open the stable version and if all stays OK after a few days I will then de-install and clean up the beta snap version of thunderbird to remove it once and for all.

Another thing to remember if I can.

Here's hoping it stays OK.

Adrian

---

### Post by adrian-h on 2021-02-03
Marking as solved, obviously an issue with the beta version as all works OK with a standard release.  PC has been rebooted several times and is getting and sending emails all OK now.

---

