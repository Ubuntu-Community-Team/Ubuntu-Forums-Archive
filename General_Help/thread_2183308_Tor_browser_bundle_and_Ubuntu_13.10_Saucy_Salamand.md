---
title: "Tor browser bundle and Ubuntu 13.10 Saucy Salamander"
date: 2013-10-24
forum: General Help
---

### Post by dirtyharry2 on 2013-10-24
Hi guys,

I'm having problems with the Tor browser bundle and Ubuntu 13.10. I've been using the current version of the Tor browser bundle with Ubuntu 13.04 for a couple months without any problems. Yesterday I updated my system to Saucy Salamander and when I started the Tor browser I couldn't type in the URL or search field. When I selected a web site from my bookmarks I couldn't enter any user names or passwords either. The blinking cursor is shown in the respective field but when I hit the key no characters appear.

Any ideas? Thanks in advance...

---

### Post by doug-ravennasprings on 2013-10-25
I can confirm this problem.  Identical issue.  I've attempted various [nearly random] acts to resolve this issue, but have come up with nothing.  I've sent a note to the support email address for tor but haven't heard back.  Since this issue is directly related to the upgrade, I suspect they are as surprised as we are.   I'll refrain from paranoid comments for now.

---

### Post by daniel-wolter on 2013-10-26
Same Problem here with Ubuntu 13.10 and Tor-Browser-Bundle 2.3.25-13

---

### Post by vanadium on 2013-10-26
This is the secret services trying to stop you to use tor through tweaks in various operating systems :lolflag:
It is a problem with ibus. You may temporarily disable ibus
```

ibus exit

```
or remove it altogether if you do not need it (it is used for foreign language input - I did not yet miss it)
```

sudo apt-get remove ibus

```

---

### Post by daniel-wolter on 2013-10-26
@vanadium: thx, the solution for my problem.

For which ubuntu needs "Ibus" ? What happensm if I uninstall ibus?

---

### Post by Jim_Granite on 2013-10-26
I put this in my Ubuntu 13.10 bash_aliases:
alias tor='ibus exit; /usr/local/sbin/tor-browser_en-US/start-tor-browser &'

Then I start TOR with the command line:
$ tor

However, it would be nice to be able to start up TOR from its own onion icon:
* [How do I pin the Tor browser to the Launcher (in addition to Firefox)?](http://ubuntuforums.org/showthread.php?t=2182827) *

---

### Post by doug-ravennasprings on 2013-10-26
Nice solution.
Here's some background on .bash_aliases for those perplexed by it not existing on their system.
[http://www.ubuntujourneyman.com/2011/05/24/100/](http://www.ubuntujourneyman.com/2011/05/24/100/)

---

### Post by dangillmor on 2013-10-26
Uninstalling ibus doesn't fix the lack of keyboard input, at least for me.

---

### Post by vanadium on 2013-10-27
You restarted the system, I suppose?

---

### Post by dirtyharry2 on 2013-10-29
Problem solved... thanks a  bunch!

---

### Post by Jim_Granite on 2013-11-05
The OP might wish to mark this thread as "SOLVED" now that killing and/or removing the ibus seems to work.
Notice that there is still the problem that I had, so, it would be nice if the OP can see if they also don't have ANY icon for the Tor Browser Bundle, when running.

It would be nice if someone confirmed that I'm not the only one with that problem!
 * [Unity bug causes Tor browser icon to accidentally merge with that of Firefox]("http://ubuntuforums.org/showthread.php?t=2182827") *

---

### Post by muppet317 on 2014-02-13
This seems like a much easier and less intrusive solution, one-line edit to the start-tor-browser script. worked for me:
[http://askubuntu.com/a/377321](http://askubuntu.com/a/377321)

---

