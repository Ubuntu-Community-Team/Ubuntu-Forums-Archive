---
title: "aptitude ignoring options"
date: 2007-04-14
forum: General Help
---

### Post by Xyem on 2007-04-14
Just a quick question really ( may apply only to 6.10 but I haven't tested on 6.06 ).

I want to use aptitude to only download the packages for installation, without actually installing them.

I run either the commands
> sudo aptitude -d
> sudo aptitude --download-only

yet, when I press 'g' to action the queue, it downloads them and installs them regardless of the switch. Is this intended behaviour and if it is, am I the only one to think it is misleading?

Otherwise, how to set packages to download only inside aptitude? The 'g' command is 'download/install/remove' packages but there seems to be no 'download' flag I can set.

On a side note, doing
> sudo aptitude -d upgrade
works as intended ( downloads updated packages but doesn't install them ).

Any thoughts on this?

---

