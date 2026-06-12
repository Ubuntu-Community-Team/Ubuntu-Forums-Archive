---
title: "Need Help to Clean up after WUBI"
date: 2007-08-07
forum: General Help
---

### Post by Curbuntu on 2007-08-07
Well, I broke my own rules -- "never try beta software on your main production machine."  I downloaded and installed WUBI today and tried it.  Having run the .exe file, I rebooted, as ordered, and chose "Ubuntu" from the startup menu.  Things went along well until a big red screen flashed up, saying:

[CENTER]Unbuntu Installer Main Menu
Invalid User Name[/CENTER]
*The username you entered was invalid.  Note that usernames must start with a lower-case letter..."*, etc.

I alt-ctrl-del'd, brought Windows XP Pro back up, uninstalled WUBI (just to be safe) then ran it again, paying special attention to the username.  (I accepted WUBI's default, which was clearly all lowercase.)

Rebooted.  Same error.  Rebooted to XP, uninstalled WUBI, deleted WUBI, awaiting its post-beta days.

Ah, but now the pain begins.  I can't boot into Windows XP.  The splash screen with the moving blue horizontal squares comes up, but it doesn't get any farther along, no matter how long I wait.  I *can* boot into Window "safe mode."  I have tried reverting to the most recent Restore Points, but to no avail.

What am I up against, and how do I fix it?

I wish WUBI all the best (I'd love to run Ubuntu on this laptop, but I'm too nervous to try letting Ubuntu repartition the drive that has all of my working data, though it's all backed up), but for me, at least, WUBI's not quite ready for prime time.

---

### Post by tuxcantfly on 2007-08-08
> Ah, but now the pain begins. I can't boot into Windows XP. The splash screen with the moving blue horizontal squares comes up, but it doesn't get any farther along, no matter how long I wait. I can boot into Window "safe mode." I have tried reverting to the most recent Restore Points, but to no avail.

Ouch, that doesn't sound good... maybe try booting the WinXP recovery cd, when you get to the menu, press "R" to get into recovery mode, login, then enter these commands:

```
chkdsk /r
fixboot
fixmbr
```

---

### Post by ago on 2007-08-08
> **Curbuntu said:**
> Well, I broke my own rules -- "never try beta software on your main production machine."  I downloaded and installed WUBI today and tried it.  Having run the .exe file, I rebooted, as ordered, and chose "Ubuntu" from the startup menu.  Things went along well until a big red screen flashed up, saying:

[CENTER]Unbuntu Installer Main Menu
Invalid User Name[/CENTER]
*The username you entered was invalid.  Note that usernames must start with a lower-case letter..."*, etc.

I alt-ctrl-del'd, brought Windows XP Pro back up, uninstalled WUBI (just to be safe) then ran it again, paying special attention to the username.  (I accepted WUBI's default, which was clearly all lowercase.)

Did you use version 7.04.04? If you used the file in download.com, that had a bug that was fixed on subsequent releases

---

### Post by Curbuntu on 2007-08-08
> **tuxcantfly said:**
> Ouch, that doesn't sound good... maybe try booting the WinXP recovery cd, when you get to the menu, press "R" to get into recovery mode, login, then enter these commands:

```
chkdsk /r
fixboot
fixmbr
```

Thanks for the quick reply!

All right, now we expose the fact that I'm ignorant bilingually -- in Linux and XP Pro: 

[LIST=1]
[*]Is the "Windows Recovery CD" the same as the original CD (which I have handy), or is it one generated subsequent to installing XP?

[*]Does the "mbr" (in "fixmbr" above) stand for "Master Boot Record"?  I've heard of it, but never had to delve into it.  Out of curiosity, why would I be able to boot into Windows "safe" mode (would that ALL Windows modes were "safe"!), but not a normal boot?
[/LIST]

Thanks in advance.

---

### Post by Curbuntu on 2007-08-08
> **ago said:**
> Did you use version 7.04.04? If you used the file in download.com, that had a bug that was fixed on subsequent releases

Yes, I did download from Download.com, so that must have been the case. I believe the version from Download.com was 7.04.01.  Are the problems I reported in ".01" known bugs that have been fixed in ".04"?

---

### Post by ago on 2007-08-08
> **Curbuntu said:**
> Yes, I did download from Download.com, so that must have been the case. I believe the version from Download.com was 7.04.01.  Are the problems I reported in ".01" known bugs that have been fixed in ".04"?

7.04.04 should have the username issue fixed, unfortunately updating download.com is a bit tricky, it's always better to download from our website or sourceforge.

---

### Post by Curbuntu on 2007-08-08
> **ago said:**
> 7.04.04 should have the username issue fixed, unfortunately updating download.com is a bit tricky, it's always better to download from our website or sourceforge.

Understood.  Meanwhile, I have to fix the "mess" Wubi made on my system (an MBR problem?).  See the other subthread for details.

Any other known bugs or "gotchas" in the beta?  And is there an official release date yet (or at least a target date)?

---

### Post by ago on 2007-08-08
> **Curbuntu said:**
> Understood.  Meanwhile, I have to fix the "mess" Wubi made on my system (an MBR problem?).  See the other subthread for details.

Any other known bugs or "gotchas" in the beta?  And is there an official release date yet (or at least a target date)?

That's due to hard reboots, not the use of wubi pre se, it can happen in windows as well (there are plenty of reported cases), it might be that the filesystem driver used by wubi (ntfs-3g) exacerbates that, but at this point it is unconfimed. We have 100K+ users so and lots of them do hard reboot, we only had a few reports about windows filesystem corruption following a hard reboot, and such threshold does not appear abnormal (take 100K windows users with relatively frequent hard reboots and you will find that quite a few of them will end up with a corrupted fs anyway). This is even more so considering that in our case people do hard reboot more often than usual, which is "understandable" since they are in an unfamiliar environment and do not know alternative ways of getting out of real or apparent jams.

Anyaway, almost always chkdisk /f will fix the issues. On our side we have taken some mesures to minimize the issues, and we have contacted ntfs-3g authors to see if they can improve the robustness on their side, but as mentioned above that is unlikely to be a wubi/linux specific issue and hence it is unlikely to be completely eliminated.

---

### Post by Curbuntu on 2007-08-11
I just wanted to check back to finish up this thread.  The boot from the XP CD, along with the three commands listed, did indeed do the trick.  Thanks very much!

---

