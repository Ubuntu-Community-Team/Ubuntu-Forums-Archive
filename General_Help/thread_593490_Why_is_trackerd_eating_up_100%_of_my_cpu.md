---
title: "Why is trackerd eating up 100% of my cpu?"
date: 2007-10-27
forum: General Help
---

### Post by sefs on 2007-10-27
I thought tracker was suppose to be less resource intensive than beagle but beagle never did this to me.  I have to keep killing the tracker process to get the cpu to behave.

---

### Post by jamiemcc on 2007-10-27
> **sefs said:**
> I thought tracker was suppose to be less resource intensive than beagle but beagle never did this to me.  I have to keep killing the tracker process to get the cpu to behave.

tracker in niced +19  so it only eays cpu if nothing else is loading your PC

for most people this should not be a problem however a few notebook users who experience a lot of heat or noisy fabs can thrittle back in the preferences (in next version we will default to +5 for notebooks by default and 0 for desktops)

---

### Post by BoardDWorld on 2007-10-28
It's taking 40-50% of my cpu! Is this really necessary??? It's not even indexing at the moment yet it remains at the constant 43-47% ish mark as it has been for the last 2 hours. I would hate to think how much that would reduce my battery life as it still uses 11% on battery! Can we remove this program?

---

### Post by sefs on 2007-10-28
for me once its started it goes straight for 100% and sticks there even when i am using the computer and its not idle and it stays this way for hours.  Its far worst than beagle.  Could this be removed for heron please.

---

### Post by obis666 on 2007-10-29
I am having the exact same problem, any solutions yet? I just installed 7.10 and all I am doing is running tsclient and firefox and trackerd is just eating all my cpu... I am running this on an Acer laptop 1gb ram and 2.7 cpu. Please help I really dont want to fall back to Feisty.

---

### Post by lanruisen on 2007-10-29
I have the same problem, trackerd runs for hours at 100%, but the funny thing is the the first time that I installed 7.10 on this laptop I had no problem with this at all, but I did a fresh install a couple of days ago and trackerd never stops unless I stop it, so consequently my laptop fan runs like crazy the whole time.

---

### Post by xadloki on 2007-10-29
Same thing here, 100% cpu usage all the time.
I kill it and it crashes the System Monitor, how can this be removed permanently ?

---

### Post by por100pre1 on 2007-10-29
Go to **System> Preferences> Sessions** and uncheck **Tracker**. It is NOT necessary to use Trackerd.

---

### Post by deadcabbit on 2007-10-29
Tracker sucks, sry; when I queried it with tracker-status and it echoed back pure garbage (cpu at 100% of course) I threw it out for good :)

---

### Post by Jorge on 2007-10-31
Try google desktop...

---

### Post by lynxus on 2007-11-01
Same here.
really annoying me now!!!!
The HDD is constantly going and cpu @ 100
Driving me insane! i cannot stand this latest version of ubuntu , ive had no end of problems!

---

### Post by tw2113 on 2007-11-03
try knowing your personal files locations more, i say.

killall -STOP trackerd on Command line worked to stop it for me. In case anyone needed it.

---

### Post by BoardDWorld on 2007-11-03
I actually I find it a future privacy risk, especially with Google. They've been buying into everyones privacy without the common consumer even realizing. It should be completely illegal to gather personal data without the average person knowing and without paying for it! I've completely removed "Trackerd" and would never consider Google's version. That's the end of my CPU problems...

---

### Post by Jorge on 2007-11-03
> **BoardDWorld said:**
> I actually I find it a future privacy risk, especially with Google.

What risk are referring to? This is a quote from Google Desktop (About):

> Your computer's content is not made accessible to Google or anyone else without your explicit permission.
Only if you enable the Advance Features (which is disable on the standard install) Google Desktop will send information over the Internet. And even in that case, the info sent will be "Non-personal usage data and crash reports".

---

### Post by BoardDWorld on 2007-11-04
Please take note of the word "**future**" in the following sentence:

*I actually I find it a future privacy risk, especially with Google.*

Google has spent literally "Billions" of dollars over the past few years solely for gathering personal data. Did you know you are identified every time you use Google search? Everything you search is logged in a database with your identification number. This really is fact.

Google plans to use this for the new future in advertising where you'll search something on the net, say the latest vehicle of your choice, then all the adds on your TV will start matching your search. So Toyota, Nissan etc will be paying Google for the information they have freely gathered on you. This is in fact a proposal in progress that has already been put forward.

Also 3 people that I know of (perhaps it is more now) have been jailed in the US through this personal database of searches. Though they did deserve to go away this clearly shows information can be provided without your consent to various Hierarchies. This is also fact. 

And here we are now trusting them with vast amounts of private information from what's becoming a vast amount of avenues.

---

### Post by Stik on 2007-11-04
Trackerd is fine... get over it :P

---

### Post by BoardDWorld on 2007-11-04
> **Stik said:**
> Trackerd is fine... get over it :P

Yes you're right, if it didn't use so much CPU usage... Did you not notice I was talking specifically about Google?

---

### Post by inversekinetix on 2007-11-04
> **tw2113 said:**
> try knowing your personal files locations more, i say.



Amen, i have 2TB in my box and I know where my files are.  I hate those indexing type things, especially if its gonna mangle my cpu.  It bad enough that ubuntu uses 20%cpu for playing mp3s.

---

### Post by mikeize on 2007-11-04
is it safe to uninstall tracker and tracker-search through synaptic?  will it mess up anything else?  I have no use for this prog myself, and it eats inordinate cpu power from time to time.

-mike

---

### Post by BoardDWorld on 2007-11-05
Yes it is, just remove "tracker" & "tracker-search-tool". This resolved my CPU problem.

---

### Post by MarilenCorciovei on 2007-11-16
I've had[ the exactly same problem]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/what-kills-my-gutsy/view") and found absolutely no need to keep trackerd, just stopped it and I'm not missing it at all.

---

### Post by firoozyves on 2007-12-07
If you still want to use trackerd, you can change the tracker preferences in System; Preferences; **Indexing Preferences**.

I made the following changes and I don't have any problem since:

On the General tab:

**Mark** Enable indexing
**Unmark** watching

on the Performance tab:

Indexing speed: **0**
**Select** Minimize memory usage

A Son service.

---

