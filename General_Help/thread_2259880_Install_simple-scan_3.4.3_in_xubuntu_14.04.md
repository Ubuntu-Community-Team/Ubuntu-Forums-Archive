---
title: "Install simple-scan 3.4.3 in xubuntu 14.04"
date: 2015-01-07
forum: General Help
---

### Post by roger_1960 on 2015-01-07
I recently found,after recent updates, that chromium and dropbox stopped working on my old AMD athlon XP-M  powered laptop.  The solution to this was to install older versions of the programs which did not need the processor to have sse2 capability (which seems to be an assumption in recent packages but which excludes them from use with my old laptop). In reaching this solution I updated the machine from Bodhilinux 2.4.0 (based on 12.04) to xubuntu 14.04

The latest version of simple-scan in xubuntu 14.04 does just work, but after pressing scan there is a delay of over 30 seconds before the document appears.  With the previous version in Bodhi it worked very quickly. (Using gscan2pdf  in 14.04 it is almost instant so I think it is a particular problem with the latest version of simple-scan)  I would like to try installing simple-scan 3.4.3 (last version in 12.04) in xubuntu 14.04.  How do I do this?  I guess I can enable the Precise repos but really need some instruction and the correct commands spelling out.  I am OK with terminal commands.

Or if anyone has any other solution..

---

### Post by DuckHook on 2015-01-08
I will show you how it's done, but first advise you that what you are asking is very dangerous.

What you are essentially doing is breaking the 14.04 repository for your installation. The reason is as follows: Repos exist on the basis that, not only the apps, but their dependencies have been tested to coexist with each other. So, the dependencies that are used for simple-scan 3.4.3 will work with every other app in version 12.04 of the OS, but not necessarily with any other version. By forcing an old app to install in 14.04, you will also force its old dependencies into your system.

This may or may not have bad effects on your system. If your system simply crashes, then this is actually the best of the worst outcomes, since you will know up front that it won't work. The really bad problem arises when your system shows no immediate or outward sign of misbehaviour, but some time down the road, you install another app that needs the current version of those dependencies and it weirds out because it is using a bugged version. Or an update occurs that months later starts making use of a feature that is debugged in the latest library, but was still bugged in the version that you now have locked to your OS. Some of those issues can be very subtle: permission problems, file locks, corrupted data, etc, most of which are next to impossible to trace back to those old dependencies that were installed. Moreover, you will have forgotten that you monkeyed with those dependencies in the first place given the passage of months or years. And since, to be brutally honest, most users don't even know what dependencies are being installed with their apps in the first place, this is just a recipe for confoundment and misery.

Of course, in the best case, nothing else uses those libraries and your whole system, along with your old app, runs tickety-boo. But this sort of don't-worry-be-happy attitude smacks too much of delusion for my liking.

With this strong warning given, here's how to install old apps. What follows is a general guide:

1. Ubuntu keeps a database of packages. They follow the convention: [http://packages.ubuntu.com/name_of_version/package_name](http://packages.ubuntu.com/name_of_version/package_name)
So, in your case, this would be: [http://packages.ubuntu.com/precise/simple-scan](http://packages.ubuntu.com/precise/simple-scan)

This web page is very useful. Not only is the *.deb* package available for download at the bottom of the page in both 32-bit and 64-bit architectures, but *it lists all of the package's dependencies*. A wise user would print this page out and keep it for posterity, to at least give himself a fighting chance to rectify any problems that might arise from the live hand grenade he is about to play with. It is very important that this page be bookmarked and kept open during the following steps.

2. After the package is downloaded, you can try installing it. The usual way is to "open" the *.deb* package, which will bring up Software Centre along with a warning that you are installing an unknown non-repository package and this is potentially fatal, etc. Powerusers will use *Apt* or *Synaptic*.

3. Chances are that it won't install the first time because it is missing critical dependencies. This is where the aforementioned web page is again super useful. By clicking on the links in that page, you can install the needed dependencies first. Cycle through all of the dependencies that *Apt* or *Synaptic* or the Software Centre is telling you it needs, and after adding all of the necessary ones, the app that was the object of all this tender loving care should install.

4. Almost immediately, your OS will detect your new app, notify you that a newer version exists and advise you to upgrade. **Do NOT allow an upgrade at this point**. If you do so, the old version that you have devoted so much time and attention to will be overwritten by the new one, all of the old dependencies will be erased, and you will have to start all over again.

5. We need to pin the app in *dpkg* so that future system upgrades do not touch this app or its dependencies. To do so, we do:```
sudo apt-mark hold pkg_name
```...replacing "pkg_name" with the name of your package, which in your case would be "simple-scan". Some people will also pin the dependencies that were earlier hand-installed, but my understanding is that *dpkg* is smart enough to have flagged them as linked to the pinned app and they are therefore dependently pinned.

6. To make sure that the app has been properly pinned, do:```
sudo apt-get update && sudo apt-get -s dist-upgrade
```The -s flag simulates an upgrade without actually doing anything. The objective is to check if the upgrade ignored the pinned app. If so, all is well.

So, in light of how dangerous such actions are, why am I giving away the instructions (especially given the sentiments in my signature block)? Because sometimes, the only possible way to have a functioning system is to use old driver modules, or it is absolutely essential to use an old mission-critical app. In my case, the newest version of *Gnucash* crashes when trying to generate journals in data files created by older versions. Moreover, in crashing, it doesn't release the file lock on the network share and could potentially corrupt the data file. Since *gnucash* is critical to my business and since I have years of transactions in the datafile, it would be excruciatingly painful to switch to another accounting app. In this case, I judged the integrity of my data to be more important than the integrity of my OS, but it's a tough choice, not to be taken lightly even in the most critical circumstances.

I hope you don't mind my saying this, but simple-scan is hardly a mission critical app and does not justify measures that can potentially bork your system. Neither are Chromium or drop-box for that matter, but you've already done the damage there. In the case of simple-scan at least, my advice would be to fix the slowness issue itself, or to work around it by installing perhaps a different scanning app. *xsane* and *flegita* are two that come to mind. Forum members would be happy to help chase down the slowness issue, I'm sure.

It is almost never a good idea to force fit an old app onto a new version for reasons of security alone, never mind the potential for breakage.

Your post raised a whole bunch of ancillary issues that I thought should be addressed, thus the long-winded reply. Hopefully, general users may find some of these thoughts and instructions useful.

---

### Post by roger_1960 on 2015-01-08
Thank you for your very thoughtful and helpful reply. I was aware of the dependencies issues and have so far had no issues with chromium or dropbox.  My old laptop is used in a laundry for scanning worksheets and saving them to dropbox (data which is then shared with clients - it would be a pain to change - so its either install working dropbox on this old machine or get a new one). I have used simplescan for years and its ideal for what we do, but I might just change to gscan2pdf, even though its unecessarily complicated for my purposes.  Your point 5 is very useful - didn't know about that command.  I'll at least use it to stop chromium from trying to update.  Once again, many thanks for taking the time to make such a full reply.

Roger

---

### Post by DuckHook on 2015-01-08
If you don't mind a bit of further meddling and uninvited advice, this time of a business nature&#8213;I take it that the laundry that you speak of is a business. If so, I've found that, when it comes to business, it never makes sense to compromise the OS for the sake of working around old hardware. In your case, the combo of scanning, dropbox, Chrome etc *is* mission-critical, and if it were me, I would be very worried about the security holes that I'm leaving wide open using obsolete, unpatched apps. I believe that your best bet at this point is to buy a cheap box, or even a used one on ebay, but one that is capable of running an unmodified 14.04 and the current patched and well-behaved versions of those apps. If your old machine does not have sse2, then it is positively ancient and the wrong tool for something as important as your business. The old machine can still be repositioned as a server of some kind and won't go to waste. Just my 2 cents.

---

### Post by roger_1960 on 2015-01-12
I have in fact now overcome my urge to prolong use of my 13 year old laptop forever and have swapped it out for a 4 year old netbook running 14.04.1. My thoughts are much the same as yours.  I'll use the old one to mess about with puppy, Slackware etc Thanks again

---

