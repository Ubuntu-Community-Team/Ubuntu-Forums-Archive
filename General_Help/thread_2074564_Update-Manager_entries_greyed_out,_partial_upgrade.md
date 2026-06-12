---
title: "Update-Manager entries greyed out, partial upgrade"
date: 2012-10-21
forum: General Help
---

### Post by Yumi on 2012-10-21
Am on Quantal. Update-Manager offers Partial-Update and there are many greyed out and inaccessible entries.

How can I set Update-Manager back to a normal state and get rid of the greyed out entries. They must be listed somewhere.

I upgraded to Quantal during the last Beta stage. All went well, the system is faster then 12.04. Initials updates went as expected.

But since a few days the Update-Manager only offers the Partial-Update. The upgrade disabled a number of 3rd-party repositories which referred to older distributions as far back as natty. I removed them since.

Sources.list is ok and all set to Quantal repositories.

The system runs stable, everything working, and faster then 12.04. I am reluctant to jeopardise this situation.

---

### Post by BlinkinCat on 2012-10-21
If you haven't run the partial Update Don't.

Wiser heads than mine can explain why - :)

---

### Post by BlinkinCat on 2012-10-21
Hi again,

If it is a partial upgrade you are referring to, look at this for starters -

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

Sorry I can't help with your other questions.

Cheers, - :)

---

### Post by Yumi on 2012-10-21
My question is not about a partial-upgrade to accept it or not, it is about how to correct a situation which has arisen and needs to be fixed. The partial-upgrade message is only one of the symtoms.

---

### Post by Yumi on 2012-10-23
Well, I took the jump and accepted the partial upgrade. All went well, system working normally.

Problem: There are lots of greyed out entries which are not accessable. How to get rid of them? There must be a list somewhere in the system which I can delete. But where?

---

### Post by Yumi on 2012-10-24
System is continous working, but it seems my updates are all in a mess. Unmet dependencies seems to be the main reason.

Example: Gimp for 12.10 depends on libbbabl-0.1.0. ;obgeg;-0.2.0 and libtiff5. I have versions of all three installed but the required versions are "but it is not installable"

Any suggestions?

---

### Post by plucky on 2012-10-24
> **Yumi said:**
> Well, I took the jump and accepted the partial upgrade. All went well, system working normally.

Problem: There are lots of greyed out entries which are not accessable. How to get rid of them? There must be a list somewhere in the system which I can delete. But where?

From a terminal ```
sudo rm /var/lib/apt/lists/* -vf
```

Then run ```
sudo apt-get update && sudo apt-get dist-upgrade
``` and see if you still get the greyed out updates.

You might have to remove the **/var/lib/apt/lists/partial** directory,but try the previous commands first.

Good Luck

---

### Post by Yumi on 2012-10-24
Thanks Plucky, this was the right advice. I had managed to do that before reading your mail and did not remove the files you mentioned. But sudo apt-get update && sudo apt-get dist-upgrade worked.

It let to a "failed load gnome-session" at login, but sudo apt-get install gnome-panel solved that (I am on gnome not unity).

Presumably the upgrade from the last beta to the release version did not happen as expected, at least not automatically. I had done a dist-upgrade from 12.04 to 12.10 beta and assumed that that was it.

---

