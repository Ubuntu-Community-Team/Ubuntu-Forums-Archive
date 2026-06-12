---
title: "[SOLVED] Firefox bit the dust"
date: 2008-06-25
forum: General Help
---

### Post by Mako Eyes on 2008-06-25
I can't really pinpoint when this problem ocurred, but I didn't notice it until I performed a system update this morning. Firefox will not start anymore and when I try to start in Terminal I get this message:

```
$ firefox
/usr/lib/firefox-3.0/firefox: error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory

```

I'm stuck using Epiphany for now, and it thankfully gets the job done very nicely. I'd still like Firefox back though...

Any thoughts? Thanks for your help.

---

### Post by jualin on 2008-06-25
Ok go to the terminal and try reinstalling firefox. > sudo apt-get purge firefox
sudo apt-get install firefox Or if you prefer do it my the Synaptic Package Manager, choosing "Complete Removal" and then just install it again. Hope this works.

---

### Post by Zorael on 2008-06-25
Try this.
```
$ sudo ln -s /usr/lib/xulrunner-1.9/libjemalloc.so /usr/lib/libjemalloc.so
```

---

### Post by nightwolf2k5 on 2008-06-25
if u din't have some important bookmarks, you could 
goto places -> home folder
press cntrl h
goto .mozilla
goto firefox
delete the xxxxx.default and profiles.ini folder and file. (Dont worry, these files get created again once firefox is started)
Start firefox now...

Wild guess it could be cuz of corrupted files..

---

### Post by Mako Eyes on 2008-06-25
Well, I didn't really try any of your methods yet... For some reason, I didn't even have to. As soon as I got the email notification for the first response, I clicked the notification (out of habit) and it opened Firefox just fine. Now it works without a hitch.

I have no idea what happened or how it "repaired itself," but I'm glad it's back. I'll mark this thread as solved and bookmark it in case this is just a fluke.

Thanks!

---

### Post by avtolle on 2008-06-25
Hazarding a guess here, you had FF open during the upgrade (which can cause problems). By shutting it down, using Epiphany, and then reopening FF, this took care of the problem. When the update notifier says there is a FF update, I close FF down and have never had a problem.

---

