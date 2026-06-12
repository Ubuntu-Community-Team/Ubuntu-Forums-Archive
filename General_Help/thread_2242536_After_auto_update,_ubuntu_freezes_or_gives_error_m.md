---
title: "After auto update, ubuntu freezes or gives error message"
date: 2014-09-02
forum: General Help
---

### Post by J Tinsby on 2014-09-02
I installed an update to Ubuntu a few days ago, when it was being installed it indicated not everything would be or could be installed " do you want to continue?" I chose "yes"

Now it seems that after that install the OS will freeze or hang and I can't move the cursor and the system won't respond, then it becomes useable again on it's own. 

One time I got an on screen error message asking me if I wanted to "ignore errors of this type and continue?" I chose "Not to ignore."

I have no screen shots of any errors to include but will do so if I get an error message on screen.

Should I run a /forcefcsk from the terminal to see if it can find or repair anything? There have been no power outages when booted that would create an error. When the OS is working it works very well and is very responsive, I cannot say what I do to make an error appear, it seems random. The system boots up just fine with no trouble fwiw.

Thank you in advance,

J T

---

### Post by ian-weisser on 2014-09-02
> **J Tinsby said:**
> Should I run a /forcefcsk from the terminal to see if it can find or repair anything? 

No. That seems likely to make things worse. fsck-ing a mounted filesystem can damage it.

Open a terminal and run the 'top' command.
Anything occupying most of your CPU cycles?
Does it change during a slowdown?

---

### Post by J Tinsby on 2014-09-02
Ian,

Nothing taking a lot of CPU cycles, the most I see is .3% to 5.7% the highest being Firefox at any one time. The list does change from second to second but never approaches even 10%. 

Maybe if it hangs again I can run the command and see what's doing it, but that's doubtful, when it hangs I can't do anything.

Thank you for that command it's new to me and very useful, glad I asked before using the other one :D

J T

---

### Post by ian-weisser on 2014-09-02
> **J Tinsby said:**
> I installed an update to Ubuntu a few days ago, when it was being installed it indicated not everything would be or could be installed " do you want to continue?" I chose "yes"

Uh oh. That could be nothing...or it could be extremely bad.
Do you recall any details of the error message.
Do you recall if it was offering you a "partial upgrade?" (That's a specific term)

On fixing the problem:
Do you just want it fixed ASAP?
Or do you want to go poking and prodding around your system to try and discover the cause?

---

### Post by J Tinsby on 2014-09-03
Ian,

I recall that the message indicated some things couldn't be installed for whatever reason. As I recall it offered me a 'partial update' and I chose to continue with the install. That's all I know, sorry no more details. I haven't a clue how to tell what wasn't installed, if in fact there is a way to do that.

As far as fixing things, sure it'd be great to find out what's going on. I don't mind poking and prodding though either. As odd as it may sound, today I changed my PS2 USB mouse to another of the same kind. It seemed that the one I was using was overly sensitive and causing double clicks on things that only needed one click. I am thinking 'maybe' this was part of the problem. Won't know 'til I spend more time with it to see.

Thanks you for your help and interest!

J T

---

### Post by christopher9 on 2014-09-03
I encountered the same situation after accepting a 'partial upgrade'....like the PC developed a mind of its own...I kept checking every few hours and when I got the regular 'Install' radio button I chose it and everything was fine after that...YMMV

I believe there is a known issue with partial upgrades...not positive but IIRC it was posted on launchpad...can't locate it now but there is this:

[URL="https://wiki.ubuntu.com/U%2B1/partial_upgrade"]https://wiki.ubuntu.com/U%2B1/partial_upgrade


[/URL]

---

### Post by J Tinsby on 2014-09-03
Christopher9,

Thank you, I had a backup that was made 10 days ago and I recovered that backup, hoping that would undo any damage by the 'partial install' and force Ubuntu to ask me for the update a second time.

That is working in that I see an update ready to be clicked on again.  So I clicked and made 2 screen shots of what it says. I do NOT remember if the questionable update started this way then changed to partial!

I'm glad your system is OK now. I am used to getting updates now and then and thought nothing of going ahead and putting it in, little did I know that it would only put in pieces of the thing.

I'm not touching the update/upgrade until I have more info.

The link you sent is a big help, but the nuts and bolts of figuring what's going to be installed and if it's OK is a bit elusive to me since I am still learning to use Ubuntu. IE: I don't know how to use the changelog, unless that's what appears on the screen during the installation. This is like asking me " Do you want hamburger or do you want hamburger?" Heck it looks the same to me :D

I'd like to see what Ian in post #4 has for me too.....


Regards,

J T

---

### Post by ian-weisser on 2014-09-03
A "partial upgrade" for non-guru users is generally a VERY BAD THING.

A normal release upgrade occurs when the package manager replaces every package on the system with new versions from the new-release repository.

A partial upgrade occurs when the package manager cannot update every package to the new version, so it updates what it can. This leaves the system in an inconsistent state. The system is not designed to function with mixed packages from two different releases...and generally functions quite poorly.

Why does a partial upgrade occur?
The most common reason is non-Ubuntu software. PPAs and other third party repositories and software. They can use dependencies and version schemas that directly conflict with Ubuntu software, and confuse the package manager. I usually uninstall such software before I release-upgrade.

Ubuntu software is extensively tested for smooth upgrades, non-Ubuntu software isn't. That's one reason we really wish PPA authors would take the couple extra steps to add their software to the tested and supported Ubuntu repositories.

What can you do about it?
Two options: The easy way is to back up your data and reinstall the newer version. The harder way is to track down and resolve the package conflict.

---

### Post by J Tinsby on 2014-09-04
Ian,

Given what you say and looking at the screen shots I provided in #7, is this update safe to use? Or will it start and then turn into a 'partial' once it looks at the installed programs? I guess there is no way to tell except try it and if it changes to partial, abort it.

All good information to know in any event.

J T

---

### Post by ian-weisser on 2014-09-04
> **J Tinsby said:**
> I guess there is no way to tell except try it and if it changes to partial, abort it.

That's one way. And it's a good way.

There is a huge difference between a normal, daily upgrade (bugfixes, security patches) and an every-six-month or every-two-years release-upgrade. Partial upgrades should happen on release-upgrades only.

If you have package management problems on daily updates or installs, the first thing to do is to open a terminal window and try the package operation (install/remove/update/whatever) there. The exact error message and it's complete context are vitally important diagnostic tools.

Release-upgrades are automatic ONLY for Ubuntu software. We eternally wish non-Ubuntu software would behave itself, but it often doesn't...and failed-upgrades/partial-upgrades caused by conflicting non-Ubuntu software is not Ubuntu's fault. My advice is to uninstall all non-Ubuntu software, and to disable all non-Ubuntu repositories, before beginning a release upgrade. If you disabled a desktop-metapackage, re-enable it. Make your system as close to origninally-installed condition as possible. You can re-enable and reinstall non-Ubuntu software easily after the release-upgrade is complete.

Yes, that's a 10-minute annoyance...but look how much time you have already spent restoring from backups and seeking forum help.

---

### Post by J Tinsby on 2014-09-04
That's the method I chose to use and THIS time I got no error messages or warnings about a partial installation. I will be far more leery of what I accept now that I know the rules of the game :D Of course I have an excuse for allowing the partial install to go on. I'm so used to MS and all it's security patches and nonsense, you have to keep it up to date at every turn :/

Many thanks,

J T

---

