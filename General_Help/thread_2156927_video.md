---
title: "video"
date: 2013-06-23
forum: General Help
---

### Post by s7c on 2013-06-23
k, so I solve one problem but after i have to deal with another one. using ubuntu, for me is a real challenge. 
lately if i play any kind of video, doesn't matter if i use chromium or chrome or netflix, after 15 minutes the system freeze. i don't get any error, one time though appeared something related to compiz or something.
it's started one week ago and since then it drives me crazy. 
any ideas or similar problems with happy endings? 
didn't suppose the 12.04 version to be very stable and reliable?

---

### Post by grahammechanical on 2013-06-23
> [COLOR=#000000]didn't suppose the 12.04 version to be very stable and reliable?[/COLOR]

A better question is how stable and reliable is the user? No offence, but we are the ones that often mess things up. Did this problem happen before you installed netflix? What hardware do you have? Come to that, what Ubuntu are you using?

You could install System Load Indicator (indicator-multiload) and that will monitor CPU load, Memory usage as well as network usage (and other things). You may find that the freezing is happening when there is plenty of RAM available and the CPU is not running at full load.

In the terminal we could run top and see just what is using how much. There is also another terminal application called htop but it has to be installed.

You need to narrow down what is causing this.

Regards.

---

### Post by s7c on 2013-06-23
i'm a novice regarding ubuntu. but i know the common sense possible problems and i make sure is neither of cpu/memory (i have intel duo core with 6g memory) related issues, before i decided to ask for help. i have 12.04 ubuntu from few months and this issues started just a week ago without me adding or removing anything beside the regular ubuntu updates. 
i have some java related problems from thinkorswim platform, i have another thread open for that but i can't narrow down the issue. from time to time, maybe once every few weeks i get the black screen with different errors...anyway i don't want to quit ubuntu cause i don't like windows but it's hard for me to have a smoth system and be able to work without any issues...

---

