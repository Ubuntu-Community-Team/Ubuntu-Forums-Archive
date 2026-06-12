---
title: "Synaptic Firefox 3 is still beta 5"
date: 2008-06-20
forum: General Help
---

### Post by Ninefold on 2008-06-20
I have updated synaptic repeatedly since the release of firefox 3 three days ago. I have done this both on the main server and the one for my country and it still says the version is:

> Firefox... 3.0b~5

I finally just gave up and installed it and it is beta 5. Can anyone help me out as to why in the repos it is beta 5 for me?

---

### Post by drs305 on 2008-06-20
Have you tried changing to another repository in synaptic. Some repositories are updated faster than others. Synaptic > Settings > Repositories > click Download From > Other and select another repository.

Added: the 3 I randomly checked in the US all had the current version, including duke and gtlib.gatech.

---

### Post by Ninefold on 2008-06-20
Thanks drs305, I didn't know that there was a list of other servers in "other". So far I have tried 4 or 5 and they all say under version b~5 for firefox 3, which I take to be beta 5 again.

I get the feeling I am doing something stupid and not seeing it. :-?

---

### Post by drs305 on 2008-06-20
> **Ninefold said:**
> Thanks drs305, I didn't know that there was a list of other servers in "other". So far I have tried 4 or 5 and they all say under version b~5 for firefox 3, which I take to be beta 5 again.

I get the feeling I am doing something stupid and not seeing it. :-?

Go to the same section and try US > [http://archive/linux.duke.edu/ubuntu](http://archive/linux.duke.edu/ubuntu)

I'm using 64-bit hardy. I use swiftweasel but just downloaded and installed FF3.0 from this site.

---

### Post by Ninefold on 2008-06-20
I tried that server and it still said "b~5". I decided to install it again and it's just a mess now. I launch what's suppose to be firefox 3 and it isn't, it's firefox 2.

I even ran it from the command prompt in /usr/bin/firefox-3.0 and it opened firefox 2. .. I have two firefox 2's installed now and one is called 3. This seems to be a separate issue.

I just can't download firefox 3 from the repos it seems. In /usr/bin/ I believe it is a symbolic link to what it called 3.0b-5. 

I checked the sources.list and it does list as being:

"http://archive.linux.duke.edu/ubuntu/"

I just don't get it.

Thanks for your help.

---

### Post by drs305 on 2008-06-20
Added: Solution posted in # 8 (Occam's Razor)

Well, before I did anything else I'd install and set up Foxmarks. It's a bookmark synchronizer that will store your bookmarks and which I believe will work with both FF2 and FF3. Otherwise export your current bookmarks so that you can import them to the new version once you get it installed.

Once you have safely saved your bookmarks, you may want to uninstall FF2 and try installing FF3 afterwards. I'd probably wait until someone offers you a suggestion as to what exactly is going on with your system and perhaps can offer a solution without uninstalling FF. You may also want to jot down which extensions you are using.

Questions they may ask include how you originally installed FF2. I'm assuming you have been using synaptic to install FF3. Also if you may have installed FF2 as root instead of with your username. You haven't locked the version of FF in synaptic or via apt-get have you (you'd know if you had)?

I can't provide much more assistance except the uninstall option. Best of luck. I'm sure you will get this sorted out soon.

Added:
If the post doesn't get much more attention you might want to make a new one with a different title, something like "I Can't Get Rid of FireFox 2" or "Won't Let Me Upgrade to FF 3". You may find the answer by searching the threads for something similar.

---

### Post by Ninefold on 2008-06-20
Let me say thank you for your effort drs305, I did learn something.

My troubles with firefox 2 and 3 I think I can deal with when the time comes that I can get a hold of firefox 3. I am just baffled as to why beta 5 appears in every repo I try. I have tried about 8 repositories now and they all say the same thing for firefox 3. I know they change because one repos in Calgary listed it different because it failed on some connections.

I am using Hardy Heron and I have firefox 2 because when I installed Hardy I removed firefox 3 beta and installed firefox 2 and I did it all in synaptic. One removed and then the other installed. It was simple and worked fine.

I have sort of backed up my stuff. I am not worried really. I will complete remove all firefox's if I know I can get the final of 3. It's this synaptic repository thing that is bugging me. How can we both connect to the same server and not see the same thing?

Anyone know how I can test what's going on? I am not skilled with apt.

I might boot the live cd and poll the repos and see what it says.

---

### Post by drs305 on 2008-06-20
In Synaptic, under Settings, Repositories, Updates, I have Unsupported udpates (hardy backports) enabled, as well as Important and Recommended ticked.

When you look at the synaptic list, is firefox-3.0 listed? Although you should get the latest by just selecting 'firefox'. Specifically I see 3.0+nobinonly-0ubuntu0.8.04.1 in the latest version. **That version is shown under hardy-updates.** Under firefox Properties, hardy still shows beta.

---

### Post by Ninefold on 2008-06-20
That did it! Thank you drs305!

I had "important" checked but I did not have "recommended" or "Unsupported updates" checked. I checked those and when I reloaded the packages firefox 3 is now listed as normal and not beta 5.

Thanks again. I will mark the thread as solved.\\:D/

---

### Post by fragos on 2008-06-21
I use the US server and Firefox 3 Final. In Software Sources I've checked the boxes for all the repositories -- main, universe, restricted and multiverse.

---

### Post by drs305 on 2008-06-21
> **fragos said:**
> I use the US server and Firefox 3 Final. In Software Sources I've checked the boxes for all the repositories -- main, universe, restricted and multiverse.

the ones you want to check if you don't see the final ff3.0 is on synaptic's repository/updates tab. for now, in hardy, the 3.0 version is in Recommended (hardy-updates). apparently in gutsy it's in Unsupported (gutsy-backports).

---

### Post by aysiu on 2008-06-21
I wouldn't recommend keeping the unsupported or proposed updates repositories enabled after you upgrade Firefox.

Check them, upgrade Firefox, and then uncheck them.

---

### Post by inanutshellus on 2008-06-27
> **drs305 said:**
> in hardy, the 3.0 version is in Recommended (hardy-updates). apparently in gutsy it's in Unsupported (gutsy-backports).


Blarg. I'm in Gutsy and can't seem to get firefox 3 via Synaptic. With default settings, I see 3.0~alpha8+nobinonly=0ubuntu. If I select Unsupported (gutsy-backports) as suggested, I see 3.0~b4+nobinonly-0ubuntu. I've tried multiple alternate servers with both settings and always get the same results.

---

### Post by drs305 on 2008-06-27
> **inanutshellus said:**
> Blarg. I'm in Gutsy and can't seem to get firefox 3 via Synaptic. With default settings, I see 3.0~alpha8+nobinonly=0ubuntu. If I select Unsupported (gutsy-backports) as suggested, I see 3.0~b4+nobinonly-0ubuntu. I've tried multiple alternate servers with both settings and always get the same results.

I had said 'reportedly' because I no longer use gutsy but several people had posted that it was in the backports. 

In any case, here is a link with ways to  install it in gutsy. Note: post 7 is pretty lengthy but post 9 suggests a different way to avoid overwriting FF2. Again, I have not used these myself:
[Firefox 3 FINAL in Gutsy]("http://ubuntuforums.org/showthread.php?t=833036")

Good luck. Maybe it will be in the repos soon.

---

### Post by inanutshellus on 2008-06-27
I can indeed go ahead and grab the tarball, I'd just prefer to keep everything managed by Synaptic. Still, no reason I can't just drop the tarball install in a week or two when/if the repos get updated.

Thanks anyway!

---

### Post by JSuresh on 2008-07-28
> I'm in Gutsy and can't seem to get firefox 3 via Synaptic. With default settings, I see 3.0~alpha8+nobinonly=0ubuntu. If I select Unsupported (gutsy-backports) as suggested, I see 3.0~b4+nobinonly-0ubuntu. I've tried multiple alternate servers with both settings and always get the same results.

4 weeks later, I'm still running into this issue (running Xubuntu 7.10).  Is the released version of firefox 3.0 not on the servers yet?

---

