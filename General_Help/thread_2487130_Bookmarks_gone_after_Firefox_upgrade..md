---
title: "Bookmarks gone after Firefox upgrade."
date: 2023-05-24
forum: General Help
---

### Post by bjngchn on 2023-05-24
(Newer computer died temporarily. ...be happy removed what bothers you all. )
...............................................................................................................................................................................................................................................
 Anyway, using an older computer now. Some web sites just don't work here, because browser is old (so what).
 It is not netscape. It is around 5 year old firefox.
  ....................................................................................................................................................................................................... 
So I had to Upgrade firefox, but only firefox, and found this command: 


 sudo apt install --only-upgrade firefox  

My laptop (kubuntu) told me, authenticity can't be checked (so, maybe not official) 
Ok, but then, why can sudo be used to install it..
 It must be in repo. Or if it is not, but an obviously fake one, then it should not be there. 
Can someone else, insert his fake/problematic firefox, and advertise it together with
 legitimate looking sudo command: if so this shouldn't be allowed.
..............................................................................................................................................................................
But I had to say Y (yes). So installed "upgraded" firefox this way.
Still not working because it is an old browser  according to some sites!!! despite fresh upgrade. 
Also  BOOKMARKS GONE. Where are they. Someome must have stolen them. 
How can this be an upgrade, if it is going down in some aspects.
(I believe  most such upgrades are done to attack privacy, steal data, 
or make stealing data more easy. Not talking about linux.  But we expect linux to be free of such stuff.)

---

### Post by bjngchn on 2023-05-24
So, basically asking, whether this is a legitimate command:


sudo apt install --only-upgrade firefox  

and how can I recover old bookmarks,
and also worrying about data theft, and backdoor creation.

---

### Post by Impavidus on 2023-05-25
The --only-upgrade means that apt should only install new versions of packages already installed, never install new packages, which could be required as dependencies. It's not what you intended. To upgrade only firefox, along with dependencies that must be upgraded too, you have to use```
sudo apt upgrade firefox
```
You write the Firefox on that system was about 5 years old. Assuming this is an Ubuntu system, that means that the Ubuntu system was over 5 years old too. That makes it an old, unsupported release. The repositories may have been removed, security certificates may have expired, and even if you point apt to the archived repositories on the old-releases server, it will have an outdated Firefox. Which release of Ubuntu is this?

Are you writing about the bookmarks stored on the old computer or those you had on the newer, broken computer? Those on the new computer won't be accessible from the old, unless you use some sort of online synchronisation service. In that case, the outdated Firefox may not be compatible with the latest form of the synchronisation service.

---

### Post by bjngchn on 2023-05-25
Ok  thanks, talking about old&working computer with older  firefox. only, 

I think bookmarks should have been preserved in any case.

---

### Post by Quarkrad on 2023-05-25
Have you got a hidden folder under /home/*yourusername* called .mozilla?

---

### Post by bjngchn on 2023-05-29
> **Quarkrad said:**
> Have you got a hidden folder under /home/*yourusername* called .mozilla?  Yes, what does it mean, what diffeence does it make?  ...................................................................................  Maybe I should unintall and reinstall firefox. Why, because it stops working for no reason, when internet is connected. And it is like, it disconnects internet also, sometimes..... ALso I prefer something which doesn't self-update.

---

### Post by SeijiSensei on 2023-05-29
Your entire Firefox configuration is stored in /home/username/.mozilla/firefox. There should be a directory with a recent date and a name made up of random characters. In that directory look for bookmarkbackups.

You need to come to grips with the fact that everything updates online these days. Do you ignore updates to your phone OS? Use Windows at any time (which takes many more times longer to update than Linux)? From other comments you've made, you seem to think that all of this is for some nefarious purpose rather than trying to deal with the ever-present issue of keeping systems up-to-date and thus more secure against recent threats.

---

### Post by bjngchn on 2023-05-29
Thanks,..I see some bookmarks there. Not all in one place. Or I don't know how to open   those files (except clicking on them).  I don't use smartphone. so no updates there. Looking for for smart (or stupid) phone with linux. Emails, videos, camera, phone, browser history,   face recognition, voice recognition, unremovable battery, closed source OS,  linkedin, fb, twittter, youtube, addressbook, shopping history, location history, all in one place. Very convenient !!!!

---

### Post by Impavidus on 2023-05-30
The snap version of Firefox stores the bookmarks somewhere else. I forgot where. When I switched from the snap version back to deb, I got my outdated bookmarks of 7 months ago, when I had switched from deb to snap. Before removing the snap version, I had exported the bookmarks, so I could simply import them in the deb version.

I'm somewhat surprised that you know or care about the bookmarks you had 5 years ago on that computer. My list of bookmarks changes on a much shorter timescale. But you aren't me.

That modern websites don't work with old versions of Firefox (because they need newer features) is the least of your problems. Old versions of Firefox are considered insecure. So are old versions of operating systems. You haven't mentioned what version of Ubuntu is on that old computer, as I asked in post #3.

BTW, I'm not particularly fond of smartphones either, but surviving in a western society without one has become rather hard.

---

### Post by SeijiSensei on 2023-05-31
Sorry. I always remove the snap version of Firefox and replace it with the version in the Mozilla repository.

If you're running the snap, everything should be under /home/username/snap/firefox.

Some of the directories are "hidden;" their names begin with a leading dot, like .config. At the command prompt you can see hidden files with the command "ls -a". From a GUI file manager, there should be an option to display hidden files.

---

### Post by poorguy on 2023-05-31
> **Impavidus said:**
> 
I'm somewhat surprised that you know or care about the bookmarks you had 5 years ago on that computer. My list of bookmarks changes on a much shorter timescale. But you aren't me.


I keep an inventory of bookmarks or web links in a folder I created using Libreoffice Writer and add to it when needed or remove from it when the links no longer work.

> **Impavidus said:**
> 
That modern websites don't work with old versions of Firefox (because they need newer features) is the least of your problems. Old versions of Firefox are considered insecure. So are old versions of operating systems. You haven't mentioned what version of Ubuntu is on that old computer, as I asked in post #3.


Without knowing any system specs of your computer there are plenty of small foot print low system resource Linux distros available that will work good on older computers.

> **Impavidus said:**
> 
BTW, I'm not particularly fond of smartphones either, but surviving in a western society without one has become rather hard.


I'm 71 years old and I'm not a big fan of change however as long as I'm still around in this world of changing technology I'm going to learn and adapt all I can as best as I can and not be stuck in the past.

---

