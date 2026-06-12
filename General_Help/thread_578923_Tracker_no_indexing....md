---
title: "Tracker no indexing..."
date: 2007-10-17
forum: General Help
---

### Post by screaminj3sus on 2007-10-17
Tracker doesn't seem to be indexing ANYTHING. I recently reinstalled ubuntu (RC gutsy, FRESH install) Tracker doesn't seem to be doing anything, all searches show no results, indexing and watching is enabled. Tracker used to work fine. No matter what I search for NOTHING.

[[IMG]http://img181.imageshack.us/img181/8328/screenshotih2.th.png[/IMG]](http://img181.imageshack.us/my.php?image=screenshotih2.png)

---

### Post by shomati_sen on 2007-10-17
In my case, tracker seems to only index the home directory and nothing more. I specified two other directories to be indexed and watched (via the preferences menu), but it doesn't seem to have any effect. I logged out and logged back in, rebooted the machine (for other reasons) and even deleted the existing tracker index and made tracker reindex everything, but still no luck. 

Shomati

---

### Post by screaminj3sus on 2007-10-17
I only ahve the default settings which is my home directory, all I have in it is 15 gb of music and a couple of pictues. It won't find ANYTHING, Index home directory is checked, enable indexing ect.. is checked.

---

### Post by screaminj3sus on 2007-10-17
alright wtf, when it does show results (RARELY) I can't see them it says 155 images, but shows none.... the ONLY files it is indexing right are files on the desktop.

[[IMG]http://img147.imageshack.us/img147/9703/screenshotno0.th.png[/IMG]](http://img147.imageshack.us/my.php?image=screenshotno0.png)

---

### Post by human on 2007-10-17
Try hitting the little orange next button in the top right.

for some reason, it doesnt create lists correctly.

---

### Post by screaminj3sus on 2007-10-17
> **human said:**
> Try hitting the little orange next button in the top right.

for some reason, it doesnt create lists correctly.

Tried that but doesn't work. I've had my computer on for a couple hours and it still won't index anything. Almost as fun as the random azureus crashes.

---

### Post by screaminj3sus on 2007-10-17
what the hell I can disable it than enable it ect.. Nothing I do makes this piece of crap work.

---

### Post by sancho panza on 2007-10-19
> **screaminj3sus said:**
> Tracker doesn't seem to be indexing ANYTHING. I recently reinstalled ubuntu (RC gutsy, FRESH install) Tracker doesn't seem to be doing anything, all searches show no results, indexing and watching is enabled. Tracker used to work fine. No matter what I search for NOTHING.

[[IMG]http://img181.imageshack.us/img181/8328/screenshotih2.th.png[/IMG]](http://img181.imageshack.us/my.php?image=screenshotih2.png)

Same here. Tracker used to work fine. Now...it comes up with NOTHING. The settings are the same as they were before...I can see the file in my home folder, the file i'm searching for has been around for weeks, but tracker cannot find it. I also have the problem of tracker  showing fewer results than it claims to have found. 

Anyone else has this problem? Any ideas?

---

### Post by arang on 2007-10-20
i can testify that the same thing goes on here i asked it to index my storage hard disk and it doesnt do anything at all about it, any ideas about what to tweak???

---

### Post by screaminj3sus on 2007-10-20
I'm downloading the final now and am going to try a fresh install.

---

### Post by LanDan on 2007-10-20
try to type in a terminal

trackerd & 
this will make sure it starts indexing what you do

trackerd -v 2 -R 
if you want to index whatis already there

---

### Post by MikeMLP on 2007-10-20
I've been having trouble since upgrading from Feisty to Gutsy at Gutsy Beta.  When I run trackerd in the terminal, I get the following:


```
...
ERROR: CreateService uri is email://1188139769.5772.20@inmate-4261/INBOX;uid=984
ERROR: failed to save email email://1188139769.5772.20@inmate-4261/INBOX;uid=984
ERROR: execution of prepared query CreateService failed due to constraint failed with return code 19
ERROR: CreateService uri is email://1188139769.5772.20@inmate-4261/INBOX;uid=995
ERROR: failed to save email email://1188139769.5772.20@inmate-4261/INBOX;uid=995
ERROR: execution of prepared query CreateService failed due to constraint failed with return code 19
ERROR: CreateService uri is email://1188139769.5772.20@inmate-4261/INBOX;uid=1000
ERROR: failed to save email email://1188139769.5772.20@inmate-4261/INBOX;uid=1000
ERROR: execution of prepared query CreateService failed due to constraint failed with return code 19
ERROR: CreateService uri is email://1188139769.5772.20@inmate-4261/INBOX;uid=1031
ERROR: failed to save email email://1188139769.5772.20@inmate-4261/INBOX;uid=1031
Segmentation fault (core dumped)
```

I did have tracker working on a fresh install of tribe 5, but really, I like beagle a lot better.  So I'm not too upset ;)
Still, something is definitely wonky ^.

---

### Post by LanDan on 2007-10-20
> **MikeMLP said:**
> I've been having trouble since upgrading from Feisty to Gutsy at Gutsy Beta.  When I run trackerd in the terminal, I get the following:


```
...
ERROR: CreateService uri is email://1188139769.5772.20@inmate-4261/INBOX;uid=984
ERROR: failed to save email email://1188139769.5772.20@inmate-4261/INBOX;uid=984
ERROR: execution of prepared query CreateService failed due to constraint failed with return code 19
ERROR: CreateService uri is email://1188139769.5772.20@inmate-4261/INBOX;uid=995
ERROR: failed to save email email://1188139769.5772.20@inmate-4261/INBOX;uid=995
ERROR: execution of prepared query CreateService failed due to constraint failed with return code 19
ERROR: CreateService uri is email://1188139769.5772.20@inmate-4261/INBOX;uid=1000
ERROR: failed to save email email://1188139769.5772.20@inmate-4261/INBOX;uid=1000
ERROR: execution of prepared query CreateService failed due to constraint failed with return code 19
ERROR: CreateService uri is email://1188139769.5772.20@inmate-4261/INBOX;uid=1031
ERROR: failed to save email email://1188139769.5772.20@inmate-4261/INBOX;uid=1031
Segmentation fault (core dumped)
```

I did have tracker working on a fresh install of tribe 5, but really, I like beagle a lot better.  So I'm not too upset ;)
Still, something is definitely wonky ^.

something broken dring upgrade fore sure
ut can be fixed with re-indexing i think

trackerd -v 2 -R

---

### Post by MikeMLP on 2007-10-20
It looked like it was working, and it indexed a lot of things, but when it got to email, it core dumped again (this time without any error messages).  I think you are right though, that it got messed up during the upgrade.  I've tried completely reinstalling tracker before, and it hasn't helped anything at all.  Finally, I would expect the files that it was able to index before doing the core dump to appear if searched for.  The search tool displays no results, even when looking for a file that was indexed before the core dump.

Oh well, at least I have beagle, and it works great!

---

### Post by chris.m.ball on 2007-10-20
I'm relatively new to this tool, having only noticed it this morning.  Here's a little history of what I've gone through this morning with what I'll call partial success and partial failure:

1.  Attempted to use the Tracker Search Tool without touching anything on a clean Gutsy install, fully patched.  No results were coming back.

2.  Located the "System -> Preferences -> Indexing Preferences" tool and clicking on the "File" tab.  From there, I added all of my base level folders.

3.  I then attempted to search again, nothing.  This lead me down the path of installing the tracker tools via apt-get.  From there, I typed "tracker-stats" - nothing was indexed, all counts were zero.

4.  I did a "ps ax | grep tracker" and "kill -9 XXXX" the process.  I opened back up the tracker search tool and tried to search for something again.  Nada, however that triggered the process to come alive again.  Within 60 seconds my CPU took a hit of about 95% for a solid 2 minutes, trackerd was eating it all up - a good sign.

5.  Once the CPU settled back down to relative idle, I typed "tracker-stats" again and started to see numbers ticking up.  After about 30 minutes now, my counts look like this:

-------fetching index stats---------

default : 0 
Files : 1073 
Folders : 174 
Documents : 1 
Images : 0 
Music : 5 
Videos : 0 
Text : 443 
Development : 191 
Other : 259 
Emails : 0 
EvolutionEmails : 0 
ThunderbirdEmails : 0 
KMailEmails : 0 
EmailAttachments : 0 
EvolutionAttachments : 0 
KMailAttachments : 0 
Conversations : 0 
GaimConversations : 0 
Applications : 218 
------------------------------------

What's ironic is that with all of those things indexed, nothing comes up in the search tool.  This leads me to believe that the indexing daemon is probably working fine but that the tool is not tapping into the index correctly, as I haven't been able to retrieve a single search result.

Thoughts?

---

### Post by chris.m.ball on 2007-10-20
FYI,

After letting my system index all day long, it now states:

-------fetching index stats---------

default : 0 
Files : 23192 
Folders : 3184 
Documents : 1 
Images : 1 
Music : 5 
Videos : 1 
Text : 6880 
Development : 2578 
Other : 10542 
Emails : 0 
EvolutionEmails : 0 
ThunderbirdEmails : 0 
KMailEmails : 0 
EmailAttachments : 0 
EvolutionAttachments : 0 
KMailAttachments : 0 
Conversations : 0 
GaimConversations : 0 
Applications : 221 
------------------------------------

I've rebooted the machine a couple times today for various reasons, and results now appear in my searching.  However I've noticed if I search for something that hasn't been fully indexed, the GUI application tends to hang when you drive into the search sub-categories.  I believe this will resolve itself once the trackerd daemon finishes indexing my entire box.  I've also noticed that the process is very system greedy with the default prioritization so some may wish to reduce this.

End result - things are slowly coming together, but if you do what I did and add all of your folders to be indexed, don't be surprised if it takes the better part of a day (or more) to index.  Mine is STILL indexing as we speak.

Cheers.:KS

---

### Post by sancho panza on 2007-10-20
Tracker has been indexing my pc for weeks, and also used to show results a week or so ago. Now, even though tracker-stats shows a lot of indexed data, tracker shows no search results. Does no one else have this problem? Does anyone have a fix?

Cheers!

---

### Post by LanDan on 2007-10-21
well..

i had the same problem till i started it manually as described above and its been working as a charm ever since, you do need to wait a long time to finish if you have  enormous amount of files tough
(i didn't restart since last sunday tough so i don't know if the indexing will start on boot like it should)

does anybody know if it supports Maildir and if you can share the index on certain directories with other users?


-------fetching index stats---------

default : 0 
Files : 62762 
Folders : 4863 
Documents : 18182 
Images : 34108 
Music : 37 
Videos : 40 
Text : 1158 
Development : 34 
Other : 4340 
Emails : 0 
EvolutionEmails : 0 
ThunderbirdEmails : 0 
KMailEmails : 0 
EmailAttachments : 0 
EvolutionAttachments : 0 
KMailAttachments : 0 
Conversations : 0 
GaimConversations : 0 
Applications : 121

---

### Post by sancho panza on 2007-10-26
It all seems to work for now...Thanks!

---

### Post by Druke on 2007-10-28
hmm I killed trackerd and had it redo it's indexing. I can watch it index in the terminal but if i try to search for anything it's "indexing" in tracker search, it has no results. I have beagle working but I'd like to have this working since its the big feature

---

### Post by jamiemcc on 2007-10-29
results should be available when indexing has finished

---

### Post by isecore on 2007-10-29
I'm running into similar problems. When I run tracker-stats it shows it has indexed all of my files:

```

-------fetching index stats---------

default : 0 
Files : 200996 
Folders : 18126 
Documents : 6293 
Images : 108473 
Music : 10483 
Videos : 1046 
Text : 14656 
Development : 17688 
Other : 24231 
Emails : 0 
EvolutionEmails : 0 
ThunderbirdEmails : 0 
KMailEmails : 0 
EmailAttachments : 0 
EvolutionAttachments : 0 
KMailAttachments : 0 
Conversations : 1126 
GaimConversations : 1126 
Applications : 607 
------------------------------------

```

But still, whenever I try to search nothing comes up! Even on files I know for a fact exist. This is extremely annoying. I used Beagle on Edgy/feisty and uninstalled it before upgrading to Gutsy since it seemed the Beagle-project had stagnated. Beagle worked wonders, but Tracker doesn't seem ready for production.

---

### Post by Kokesh on 2007-10-30
I have the same problem. Tracker shows no results, but I can see in stats that it has 12000+ files indexed! I tried Deskbar live-search and also normal Tracker search tool.

---

### Post by sblanzio on 2007-11-01
same problem here

there's a bug filed about this I think
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/148118](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/148118)

---

### Post by Kokesh on 2007-11-01
It works now for me, started after some restarting, trackerd killing and restarting.. strange

---

### Post by cyclocross on 2007-11-02
If I kill trackerd and restart it will work fine until the next reboot, after which I will either get no results are very few.  This is frustrating, when it works I love it!  However tracker just isn't reliable at all.

---

### Post by jamiemcc on 2007-11-02
We will have 0.6.4 out shortly which should fix these issues (corruption/not closing down cleanly)

---

### Post by 23meg on 2007-11-03
> **jamiemcc said:**
> We will have 0.6.4 out shortly which should fix these issues (corruption/not closing down cleanly)

Will Gutsy get a SRU?

---

### Post by werewolves on 2007-11-16
> **jamiemcc said:**
> We will have 0.6.4 out shortly which should fix these issues (corruption/not closing down cleanly)

I'm sorry, but by "these issues" do you mean the fact that it's indexing but the search tool shows no results?  I'm in the same boat as these other folks.  It seems to be indexing fine.  I stopped and restarted trackerd (which seemed to cause it to re-index).  I waited until it was done.  tracker-stats shows lots of files, but I get nothing in search results.](*,)

Anyone find a work-around for this yet??

EDIT: OK, this is freakin' weird.  After a re-boot (which isn't my first re-boot by a loooong shot) I now have tracker results!  What's weird though, is that the test text file I wanted it to find is not showing up.  This is pretty flaky stuff.

---

### Post by Kokesh on 2007-11-18
It was the same here. All was alright after reboot. Than it appeared once more. I can't check it now, because I'm sitting on XP :( I had some smoke coming from my motherboard... When I get new hardware, I'll check it.

---

### Post by hihihi on 2007-11-22
to confirm!: yes indeed, trackerd keeps all it knows from the user, kind of cool, hard head

---

### Post by hihihi on 2007-11-24
tracker is now more creative and gives me today this message (new): "Process /usr/bin/trackerd exited with status 0" after pressing on search button, ok, it does not like me...

---

### Post by ethanay on 2008-03-15
I think that these are a couple of separate (maybe related) issues.

I never received an error message, but trackerd had stopped displaying any search results, despite my index being complete.  All I did was kill the process and restart it via terminal, and it started displaying results again.

It's been a few weeks since I've restarted my computer, so it might have something to do with going through multiple hibernate/sleep and resume cycles and something not shutting down and/or reinitializing properly.

Also, I can list a few other variables:

I have it integrated with the Ubuntu Deskbar, which has crashed on me more than a few times.

I have also installed the 3rd party Thunderbird extension to index Thunderbird e-mails (currently no native support with Tracker; you can search for any e-mail but you can't open it directly from the search results...but still helpful!) so that might have initially caused some issues, too.

cheers,
ethan

---

