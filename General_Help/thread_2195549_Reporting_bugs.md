---
title: "Reporting bugs"
date: 2013-12-24
forum: General Help
---

### Post by sideburns on 2013-12-24
My sister's running Xubuntu on her netbook and is unable to update it.  The update program simply asks her to report the bug.  As she's very, very non-tech, and I have decades of computer experience (I've been running Fedora Linux as my primary OS for about a decade now.) I've been trying to help her.

The instructions I found, by following links posted here, are long, involved and confusing.  We were able to find out that the program is named update-manager, and the package (AFAICT) is update-manager-core.  Alas, ubuntu-bug can't work out what package this is.  If my sister were alone, about all she could do at this point is throw up her hands and prepare to re-install from scratch.  We need help, because your instructions are exceptionally hard to follow.  And, of course, until this is fixed, she can't update her netbook.

Compare this now, with the process in Fedora, a geeky, bleeding-edge distro that's never been successfully accused of being user friendly.  If my package manager (yumex, for me) crashed, I'd see an icon for abrt on my tray.  Click on it, and the complete process of generating and uploading the report happens automatically; about all I need to do is fill out a description of what I was doing, what I expected and what happened.

---

### Post by deadflowr on 2013-12-24
> [COLOR=#000000] And, of course, until this is fixed, she can't update her netbook.[/COLOR]

Of course she can update.
Run the terminal commands.
Not as simple, but will get her updated.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by sideburns on 2013-12-24
We'd already tried apt-get and got an error message that the program wasn't found.  (Maybe she mistyped; I wasn't able to see her screen.)  We tried again and got this:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

And, in any event, even if apt-get works, it addresses neither of our issues: it doesn't get update manager fixed and ignores the problem my non-tech sister (and other non-tech Ubunut users) is having understanding the long, complicated process of getting a bug reported.

---

### Post by deadflowr on 2013-12-24
Heres' for the apt problem
[http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err](http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err)
At least she'll be able to fix that part and run a terminal update, atm.

I will agree, Ubuntu's bug reporting is a little tedious at times.
[Tips on bug reporting here]("https://help.ubuntu.com/community/ReportingBugs")

And off chance.
If she runs 
```
update-manager
```
from a terminal, what is the result?

---

### Post by sideburns on 2013-12-25
Yes.  I found those instructions for reporting a bug and tried to follow them.  It reminded me of what I had to go through to report a Fedora bug, about ten years ago.  Maybe the Ubuntu devs need to take a look at abrt, and ask themselves why their own "system" is so outdated.

Will try the other instructions, probably on Boxing Day at the earliest, and see what happens.

---

### Post by ian-weisser on 2013-12-25
> **sideburns said:**
> I have decades of computer experience (I've been running Fedora Linux as my primary OS for about a decade now.) I've been trying to help her.

Ubuntu does have easy bug reporting, too. The application is called 'apport'.

The pre-release version of Ubuntu has it enabled by default so reasonably-skilled  volunteer testers can report the bug, so it can be fixed before release.

After release, only crashes are reported by apport (that's a setting you can change), and only high-priority bugs will be fixed after release. Your sister's system perhaps doesn't have it turned on.

One big problem with "easy" bug reports, and the reason Ubuntu limits easy reporting to pre-release testing, is that it frustrates a lot of people unnecessarily:
- Users get frustrated when their bug gets rejected or seemingly ignored or when they don't know how to provide critical information the triager or developer needs.
- Volunteer triagers and developers get frustrated wading through stacks of duplicates, misfiled bugs, incomprehensible bugs, complaints and rants, wishlists, and misplaced support requests.

---

### Post by sideburns on 2013-12-25
Yes, and that's why abrt allows you to write your own comments before submitting the bug report.  Tell me, how many bug reporters get frustrated by all the work needed to prepare the report on their own and Just Give Up?

If apport is so great, why haven't you told us, yet, how to turn it back on?  Once that's done, we can try another update and when it crashes, let it do its stuff.  If I were in your place, that's what I'd have done after reading my first post.

---

### Post by SantaFe on 2013-12-25
Here's a link that tells how to do it.  The first section will work fine in Xubuntu, the second answer is for Ubuntu. ;)

[http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport](http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport)[ ]("http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport")

---

### Post by sideburns on 2013-12-25
Thank you.  I've passed this on to her and will see what happens.

---

### Post by sideburns on 2013-12-27
OK.  We enabled apport and tried update-manager again; it failed, and apport did nothing.  (Maybe we needed to start it?)  We then followed the instructions for clearing out the apt-get databases and updating from the CLI and they worked.  So far, so good.  Thanx.

******************************

This is weird!  Just after I posted this, my sister ran update-manager and it found 504 updates.  I thought that apt-get update would have taken care of that.  Any thoughts?

---

### Post by ian-weisser on 2013-12-27
> **sideburns said:**
> This is weird!  Just after I posted this, my sister ran update-manager and it found 504 updates.  I thought that apt-get update would have taken care of that.  Any thoughts?

Her package manager, while broken, could not update.

---

### Post by sideburns on 2013-12-27
Obviously.  However, I thought that running apt-get update would have taken care of everything.

---

### Post by ian-weisser on 2013-12-28
Then perhaps I don't understand the question.
Are you asking the difference between apt-get's update and upgrade?

---

### Post by sideburns on 2013-12-28
No.  I'm asking what's the difference between what apt-get update does and what update-manager does.

---

### Post by JKyleOKC on 2013-12-28
> **sideburns said:**
> No.  I'm asking what's the difference between what apt-get update does and what update-manager does.I'm getting into this quite late, but this question is easy to answer. "apt-get update" does only half the job and must be followed by "apt-get upgrade" to finish; "update-manager" does the whole thing behind the scenes (actually spawning the same low-level child processes to do so).

The command names in apt-get are quite misleading, especially to newcomers or those not fluent in Debian-speak. I began using Linux with Slackware 2.0, eventually moved to Mandrake 8.1, and came to Xubuntu at 7.04. It took me quite a while to learn the new phrasing of things here. In apt-get, "update" updates the internal list of possible updates but does NOT fetch them or install them. Doing that is the job of "upgrade," which any Red-Hat-based expert would expect to do an entire distribution upgrade, not just a set of file updates.

To support your sister, you probably need to become fluent in Debian-speak. It will also help to become familiar with the "upstart" package, which is another area that is quite different from Red-Hat-based standards, but that's a different subject entirely!

Hope this helps a little bit. Things really do work, once you discover the correct magic words to get them going.

---

### Post by grahammechanical on 2013-12-28
I have had this error a few times

> [COLOR=#000000]Reading package lists... Error![/COLOR]
[COLOR=#000000]E: Encountered a section with no Package: header[/COLOR]
[COLOR=#000000]E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_T ranslation-en[/COLOR]
[COLOR=#000000]E: The package lists or status file could not be parsed or opened.[/COLOR]

As far as I can guess, it is down to a script having a blank line at the top. Apt-get looks for the header and expects it on the first line but if there is a blank line then apt-get will throw up that error. I may be wrong on all of this but there are two things that I am right about. It is nearly always the in18_Translation file and these commands will fix it.

```
sudo rm /var/lib/apt/lists/* -rf
```
```
sudo apt-get update
```

We will be asked to put in our password word. It will not print out on the screen but it will be detected. The first command removes/deletes all the files in the list folder/directory. The second file will replace them including a new, possibly corrected version of the file/list that was causing the problem. Its worked for me a few times.

Regards.

---

### Post by sideburns on 2013-12-28
I come from the Fedora side of the fence, using yum (or the yumex front end) for updating my system.  For yum, update and upgrade are, for all practical purposes, the same.  And no, I don't expect to need to become fluent in Debian because I can always ask here on the rare occasions I need to.

---

