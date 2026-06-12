---
title: "APT not working, System error messages"
date: 2015-09-10
forum: General Help
---

### Post by Darrell_Wellsman on 2015-09-10
Every time I log in lately I get a prompt regarding a system error. In the top corner of my screen there is a little red circle with a line in the middle of it. It tells me to open Package Manager, and says that I have unmet dependencies, then references the file mentioned below. 

When I attempt to open Ubuntu Software Centre it does not work. A window opens for it, displays the little spinny circle, then autocloses after some time. I just attempted to use apt-get in terminal to install unrar and got the following message:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.


I can still install from tarballs, and for the most part my computer is running okay. Though it sometimes takes a few tries to start up. It would still be nice to know how to solve. Would uninstalling Steam help (Somehow?)

---

### Post by QDR06VV9 on 2015-09-10
It would help if you told us how you installed steam? And what version of ubuntu you are using.
You could try un-installing steam, And of course the usual  Updating your system if you have not done so.
```
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
The dist-upgrade will not take you to a newer version of Ubuntu but pull in some Deps if needed.
But I would un-install steam first. then run those commands.
Let us know how things sort out.
Regards

---

### Post by Darrell_Wellsman on 2015-09-11
I don't actually know how to remove steam without APT. As mentioned whenever I run apt-get I get the above error message.

This includes apt-get remove and apt-get upgrade.

I could like, manually delete stuff, but I have a feeling I would miss headers and screw it up worse that way.

---

### Post by Bashing-om on 2015-09-11
Darrell_Wellsman; Hello

The reported errors indicate a inconsistency ( corruption) in control files .
More than steam 'may' be effected . How about we remove the control files and have the system rebuild anew ?
try:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
in this sequence 'update' will rebuild the data-base control files that were removed .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2015-09-11
> **Bashing-om said:**
> Darrell_Wellsman; Hello

The reported errors indicate a inconsistency ( corruption) in control files .
More than steam 'may' be effected . How about we remove the control files and have the system rebuild anew ?
try:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
in this sequence 'update' will rebuild the data-base control files that were removed .[INDENT][INDENT]maybe yes[INDENT][INDENT][INDENT]could be not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

+1 Good Eye When they don't put things like this in code tags, I tend to just skim.(See how much easier it is to read);)
> [COLOR=#000000]Reading package lists... Error![/COLOR]
[COLOR=#000000]E: _**Encountered a section with no Package: header**_[/COLOR]
[COLOR=#000000]E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i1 8n_Translation-en[/COLOR]
[COLOR=#000000]E: _**The package lists or status file could not be parsed or opened.**_[/COLOR]

Then I give a Half A__ answer.(But not intentional):o
My Bad
Thanks for picking that up [COLOR=#000000]Bashing-om
Regards[/COLOR]

---

### Post by Bashing-om on 2015-09-11
OH runrickus;  That ^^ is why we do it this way, for the peer review ...

Maybe this makes up a bit for all the irons of mine you have pulled out of the fire.
We await and see what haps next.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2015-09-11
> [COLOR=#000000]all for 1 and one for all[/COLOR]
As it should be>:D
You Rock and keep on Bashing-om:popcorn:
Talk to you later.Regards

---

### Post by Darrell_Wellsman on 2015-09-11
Thanks for the timely response. Trying right now, and so far so good, the first two steps got apt-get working again. Hopefully the other two get the error reports to stop so I can get on with reading comics!

Its nice to see such good rapport in the community too. Even if I lack the background to understand it.

---

### Post by Darrell_Wellsman on 2015-09-12
Okay so, that particular problem is solved! I am still getting system errors having to do with something called Apport on startup, but there seem to be no actual symptoms of this problem so far and I am successfully reading comics!.

---

### Post by Bashing-om on 2015-09-13
Darrell_Wellsman; Hey hey !

You do good work.

As this situation is under control:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And open a new thread on the " Apport " issue .

[INDENT][INDENT]we see you there
[/INDENT][/INDENT]

---

