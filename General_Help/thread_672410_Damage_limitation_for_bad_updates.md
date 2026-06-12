---
title: "Damage limitation for bad updates"
date: 2008-01-19
forum: General Help
---

### Post by Zill on 2008-01-19
The recent bad xserver-xorg update has highlighted the lack of readily available user information to help repair a broken system.  While experienced users may trawl through the forums for information, this is not desirable for new and/or inexperienced users.

If an update is found to cause problems then I suggest the following:

1)  Immediately disable the update in all repositories.
2)  Clearly promulgate advice about the bad update on the home pages of ubuntu.com and ubuntuforums.org.
3)  Advise users about the bad update automatically via update-notifier.

It should be possible to implement 1) and 2) immediately.  In order to implement 3) some work would be required for update-notifier.  Is this work feasible?

Any comments on these suggestions?  How could they be implemented?  I have considered blueprint but this doesn't seem quite appropriate.

---

### Post by HermanAB on 2008-01-19
Simple: Don't fix it if it ain't broke.

Most Ubuntu users run desktop systems and are behind firewalls.  In these cases, running frequent updates is not a good idea.  I only install an update for something if there is a damn good reason - installing all available updates in one swell foop is just looking for trouble.  

In general, I re-install my machines once a year with the latest Linux version and I avoid doing updates.  The result is that my machines are stable and humming nicely thank you.

Cheers,

herman

---

### Post by pytheas22 on 2008-01-19
Not installing updates is not an acceptable solution, in my opinion.  A lot of the updates address real security vulnerabilities.  True, a lot of desktop users might not be that vulnerable or concerned about the latest buffer overflow vulnerability, but what about people managing servers that NEED to be as stable and secure as possible, all the time?  Addressing new-found vulnerabilities is important for them, and they should be able to install whatever updates they think they need.  I think there should be a more streamlined process to address updates with bugs in them.

---

### Post by cytg on 2008-01-19
as i stated here in the "Gutsy freezes" thread ; [http://ubuntuforums.org/showpost.php?p=4165307&postcount=75](http://ubuntuforums.org/showpost.php?p=4165307&postcount=75)

i also had an issue with VLC last night .. pretty annoying that this sort of stuff can happen. Perhaps ubuntu should consider another level of support and testing.. maybe something like

1. Restore Points (like in XP). This may defeat the purpose and be defective by design, i dont know, the problem should perhaps be attacked at another level.

2. Segmented update profiles. Give users a choice as to what update-segment they will be in, 1,2 or 3. Level 1 gets the updates first, say a few days before everybody else, reports are gathered and if results are acceptable, push to level 2 and repeat.

3. Building upon suggestion 2. create online database of hardware profiles (with users acceptence) perhaps linked to ubuntuforums, so users with similar hardware constructs will have an easy and direct way to communicate 'issues'.. If this construct was linked directly from the update manager, alot, ALOT, more users would be able to find eachother. and troubleshott issues.

---

