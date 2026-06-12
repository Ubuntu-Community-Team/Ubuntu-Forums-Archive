---
title: "Thunderbird updates without permission"
date: 2015-04-08
forum: General Help
---

### Post by newbie13 on 2015-04-08
When any update is available Software Updater shows options to select updates and install them. There are few apps which I don't use but might need in future such as firefox, thunderbird etc. As I am on a limited internet plan I don't update apps which I don't use. But whenever there is an update for thunderbird, even after deselecting it from updating it updates and wastes my data. This has happened two times consecutively and no other app does this.

Any help?

---

### Post by dino99 on 2015-04-08
nobody force you to have them installed; a non installed app is never updated, only the database is updated (simple list of available updates, not the updates themselves)

---

### Post by deadflowr on 2015-04-08
Normally i'd say use a [hold]("https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages").
But since you are not using Thunderbird, now, uninstall it.
If you ever do want to use thunderbird in the future, you will want to use the most recent version, typically.
And the update for the latest version is roughly going to be the same size as it would be if you did it from a fresh install.
So it is not like you will be saving yourself any download bandwidth by keeping it. 

For prosperity. though,
By holding a package you tell the system to lock that version, no matter what.
To do so,
use: 
```
sudo apt-mark hold packagenamehere
```
to mark a package for holding.
And if you want to unhold it
use:
```
sudo apt-mark unhold packagenamehere
```
to unhold the package.

But I would stress you will not be saving yourself much by holding thunderbird.
And not surprisingly, firefox is pretty much the same, so if that package bothers you as well...

---

### Post by newbie13 on 2015-04-09
Okay so I will uninstall it as it I will have to update it again. Firefox is not an issue because it does not update on its own.

But why is that happening? Is it a bug or anything?

Thank you

---

