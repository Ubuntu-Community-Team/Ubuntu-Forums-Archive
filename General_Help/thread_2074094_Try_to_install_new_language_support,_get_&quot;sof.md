---
title: "Try to install new language support, get &quot;software database is broken&quot; message"
date: 2012-10-20
forum: General Help
---

### Post by rudeboyskunk on 2012-10-20
I installed 12.10 and it just didn't work for me, so I re-installed 12.04.1, and after working out the usual stuff, I went to install the extra language packs I need (Korean, German, Spanish).  However, when I try to install them from the Language Support part of the System Settings control panel, I get this error message:

"Software database is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

I checked everything in Synaptic (repos, broken packages, etc) that I could.  I did sudo-apt-get update && sudo apt-get dist-upgrade like 1,000 times.  I tried sudo apt-get install -f.  I tried sudo dpkg --configure -a.  I tried installing each language separately, one at a time, and got the same error message.  I've never had this problem before, and never had any problem installing language support before.  Everything I have found by googling/duckduckgoing this problem points to the above-mentioned solutions.

I'm using a Gateway NV series laptop (64 bit) that I bought in 2010 and have been running Ubuntu on it since (updated every six months with new releases).  I always have no problems with installing language support.

---

### Post by rudeboyskunk on 2012-10-21
I AM A GENIUS.

Ok, I searched in Synaptic for all the language packs, and noticed that language-pack-ko-base (or something like that) had a CONFLICT in its properties dialog box with language-pack-gnome-ko (or something like that) for the Korean (I assume it would be the same with Spanish and German).  The only way I figured there would be a version conflict is if I was getting some packages from a more "bleeding-edge" repo, WHICH I WAS.

SOLUTION:

I went to the repos dialog box in Synaptic and unselected "precise-proposed" as a source, did a quick apt-get update and then was easily able to install the packages.

I will accept payment in the form of flattering praise.

---

