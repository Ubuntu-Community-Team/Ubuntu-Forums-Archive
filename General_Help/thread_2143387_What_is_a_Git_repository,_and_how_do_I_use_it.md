---
title: "What is a Git repository, and how do I use it?"
date: 2013-05-08
forum: General Help
---

### Post by temporos on 2013-05-08
I've been having issues with the pcmanfm file manager not starting in 12.10 after [changing the wallpaper via bash script]("http://ubuntuforums.org/showthread.php?t=2076417").

I looked around and found [this]("http://ubuntuforums.org/showthread.php?t=2074242") thread, which alerted me to [a known bug that was apparently solved]("http://sourceforge.net/tracker/?func=detail&aid=3578503&group_id=156956&atid=801864").

The bug tracker page mentions that it's solved in "the latest Git repository." :confused: What's that, how do I get it, and how to I use it to fix this bug? From what I've read, a Git repository doesn't seem much different than a PPA. Is this correct? Can I simply add it like I would a PPA and then force an update using *apt-get*?

---

### Post by pqwoerituytrueiwoq on 2013-05-08
a git repo has source code a ppa has compiled applications
you have to compile it from git, unless it is scripts

this needs to be compiled
[https://github.com/geekless/pcmanfm](https://github.com/geekless/pcmanfm)
**i don't know how to compile this, check the readme

---

### Post by papibe on 2013-05-08
Hi temporos.

Git is a distributed revision control and source code management (SCM). A Git repository contains the **source code** of the project or application.

In order to install a program from a Git repository, you would need to:
[LIST]
[*]Install the git client.
[*]Install several development tools.
[*]Checkout (download) the source code.
[*]Configure it.
[*]Compile the code to generate a binary program.
[*]Install it into your system.
[/LIST]
Here's example of getting VLC from the Git repositories: [Howto: Compile the development version of vlc under the latest Ubuntu release]("http://ubuntuforums.org/showthread.php?t=2141949").

A PPA contains already compiled and ready to install software.

I would recommend first trying to find pcmanfm's PPA with package versions above the one solves the problem. They are usually named either unstable, dev, nightly build, etc. 

Another alternative would be to enable 'Pre-released updates' in your 'Software Sources'. This would only solved the problem if the new version is already there waiting for proper testing. Note that this would enable the installation of all pre-released packages.

Does that help? Let us know how it goes.
Regards.

---

### Post by temporos on 2013-05-15
Sorry it took so long to respond. Life's been demanding unrealistic amounts of my time lately. x_x;

Anyway, I did find the PPA lubuntu-dev/lubuntu-daily which contains the most recent (dev) updates for pcmanfm. Of course, this also means I'll be getting dev updates for **all** lubuntu packages. :neutral: It's going to take a reboot and probably a few days for it to fetch the latest package updates on its own, so I'll let you know how that goes in a bit.

---

### Post by temporos on 2013-05-19
Thanks on two counts. First, you explained quite nicely what a git repository was. Secondly, this specific issue with pcmanfm was remedied by your suggestion. I'll mark this as "solved."

Unfortunately, a few other pcmanfm issues popped up with the dev update. :sad: That's a separate issue, though, so I made [a new thread]("http://ubuntuforums.org/showthread.php?t=2146841") for it.

---

