---
title: "can the individual snap folder be a soft link"
date: 2021-11-16
forum: General Help
---

### Post by lister171254 on 2021-11-16
Now that Canonocal makes firefox only available via snap, I have an issue with the following

I always had firefox and thunderbird in an encrypted folder with soft links from the home folder for ".mozilla" and ".thunderbird"

When I tried to do the same with the snap folder and then started firefox with "snap run firefox" I got an error that folder 701 could not be accessed

Is therea a supported way of having the snap folder somewhere other than home?

---

### Post by TheFu on 2021-11-17
Snaps cannot access anything that is outside the HOME and that HOME must be under /home/ to work.  This is hard-coded. Some think this is extremely short-sighted by the snap team. Inside ~/snap/ there are symlinks between different versions, btw.  There is a link to the "current snap to be used there. I suspect $HOME/snap/ is also hard coded.

Perhaps looking at this a different way would be useful?
If you encrypted the entire /home partition/LV, then that data would be unavailable to anyone when at rest (i.e. powered off).  That's the best that any encryption can accomplish.  When encrypted storage is mounted and accessible, it is the same as storage that was never encrypted.

---

### Post by lister171254 on 2021-11-17
Thanks for the explanation.

I'm sure Canonical thinks that snap is the best thing since sliced bread, but .....

I had a reason for not encrypting /home and things worked as expected until firefox was moved to snap.
Guess I'll be using the firefox download instad.

---

### Post by TheFu on 2021-11-17
There is probably a PPA which doesn't use snaps.
Or there is Linux Mint, which doesn't force snaps on their users, but is very similar to Ubuntu-Mate, but I think Mint only builds off Ubuntu LTS releases - don't quote me on that.

There are a few snaps which seem to do exactly as the snap goals outline. They work great!  And then there are others ...

---

### Post by lister171254 on 2021-11-17
Happy to just download from mozilla.

I guess one gripe is that something as important as Firefox should not have been moved automatically to snap.

---

### Post by TheFu on 2021-11-17
They moved Chromium in 19.10 which broke some of my workflows and protections. My solution was to run 18.04 in a VM and use it for running chromium without the snap.  This lets me control the security surrounding that browser.

With firefox, I also have a sandboxing tool to provide extra security with a few scripts that run it for trusted locations or not-so-trusted locations. Both can run concurrently, which is nice.  Never trust the "incognito mode" in a browser.  Use it as necessary, but don't trust it. Take outside steps. My sandbox script also limits the amount of resources that Firefox and Thunderbird can see/access, so the bloat can't get too large and appear to use 40G of RAM when it is only using 3G in reality.  There's something wrong with the memory use in firefox and thunderbird that I have to assume comes from the cross platform framework they built.  Other browsers don't behave that way. Anyway, by using cgroups ( which is how Linux Containers and snaps work), we can limit the access for different applications.

Today, I've been fighting to get a videoeditor working. I know which one can do what I need - it used to work, but I can't use the snap version because video files aren't stored on the same partition as /home/ or under /media anywhere.  There's more than 40TB of storage and our workflow places those files elsewhere and they use NFS.  I've read that NFS is finally supported by snaps, but they still don't like data outside /home/.  I actually had to violate our HOME directory policy to get my home moved to be under /home just for snaps to have any chance of working.  

It shouldn't be this hard.

Software is supposed to make life easier.

---

