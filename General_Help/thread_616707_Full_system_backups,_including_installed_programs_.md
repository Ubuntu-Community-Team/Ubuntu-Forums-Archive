---
title: "Full system backups, including installed programs not in repos...?"
date: 2007-11-18
forum: General Help
---

### Post by flamacue on 2007-11-18
I would like to be able to make a full system backup, however, I don't want to make a full partition image.  It seems to me that making a full partition image would be a waste of space:  given all the stuff that's freely available from the online software repositories, why duplicate it in my image, when a list of programs installed (with version numbers) would suffice?

So...is it possible to make a backup that includes:
[LIST]
[*]my user data
[*]a list of programs currently installed
[*]customizations (e.g. programs installed from .debs, manually compiled, etc.)
[/LIST]without the stuff from the repositories?  And ideally to have it kept in a standard format, e.g. .tar.bz2.

I've looked around quite a bit, and not seen any such thing.

If it doesn't exist, does it sound like a good idea?  Anybody to whom I might want to suggest it as a project or feature addition?

---

### Post by scorp123 on 2007-11-18
Take a look here .... the backup tool they discuss there is called "hubackup" and you can install it via "Synaptic":
[https://wiki.ubuntu.com/HomeUserBackup](https://wiki.ubuntu.com/HomeUserBackup)

I myself use this low-level-we-need-the-command-line-for-this method:
[http://linuxmint.com/forum/viewtopic.php?t=3969](http://linuxmint.com/forum/viewtopic.php?t=3969)

---

### Post by Irihapeti on 2007-11-18
If you just want a record of all the programs you have installed, Synaptic can do this for you: File->Save markings and check Save full state, not just changes. It generates a text file. Use it with File->Read markings later on when you want to reinstall.

---

### Post by flamacue on 2007-11-18
The upshot:  Irihapeti's post is the main thing I was missing, plus a little discipline.  I can produce an importable package list with Synaptic, and keep a copy of all downloaded .deb's / executables and compiled binaries in a special folder....under /home (duh, me!).

I think it would be nice to have the package list functionality integrated with a tool like sbackup.  Then it becomes more like an image tool, with a nice (.tar.gz) file format.  What do you think?

Below is a bit of me thinking aloud.  I condensed my conclusions above, but thought I'd leave the rest for...posterity.  :)

Thanks for your help, guys.

(EDIT:  Irihapeti's post got me to research and realize that Synaptic is *not* the same as "Add / Remove Applications"--it's much more powerful!  I used to use aptitude when I wanted that power...yay GUI!)



> **scorp123 said:**
> Take a look here .... the backup tool they discuss there is called "hubackup" and you can install it via "Synaptic":
[https://wiki.ubuntu.com/HomeUserBackup](https://wiki.ubuntu.com/HomeUserBackup)
Not quite what I had in mind.  I'm mainly thinking of the "Norman" case--he gets all his personal data from his backup, but has to reselect all his packages to reinstall.  And if he has any that he installed from somewhere other than the repository, he's got to hunt them down again.

> I myself use this low-level-we-need-the-command-line-for-this method:
[http://linuxmint.com/forum/viewtopic.php?t=3969](http://linuxmint.com/forum/viewtopic.php?t=3969)
Getting warmer here, though it's still a lot of CLI stuff.  I'd rather use a GUI tool, but I wouldn't be opposed to writing scripts if I could reuse them without rethinking them everytime.

The main thing here is "Step 3: Our package selections", and Irihapeti's post seems to speak to using a GUI tool (Synaptic) to take care of the same.

However, this still doesn't capture packages installed from non-repository sources (downloaded .deb files and executables).  Are there some tools we can use to capture these after the fact, or to monitor the system for them as they are installed?  (Alternatively, I can start behaving now, by keeping a copy of any non-repos package installers in a special dir...and back that up.  :))

---

### Post by Irihapeti on 2007-11-18
If you compile programs using checkinstall (it doesn't always work, though, it seems), then they show up in Synaptic package manager as a separate section, and they are included when you generate the "Save markings" file. (I've just tested it.)

That won't automatically fetch them for you, though, unless you have some way of telling Synaptic where to find them. Because I'm on dialup, I keep local copies of all downloaded packages in a local repository - I *don't* want to download everything again. The only problem is that I can't put checkinstall packages in there because they somehow mess up the Packages.gz file and I get an error.

So that leaves binaries compiled with /make. I keep a folder with these packages in them that gets backed up with my personal stuff. I probably have less than 10 of them, though, which makes things fairly simple. I keep the checkinstall debs (again, fewer than 10 or so) there, too.

You've got me curious - I'll be interested to see what comes of this.

---

### Post by mike555 on 2007-11-18
There is an app. called apt2CD (I think) that backs up all your installed and updates so you can put them on a CD , so if you need to install again you can get them from the CD instead of remembering to download them all .......

---

### Post by scorp123 on 2007-11-19
> **mike555 said:**
> There is an app. called apt2CD (I think)  The name of the package is "aptoncd" and it can be installed via Synaptic. It's useful if you want to clone several machines without having to download the same packages again and again (especially useful if your broadband is not a flat rate and has a quota per month). And you can also use it for backup purposes; I personally have not used it in that capacity yet but I heard from people who did and they say it's useful.

---

### Post by kpkeerthi on 2007-11-19
> I myself use this low-level-we-need-the-command-line-for-this method:
[http://linuxmint.com/forum/viewtopic.php?t=3969](http://linuxmint.com/forum/viewtopic.php?t=3969)


Thank you very much scorp123. The ***best*** backup solution I ever loved (especially your style of illustration in that post). Would you mind printing that post to keep for my reference?

---

