---
title: "Software updater broken"
date: 2013-09-07
forum: General Help
---

### Post by bkline on 2013-09-07
I rebooted my Xubuntu 13.04 laptop after a set of updates.  When the machine came back up, the update icon was back in the tray, saying "There are 11 updates available."  So I clicked on "Show updates" at which a dialog window came up and said "The software on this computer is up to date."  So, thinking the tray icon needed to catch up, and that it would do so after I dismissed the dialog window, I clicked OK.  But the tray icon remained, still insisting that there are 11 updates to be installed.  So I clicked on "Show updates" again and got the same dialog window saying the computer is up to date.  After repeating this cycle several more times, I began to wonder if the repository is in a confused state, and sending out faulty information.  How would I go about determining if this theory is right?

---

### Post by BlinkinCat on 2013-09-07
Hi,

I don't have answer but had similar problem.

Running 
```

sudo apt-get update

```

and 
```

sudo apt-get upgrade

```

gives a temporary fix at least.

---

### Post by bkline on 2013-09-07
Thanks, that worked.

---

### Post by BlinkinCat on 2013-09-07
> **bkline said:**
> Thanks, that worked.

My pleasure, hopefully the problem will be rectified in an update - ;)

---

### Post by bkline on 2013-10-09
> **BlinkinCat said:**
> My pleasure, hopefully the problem will be rectified in an update - ;)

I would have thought something as annoying as this would have been fixed pretty quickly, but it's still plaguing all my Ubuntu systems a month later.

---

### Post by bkline on 2013-10-09
Perhaps the problem has never been fixed because everyone assumed someone else would report it.  I searched through launchpad and didn't see any bug reports matching this behavior.  So I filed a report myself:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1237562](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1237562)

---

### Post by bkline on 2013-10-10
Well, I'm told that the bug I filed is likely a duplicate of [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1223321](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1223321).  I don't feel too bad that I didn't find that one (I did spend about 15 minutes searching): much of the discussion is not about how to fix the problem, but about how hard the bug report will be to find, given the unintuitive (from the perspective of the end user) way the issue is described.  And I'm not 100% certain that the report I filed is a duplicate.

---

### Post by bkline on 2013-10-10
This is indeed caused by [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1223321](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1223321).  Apparently a modification has been introduced to the Ubuntu software update mechanism which allows the maintainer to mark updates to a packages as "only give this update to a small, randomly selected subset of users of this package, and release it to the rest of the package's users gradually, so if the randomly selected guinea pigs report that the update is badly broken I can pull it from distribution, without having adversely affected the users who didn't get the update yet" (I'm paraphrasing, obviously).  It's a clever idea, but apparently the tray icon which nags you to install the updates which it claims are ready hasn't been modified to check to see whether any of those updates are being throttled by this new phased release approach.  Hence the infinite sequence:

Ubuntu: you've got updates waiting to be installed
You: go ahead and install them
Ubuntu: your system's already up to date; nothing to install
You: OK
Ubuntu: you've got updates waiting to be installed
You: so install them already!
Ubuntu: nothing to install
and so on ....

As far as I can figure out, the workaround posted above (which I'm using) just means that I'm circumventing the phased release scheme altogether, forcing my machines into the pool of guinea pigs for package updates which maintainers might be a little nervous about.  I hope they get this fixed soon, as this get old quickly when you have a bunch of Ubuntu systems, as I do.

[Here]("http://www.murraytwins.com/blog/?p=127")'s some background information on the new throttling mechanism, which you might want to read to correct any garbling I've introduced in my summary of what it does.  Oddly, the blog post makes no mention of this side-effect bug.

---

### Post by slickymaster on 2013-10-10
Accordingly to [post # 15]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1223321/comments/15") of the bug report:> This bug was fixed in the package update-notifier - 0.147Did you already update your update-notifier package? You can view the version of the one you have installed running the following command at a terminal window:```
apt-cache policy update-notifier
```

---

### Post by bkline on 2013-10-11
[The Reply with Quote mechanism garbled your original message - something to do with broken smiley handling I suspect - so I had to do the quoting by hand.]

> **slickymaster said:**
> Accordingly to [post # 15]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1223321/comments/15") of the bug report: "This bug was fixed in the package update-notifier - 0.147." Did you already update your update-notifier package? You can view the version of the one you have installed running the following command at a terminal window:```
apt-cache policy update-notifier
```
update-notifier:
  Installed: 0.134
  Candidate: 0.134
  Version table:
 *** 0.134 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main i386 Packages
        100 /var/lib/dpkg/status

As far as I know, this is the latest version made available to the repositories for the latest released version of Ubuntu.

> Please mark your thread as solved if you get a satisfactory response.

I thought I already had marked the thread as "solved" already (having received a partial workaround).  Is there some other magic I need to do?

---

### Post by slickymaster on 2013-10-11
Here you go: [https://launchpad.net/ubuntu/+source/update-notifier/0.147](https://launchpad.net/ubuntu/+source/update-notifier/0.147)

---

### Post by bkline on 2013-10-12
Assuming you provided that link so I can download and install the newer version: the picture I've been given of the Ubuntu software management system -- a picture which may be misinformed, but it's what I've got -- goes something like this: I can either let the update manager take care of installing and updating software from the repositories, paying the price of not always having the most up-to-date versions available as quickly as I might prefer, or I can download and install the software by hand myself, in which case the price is that the update manager is no longer able to take care of upgrading the software and managing the dependencies.  If this picture is accurate, I think I'd prefer to pay the first price, knowing that the update manager will keep my system from becoming a tangled dependency nightmare.  If my picture is flawed, could you point me in the direction of some documentation which would give me a more accurate understanding of exactly how the update manager works?  If my original assumption about why you provided the link is wrong, please correct me ("Here you go" was all I had to go on).

Thanks!

---

### Post by bkline on 2013-10-12
PS - I think I figured out that you weren't telling me to mark my thread as solved -- that was just part of your signature, provided as general advice to the world.

---

### Post by bkline on 2013-10-12
Here's an example of a recent thread which represents yet another tale of woe posted by someone who installed a piece of software by hand, ending up with a hopelessly confused package management system:

[http://ubuntuforums.org/showthread.php?t=2165909](http://ubuntuforums.org/showthread.php?t=2165909)

I didn't read the whole thread (it wanders off into an unrelated discussion) but you can see how I got the picture I have of the dangers of installing software by hand if you want to keep the package manager sane.  Again, I really do want to deepen my understanding of how it really works.  I've been looking for a while for a users' guide to best practices in this area.  Would be most grateful for a pointer to such a guide.

---

### Post by slickymaster on 2013-10-13
Once downloaded and extracted, [update-notifier_0.147.tar.gz]("https://launchpad.net/ubuntu/+archive/primary/+files/update-notifier_0.147.tar.gz") contains a text file named **INSTALL **with installation instructions.

---

### Post by bkline on 2013-10-14
@slickymaster: I really appreciate your help.  However, it's clear that I'm not doing a very good job of conveying the part that's causing me to hesitate.  I'm familiar with the process of building and installing software using .configure and make.  What I'm not so sure about is the confusion I might present the package manager with if I bypass its control of the software installed on my systems and install the software directly.  Let me try an analogy.  Imagine you're my accountant, and you're a really good accountant, but I start writing checks and making deposits without telling you about them.  Isn't that going to make it impossible for you to do your job properly?  Doesn't something along these lines happen if I install or upgrade software without telling the package management system?

---

### Post by slickymaster on 2013-10-15
I understand perfectly your point of view and I believe it to be absolutely correct. Further more I consider your approach to the whole issue as the correct one.

That said I'm starting to second guess my previous suggestion of using **update-notifier (0.147)** because this package it's a Saucy (Ubuntu 13.10) package and you are running Raring (Ubuntu 13.04).

Anyway if you really want to install it without having to compile it, you can download it as a .deb file and when double click it the Ubuntu Software Center will install it. As I don't know the architecture of your computer I'll leave you both the links:

[update-notifier (0.147) - amd64]("http://packages.ubuntu.com/saucy/amd64/update-notifier/download")
[update-notifier (0.147) - i386]("http://packages.ubuntu.com/saucy/i386/update-notifier/download")

---

### Post by bkline on 2013-10-15
Thanks.  I've got some of both.  Very much appreciate your patient assistance.

---

### Post by bkline on 2013-10-15
Ran into dependency failures:

"Dependency is not satisfiable: libpango-1.0-0 (>= 1.18.0)"

I'm going to stick with what's in the repositories for 13.04 until time to upgrade to 13.10.  Again, thanks for your assistance.

---

### Post by slickymaster on 2013-10-16
> **bkline said:**
> Ran into dependency failures:

"Dependency is not satisfiable: libpango-1.0-0 (>= 1.18.0)"

I'm going to stick with what's in the repositories for 13.04 until time to upgrade to 13.10.  Again, thanks for your assistance.

Again, I think it's the right move, even because tomorrow is the release of Saucy.

But just FYI, Pango is a library for layout and rendering of text and forms the core of text and font handling for GTK+-2.0 with an emphasis on internationalization and can be used anywhere that text layout is needed.

[U]For Raring:
[/U][libpango1.0-0 - amd64]("http://packages.ubuntu.com/raring/amd64/libpango1.0-0/download")

[U]For Saucy:
[/U][libpango-1.0-0 - amd64]("http://packages.ubuntu.com/saucy/amd64/libpango-1.0-0/download")
[libpango-1.0-0 - i386]("http://packages.ubuntu.com/saucy/i386/libpango-1.0-0/download")

---

### Post by bkline on 2013-10-24
To close the loop: I updated the systems to 13.10, which brought the update-notifier package up to version 0.147 (which, by the way, is a version number which implies that the package isn't ready for public release yet in the traditional software versioning systems, so perhaps I shouldn't have been surprised at the problems).  At any rate, the original problem appears to have been resolved.  Thanks again for the assistance.

---

