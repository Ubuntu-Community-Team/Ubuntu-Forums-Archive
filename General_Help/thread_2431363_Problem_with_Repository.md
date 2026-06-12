---
title: "Problem with Repository?"
date: 2019-11-15
forum: General Help
---

### Post by WB0HYQ on 2019-11-15
I hope this is in the right place. If not, please move.

For the last week there seems to be some sort of problem with the main Repository. I keep getting "Check my connection" when I try to update. I know my connection is just fine because everything else runs at top speed (gigabit LAN card). If it finally connects, there is a better than even chance the download will be at a speed somewhere neat 150-200Kbps when I normally get 2.2 - 2.5 MBps. Even at this speed, I see the download getting hung up and numerous retries attempted as the same segment is downloaded several times in a row Indicated by, say, 15.5Mb being retried many times before moving to 15.6Mb).

KUbuntu 18.04LTS

Bill

---

### Post by WB0HYQ on 2019-11-16
For the last 24-hours I am totally unable to contact the Repository. I'm told to check my connection, which is a false answer. There is nothing wrong with my connection.

Bill

---

### Post by dragonfly41 on 2019-11-16
I have used this on occasions to refresh update ..

sudo rm -rf /var/lib/apt/lists/* 
sudo apt-get update

---

### Post by SeijiSensei on 2019-11-16
Try a different source.  In Discover, choose Sources, then click the Software Sources button.

[https://www.politicsbythenumbers.org/images/discover-sources.png](https://www.politicsbythenumbers.org/images/discover-sources.png)

[www.gtlib.gatech.edu](www.gtlib.gatech.edu) has been pretty reliable for me along with mirrors.mit.edu.

---

### Post by WB0HYQ on 2019-11-19
For some reason, I stopped getting notification emails for this thread. i apologize.

Both responses seem to be good ones, however, Seiji-teacher, I can't seem to find the "Discover" you mention. As for Dragonfly's response, I am always leery of removing entire blocks of files with a wildcard.

I removed all but one of the repositories listed in my Software & Updates application and have limited success with just that one. I'm wondering if somehow my DNS cache may have been somehow corrupted. But, if that were the case, then websites and the like would become not found as well. I'll keep at it.

Bill

---

### Post by SeijiSensei on 2019-11-19
Discover is the name of the application used to update software on KDE.

From the "K" menu, choose Applications > System > Software Center.

---

### Post by WB0HYQ on 2019-11-20
Oh. I know about the Ubuntu Software Center. I use it to find applications I might use. Don't see anything like the Sources or Software Sources though.

For system updates, I've been using Settings -> Software & Updates. The one with the tabs across the top like Ubuntu Software, Other Software, Updates, Authentication, Additional Drivers, Developer Options and Livepatch. Is there another Discovery thing out there that allows me to do the choosing you mention?

The only check boxes on the "Ubuntu Software" tab that allows me to update the system without the error is "Canonical-supported free and open-source software (main) AND Community-maintained free and open source software. (universal). If I check any of the other boxes, the update will fail with the dumb "check your connection" error. I can't check ANY of the boxes on the "Other Software" tab or it will fail. On the "Updates" tab, I can check Important security updates (bionic-security) AND Recommended updates (bionic-updates). There are 18 trusted software providers under the "Authentication" tab. "Additional Drivers" always tells me there aren't any available.

I've found nothing like the PNG screenshot you linked to.

Bill

---

### Post by CatKiller on 2019-11-20
One thing that occurs to me is that you should check which mirror you're using. The software repositories are mirrored all over the world on a variety of machines; some from Canonical, some from donated time on shared machines. Almost all of those machines are going to be a long way away from you. If your internet is generally fine but updates are slow, that seems like a likely candidate.

You can set the mirror using the software-properties dialogue, which can be launched through Discover or Muon, and you've already found, or by editing your sources.list directly. Whichever you prefer. It all controls the same package management framework.

---

### Post by WB0HYQ on 2019-11-20
It's not that updates are slow, they are either at nearly the maximum speed allowed on my AT&T line (I normally download at around 2.5MBps) or I get the "your connection is broken" message. But, I only get that message for system updates, nothing else. I realize the "broken" message is completely wrong and should try to give me more information as to WHY it cannot download, but it doesn't.

I found Muon in the Software Center. I'll give it a try.

Bill

---

