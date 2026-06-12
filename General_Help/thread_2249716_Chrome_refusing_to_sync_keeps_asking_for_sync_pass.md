---
title: "Chrome refusing to sync: keeps asking for sync passphrase"
date: 2014-10-24
forum: General Help
---

### Post by Mike_Walsh on 2014-10-24
Morning, everybody.

I appear to have a small problem with Chrome..!

I run several of the 'buntu distros, and have Chrome installed on every one.....so the 'syncing' feature comes in handy. Every install of Chrome is up-to-date, so there's no problems there.

I also run 'Slacko' Puppy Linux 5.7.1.....the current release. It comes with Firefox 17 ESR as standard, but I decided last night to install Chrome from the Puppy repositories (you can't install the download from Chrome, because that only comes in .deb or .rpm formats, plus a few other non-mainstream ones). It doesn't come in the correct format for Puppy to recognise and use.

I didn't find out till after installing it, that this is version 25. Chrome is currently on 38..

Anyway; this is where the problem started. I signed into Chrome as I normally do.....only this time, it came up with 'Sync error has occurred; your data has been encrypted with a different passphrase on another computer. Please enter passphrase below'.

Does anybody know what this 'sync passphrase' IS? I have always had the same password on Chrome for years now; so I don't see how there can be another one!

I'm STUMPED. Doesn't stop me using Chrome; but it's annoying to have to manually transfer bookmarks and settings from one distro to another. Has anybody come across this one before.....and if so, how did you manage to sort it out? I'd love to know.

Failing that, does anybody know how you can actually get in touch with a Google rep in the UK, so as to resolve the issue?

Any suggestions, as usual, much appreciated.


Regards,

Mike.

---

### Post by kc1di on 2014-10-24
Hi Mike,

there may be a clue on this [puppy page]("http://www.murga-linux.com/puppy/viewtopic.php?t=86501").  It's about upgrading to Chromium 34 on puppy, but should work for Chrome also.
Think there are a couple packages your missing in puppy that need to be installed first.  In any event hope it's helpful. It's been awhile since I played with slako.
libgconf2 and libgnome-keyring are the missing packages. 
Good Luck :)

---

### Post by slickymaster on 2014-10-24
By default, your passwords are encrypted with your Google Account credentials. You may choose to encrypt all your synced data with your own sync passphrase.
If you change your encryption method on one computer, you might receive a sync error notification on other computers where you’re syncing your data. Enter the new sync passphrase on other computers to resolve the error.

See this: [Protect your synced data]("https://support.google.com/chrome/answer/1181035")

---

### Post by Mike_Walsh on 2014-10-24
Thanks for the quick replies, guys.

@Dave; Thanks for the info, mate. I don't know why it is, but Puppy, although up-to-date in quite a lot of respects, always seems to use very old browsers, which aren't supported by anybody else. But regardless of whether I can update it or not, the damage has been done.....I'm being asked for a 'passphrase' which I KNOW I don't have; and it's affecting every distro in which I run Chrome!

@Slickymaster; Thanks for that link. Trouble is, I've already followed the info in that link, and it keeps sending me back to the log-in page, and asking me for this 'passphrase'. I have NO idea what the passphrase is; nor do I know where I'm supposed to get it from. I could understand it if I'd changed my password in the past, but I haven't.....I've always used the same one. So; where do I go from here? Any ideas?

Regards,

Mike.

---

### Post by kc1di on 2014-10-24
Give [this page ]("https://support.google.com/chrome/answer/1181035?hl=en&p=settings_encryption")a try it may work.
Seems google assigns a passkey to encrypted data even if you did not ;)

---

### Post by slickymaster on 2014-10-24
Have you tried to reset sync via the Google Dashboard. This will delete all synced data from Google’s servers and disconnect all synced computers and devices, but not the data that’s on your computers or devices. So your current preferences, bookmarks, and passwords will remain available in the browser. You can then re-enable sync with a new passphrase.

---

### Post by kc1di on 2014-10-24
I have slacko working here wit chromium 34 as per the page I first posted.  everything included snyc working fine.

---

### Post by Mike_Walsh on 2014-10-24
> **slickymaster said:**
> Have you tried to reset sync via the Google Dashboard. This will delete all synced data from Google’s servers and disconnect all synced computers and devices, but not the data that’s on your computers or devices. So your current preferences, bookmarks, and passwords will remain available in the browser. You can then re-enable sync with a new passphrase.

'Fraid so. That was the next thing I tried!

Sorry for the delay; been out in the garden. Let me get this straight. You say if you reset it via the dashboard, that you need to set it with a new passphrase? Now, THAT I wasn't aware of...I'll give it a try...let you know how I get on.

Regards,

Mike.

---

### Post by Mike_Walsh on 2014-10-24
> **kc1di said:**
> Give [this page ]("https://support.google.com/chrome/answer/1181035?hl=en&p=settings_encryption")a try it may work.
Seems google assigns a passkey to encrypted data even if you did not ;)

Thanks for that, Dave...I've had a look at it; not one I came across last night, when I was researching ways to fix this.

Snag with THAT is that it won't LET me sign in UNTIL I enter this 'passphrase'. I'll quite happily set my own passphrase, IF & WHEN I can GET signed in.....do you see the problem?

Until I CAN sign in, I'm pretty much stuffed!

Cheers! :)

Regards,

Mike.

---

### Post by Mike_Walsh on 2014-10-24
Thanks for the 'Puppy' tip, Dave; it's all installed nicely, and up-and-running. Still got the syncing problem, but I can still use Chromium...it definitely works. At least this version lets me access the App Store...that's something!

Regards,

Mike.

EDIT: Curiouser & curiouser! Your tip, Dave, has apparently solved BOTH problems at the same time. Wiping the 8 GB flashdrive, doing a fresh install of 'Slacko' (with a change to the SysLinux bootloader, since my original MBR appeared to be corrupted), and following your link to install Chromium 34, instead of version 25 as supplied in the Puppy repo's.....it's also cured the syncing problem with all my OTHER Chrome installs; they're ALL behaving themselves now.

Thanks for that! Appreciated.

I'll mark this one 'Solved'!

---

### Post by nerdtron on 2014-10-24
Post number 4 and 5 here are worth a shot as it solved their problem [http://ubuntuforums.org/showthread.php?t=2249594](http://ubuntuforums.org/showthread.php?t=2249594)

---

### Post by kc1di on 2014-10-24
Happy it worked out for you :) 
enjoy

---

### Post by Mike_Walsh on 2014-10-24
> **kc1di said:**
> Happy it worked out for you :) 
enjoy

Thanks again, Dave. From what I can see of it, it looks as though Chromium 25 is no longer compatible with the current syncing procedures.

I'm not TOO fussed. Google have issued 4 updates to Chrome/Chromium in the last 3 months or so; I was still using version 34 of Chromium as recently as late July/early August.....so it's not THAT out of date!

I'm quite pleased, really. Up until this last attempt (I'd been using 'Precise Puppy, rather than 'Slacko'), I'd only got the one browser (SeaMonkey), and I could NOT get my Epson SX218 all-in-one to work at all. That was until I realised that Puppy is a 32-bit operating system.....and I was using 64-bit drivers, since my system is 64-bit, and all my other distros are 64-bit! Now I've got Firefox AND Chrome, and my Epson all-in-one is finally doing what it was supposed to all along.

It's an easy mistake to make, actually. The AMD Athlon 64 CPU in my system was the very first processor on the market, back in 2003/4, to run 32- OR 64-bit OSs & applications natively, with no input needed from the user. So I could be forgiven for thinking it was 64-bit, since it ran perfectly okay; but, thinking about it, the fact there was no choice of OS on the Puppy download page WAS a bit of a giveaway, since a 32-bit system WILL run with ANY CPU manufactured in the last 10 years...

> [COLOR=#000000]It's been awhile since I played with slako.[/COLOR]

I like your turn of phrase! It's exactly what I do; have a 'play' with Puppy, when I'm getting fed up with the others. I think it's a really neat little distro; but coo! 'Rox-filer' DOES take some getting used to, doesn't it?

Regards,

Mike.

---

### Post by kc1di on 2014-10-25
Yes in deed slako and all the puppys take some getting used to ;) 
I always keep a couple discs or usb drives load with one or the other and use them every once in a while.  especially on older equipment.
In any event they are fun distros to play with.
Have a good Weekend.
Dave ;)

---

