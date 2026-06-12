---
title: "Firefox, dissapears?"
date: 2005-07-23
forum: General Help
---

### Post by yay4furryanimals on 2005-07-23
I'm getting a strange problem with firefox, doesn't look like anyone else has it.

In KDE and XFCE when I use firefox, I go to look at my history/bookmarks, anything dealing with the side bar, it will randomly close firefox without warning, and all other firefox processes as well.  It's very random.  It happens regardless of what method I use to view the sidebar (shortcut keys, menu, toolbar button).  Strange.  

Sometimes I can even open firefox and do ctrl+b tons of times, and no problem, but then try at a different time and it bombs (no messages).

Anyone have this problem?  Any log files I can look at?

---

### Post by scoon on 2005-07-23
Hey there, 

Open up a shell and start firefox from there.  When it crashes maybe that will have some info.  If not, try using strace with firefox for way more verbose debugging. 

regards, 

scoon

---

### Post by jeremy on 2005-07-24
Is it the latest version from the repo's? If so, read [http://ubuntuforums.org/showthread.php?t=51058](http://ubuntuforums.org/showthread.php?t=51058)

---

### Post by yay4furryanimals on 2005-07-24
Well I don't even have any extensions installed this is the straight pack from ubutnu rep, 1.0.2

Good idea about the strace.  Getting firefox to seg fault again was nearly impossible, it's such a hard bug to reproduce. I had to redirect strace's stderr to a file because I think the slow console printing was actually helping it not to SEGFAULT.

Here's a snippet of strace when the browser dumped:
```
events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=16, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=4, events=POLLIN}], 8, -1) = 1
ioctl(3, FIONREAD, [32])                = 0
read(3, "\0028\2769\303\274\23\0\324\0\0\0K\0`\2\0\0\0\0\310\1w"..., 32) = 32
futex(0x7fd1f8, FUTEX_WAKE, 1)          = 1
futex(0x7fd1e8, FUTEX_WAKE, 1)          = 1
stat("/usr/lib/mozilla-firefox/res/builtin/userHTMLBindings.xml", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
open("/usr/lib/mozilla-firefox/res/builtin/userHTMLBindings.xml", O_RDONLY) = 31
lseek(31, 0, SEEK_CUR)                  = 0
lseek(31, 0, SEEK_END)                  = 0
lseek(31, 0, SEEK_SET)                  = 0
stat("/usr/lib/mozilla-firefox/res/builtin/userHTMLBindings.xml", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
lseek(31, 0, SEEK_CUR)                  = 0
lseek(31, 0, SEEK_END)                  = 0
lseek(31, 0, SEEK_SET)                  = 0
close(31)                               = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
unlink("/home/charris/.mozilla/firefox/nc3s345b.default/lock") = 0
rt_sigaction(SIGSEGV, {SIG_DFL}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [SEGV], NULL, 8) = 0
tgkill(8667, 8667, SIGSEGV)             = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
```

I thought maybe originally userHTMLBindings.xml needed to exist, so I did  a touch.  But as you can see it opens and closes fine, (Before in a previous segfault it would give NOEACCESS errors).

It's a shame, everything else works perfectly fine.  just this random sidebar seg fault. :(

---

### Post by yay4furryanimals on 2005-07-24
Here's two more:
```

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
}], 8, -1) = 1
ioctl(3, FIONREAD, [32])                = 0
read(3, "\0028d\364\371*\36\0\324\0\0\0K\0\0\3\0\0\0\0\5\1\20\1"..., 32) = 32
futex(0x823aa8, FUTEX_WAKE, 1)          = 1
futex(0x823a98, FUTEX_WAKE, 1)          = 1
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
futex(0x6e5df8, FUTEX_WAKE, 1)          = 1
futex(0x6e5de8, FUTEX_WAKE, 1)          = 1
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
```

Note the futex call.  This sidebar seg fault always happens when it seems when I let firefox idle then come back and do a ctrl+b

I don't see anyone having this problem.  I wonder if it's an AMD64 build problem.

I'm an AIX developer, is there something I can do to help debug this?

---

### Post by jer1ch0 on 2005-07-24
I am having a similar problem with Firefox 1.0.2. Random crashes - mostly when clicking a link. 
Sorry I can't be of any more help.

---

### Post by yay4furryanimals on 2005-07-24
[QUOTE=jer1ch0]I am having a similar problem with Firefox 1.0.2. Random crashes - mostly when clicking a link. 
Sorry I can't be of any more help.[/QUOTE]

Did you install lib flash on a 64 bit platform by any chance?  Firefox will crash on macromedia flash pages.

---

### Post by username1 on 2005-07-24
Since FireFox upgraded a couple of days ago I also have this problem, anything to do with the side bar, anything that should open in an external application, stuff on the tools menu (e.g. clicking extensions) all cause FireFox to evaporate.

This is a 32bit installation and all was working fine pior to the upgrade of FireFox

---

### Post by yay4furryanimals on 2005-07-24
[QUOTE=jeremy]Is it the latest version from the repo's? If so, read [http://ubuntuforums.org/showthread.php?t=51058](http://ubuntuforums.org/showthread.php?t=51058)[/QUOTE]

Ok, looks like the extension problem is related to also the sidebar problem looking through the bugzilla posts there.   To resolve the problem I rolled back like the post said, but for you other's having problems dont be confused.  Eventhough the post says to roll back to 1.0.2, it's a different version it seems then the 1.0.2 version I had problems with that update manager downloaded.

Hope this helps someone else.  Thank you everyone.

---

