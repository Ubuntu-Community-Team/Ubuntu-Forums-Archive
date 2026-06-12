---
title: "The snap pending update message"
date: 2022-07-16
forum: General Help
---

### Post by de Bacon on 2022-07-16
Hi,
Running Ubuntu Studio 20.04 (fully updated).  I continue to get these popups: "Pending update of"thunderbird" snap, close the app to avoid disruptions."  Looking at another's post on this subject the resolution was stated as: to update snap.  

I did that with command: 

[INDENT]snap refresh[/INDENT]
Received the response, 
[INDENT]All snaps up to date.[/INDENT]
 
Then I followed that with
[INDENT]snap refresh --time[/INDENT]
the response,
[INDENT Last: today at 13:19 PDT
next: today at 20:20 PDT [INDENT


About three minutes later I got the message pop up again, the time stated (9 days left), the same as it was before I updated???

I don't quite understand how that could happen.

Anyway, thanks for the time to respond.  I don't like this nagging issue.  I thought I had fixed it many times in the past, but the message continues to pop up, sometimes days in-between. Previously the days left always went back to 13 days, not this time.  

Maybe some background information could further assist here.  When I attempted to upgrade from 18.04, to 20.04, (October 10, 2020) due to the bios change and my ignorance, it crashed my system, so I had to fresh install at that point.  After I got it running again 5 days later, had to learn how to set up the new secure bios replacement (what ever the acronym) the new system's thunderbird package when loaded through synaptic wouldn't allow me to transfer my thunderbird backup files into the version of thunderbird provided by the repository. Actually it would allow it for the opened session, but after a reboot, Thunderbird went back to its "fresh install state."  I tried that many times over several days.  After days of trying, with no success, I downloaded a copy of thunderbird from Mozilla and manually loaded it with the instructions that Mozilla provided.  With that I could use my email backup, replacing the x.default file with my backup, by changing the symbolic folder name to coincide with the stock file, x.default.  

When this popup issue began, I fooled around some in trying to figure it out.  Finally a couple of days ago, I did a backup of my then existing x.default file, followed by manually removing thunderbird then loading the version from synaptic.  I was able to add my backup with this version (???)(I don't know what is different).  But since then the popup message continues to count down by the day, is now at 9 days.  That is all I know, and what I know is little really.  I have no computer education and have profound dyslexia so reading is quite a difficult hindrance thing for me.

Again thanks for reading and the time to assist.  

Tom

---

### Post by grahammechanical on 2022-07-16
On Ubuntu 22.04 Firefox is a snap and for nine days I have been getting a warning that Firefox will be updated in a certain number of days. An hour ago I loaded into 22.04 and Firefox snap updated without action from me. I was given a warning. 

It seems to me to be a bit pointless to give a warning days in advance and then give some kind of a count down every time Ubuntu is loaded. But as I think about it there may be people who never shutdown their machines and never close Firefox. So, they may appreciate being given advance warning. This may especially be useful if many computers are involved.

Snaps update independently from the rest of the system and the snap update of Firefox is very fast compared to an update to the deb version which requires the full Firefox package of many mega bites to be downloaded.

Regards

---

### Post by de Bacon on 2022-07-16
I shut down my computer at the end of my every day.  Thus it still makes no sense to me.   I did the "snap update"  and only a few minutes later a new popup showed up without a days change.  If I shut my computer off each day, I shouldn't get one of these messages!

Thanks for the response, I like your signature!  Ya can't fix stupid!

---

### Post by de Bacon on 2022-07-17
This thing is continuing its countdown, despite the manual update done yesterday.  Down to 8 days left this morning shortly after booting up!  Email is extremely important!  I need to get this issue resolved, whereas updating snap yesterday actually did nothing.

I have tried all that I can think of.  Somebody must know something about this, I don't think I am the only one experiencing this issue. 

Thanks again for reading, I am hopeful for some assistance with this issue.

---

### Post by deadflowr on 2022-07-17
This is a by-product of refresh-app-awareness,
which is suppose to prevent refreshing snaps that are in use.

(the main issue with that was that whenever an app is refreshed, any running instances seemingly crash.
Refresh-app-awareness is meant to prevent this, but as seen in this thread, there are side-effects.)

Likely some apps continue running in the background even after closing them.

More on refresh-app-awareness here: [https://forum.snapcraft.io/t/refresh-app-awareness-call-for-testing/29123]("https://forum.snapcraft.io/t/refresh-app-awareness-call-for-testing/29123")

---

### Post by de Bacon on 2022-07-17
deadflowr,

Thanks for the info.  After my writing here this morning, I tried something else.  It may have worked?  At least the message didn't pop up again afterward.

I rebooted the computer, after log-in, I opened a terminal and again did the update of snap.  This time it did something different.  I entered the code, pushed enter, and it downloaded something.  I don't know what it was as I am unable to read well enough to read before it vanishes.  Since then, after opening Thunderbird, no message popups have occurred.  I have my fingers crossed and my legs too, even though I am not superstitious.  Maybe it worked, maybe not, although; I should know by the end of the day.  

I shall read the link you provided as it is likely somewhat helpful, and with it here in this thread, I can reference it again in the future if needed.

Thanks!
If not I shall be back.

Tom

---

### Post by de Bacon on 2022-07-18
It is a day later, it seems that this issue has been solved.   If you  have one of these issues with the popup: "Pending update of "x" snap , close the app to avoid disruptions." this is how I solved it where the variable "x" was Thunderbird.

[INDENT]1. re-boot
2. log in
3. before starting any programs run the command ```
snap refresh
```
[/INDENT]

It may be overkill to "reboot," yet a day later, I've seen no more of these popups. 

Regards to all,

---

### Post by oygle on 2022-07-27
I don't need or want snap at all. It is bloatware and causes problems with other packages, plus does updates without my control. This may help - "How can I stop apt from installing snap packages?" - [https://askubuntu.com/questions/1345385/how-can-i-stop-apt-from-installing-snap-packages](https://askubuntu.com/questions/1345385/how-can-i-stop-apt-from-installing-snap-packages)

Also this article goes into the mount side of things - [https://linuxhint.com/turn-off-snap-ubuntu/](https://linuxhint.com/turn-off-snap-ubuntu/)

I have been following the steps outlined at [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) , however the next update from **apt** goes and reinstalls firefox/snap. I guess I could drop firefox and use Tor browser, much more secure and stable.  Or as one person posted, they only get the firefox updates from the Mozilla site and not the Ubuntu package repository.

---

