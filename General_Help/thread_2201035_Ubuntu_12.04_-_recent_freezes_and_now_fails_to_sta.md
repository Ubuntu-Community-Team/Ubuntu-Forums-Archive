---
title: "Ubuntu 12.04 - recent freezes and now fails to start"
date: 2014-01-22
forum: General Help
---

### Post by rawlins02 on 2014-01-22
Been having issues lately with windows freezing (window dims). Several hard shotdowns needed past couple days. 12.04 worked flawlessly for about one year. Dell Studio XPS 1645. Other details in my signature.

Now the machine will not start. It gets to the purple screen that says Ubuntu with 5 dots that go from white to red. Won't go further.

The error I saw just before I did a hard shutdown said something about "Ubuntu has experienced an internal error". When I clicked details, the message referenced: 

```

/usr/bin/do-release-upgrade

```

Now, restart not happening. This is a work machine, so a rapid repair is needed.

---

### Post by rawlins02 on 2014-01-22
I got the machine to start. Booted to recovery mode and selected proceed with normal start (or words to that effect). Messages during startup indicated:

```

/dev/sda7: UNEXPECTED INCONSISTENCY
run fsck manually
mountall; fsck  /usr [1095] terminated with status 4

```

I selected attempt to fix errors and I got to the login screen. Once loged in I noted that displays did not have the right resolutions, but using display manager I got them back to what I prefer.

I'll mark thread solved but will repost if the freezes persist.

---

### Post by TheFu on 2014-01-22
do-release-upgrade is just a note that there is a newer (not necessarily better) release available. IMHO, staying on 12.04 is the right thing for almost everyone for about 5-6 more months.

So the real question is what is failing during boot?  A few techniques that I would try are:
[LIST=1]
[*]check the system log files - looking for warnings and errors
[*]boot off a liveCD or USB flash drive to see if all the hardware works (this excludes the HDD, disk controller and SATA cable)
[/LIST]

The logs for boot might not be available.

When the machine appears to lock up, can you switch to a different console and login? This would be a non-GUI interface.
Or can you ssh into the machine from a different box and look for issues in the system logs?

The great thing about UNIX/Linux is the system log files. Anything important will be in there provided they are not overwritten.

---

### Post by TheFu on 2014-01-22
> **rawlins02 said:**
> I got the machine to start. Booted to recovery mode and selected proceed with normal start (or words to that effect). Messages during startup indicated:

```

/dev/sda7: UNEXPECTED INCONSISTENCY
run fsck manually
mountall; fsck  /usr [1095] terminated with status 4

```

I selected attempt to fix errors and I got to the login screen. Once loged in I noted that displays did not have the right resolutions, but using display manager I got them back to what I prefer.

I'll mark thread solved but will repost if the freezes persist.

Shutting down (meant to say **powering off**) a system is dangerous to open file systems.  If you haven't run fsck manually from a live-CD, then you still need to do that.  If there are any issues, start looking for disk-related hardware issues.  I'd also ensure my backups were 100% recoverable. This could be just a warning of bad things to come ... or it could be almost nothing.

There are other ways to run fsck, but it was much easier to have you run it from a liveCD boot. That prevents any of the "this or this or that or that" instructions.

---

### Post by rawlins02 on 2014-01-22
> **TheFu said:**
> Shutting down a system is dangerous to open file systems.  If you haven't run fsck manually from a live-CD, then you still need to do that.  If there are any issues, start looking for disk-related hardware issues.  I'd also ensure my backups were 100% recoverable. This could be just a warning of bad things to come ... or it could be almost nothing.

OK. Thanks for the suggestion. I will do fsck manually from live-CD. I've noted no problem behavior over past several hours, so hopefully all is well. Yes I regularly backup /home.

---

