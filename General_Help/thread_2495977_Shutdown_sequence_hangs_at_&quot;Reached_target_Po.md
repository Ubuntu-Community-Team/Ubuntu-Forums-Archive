---
title: "Shutdown sequence hangs at &quot;Reached target Power-Off.&quot;"
date: 2024-03-10
forum: General Help
---

### Post by johsal on 2024-03-10
I boot two different versions of Xubuntu by ISO, 16 (Xenial) & 20 (Fossa).

Xenial shuts down normally. Fossa hangs at the title quote you can also see in the photo:

At that point I power-off with the power button. Am I missing a trick for Fossa shut down?

---

### Post by johsal on 2024-04-04
UPDATE: I am getting the error on a different machine, Xubuntu Fossa (20) won't shut down.

I have noticed a difference: If I boot the os on a USB, it shuts down. If I boot exactly the same on different media (internal HD), shutdown hangs. 

Can this be fixed or reported as a bug?

---

### Post by johsal on 2024-04-09
[SIZE=3]Ubuntu 16 by USB thumbdrive[/SIZE]
*[SIZE=3]normal shutdown[/SIZE]*
[SIZE=3]
[/SIZE]
[SIZE=3]Ubuntu 20 by USB thumbdrive[/SIZE]
*[SIZE=3]normal shutdown[/SIZE]*
[SIZE=3]
[/SIZE]
[SIZE=3]Ubuntu 16 by internal HD[/SIZE]
*[SIZE=3]normal shutdown[/SIZE]*
[SIZE=3]
[/SIZE]
[SIZE=3]Ubuntu 20 by internal HD[/SIZE]
**[SIZE=3]shutdown hangs[/SIZE]**
[SIZE=3]
[/SIZE]
[SIZE=3]very mysterious![/SIZE]

---

### Post by johsal on 2024-04-15
[SIZE=3][SIZE=5]more Xubuntu testing:[/SIZE]

Jammy Jellyfish (22) by USB HD[/SIZE]
**[SIZE=3]shutdown hangs[/SIZE]**[SIZE=3]

Bionic Beaver (18) by USB HD[/SIZE]
*[SIZE=3]normal shutdown[/SIZE]*
[SIZE=3]
Fossa Focal (20) is *only* shutting down by USB FLASH (thumbdrive). It is *not* shutting down by internal HD *or* USB HD.

Fossa begins to boot by extracted .iso (live), hanging 'Unable to find a medium container a live file system'. That was an experiment to see if I can shutdown live Fossa on disk. 

Fossa is most important, still stuck booting it USB FLASH.


[/SIZE]

---

### Post by johsal on 2024-04-15
[SIZE=3]commensurately succinct:

Beginning at Xubuntu Fossa a LIVE boot *only* shuts down on a thumbdrive.[/SIZE]

---

### Post by MAFoElffen on 2024-04-15
Have you filed a Bug Report at Launchpad.net with your PC hardware information and the ISO release information? Please provide the link to that here.

That would be a start for that kind of error.

I am curious as to why your concentration is on installing Focal 20.04 LTS, which only has a year of support left(?) Especially when 24.04 LTS releases in about a week... If required for something, you might want to mention that in your Bug Report.

---

### Post by #&amp;thj^% on 2024-04-15
To help aide with that report, On your next shutdown or reboot run **"sudo systemctl start debug-shell**", then shut down/reboot, and when it hangs do "**Ctrl+Alt+F9**" look at "**systemctl list-jobs**" (hanging jobs), or "dmesg" if you see any hanging jobs/errors there? Do you get some meaningful errors at the end of "journalctl"? 

The ideal message of course would be 
```
 systemctl list-jobs
No jobs running.

```

Dang I forgot this one, if anything meaningful shows:
```
last -x | grep shutdown | less
```

---

### Post by him610 on 2024-04-15
> shutdown hangs
How long (mm:ss) does it hang?

There are hidden processes that take about 01:30 to close down. 
If you press F3 during the hang, you may see on the screen which process is hanging.

---

### Post by johsal on 2024-04-17
> **MAFoElffen said:**
> Have you filed a Bug Report at Launchpad.net with your PC hardware information and the ISO release information? 

Launchpad.net reporting is what I need to read. Thanks I will check that out.

> 
I am curious as to why your concentration is on installing Focal 20.04 LTS, which only has a year of support left(?) 

I encourage people who want to adopt new releases & test new, but for a user like myself it is a troublesome burden.

The main reason I ever update is newer Chromium-based browsers. Xenial tops out at v106 without extra dependencies like GLIB. I think Bionic still runs current, but I prefer Fossa for customization compatibility, ie, the work I have already done to make it an OS I can use.

I am in Xubuntu Bionic at the moment purely because I need a current browser & know it will shut down. Fossa won't.

---

### Post by johsal on 2024-04-17
> **him610 said:**
> How long (mm:ss) does it hang?

There are hidden processes that take about 01:30 to close down.
If you press F3 during the hang, you may see on the screen which process is hanging.

I wrote a thoughtful response to this lost on auto-logout refresh.  briefly:

infinite hang
Normal shutdown is speedy.
I will try F3.

---

### Post by johsal on 2024-04-17
Another technique to try thanks.

I will report any new revelations.

> **1fallen said:**
> To help aide with that report, On your next shutdown or reboot run **"sudo systemctl start debug-shell**", then shut down/reboot, and when it hangs do "**Ctrl+Alt+F9**" look at "**systemctl list-jobs**" (hanging jobs), or "dmesg" if you see any hanging jobs/errors there? Do you get some meaningful errors at the end of "journalctl"? 

The ideal message of course would be 
```
 systemctl list-jobs
No jobs running.

```

Dang I forgot this one, if anything meaningful shows:
```
last -x | grep shutdown | less
```

---

