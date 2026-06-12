---
title: "[SOLVED] Wine Stops Running Mailwasher Pro All of a Sudden?? (It loads but is Invisib"
date: 2008-03-13
forum: General Help
---

### Post by OzzyFrank on 2008-03-13
OK, I've successfully run Mailwasher Pro 3.2 using Wine since Edgy (6.10) and all was fine on Gutsy (7.10) too, until I built my new Quad-core and decided to switch to 64-bit Ubuntu Gutsy. I did the usual, being install through Wine, then copy over the backed up folder so my filters etc were there.

Now, at first it all ran OK, then all of a sudden Mailwasher stopped appearing, though is still there as a running process. Oh, when I say it all ran fine I should say I never got to actually use it, since I was opening the program to check if the filters had been successfully added (there's an art to it I had forgotten), and was about to manually add my accounts and start using it.

Up to this point, Mailwasher would appear and the accounts box would appear on top of it, since it knew I needed to add some accounts. The last time this was accessible to me, I added one of my accounts, and the reason I mention this will become clear.

Now, as I said, suddenly Mailwasher stopped loading, so I tried it all, being reinstallations of the app etc. I tested Wine with my other apps, and the rest seem fine. So I decided to leave Mailwasher.exe as a running process and see what happens... and at least something did.

Either due to my putting in wrong settings for that one account, or due to heavy traffic while downloading, I did get the error message box pop up telling me it couldn't connect to the account. I doubt I put the wrong settings, as the box would then appear every 10 mins, so assume that invisible to me, Mailwasher was in fact checking my mail and only complaining those times when my downloads were taking up the bandwidth (which I am used to).

So, if Wine seems fine, and Mailwasher is indeed loading, why can't I see it? Is there any way to correct this? A Wine command/switch/option that I can try with Mailwasher.exe? I'm perplexed, as it ran fine on all Ubuntu 32-bit versions, and even on 64-bit Gutsy for a short time... and, like I said, tried the old uninstall-and-reinstall a few times and no go (the installer runs fine). And previously, I could even just double-click the .exe on my Windows drive and it would load, and now nothing any which way! I really would like it back, as originally not finding an equivalent prevented me from using Ubuntu as my main OS, and then tried it with Wine and was delighted.

If anyone knows of an Ubuntu equivalent that may have appeared in the last year or so, please tell me too. It would have to NOT be an IP tables based one I can't see, or a terminal app, or the "free" Linux version of Mailwasher (which is free for 30 days, hahaha)... but a proper wysiwyg program as powerful and user-friendly as Mailwasher Pro.

Hope someone can help, as this is driving me nuts!! Cheers

---

### Post by kyphi on 2008-03-13
The current version of Mailwasher Pro is 6.1, so an update might be in order.

I run Mailwasher 6.1 via Crossover Linux which makes it a breeze to install and run.

The Linux versions were scrapped, they were not fully functional and the early versions were extremely ugly..

There is no equivalent in the Linux world.

---

### Post by OzzyFrank on 2008-03-13
Hi, and thanks. Well, my version should be running fine, so the problem is with Wine not running it properly. So I should ask about Crossover Linux, since you run it. Is that free like Wine (heard Crossover Office isn't free)? Can I have apps running in both on one system, or to use one emulator do I have to uninstall the other? I will give Mailwasher Pro 6.1 a go though. Still a frigging mystery as to what went wrong... like I said, even starting from scratch with a new 64-bit Ubuntu system saw it working at first... hopefully some Wine guru can explain it, hehe.

And for you programmers/developers out there: WHAT THE HELL ARE YOU DOING?? Stop writing apps that have a million equivalents already, and get to making a wysiwyg customisable email filter that one can add rules/filters/blacklists/friend-lists/etc to, that can BOUNCE back email before it ever gets to your PC's Inbox (this is what makes Mailwasher Pro so awesome, as many of the spammers take you off their lists once you've bounced back their junk).

---

### Post by OzzyFrank on 2008-03-13
Oh, just from looking at other threads, I thought I would add that anyone wanting to suggest that Thunderbird or other programs have "great email filters", please don't waste your time. The BIG (ok, HUGE) difference is the ability to bounce back the emails before it ever hits your inbox. The only thing in Linux that can do similar, apparently, are IPtable based programs that run in the background, and are hardly customisable (in Mailwasher I can see who is getting automatically blacklisted, and can unmark senders that shouldn't be blacklisted, and add those that should, just by ticking/unticking check-boxes). Thanks to all in advance.

---

### Post by OzzyFrank on 2008-03-13
No go, dammit! The installer runs fine... then when it finishes and asks if I want to run it, the Register box hops up, but with no Mailwasher Pro behind it, like it was in Windows a few minutes back. Getting out of that, there is an animated tour of features, but once again in Windows the main app was behind it, but not in Ubuntu. So, once I clicked out of that, Mailwasher is running somewhere, but is not visible and so is not accessible. I knew upgrading wouldn't help, but it was worth a try.

Now I really would like a Wine expert to suggest something... or more info on Wine vs Crossover Linux. Are there people out there who run both, or have totally gotten rid of Wine in favour of Crossover Linux? Cheers

---

### Post by OzzyFrank on 2008-03-13
Also can confirm that uninstalling Wine and reinstalling it did nothing. Even though there was no update for it in Update Manager, it still downloaded 33.2Mb, so was hoping for the best. But no... my Mailwasher Pro is cursed, no matter what version, or where I try to run it from, or anything!

OK... just tried the option to "Emulate a virtual desktop" under Graphics in the Wine config, and Mailwasher now pops up in that window. I suppose it is mere trivium or fussiness on my part to complain about this, but I rather liked Windows apps appearing as normal Linux ones... and would still like someone more knowledgeable to explain what happened, or if there is a workaround/command option (this is so I can add to my understanding of these technical matters).

Would it be a bug in the last Wine update or something? It obviously isn't Mailwasher nor Ubuntu 64-bit (since it ran ok at first).

Anyway, at least if someone goes searching for the answer to Wine loading an app but it not being visible, this workaround should help get it back.

Now, if anyone knows how to make Wine do this for only one app, not all of them (which it will do with this setting), please post it here! As most of us know, there is a long string of command for any launcher to an exe file (eg: env WINEPREFIX="/home/ozzman/.wine" wine "C:\Program Files\MailWasher Pro\MailWasher.exe") so can one alter this so only this program opens in a virtual window when I reset Wine to its default setting? Since this seems to do with graphics settings, are there command options I can add to this string? I figure there must be. Thanks in advance again.

---

### Post by kyphi on 2008-03-13
The left hand is called "Wine" and the right hand is called "Crossover" belonging to the same being.

Crossover costs $42.00 AUD and since some developments are passed onto Wine, you can think of that modest fee being a little something to support two worthwhile projects.  Remember that programmers need to eat too.

Currently Crossover is also working on "Crossover-Games" which is in Beta stage.

I have never been successful in running anything that I need using Wine.  That is not to infer that Wine is not useful but rather that I have not needed it.

Crossover runs the two programmes that I need and cannot work without.  These are Mailwasher Pro and Pedigree Explorer (for animal breeders).

Another option to run programmes written for Windows is to use a Windows installation in VirtualBox.

Whichever you wish to use, Crossover or VirtualBox, if installed both are readily accessed from the Applications menu on your Ubuntu desktop.

---

### Post by OzzyFrank on 2008-03-14
Hi, and thanks [COLOR="Indigo"]kyphi[/COLOR] for that interesting info. I had no idea Wine was from the same mob, and everything you said made sense. As for paying for Crossover, well, besides the fact that I've paid for so much Windows software over the years, and was hoping to make my Ubuntu experience as cost-free as possible, I've read some reviews that claim Crossover is hardly any better than Wine. I'd really want to be getting something pretty amazing for my money (ie run _every_ Windows app I could possibly need), I don't use enough Windows programs to justify the expenditure.

As for Wine not running Mailwasher Pro (which I agree is an app worth wanting to have on every desktop I use), as you would have read, I never had any hassles... till now.

Anyway, while my steps used and the results obtained above couldn't really justify marking this as [SOLVED], I tried some more things, got a step closer, and finally it is back to what it was.

OK, first off doesn't look like (by using the config) you can have one app in the virtual desktop window and others as standalone (would still be interested to hear if you could force this with a command/option). And while all the apps running in a window is fine if it gets the job done, you can't minimise that (you can the apps within it though, which is the only way to switch between them if you maximise one). Also, don't quote me, but it seemed DVD Shrink was less stable within it (would successfully shrink a DVD, but then disappear at the end of it).

So I thought I would add an application under Application Settings (had tried that but none of the following steps, just telling it to think it was in XP). First, for the default (global) setting, I unchecked "Emulate a virtual desktop" under Graphics (back to the default setting), then for Mailwasher.exe I removed "Allow the window manager to control the windows".

This time, all apps would load in their own windows, and all but Mailwasher even had desktop effects etc. While I was warned that for the better emulation the app would be disconnected from the window manager, and so not end up on the task-list/taskbar, I didn't expect it to be always on top (doesn't look like you can change that anywhere). Then when you minimise it, it doesn't end up on the taskbar, but as a blue rectangle at the bottom of the screen - no big deal, till I realised that was always on top too (not good when watching a DVD, hehe).

So, while I was trying to choose the less of 2 evils, I decided to check if re-enabling "Allow the window manager to control the windows" to Mailwasher.exe would change anything, and up popped Mailwasher Pro in all its former glory. I can (almost) safely say it's fixed, as I exited a couple of times and it still appears as it should.

So, for your Wine apps that disappear but show up as a running process, I would say add it as a new application under the default settings, tell it not to run as the others, then tell it to run as the others, hehe. Hey, it worked, no matter how weird the process! Hope it does for others, but since I doubt those in need will read it here, I will have to post it as a new how-to thread.

Thanks for your help, and hope this can be of use to others! Cheers.

---

### Post by OzzyFrank on 2008-03-14
PS: I can't believe it, but Mailwasher Pro now runs *better* than before, sort of. What I mean is that **forever** (ie since Ubuntu 6.10 through to when it stopped appearing) whenever I closed Mailwasher Pro, an error message box would appear twice and I would have to close it/them before going to exit a second time (which would then close the app).

When in the virtual desktop window and also its own window disconnected from the window manager, it mostly went down to one error message box to click through before being allowed to close the app again. Now that it's in its own window with desktop effects and noted on the taskbar (like before), I get no error messages at all and the app closes instantly (_not_ like before!).

Trivial but worth mentioning.

---

