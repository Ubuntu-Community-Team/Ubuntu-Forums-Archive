---
title: "Bug handling process"
date: 2013-08-03
forum: General Help
---

### Post by anti_thesis2 on 2013-08-03
How come not all of the old bugs are being handled? Take, for example, [this bug](https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/946956). It's from well over a year ago, and it's been confirmed, but it has no priority and it has not been assigned. It doesn't look like anyone is ever going to fix it.

How exactly does bug fixing work, in this regard? I don't know if it still exists in Ubuntu 13.04, but this specific one happened to me in the LTS version. My issue isn't necessarily this specific bug, but the way it's generally handled. If a new version of Lyx comes out which solves this issue, the new Ubuntu will have this fixed version, while the LTS version is supposed to be a more tested system which thus uses the old, unfixed version. If LTS doesn't get a fix nor an update, doesn't that make 13.04 more stable in this regard? What's the use of using LTS if not all the bugs get solved even in the long run?

---

### Post by grahammechanical on 2013-08-03
Would you agree that Lynx is the kind of software that Ubuntu developers call Upstream?  And further more, that Lynx is not an application that is part of the Ubuntu distribution? It is not part of the default install. Do you agree?

In that case all that the Ubuntu bug squad can do is pass the bug Upstream. It is up to the Lynx developers to fix this bug. You really should be asking the Lynx developers about this complaint.

In one sense all Ubuntu versions are stable. Only the development branch is viewed as unstable. I have been using the development branch continually (daily) and I consider it stable but not without issues. This I expect from the development branch.

Ubuntu 12.04 is stable. So is 13.04. And there are Backport repositories. This link explains what Backports are and how they are used.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Your problem is with software that is not the responsibility of the Ubuntu developers but you expect and demand that the Ubuntu developers fix someone else's software. You take a issue with an application and you make it a complaint about the Ubuntu distribution. This is behaviour that I do not like.

Regards.

---

### Post by ian-weisser on 2013-08-03
The short answer is that the bug has not been properly Triaged yet. See [https://wiki.ubuntu.com/Bugs/HowToTriage](https://wiki.ubuntu.com/Bugs/HowToTriage)
Triage is done by volunteers like you or me. Including you. Yes, you. We pick out the bugs we feel comfortable working with.

Your question seems to assume that some group of experts is responsible for handling bug reports. That would make sense if Ubuntu were a commercial product that you purchased. Ubuntu is, however, a community project that relies upon volunteers to report, diagnose, prioritize, and organize most bugs in the tracker. The Ubuntu Bug Squad ( [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad) ) handles this work, including bug triage, and welcomes new volunteers.

As _[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1087323")_grahammechanicalproperly pointed out, much of the software in Ubuntu comes from upstream projects. Part of triaging a bug also includes getting those upstream experts into the discussion. 

Canonical does employ a small group of paid engineers to fix critical bugs. We don't get to decide what they work on. Their employer does that.
You can also fix many bugs by purchasing paid support...or offering a bounty...or investigating, downloading the source code, and patching it.

---

### Post by anti_thesis2 on 2013-08-03
> **grahammechanical said:**
> Would you agree that Lynx is the kind of software that Ubuntu developers call Upstream?  And further more, that Lynx is not an application that is part of the Ubuntu distribution? It is not part of the default install. Do you agree?

In that case all that the Ubuntu bug squad can do is pass the bug Upstream. It is up to the Lynx developers to fix this bug. You really should be asking the Lynx developers about this complaint.

In one sense all Ubuntu versions are stable. Only the development branch is viewed as unstable. I have been using the development branch continually (daily) and I consider it stable but not without issues. This I expect from the development branch.

Ubuntu 12.04 is stable. So is 13.04. And there are Backport repositories. This link explains what Backports are and how they are used.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Your problem is with software that is not the responsibility of the Ubuntu developers but you expect and demand that the Ubuntu developers fix someone else's software. You take a issue with an application and you make it a complaint about the Ubuntu distribution. This is behaviour that I do not like.

Regards.

But the point is that the developers may in fact have fixed the issue. It is not up to the Ubuntu developers to fix other people's software, but if the software is already fixed and Ubuntu just doesn't update to the fixed version, that's something the developers of that specific program can't do anything about.  Why does the LTS version not have the newest versions of programs in the repository? To keep not just the base system, but also the individual programs more stable, right? But when the newer version is in fact more stable and has critical bugs as these fixed, it's a moot point to stick to the old version. There's backports for that, but wouldn't it be preferred, in these cases, to have the newer / more stable version in the main repositories so that people won't have to find out it's time for an update the hard way (in the case of everyone who has suffered from this bug, through data loss)?

If Ubuntu doesn't handle upstream programs, why do people submit them to the Ubuntu launchpad in the first place? Just so they can be forwarded later on? Why not submit them to that program's bugtracker in the first place?

Please note that this is not as much a complaint as it is an attempt to gain insight in how bug tracking and development inside the Ubuntu project work. I also don't recall to have used any attacking language. Is inquiry unpreferred?


> **ian-weisser said:**
> The short answer is that the bug has not been properly Triaged yet. See [https://wiki.ubuntu.com/Bugs/HowToTriage](https://wiki.ubuntu.com/Bugs/HowToTriage)
Triage is done by volunteers like you or me. Including you. Yes, you. We pick out the bugs we feel comfortable working with.

Your question seems to assume that some group of experts is responsible  for handling bug reports. That would make sense if Ubuntu were a  commercial product that you purchased. Ubuntu is, however, a community  project that relies upon volunteers to report, diagnose, prioritize, and  organize most bugs in the tracker. The Ubuntu Bug Squad ( [https://wiki.ubuntu.com/BugSquad](https://wiki.ubuntu.com/BugSquad) ) handles this work, including bug triage, and welcomes new volunteers.

As grahammechanicalproperly pointed out, much of the software in Ubuntu  comes from upstream projects. Part of triaging a bug also includes  getting those upstream experts into the discussion. 

Canonical does employ a small group of paid engineers to fix critical  bugs. We don't get to decide what they work on. Their employer does  that.
You can also fix many bugs by purchasing paid support...or offering a  bounty...or investigating, downloading the source code, and patching  it.

But this bug affects 26 people. Doesn't it strike you as noteworthy  that none of them has triaged this bug, especially considering the fact that triaging doesn't sound like a big task? Maybe the users aren't being  informed on the process enough? I, for one, had no idea it needed to be  triaged (the bug page itself mentioned nothing about it) or that people like me are allowed and expected to do so, and I had to find out about it by creating this very topic, the kind of thing not everyone does. Wouldn't it be a good  idea to show a noticeable text telling the user that they can help, and  how, at the top of such pages? After all, since they are the ones who  have the bug, they might well be able to provide valuable information.

---

### Post by ian-weisser on 2013-08-04
> **anti_thesis2 said:**
> Why does the LTS version not have the newest versions of programs in the repository? To keep not just the base system, but also the individual programs more stable, right? But when the newer version is in fact more stable and has critical bugs as these fixed, it's a moot point to stick to the old version. There's backports for that, but wouldn't it be preferred, in these cases, to have the newer / more stable version in the main repositories so that people won't have to find out it's time for an update the hard way (in the case of everyone who has suffered from this bug, through data loss)?

Determining if the newer upstream version is more (or less) stable, and deciding if backporting the new version is appropriate (sometimes it's not) is part of the Backporting process. Are you asking about backporting? Or are you asking for more backports? Or are you asking for some kind of change to the backporting process?

> **anti_thesis2 said:**
> If Ubuntu doesn't handle upstream programs, why do people submit them to the Ubuntu launchpad in the first place? Just so they can be forwarded later on? Why not submit them to that program's bugtracker in the first place?

The short answer is that it's good manners to triage bug reports at the Ubuntu level first before sending them upstream.
The interaction between independent mostly-volunteer organizations depends on everyone being polite and supportive. Good feelings and perceived fair treatment between organizations matters in this free-license and no-contract environment.

We consider it rude to ask unskilled users to send bug reports directly to developers. Unskilled users -by definition- have not learned the skills to create a useful bug report. Nobody wins - the developer is annoyed, the user is embarrassed, and the bug is not fixed.
So unskilled bugs get triaged by a human, and upstreaming the bug is part of the process.
 
Skilled users are welcome to send bugs upstream directly. We ask that they also create a Launchpad bug linked to the upstream item, because that's where other Ubuntu users will look first. 

We consider it *very* rude to send automatically-generated bug reports (by the apport application) upstream...it could be considered a form of spamming. So apport creates a bug in launchpad, and a human triager reviews it and upstreams it.



> **anti_thesis2 said:**
> Is inquiry unpreferred?
Inquiry is welcome. Some of your phrasing was perhaps unfortunate. Happens to everyone -including me!- from time to time.




> **anti_thesis2 said:**
> [...] this bug affects 26 people. Doesn't it strike you as noteworthy  that none of them has triaged this bug [...]? 
No. Not everybody wants to triage bugs. Many users have not learned the right skills for general triage. Many do not have the specific knowledge of software required for some bugs.

For example, do you know anyone who has experience with KDE SPI interfaces? Since tracking down which application is creating an invalid SPI interface seems to be key to figuring out this bug, a triager who doesn't understand that system (like me) won't get very far.



> **anti_thesis2 said:**
> Wouldn't it be a good  idea  to show a noticeable text telling the user that they can help, and  how,  at the top of such pages? After all, since they are the ones who  have  the bug, they might well be able to provide valuable  information.

Reporting a useful bug is a teachable/learnable skill. And there's a whole bunch of wiki pages (and websites) devoted to it. Much more to learn than a paragraph of text can convey. Usually, most of the work a triager does is asking the reporter for clarifications and more information.

Telling an unskilled reporter that they need to learn new skills and invest a lot of time in the bug seems like a poor way to recruit new triagers, a great way to frustrate users. We do want them to report bugs!

Usually, we wait until somebody complains, and then ask them to get involved. Every triager started as an unskilled bug reporter.

---

### Post by anti_thesis2 on 2013-08-04
Thank you for the greatly detailed explanation. I still think that a bit of visibility of the wiki pages can't hurt and doesn't have to upset users or keep them from reporting the bugs at all, but I do understand the strategy. The answer was satisfactory.

---

