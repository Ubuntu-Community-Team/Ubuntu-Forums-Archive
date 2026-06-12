---
title: "Boinc screensaver"
date: 2018-08-08
forum: General Help
---

### Post by verenard on 2018-08-08
Running ubuntu 18.04 I want to make the Boinc screensaver work. Online forums say modify .xscreensaver file but I don't think I have that.
I want the pretty scientificamal graphics on my machine!

---

### Post by oldos2er on 2018-08-08
Boinc screensaver has never worked in Linux as far as I know.

---

### Post by verenard on 2018-08-09
It says here it's possible. [https://boinc.berkeley.edu/wiki/BOINC_screensaver](https://boinc.berkeley.edu/wiki/BOINC_screensaver)

---

### Post by NM5TF on 2018-08-09
> **oldos2er said:**
> Boinc screensaver has never worked in Linux as far as I know.

it is possible...

I had it working in Ubuntu a couple of years ago....gave it up though....don't remember why, maybe resource hungry ???

@Verenard.....have you tried installing xscreensaver?

tommy

---

### Post by verenard on 2018-08-10
No I don't even know what it is. Well, probably not a goer then - thanks. If anyone has it working let us know.

---

### Post by NM5TF on 2018-08-10
xscreensaver is exactly what it says....a collection of about 229 screensavers plus it can also control monitor blanking/locking & power management....

[https://www.jwz.org/xscreensaver/]("https://www.jwz.org/xscreensaver/")

but I don't seem to remember having to modify it to get BOINC working....but it's been several years since then...

tommy

---

### Post by oldos2er on 2018-08-11
I've tried using the info at [https://boinc.berkeley.edu/wiki/BOINC_screensaver](https://boinc.berkeley.edu/wiki/BOINC_screensaver), don't know what I'm doing wrong but I've never been able to get it to work reliably.

---

### Post by verenard on 2018-08-11
Maybe I'll email boinc and ask someone in the project

---

### Post by oldos2er on 2018-08-11
There have been several threads on this subject on their support forum, [https://boinc.berkeley.edu/dev/forum_index.php](https://boinc.berkeley.edu/dev/forum_index.php)

Please let us know if you find anything useful!

---

### Post by verenard on 2018-08-12
All that effort and they can't make a little screensaver for me ?

---

### Post by NM5TF on 2018-08-12
just looked at the latest 22 JUN 18, BOINC install page  [https://boinc.berkeley.edu/wiki/Installing_BOINC]("https://boinc.berkeley.edu/wiki/Installing_BOINC")....

they have very specific directions to install in Linux.....```
sudo apt-get install boinc-client boinc-manager
```

give that a try & let us know.....

tommy

---

### Post by verenard on 2018-08-13
Well I followed advice on an offical boinc page and installed from software centre.
Now I just tried your command, and terminal says I have both of those up to date, so that can be crossed off.

---

### Post by verenard on 2018-08-13
Are there any obvious things to do with lock screen or power settings that I should do but have missed ?

And for any project with graphics, there is a "show graphics" button which is greyed out. Could be a clue.

I just installed a bunch of projects with pretty graphics - ateroids, Einstein, cosmology, climate prediction - and all of them have the show graphics button greyed.

---

### Post by verenard on 2018-08-13
OK so I assumed that I would already have xscreensaver installed if it was still a current project, but turns out it doesn't come with ubuntu you have to install it. 
So now I have xscreensaver, which might help.

---

### Post by NM5TF on 2018-08-13
from the SETI@home web page....[https://setiathome.berkeley.edu/forum_thread.php?id=76562]("https://setiathome.berkeley.edu/forum_thread.php?id=76562")

"There are two reasons why the Show Graphics button would be grayed out: 1) The workunit is not currently running. Make sure when you select the workunit, that it is in Running status. 2) You are trying to show graphics on a workunit that is running on the GPU. SETI@home's GPU application does not have graphics, so you will not have the option to show graphics in these cases."

from another thread...

"After clicking on the tasks, you do need to click on one of the individual tasks to highlight it before the show graphics button stops being greyed out."

and one other possibility comes to mind.....as a last resort you could download the Windoze version and run it in Linux using WINE...I have not tried this myself

tommy

---

### Post by verenard on 2018-08-14
I'm sure I clicked everything I need to.
I also got xscreensaver and modified the config file like you're supposed to. Probably doing something wrong with basic ubuntu  settings or something.

---

### Post by verenard on 2018-08-14
OK I got as far as installing xscreensaver and adjusting the config file. Now I get a proper show graphic button when I click on a running work unit.
Trouble is nothing happens when I do so.
In fact Einstein is the only one with a none greyed button, the others like Cosmology are all greyed.

---

