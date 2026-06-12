---
title: "Too many updates"
date: 2008-06-05
forum: General Help
---

### Post by akshayas1986 on 2008-06-05
Hi guys,

I have been using Ubuntu for a very long time now. Ever since I got 7.04, I have loved it and though I do use windows, I spend only 20% of my time on it and rest of it on Ubuntu.

I have one issue with Ubuntu though not a very big one. I noticed that from Gutsy release, the number of updates have become too many. Almost every other day, there is 30 to 40 MB of updates. As a first step, I have removed a lot of redundant packages but that has not helped me much. I want to know why there are so many updates and any steps I could take to reduce them.

Thanks
Akshaya Srivatsa

---

### Post by iaculallad on 2008-06-06
One way of reducing your updates: Goto your Software Sources->"Updates" tab and uncheck what you don't need to be updated. (Gutsy-Security, Gutsy-Updates, Gutsy-Proposed, Gutsy-Backport).

---

### Post by zvacet on 2008-06-06
> I want to know why there are so many updates 

Because developers are fixing and improving Hardy.If you really want you can uncheck all repos** exept security**.I don´t believe that you don´t want security updates.

---

### Post by kesman on 2008-06-06
BTW why do you want to disable updates? 30-40MB a day isn't much for a decent internet connection I guess. Of course you could disable automatic update checking, and run the update manager manually, say, once a month.

---

### Post by heatblazer on 2008-06-06
Remove the hardy proposed updates. Mom had the same problem on her xubuntu. Tons of updates. Make sure you don`t have 3rd party updates, you can set the Wine or you can add the REP manually.

---

### Post by indytim on 2008-06-06
If the underlying issue is the amount of time spent each day doing the update thing, suggest considering doing your updates one day per week.  I usually do updates only on Saturday mornings.  This also coincides when I'm running my weekly partition backups (partimage).

Hope this helps,

IndyTim

---

### Post by jongkind on 2008-06-06
> **akshayas1986 said:**
> 
I want to know why there are so many updates and any steps I could take to reduce them.

In my experience the following is effective in reducing the time that you spent on it:

[LIST=1]
[*]From your start menu: system-administration-software sources
[*]Select Updates tab
[*]After the "check for updates:" box, select every fortnight
[*]Also select download updates in the background
[/LIST]
Good luck

---

### Post by rhmercer on 2008-06-06
All of the feedback was very help full thank you very much..........:)

---

### Post by akshayas1986 on 2008-06-07
First of all, thanks to all of you for your feedback.

Like I had mentioned before, its not a big deal at all. I just dont like to see the red symbol on the taskbar every two days saying I have updates!! I will do what you guys suggested-Disable automatic updates check and just do updates every one in 5 to 10 days.

Cheers
Akshaya Srivatsa

---

### Post by kesman on 2008-06-09
If I remember correctly, you can also set the manager to check updates only once a week or so.

---

### Post by nisarg on 2008-06-19
I think its bit annoying having to run these updates so frequently. Obviously its a goo d thing but not too convinient I suppose. 
Under Software sources -> Updates 
I only have i)important security updates ii) recommended updates and set to check for updates every forthnight, to notify about available updates.
It believe it still seems to pop up with updates atleast once a week.
Any ideas why? I am considering switching automatic updates off, and try to may be schedule a cron job.
Secondly, what about the disk-space these updates take up? Is there a way to clean up? Where are these updates downloaded?
Inputs appreciated.
Thanks.

---

### Post by avtolle on 2008-06-19
Here's what I do after installation of updates; from terminal```
sudo apt-get clean
``` to clean things up. For an example, running this command after a bunch of updates freed up .1 GB room the other day on my HDD. Yes, I'm OCD, running ```
df-h
``` before and after running the clean command to see how much room (if any) is added.

As to where the updates are dowloaded, "it depends". Disk space: sometimes, the updates actually reduce the space taken up by the version being updated; often, a bit more is used.

---

### Post by nisarg on 2008-06-19
Thank you thats was useful.

> **avtolle said:**
> Here's what I do after installation of updates; from terminal```
sudo apt-get clean
``` to clean things up. For an example, running this command after a bunch of updates freed up .1 GB room the other day on my HDD. Yes, I'm OCD, running ```
df-h
``` before and after running the clean command to see how much room (if any) is added.

As to where the updates are dowloaded, "it depends". Disk space: sometimes, the updates actually reduce the space taken up by the version being updated; often, a bit more is used.

---

### Post by knudsenjoe on 2008-06-20
This is my own personal opinion, and not a slam against anyone...

I love seeing the updates! It lets me know that there are folks out there working to help me keep a great OS going. If the autoupdater don't come on, I check for updates myself. 

I just wanted the folks who do the updates to know I appreciate the updates, and them for making them.


I'm also sure the OP was not trying to slam anyone either.

UBUNTU ROCKS!!!!!!!!!!!!!!!!!!!!!!
:guitar:

---

### Post by ka9qlq on 2008-07-18
I don't mind all the updates but I'd like to have a way to find out more info on what the update is doing. I just got a kernel update this week but I can't find what the update "fixed. I'd be nice if there was an RSS feed showing the updates and what they "fix."

---

### Post by avtolle on 2008-07-18
On this week's kernel update, it was a security update. Details may be found at the Community News and Announcements subforum.

---

### Post by Vorian Grey on 2008-07-18
I am on dialup here at home and I don't mind the updates. If it's too large I let it download after I've gone to bed. Works lke a charm.

---

### Post by bodhi.zazen on 2008-07-18
If it is not broken, why fix it ?

Either do not update or go for security updates only.

---

### Post by Joeb454 on 2008-07-18
I'd have to agree, security updates only whenever I got them through on a dial-up connection :)

---

### Post by TimoFromSA on 2010-11-11
Hi
I'm a (really) new Ubuntu user. I just installed 10.04 on my emachines netbook, a few days ago, and love it so far except the update manager is telling me that there are 326 updates to install, which on my 3 internet plan (3Gigs) will take about 10 hours!! Oh my God, will that blow my plan to pieces!
Is there an another or easier way to do this?

Thanks in advance for help and suggestions
(remember I did say REALLY new user, also meaning not all that computer literate, so no super techie answers please)

---

### Post by bodhi.zazen on 2010-11-11
> **TimoFromSA said:**
> Hi
I'm a (really) new Ubuntu user. I just installed 10.04 on my emachines netbook, a few days ago, and love it so far except the update manager is telling me that there are 326 updates to install, which on my 3 internet plan (3Gigs) will take about 10 hours!! Oh my God, will that blow my plan to pieces!
Is there an another or easier way to do this?

Thanks in advance for help and suggestions
(remember I did say REALLY new user, also meaning not all that computer literate, so no super techie answers please)

If you are familiar with the command line you can do a "net install". This will download and install the latest packages and will save on bandwidth.

The base install is command line only, you then can install the rest, from the command line, with :

```
sudo apt-get install ubuntu-desktop
```

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

There are several on line guides that detail the necessary steps.

Over time the updates will lessen.

---

### Post by gypaete09 on 2011-08-23
> **ka9qlq said:**
> I don't mind all the updates but I'd like to have a way to find out more info on what the update is doing. I just got a kernel update this week but I can't find what the update "fixed. I'd be nice if there was an RSS feed showing the updates and what they "fix."

I don't have a real problem with the Ubuntu updates, but just the ever increasing number since last year reminds me of my days as a M$ certified engineer, and of the fact that the updates (under widoze) gradually made the machines slower and slower, or worse, (XP SP3) took them down in certain cases.
I would not want to see the same chaos unfold under my beloved Linux. (I quit windows long ago, except fo some apps under Virtualbox that can't do without.)

Suggestion: if it were still possible to read what the updates do *after* starting the download, this would be very welcome. Unfortunately, one has to read the details *before* the download is started, otherwise the window with the infos is inaccessible. Logically, everyone (me at least) starts the updates download immediately and then realizes he/she would now have time to read the details...too late.

---

