---
title: "How to Purge Open Drive?? -- Does Ubuntu Software app have only secure software?"
date: 2019-02-09
forum: General Help
---

### Post by spazz2 on 2019-02-09
Hi All.
Can anybody tell me how to purge application "Open Drive". (Google Drive client for linux).
I downloaded this through the the ubuntu software catalog / portal app .
Ever since downloading it , I instantly started getting boot errors and errors arising through general use in ubuntu.


I'm not sure how to export the error text / message that is displayed when I boot into Ubuntu (which happens every time now).


It was the only application I have installed for a long time now, and the problems started occurring immediately after install.
Maybe the error is not related, but it seemed to correspond exactly when I installed this application.
I have tried uninstalling it using the ubuntu software catalog, which has uninstall options in it -- but this has had no effect. 


Is everything that is downloaded in the ubuntu software app supposed to be safe and tested ?
Or will some of it cause system bugs / security issues? etc.


Thanks in advance for any assistance.

---

### Post by TheFu on 2019-02-09
The software application includes core, non-core and 3rd party repositories.  There's no way that Canonical can ensure security or even compatibility with those 3rd party repos.

However, you can control which repositories are used. There should be a tab for the main ones with checkboxes as to which you want to include and which you do not.  The complete list is in /etc/apt/sourced* and subdirectories.

There are repos that you might have added without understanding what that meant or they may have been added by installing a program by using a .deb file.  The non-core repos add this way are called "PPAs" and they extend the package management system so that the PPA creator and update their packages and we all get the latest version of their software.  By using reputable PPAs, we end up running the most stable, least buggy code on our systems.  Well, that is the intent, but bad code happens in all programs and sometimes it gets released.

There is no way for Canonical to test everything in their releases or their repos.  They lean on the reputation of the upstream team greatly.  Each project team has their reputation and history of releasing good code and not-so-good code.  In theory, we can find projects with poor reputations and decide not to use that project.  But, Linux is about having choices and many people still choose to use code from projects with a history of bad releases and poor security in their code.

As for "safe and tested" - there are many tools included in Linux that aren't safe to use, but these are included in base installs all the time.  Linux will let you shoot yourself in the head, chest, arm, leg, foot or toe by doing dumb things.  The tools cannot tell whether any specific use is pure genius or pure stupidity.  Both happen all the time, sometimes from the same user, in the same day.  I've done some really dumb things and some brilliant things on Unix systems over the years.  I've watched others do the same.  For example, watched a man delete 3 months of work because he included an extra space in 1 command.  It took a team of 8 people 5 days to re-create his work ASAP.

There are always bugs and security issues. Always.  All non-trivial code has bugs.

You can minimize the risks for bugs and stability by only using core repo programs.  That usually isn't too useful, so people add a few PPAs. Every PPA increases the risks. Stay with only a few PPAs, not all that you read about, and only use the ones you absolutely must have the newest code for.  

PPAs are extremely powerful. Through those, we effectively provide root control of our systems so some random team (or individual) over the internet. The power to install conveys the power to do anything on Linux with either the pre-install or post-install scripts included inside every package.

---

### Post by deadflowr on 2019-02-09
It's a snap package, so try removing through the terminal
```
sudo snap remove odrive-unofficial
```

---

### Post by spazz2 on 2019-02-14
Hi Fu ! 
Thanks so much again for taking the time to explain those differences (between core repos etc) a bit differently (and even further) in a separate context, with further examples of how things can go terribly downhill with an extra keystroke!
My apologies for being a bit slow on the uptake here!!
(You did explain these difference a bit previously within another context).
Also my apologies for being a poor researcher.
I suppose I could have looked into it further -- I'm a bit overloaded with study at the moment.
(All fundamental electronics stuff -- so many theorems !!! Thevenins, Norton's, superposition theorem etc.
My head !!  \_0o0_/ aaah !     )
Sadly, my William Shotts reading must be put on hold for a bit  ):


I will be far more minimal and careful with installs for a while !
I think I will even look into what are the cleanest most stripped down base-OS-installs.
A bit worrisome that suspicious / unstable items can be installed on a fresh OS.


PS. 
I now suspect the boot issue is perhaps with Ubuntu 18.1 Cosmic Cuttlefish,
rather than a package --
as what appears to be the same error at system login has occurred on fresh Ubuntu installs on 2 separate laptops.
I think perhaps I should have stuck with Bionic.
The issue didn't appear immediately on my desktop with same OS, though.
It only seemed to coincide there straight after that package install.


Anyway, I will reinstall OS, and see how it all goes.


Cheers !

---

### Post by spazz2 on 2019-02-14
Thanks deadflowr !
That seems to have done the trick !
I did not get the boot error after having removed OpenDrive.

I was beginning to suspect the boot issue is perhaps with Ubuntu 18.1 Cosmic Cuttlefish,
rather than a package --
the same (or similar) error at system login has occurred on fresh Ubuntu Cosmic installs on 2 separate laptops.
(but did not occur with Bionic)

....So now I am slightly confused about cause.

Cheers.

---

### Post by him610 on 2019-02-14
> Google Drive client for linux
Definitely NOT affiliated with Google Drive. 
Open Drive, Inc is a commercial company that wants to sell you something in exchange for your $$.

---

