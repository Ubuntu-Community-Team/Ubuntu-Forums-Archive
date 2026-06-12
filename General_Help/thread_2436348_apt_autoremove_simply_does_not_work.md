---
title: "apt autoremove simply does not work"
date: 2020-02-04
forum: General Help
---

### Post by maxbb on 2020-02-04
So, I decided to check out kubuntu, lubuntu and xubuntu: installed them via apt. Stuff was kind of broken (separate story I won't get into here) so I decided to remove it all

I run `apt remove kubuntu-desktop` etc. 

followed by `apt autoremove`

However, this still left a LOT of junk behind.

I tried cleaning up by doing `apt remove lx\*` and `apt remove xfce\*` and so on and on (followed by "autoremove").

But there is still junk like `plymouth-theme-kubuntu-logo` etc.

Now, I can't simply go though /var/log/dpkg.log and remove everything I supposedly "installed" today (because it lists things like libc-bin.

Anyway, I don't know if it's me who's doing this wrong, but having used Linux since the late 90s, I don't consider myself a noob, and I'm inclined to think this functionality is utterly broken (and its existence is misleading)

---

### Post by CelticWarrior on 2020-02-04
Removing the meta-packages (e.g. "kubuntu-desktop") does NOT remove what those meta-packages actually installed (hundreds of other packages). It's not a problem with autoremove because that command only removes orphaned packages and the packages installed by the met-packages don't have the met-packages as dependencies.

---

### Post by maxbb on 2020-02-04
> **CelticWarrior said:**
> Removing the meta-packages (e.g. "kubuntu-desktop") does NOT remove what those meta-packages actually installed (hundreds of other packages). 

So how is one supposed to remove them?

---

### Post by CelticWarrior on 2020-02-04
> **maxbb said:**
> So how is one supposed to remove them?

Manually (and there will be dragons).

That's the downside of installing multiple desktop environment: They're usually very easy to install thanks to the meta-packages but removing them entirely (and expecting a functional system afterwards) is in the polar opposite. Reinstalling the original OS will likely be a lot faster and safer.

---

### Post by maxbb on 2020-02-04
> **CelticWarrior said:**
> Manually (and there will be dragons).

That's the downside of installing multiple desktop environment: They're usually very easy to install thanks to the meta-packages but removing them entirely (and expecting a functional system afterwards) is in the polar opposite. Reinstalling the original OS will likely be a lot faster and safer.

But why?!

Why doesn't Ubuntu/apt/dpkg manage these dependencies automatically? It's just a directed acyclic  graph...

---

### Post by CelticWarrior on 2020-02-04
I'm not a dev and it's very unlikely you'll find one here.

May I also suggest that you try to understand how things work first instead of demanding changes just because? Most of your posts suggest you don't know as much as you think you do and in spite of that you tend to complain about the things you don't understand in a somewhat confrontational way to people who, again, are just users like you, not Ubuntu developers.

---

### Post by maxbb on 2020-02-04
> **CelticWarrior said:**
> I'm not a dev and it's very unlikely you'll find one here.

May I also suggest that you try to understand how things work first instead of demanding changes just because? Most of your posts suggest you don't know as much as you think you do and in spite of that you tend to complain about the things you don't understand in a somewhat confrontational way to people who, again, are just users like you, not Ubuntu developers.

So let me see if I understand: you can't explain why this is the way it is. But you think I shouldn't question it because I don't know why this is the way it is? (I'm a programmer BTW, but I work on scientific software)

---

### Post by CelticWarrior on 2020-02-04
> **maxbb said:**
> So let me see if I understand: you can't explain why this is the way it is. But you think I shouldn't question it because I don't know why this is the way it is? (I'm a programmer BTW, but I work on scientific software)

What I said is there's no point in complaining **here** (and merely echoing a sentiment already expressed in a thread of yours back in 2017).

And I have an idea why this is, definitely, but I'm not in the mood of explaining it to you, considering the original reply answered your initial question and also corrected the misunderstanding about the autoremove "functionality is utterly broken (and its existence is misleading)".

---

### Post by maxbb on 2020-02-04
> **CelticWarrior said:**
> What I said is there's no point in complaining **here** (and merely echoing a sentiment already expressed in a thread of yours back in 2017).

And I have an idea why this is, definitely, but I'm not in the mood of explaining it to you, considering the original reply answered your initial question and also corrected the misunderstanding about the autoremove "functionality is utterly broken (and its existence is misleading)".


I did not write anything about autoremove in 2017.

You don't need to know the intricacies of how something works to suspect a problem. Iowa just messed up their primaries. Transunion leaked everyone's credit data to hackers. I don't know the details. I don't want to know the details. But I'm inclined to think there was a problem.

---

### Post by wildmanne39 on 2020-02-04
Let's get back on topic and stick to the issue at hand and please by nice, you may want to review the rules of the forum:

[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

Specifically:

> The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.

We do not allow threads to go off topic or negative interaction between members.

Thanks

---

### Post by Frogs Hair on 2020-02-04
These [commands]("https://www.psychocats.net/ubuntu/pureubuntu") are outdated, but they were based on packages added while installing various desktop environments and only for reference. As a person who has experimented with installing and removing different DE's I found the synaptic package manager a helpful tool , but in the end it was quicker to reinstall the desired version of Ubuntu. Testing from live disk/usb or using a vm to experiment with different flavors of Ubuntu is much easier than hunting down orphaned packages.

---

### Post by Artim on 2020-02-04
Save your docs, pics, videos, bookmarks, etc (not the /home* partition* because it has all the default desktop settings and stuff you don't want) to a separate drive and re-install the 'buntu you wish (Lubu, Xubu, Ubu, whichever).  Metapackages are not "real" packages, and each installed package would have to be manually uninstalled.  It becomes a confusing mess!

I cannot tell you why removing meta-packages won't take out everything they install, but I can tell you that "autoremove" only purges "orphaned" packages.  You probably have none!  But your HDD is full of abuncha cruft you don't want.  Do the simple and easy thing:  Backup and re-install.

---

### Post by Skaperen on 2020-02-04
> **maxbb said:**
> But why?!

Why doesn't Ubuntu/apt/dpkg manage these dependencies automatically? It's just a directed acyclic  graph...

this might be considered an unusual use.  i would disagree with that because i have had the same problem.

what i do is save a list of what packages i have installed before i do this.  then i can use that as a control and purge everything not on that list.  actually, i save such a list when i do upgrades or install or remove any package.

i save a list of objects in certain directories, too.

---

### Post by QIII on 2020-02-05
I would certainly agree that it should be easier to remove the lot -- and that if it is this difficult it needs to be addressed.  

One of our formerly very active members, aysiu, used to religiously maintain [https://www.psychocats.net/ubuntu/index.php](https://www.psychocats.net/ubuntu/index.php).  I don't think so much any more.  Somewhere in there there were some articles about returning to "clean" versions after adding other DEs.  Unfortunately, some of that stuff is so old I don't know if any of it would be useful -- or safe.

Since all of us here, including the Staff, are end-user volunteers, we can't answer for or make any changes to what the devs do.  However, this might be one of those things you'd like to discuss with the devs.  That can be done by joining in on this mailing list:  [https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss)

If you are an IRC type, one of the channels [here]("https://wiki.ubuntu.com/IRC/ChannelList") might get you in contact with the devs.

One thing is certain:  If it has not yet been brought to their attention and is not now, they'll never know.

---

### Post by TheFu on 2020-02-05
Metapackage dependencies are a **singly linked list**. One-way only.  They exist for convenience.  
Breaking a metapackage is easy. For example, each flavor has a different terminal program.  Remove that and the metapackage breaks. The packages that the metapackage is dependent on don't know anything about the metapackage.  Similarly, the libc package doesn't know any packages which are dependent on it. There must be thousands of those.

If we want to remove packages using globbing, use apt-get.  If we want to see a list of packages and select which to remove, use synaptic.  ubuntu.com has package dependencies, so if we like, we could take those dependencies and remove them, but other packages might also be dependent on those packages.

---

### Post by ajgreeny on 2020-02-05
Run the command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log | grep kubuntu-desktop
``` sandyou can quickly find the date and time you installed that metapackage.

You could then, by replacing **kubuntu-desktop** in that command with the date and an edited part of the time string, see what other packages were installed at approximately the same time as your metapackage.

It will be a long list and it may take some time to sort out exactly what was added by that one simple command, but it is possible (I have done it as an experiment when I had some spare time using a virtual install).  You can then remove all those packages with the ```
sudo apt purge
``` command

I also believe, however, that it is probably a lot simpler, and a great deal quicker to reinstall having backed up your data files.  A reinstall of the OS itself takes @ 15 minutes in my experience, then a bit longer if you need to add extra packages you want. It's your choice, but that's what I would do!

---

