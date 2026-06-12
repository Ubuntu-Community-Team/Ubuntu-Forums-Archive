---
title: "Solving dependencies when upgrading a package."
date: 2017-02-07
forum: General Help
---

### Post by AwaitingUserInput on 2017-02-07
I want to upgrade package rawtherapee to the most recent one. The Rawtherapee developers maintain a PPA with the most recent release in it. I've added their PPA to my software sources.

Even so, I cannot get apt-get to upgrade to the latest package.
```

The following packages have been kept back:
  rawtherapee
```

I just did an apt-get dist-upgrade thinking that would solve the problem, but it doesn't.

After more searching, I found that dist-upgrade is not recommended in these cases, and that I should find the missing packages, install them individually through *apt-get install*, and then rawtherapee will upgrade.

Here are dependencies:```

$ apt-cache depends rawtherapee
rawtherapee
  Depends: libatkmm-1.6-1v5
  Depends: libc6
  Depends: libcairomm-1.0-1v5
  Depends: libcanberra-gtk3-0
  Depends: libcanberra0
  Depends: libexpat1
  Depends: libfftw3-single3
  Depends: libgcc1
  Depends: libglib2.0-0
  Depends: libglibmm-2.4-1v5
  Depends: libgomp1
  Depends: libgtk-3-0
  Depends: libgtkmm-3.0-1v5
  Depends: libiptcdata0
  Depends: libjpeg8
  Depends: liblcms2-2
  Depends: libpangomm-1.4-1v5
  Depends: libpng12-0
  Depends: libsigc++-2.0-0v5
  Depends: libstdc++6
  Depends: libtiff5
  Depends: zlib1g
  Conflicts: rawtherapee-data
  Conflicts: <rawtherapee-default>
  Conflicts: <rawtherapee-fresh>
  Conflicts: rawtherapee-unstable
```

Should I just retype every package listed as "depends" in an *sudo apt-get install *command? Do I have to worry about conflicts between 2 different versions of the packages?

What about the "Conflicts" listing that's at the end? Not sure where to go from here.

---

### Post by oldrocker99 on 2017-02-07
There very well may be conflicts. I can't try to duplicate your problem as I'm running 17.04, and there are no Zesty packages on the PPA page.

---

### Post by AwaitingUserInput on 2017-02-07
> **oldrocker99 said:**
> You don't have to do a separate *sudo apt-get install* command. Just separate filenames by spaces and you should be able to get all of them in one fell swoop.

Yes I'm aware of that, but I would tell it to install every one of the packages listed from the apt-cache output?

---

### Post by mc4man on 2017-02-07
You need to remove rawtherapee-data, then rawtherapee will be able to be upgraded.
```
sudo apt purge rawtherapee-data
```

---

### Post by Bucky Ball on 2017-02-07
None of those upgrades commands are going to do much without this one first:

```
sudo apt update
```

ALWAYS run that first. You should install the PPA, run the update command I have given, install the updated app. Perhaps you forgot the update command.

---

### Post by AwaitingUserInput on 2017-02-08
> **mc4man said:**
> You need to remove rawtherapee-data, then rawtherapee will be able to be upgraded.
```
sudo apt purge rawtherapee-data
```

This did the trick! Thanks.

One question: how did you know that I only needed to purge rawtherapee-data? Why not the other packages that were listed as conflicting (see OP for the full list)?

I'm hoping to learn why these things work so I don't have to run to the forums everytime some small issue comes up.

---

### Post by mc4man on 2017-02-09
> **AwaitingUserInput said:**
> This did the trick! Thanks.

One question: how did you know that I only needed to purge rawtherapee-data? Why not the other packages that were listed as conflicting (see OP for the full list)?

I'm hoping to learn why these things work so I don't have to run to the forums everytime some small issue comes up.

a couple of hints - 
from the apt-cache depends
Conflicts: rawtherapee-data

And glancing at the ppa noticed their build does not produce a  whatever-data package
So in this particular case you'd need to 1st. remove the data package as there is no upgrade to it & it conflicts.
(- possibly if they also set the ppa rawtherapee package to Replaces: rawtherapee-data then it may have been removed by apt as part of the update..

---

### Post by AwaitingUserInput on 2017-02-09
Cool. Thanks for the lesson! Thread solved.

---

### Post by mc4man on 2017-02-09
You'd probably find some advantage to using synaptic, in some cases it's better than apt from the command line
(- there are some rare cases where synaptic will choke on upgrades depending on order enabled when individually marking vs. 'Mark all Upgrades' button.
So in this case it would do the proper thing, see screen
(- plus the history option  in synaptic can be quite useful..

---

