---
title: "bittorrent,bitcomet, azureus NOT linux compatible (??)"
date: 2008-02-03
forum: General Help
---

### Post by nweissma on 2008-02-03
i'm likely making a shameful error: i understood that bittorrent, bitcomet and azureus are _NOT linux-compatible _

i can't reconcile these "facts" with [https://help.ubuntu.com/community/BitTorrent]("https://help.ubuntu.com/community/BitTorrent")

---

### Post by NineseveN on 2008-02-03
bittorrent and Azureus are both downloading on my Ubuntu box as we speak. They're cross-platform independent (azureus is built in Java), Azureus is in the default Ubunutu repositories as I recall, and BT is installed by default.

---

### Post by accatagon on 2008-02-03
Bit torrent is a protocol and a piece of software. The old version of the software apparently runs on Linux but not the new one. 

 Azuerus is not entirely "compatible" with Linux because you need the sun-JRE to to run it, and that's not open source (though the next version is slated to be). In this case though, ubuntu lets you download the JRE despite not being open source. Whether you wish to do that is up to you. 

Otherwise, there are other Linux-compatible implementations of the protocol. The choice of which to use is up to you. There's a comparison on Wikipedia at [http://en.wikipedia.org/wiki/BitTorrent_client](http://en.wikipedia.org/wiki/BitTorrent_client)

---

### Post by nweissma on 2008-02-03
from what i see [http://https://help.ubuntu.com/community/AzureusHowTo]("http://https://help.ubuntu.com/community/AzureusHowTo") azureus will not work for gutsy gibbon -- am i wrong?

---

### Post by NineseveN on 2008-02-03
> **accatagon said:**
>  Azuerus is not entirely "compatible" with Linux because you need the sun-JRE to to run it, and that's not open source (though the next version is slated to be). In this case though, ubuntu lets you download the JRE despite not being open source. Whether you wish to do that is up to you.]

That's sorta splitting hairs, don't you think?  It runs in Ubuntu (Linux) with nearly no effort; install from  the repo and the Sun JRE is included as a dependency...it's virtually transparent to the end user.

I get what you're saying, but for all intents and purposes, in realistic terms, Azureus is compatible. On a sincerely technical standpoint, perhaps not...but on an average end-user level, it is.

Cheers.

---

### Post by NineseveN on 2008-02-03
> **nweissma said:**
> from what i see [http://https://help.ubuntu.com/community/AzureusHowTo]("http://https://help.ubuntu.com/community/AzureusHowTo") azureus will not work for gutsy gibbon -- am i wrong?

That page could use an update I guess, I'm running 7.10 Gutsy and Azureus, it's in the add-remove programs. ;)

---

### Post by nweissma on 2008-02-03
what do you mean"install from the repo"?

---

### Post by nweissma on 2008-02-03
don't mean to be a pest..but i can't figure out how to use this azureus..i tried to install on vista-32 -- i need  it to download the linux distros, which will shortly be installed (as soon as i can unconfuse myself) -- and all i can get is the Vuze video player. how do you operate azureus? is there a special installer that i am missing?
btw,tucows also shows that azureus is not linux compatible [http://http://www.tucows.com/search.html?search_scope=lin&search_lib=soft&search_adv=0&search_size=&search_size_multi=b&search_terms=azureus&srch_pf=lin&x=0&y=0]("http://http://www.tucows.com/search.html?search_scope=lin&search_lib=soft&search_adv=0&search_size=&search_size_multi=b&search_terms=azureus&srch_pf=lin&x=0&y=0")

---

### Post by zvacet on 2008-02-03
> what do you mean"install from the repo"?

First of all be sure that you have all repos open,so go to the system>admin<software sources>chek all boxes under Ubuntu software tab and under updates tab.Reload.Now go to the synaptic and in search box type azureus and when synaptic find it mark it for installation and install.You can also try Ktorrent,Deluge,[Transmission](http://www.getdeb.net/search.php?keywords=transmission).

---

### Post by sloggerkhan on 2008-02-03
Azureus is bloated. On windows, try uTorrent, or even see how deluge ([http://deluge-torrent.org](http://deluge-torrent.org)) is working. On ubuntu, use Deluge.

---

### Post by linuxisfree on 2008-02-03
> **nweissma said:**
> what do you mean"install from the repo"?

"Install from the Repos" means that you can install the app (in this case Azureus) from the repositories in the Synaptic Package Manager (System-->Administration-->Synaptic Package Manager) or Add/Remove (Applications-->AddRemove...)... that is provided these repositories are enabled.

Hope that helps:D

---

### Post by nweissma on 2008-02-03
thanks re deluge.. but why would i want mission-critical software that's unstable[http://deluge-torrent.org/downloads.php]("http://deluge-torrent.org/downloads.php")?

---

### Post by NineseveN on 2008-02-03
> **nweissma said:**
> don't mean to be a pest..but i can't figure out how to use this azureus..i tried to install on vista-32 -- i need  it to download the linux distros, which will shortly be installed (as soon as i can unconfuse myself) -- and all i can get is the Vuze video player. how do you operate azureus? is there a special installer that i am missing?

If you're actually working inside of Windows right now, then the Liunux version of Azureus won't help you, it won't run in Windows. You need the windows version to download the Linux distro, then once inside Linux after you've installed it, you'll need to install the linux version of your software to operate there.


> btw,tucows also shows that azureus is not linux compatible [http://http://www.tucows.com/search.html?search_scope=lin&search_lib=soft&search_adv=0&search_size=&search_size_multi=b&search_terms=azureus&srch_pf=lin&x=0&y=0]("http://http://www.tucows.com/search.html?search_scope=lin&search_lib=soft&search_adv=0&search_size=&search_size_multi=b&search_terms=azureus&srch_pf=lin&x=0&y=0")

I think you're misunderstanding a fundamental difference between Windows and Ubuntu/Linux...you don't need to download software outside of the OS for the most part.

Here's an example:

In Windows, if you wanted Azureus and were getting ready to install Windows on a new PC, you'd download the Azureus program from download.com (or wherever), burn it to a CD and then once you had Windows installed, you'd load the CD and run the .exe from there....follow me so far?

This is generally not the case in a user-friendly Linux distro such as Ubuntu. In Ubuntu, for example, you install the OS, then, once inside, you go to the main menu and find "Add/Remove..." and click on it. Once the window loads, you're rewarded with a categorized list of more programs than you can imagine, all installable by merely checking a box and clicking a button titled "Apply Changes".

The software in the lists above come from Repositories (repos for short), which are basically file servers where programs are deployed by the the OS developer for installation. These files are checked to make sure they're not malicious or infected of course, but really, installing something like simple Azureus (or any other piece of software in the repositories) is as simple as opening a menu, checking a box and hitting a button.

There are other ways to install software in Ubuntu and other flavors of Linux, but this is probably the easiest way to start. You won't always get the most recent versions (as not all of them have been tested and added to the repositories), but you'll have many programs right at your fingertips.

When we say things like "enabling other repos" or some such thing, what we're saying is that there are other repositories (collections of installable software) that you can enable to gain access to even more programs to install. Adding other repos you the sources that you Add/Remove programs menu or your package manager is as simple as editing a text file or copying and pasting a link in your Software Sources menu.

It's difficult to explain fully without you actually being inside of the OS though...so in short, you can make a list of what you want to install in Ubuntu (or Linux in general), and then once you have the OS installed, you can start installing them through Add/Remove or the actual Package Manager (slightly more complex, but not much).

Maybe I'm misunderstanding you, but it sounds like you're going about this in the wrong order and trying to get the wrong version for the different operating systems.

---

### Post by cozmicharlie on 2008-02-03
I agree with NineseveN - you may be going about this the wrong way.  Azurues is compatible with Linux from a user standpoint as NineseveN explained.  Just to add to what NineseveN wrote - you may want to check out this site [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) - it explains how to add programs in Ubuntu and even has video tutorials.  You may want to do a little reading before you jump into it though.  Ubuntu is not Windows so it does require you learn a whole new system. As per Azureus if you search the tutorial section of the forum you will find a number of excellent How To's for installing Azureus.  The Azureus WIKI is also excellent.  If you have any problems post in the forum and someone will help.

---

### Post by NineseveN on 2008-02-03
> **cozmicharlie said:**
> I agree with NineseveN - you may be going about this the wrong way.  Azurues is compatible with Linux from a user standpoint as NineseveN explained.  Just to add to what NineseveN wrote - you may want to check out this site [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) - it explains how to add programs in Ubuntu and even has video tutorials.  You may want to do a little reading before you jump into it though.  Ubuntu is not Windows so it does require you learn a whole new system. As per Azureus if you search the tutorial section of the forum you will find a number of excellent How To's for installing Azureus.  The Azureus WIKI is also excellent.  If you have any problems post in the forum and someone will help.

That link is excellent! *saved for future reference. Thanks for sharing it.

---

### Post by sloggerkhan on 2008-02-03
> **nweissma said:**
> thanks re deluge.. but why would i want mission-critical software that's unstable[http://deluge-torrent.org/downloads.php]("http://deluge-torrent.org/downloads.php")?

Umm.... not sure what you mean here.
I will say that 'unstable' means different things to windows and linux users.
Quite honestly, I find this whole thread kinda confusing.

---

