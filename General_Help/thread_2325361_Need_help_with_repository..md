---
title: "Need help with repository."
date: 2016-05-21
forum: General Help
---

### Post by jordi18 on 2016-05-21
NOT SURE IF THIS IS WHERE I PUT THIS. NEW TO ALL THIS STUFF. So I am trying to install live wallpaper. I add the repository witch is: ```
sudo add-apt-repository ppa:fyrmir/livewallpaper-daily
```

Then I try and install it. thats where I get a problem. 
```
sudo apt-get install livewallpaper livewallpaper-config livewallpaper-indicator
```

The error I get is:

```
E: Unable to locate package livewallpaperE: Unable to locate package livewallpaper-config
E: Unable to locate package livewallpaper-indicator
```

---

### Post by Bashing-om on 2016-05-21
jordi18; Hello;

Looks good, except I do not see where you updated the system to find that new source:
```

sudo apt update

```
But, I would expect " livewallpaper-config" and " livewallpaper-indicator " to be a part of the meta packaging and included in the install .

[INDENT][INDENT]I can be known to be wrong
[/INDENT][/INDENT]

---

### Post by jordi18 on 2016-05-21
I did sudo apt update.
I am still getting the same error.

---

### Post by Bashing-om on 2016-05-21
jordi18; Hey ...

What error and in what context ?
Please post the outputs of terminal commands:
```

sudo apt update
sudo apt full-upgrade

```
so we know the status of the package manager.

[INDENT][INDENT]good place to start, troubleshooting
[/INDENT][/INDENT]

---

### Post by coffeecat on 2016-05-21
Support thread.

*Thread moved to **General Help**.*

---

### Post by jordi18 on 2016-05-21
Really sorry about this. Apparently, when I connect to a different internet connection, it works. Does not make sense to me although I had a suspicion that this might of caused it. Thanks a lot for your time and efforts.

---

### Post by Bashing-om on 2016-05-21
jordi18; Good deal /

Pleased that you returned and gave the resolution.
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

