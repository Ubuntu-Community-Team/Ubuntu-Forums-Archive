---
title: "Iteratively resolving &quot;../lib/firefox/firefox&quot;"
date: 2008-01-10
forum: General Help
---

### Post by Phrawm48 on 2008-01-10
I'm working on a little script that iteratively uses *readlink* to list all links-to-links-to-links until they reach the final destination.

I believe I need to use a script because while *readlink* includes switches (-e, -f, -m) that will trace links-to-links to their final destination and deliver that end-value, the program has no switch that iteratively lists each link along the way to the destination.  I say I believe this because I've looked at *ls* and *namei* but these don't seem to help...

But there's a bit of a problem with how *readlink* handles certain links.  For example, consider the series of links that point to *firefox*:

> 
[B]# Use *which* to get pathname for firefox
[/B]ric@ric-desktop:/$ which firefox
/usr/bin/firefox

[B]# Use *readlink* to get first link in sequence of links to Firefox
[/B]ric@ric-desktop:/$ readlink /usr/bin/firefox
../lib/firefox/firefox

[B]# Try to use readlink to resolve the relative reference but can't
[/B]ric@ric-desktop:/$ readlink ../lib/firefox/firefox
[*Readlink *returns empty line here]

**# *cd* to directory containing first link in series  and list it**
ric@ric-desktop:/$ cd /usr/bin
ric@ric-desktop:/usr/bin$ ls -l firefox[COLOR=YellowGreen]
[COLOR=Black]lrwxrwxrwx 1 root root 22 2007-12-05 00:11 firefox -> [/COLOR][/COLOR][COLOR=Black]../lib/firefox/firefox[/COLOR]

[B]# Since *readlink* gets "stuck" here, use *cd* to move to relative directory
[/B]ric@ric-desktop:/usr/bin$ cd ../lib/firefox

[B]# The final destination is /usr/lib/firefox/firefox
[/B]ric@ric-desktop:/usr/lib/firefox$ ls -l firefox
-rwxr-xr-x 1 root root 8625 2007-12-04 04:45 firefox
So far, the only way I've found to get past links of the form *../path1/path2/...* is with *pushd* commands.  Alas, I end up counting them to *popd* back to where I started from which seems a silly way to solve this problem...

The key question is, then, does anyone have any ideas how I can get this script to work through those sorts of relative directory references?

Cheers, thanks, & Happy 2008 to all,
Ric
SFO

---

