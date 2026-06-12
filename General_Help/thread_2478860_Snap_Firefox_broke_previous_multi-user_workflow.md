---
title: "Snap Firefox broke previous multi-user workflow"
date: 2022-09-07
forum: General Help
---

### Post by fragged on 2022-09-07
I make significant use of many browser profiles which I generally create Linux users for. E.g., `useradd -m MyUser; sudo -u MyUser firefox &`). I do this to segregate browser histories / manage per-browser settings.

Recently I upgraded from 21.10 to 22.04 which has moved Firefox from apt to snap. Initially I had an issue with cgroups v2 which I've reverted to v1 (afaict, this is a bug). 

However, now when attempting to start profiles, I experience several unwanted behaviours: 

- `/snap/bin/firefox` warns `mkdir: cannot create directory '/run/user/1010': Permission denied`, it also takes a few seconds to load firefox
- When attempting to open a second firefox window via a shell (e.g., `sudo -u MyUser firefox & sleep 10; sudo -u MyUser firefox`, the latter command complains that firefox is already running. Previously, running the equivalent would open a new window in Firefox.

How can I fix these two issues? I'm open to a better mechanism for managing profiles, I would use on average 5-10 profiles on a daily basis. This number grows/shrinks. This workflow is for a very specific use case and not something I expect others will use, the browsers need independent settings / plugins etc.

---

### Post by &amp;KyT$0P# on 2022-09-07
There are several solutions.

One way would be to use a non-snap Firefox.  You have at least two options there:

1) Download and extract the [official Mozilla build tar.bz2]("https://www.mozilla.org/firefox/all/#product-desktop-release"), or

2) Install Firefox as .deb from Mozillateam PPA (requires advanced user knowledge of apt pinning, as noted in the guides [here]("https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04") and [here]("https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/"))

And it is also possible that the flatpak of Firefox either would work with your use case or could be tuned to through Flatseal.

[HR][/HR]
Another way might be to use [Firefox's profile manager]("https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles") instead of using different entire user accounts.

---

### Post by fragged on 2022-09-09
I'm interested in using snap or similar - the use of containerised apps is overall a good idea, and not using them will be a continual battle with Ubuntu. 

As such, I'm still interested in fixes to my actual problem, as opposed to workarounds.

---

### Post by #&amp;thj^% on 2022-09-09
> **fragged said:**
> I'm interested in using snap or similar - the use of containerised apps is overall a good idea, and not using them will be a continual battle with Ubuntu. 

As such, I'm still interested in fixes to my actual problem, as opposed to workarounds.

I'm confused by this>> "I'm interested in using snap or similar - the use of containerized apps is overall a good idea"
I felt that halogen2 gave some solutions to that, outside of just plain ole firefox, but even that could run sandboxed through firejail
and flatpak configured with flatseal.
Or just run the snap version of firefox and problem should be solved. 
As for browser profiles you'll have to be *very detail* specific to your wants, we all here, set things very differently.
And perhaps show us your profile .txt, other wise we will continue down a rabbit hole, >>> No fun for you or anyone trying to help you. ;)

---

### Post by fragged on 2022-09-09
You're suggesting fighting Ubuntu / snap defaults, which from experience, is a bad idea. If I thought any alternative distros were a more optimal, I'd switch to those.

---

### Post by &amp;KyT$0P# on 2022-09-09
> **fragged said:**
> I'm still interested in fixes to my actual problem, as opposed to workarounds.

None of the ideas I suggested are "workarounds", based on my understanding of what you're trying to achieve.  If you want to stick with snap Firefox, did you follow the link about Firefox's profile manager?  In what way(s) does that not serve your case?

---

### Post by #&amp;thj^% on 2022-09-09
> **fragged said:**
> You're suggesting fighting Ubuntu / snap defaults, which from experience, is a bad idea. 

There is no fight involved on my end, just no snaps. ;) As I said we all do different...
I'll leave you with halogen2.

---

