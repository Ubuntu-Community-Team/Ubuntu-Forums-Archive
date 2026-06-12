---
title: "Clean Install of 7.10; After fsck, Files Missing!"
date: 2007-11-19
forum: General Help
---

### Post by acheong87 on 2007-11-19
All I did so far was install Gutsy, setup Firefox, and do some homework.  I'd greatly appreciate it if someone could tell me where I possibly went wrong.  Thank you!

Before installation:

sda1 (ntfs): Windows
sda2 (ext3): I kept my music and Firefox profile here; expecting myself to one day migrate to Linux, I planned to mount this partition as /home.  Windows (iTunes, Firefox, etc.) accessed it via Ext2IFS.
sda3 (unformatted)
sda4 (linux swap)

After installation:

sda1 (ntfs): Windows
sda2 (ext3): /home
sda3 (ext3): /
sda4 (linux swap)

1. First, I edited Profiles.ini in Ubuntu so that it would use the Firefox profile I already had from windows.  But this didn't work.  Then I saw that all the files were owned by "root", so I chown'ed everything in my profile folder (i.e. "dfk4ezkz.default") to my user name.  (Perhaps that was a mistake?)  This worked as far as bookmarks and saved form information, but none of my add-ons were functioning.  For the time being, I ignored the problem.

2. Second, I did some homework - I wrote a simple Perl program.  I also added a keyboard shortcut for opening the terminal.  Then, I shut down Ubuntu and went into Windows, which was hibernated.  (Could hibernating Windows cause issues?  I suspect that it wouldn't properly unmount sda2 (/home) under hibernation, so it may.)  I just had to check something on Windows.  Then, I hibernated Windows again (at the time, I didn't realize hibernation might cause problems), and booted back into Ubuntu.  This time, I was sent to a maintenance shell or something because fsck failed.  It told me to run it manually.  So I did, and a lot of stuff came about something being owned by 61 users (?) and whether I'd like to clone this and that or remove this and that, and fixing incorrect inode sizes, etc.  Finally, I exited that shell, and it continued to the graphical login.  Upon logging in, I found that my keyboard shortcut was gone, and more importantly, my homework was gone.  And my Firefox bookmark was reset, but I was able to pull a backup out.  So I went back into Windows, and when I opened Firefox, it started updating all my Addons and welcomed me to Firefox 2.0.0.9 as if I had just installed it.  I'm so confused about what happened.

I think it has to do with permissions - the discrepencies between "root" and "awc" (my username).  I wonder if Windows is considered "root" when accessing ext3 partitions via Ext2IFS.  Or maybe something else?

Thanks in advance for any help/suggestions!  Perhaps I should not try to share data between Windows and Linux?  (I know that this is always an alternative, but I would like to be able to share data, at least until I get comfortable enough with Ubuntu to stop using Windows.)

---

