---
title: "Make Hibernate/Resume faster!"
date: 2007-11-08
forum: General Help
---

### Post by EtherBunny on 2007-11-08
While I don't expect Linux to have as good hibernate and resume as Windows, I do expect it to be reasonably close.

On my laptop, under Ubuntu Gutsy, hibernation takes about 15 seconds and resuming takes about 30-35 seconds.

On the same laptop, under windows Vista the thing hibernates in about 10 seconds and resumes in about** 8 seconds!!!**

This is really the only fault in Ubuntu that actually bothers me. 35 seconds vs 8 seconds is the difference between waiting for my laptop to start up and having my laptop powered up and good to go when I need it.

I'll even be willing to look past all the glitches and bugs that happen when you resume under Linux. I just want the speed, that's all.

---

### Post by MCMcButtah on 2007-11-08
I have a toshiba U305 and even with the gutsy release suspend didn't work. So I upgraded to the 2.6.23 kernel and hibernation/suspend works great now. It takes about 2-3 seconds to suspend and unsuspend...it seems almost instant actually...maybe even a tad faster than vista did. I read allot of work went into suspend issues with 2.6.23 which is why I tried it. The only problem I have is sometimes when the laptop comes out of suspend my wireless card is no longer there requiring a reboot. I suppose there probably is a modprobe i can do or something like that but I have been too lazy to google it.

---

### Post by EtherBunny on 2007-11-09
Suspend works in about 2 seconds for me too, but it's not the same thing as hibernate.

Vista just floored me with the amazing speed at which it was able to resume from hibernation and I would really like Linux to, if not match it, at least come close.

Vista : 8 seconds on average
Ubuntu: 35 seconds on average

There's got to be SOMETHING I can do to make it resume faster..

---

### Post by EtherBunny on 2007-11-09
anyone?

---

### Post by EtherBunny on 2007-11-09
please?

---

### Post by EtherBunny on 2007-11-09
let's see how many times I can bump this before someone replies and/or complains.

---

### Post by ppl on 2007-11-09
It is not even working on my laptop! I mean when it resumed, I always end up lost my Wifi connection and I need it always on! Ubuntu is my main OS, but I really miss Windoz on this point. Well, maybe I am lazy to set it up, but everthing else work out of box!

---

### Post by reacocard on 2007-11-09
there's a couple of alternative hibernate methods, namely tuxonice (formerly suspend2) and uswsusp. uswsusp is in the repos, and there are guides on the forum to configuring it to work nicely with the ubuntu tools, but in my experience it is less reliable than the built-in hibernate. tuxonice on the other hand works great, very fast and reliable suspend and resume (and optionally a pretty progressbar!), but it's very difficult to enable in ubuntu, as it requires patching the kernel.

---

### Post by reacocard on 2007-11-09
> **ppl said:**
> It is not even working on my laptop! I mean when it resumed, I always end up lost my Wifi connection and I need it always on! Ubuntu is my main OS, but I really miss Windoz on this point. Well, maybe I am lazy to set it up, but everthing else work out of box!

that happens to me sometimes too. my solution? add scripts under /etc/acpi/suspend.d and resume.d to stop and start network manager before and after resume.

---

### Post by EtherBunny on 2007-11-09
Thanks for the tips! I'll try the alternatives.

---

### Post by ppl on 2007-11-09
> **reacocard said:**
> that happens to me sometimes too. my solution? add scripts under /etc/acpi/suspend.d and resume.d to stop and start network manager before and after resume.
Thank for the info, I will try it out, after exam, well maybe after upgrade to Gutsy.

---

### Post by ResumeMan on 2007-11-29
So I've created the scripts where this thread suggested, as described in [this post]("http://ubuntuforums.org/showthread.php?t=626252"). And it doesn't seem like the scripts are even getting run when I resume using s2ram.

Any ideas what may be happening??

---

### Post by reacocard on 2007-11-29
> **ResumeMan said:**
> So I've created the scripts where this thread suggested, as described in [this post]("http://ubuntuforums.org/showthread.php?t=626252"). And it doesn't seem like the scripts are even getting run when I resume using s2ram.

Any ideas what may be happening??

did you make sure that they are executable, and that you are suspending via acpi?

---

### Post by ResumeMan on 2007-11-29
The answer to your first question is, yes I did. The answer to your second question is...I dunno. Is the acpi the default, Ubuntu suspend? Is that then to say that s2ram is NOT using acpi?

I had a feeling that that might be the case. If so, then how DO I direct s2ram to shut down and re-mount my shares??

---

### Post by reacocard on 2007-11-29
> **ResumeMan said:**
> The answer to your first question is, yes I did. The answer to your second question is...I dunno. Is the acpi the default, Ubuntu suspend? Is that then to say that s2ram is NOT using acpi?

I had a feeling that that might be the case. If so, then how DO I direct s2ram to shut down and re-mount my shares??

s2ram does not use acpi, s2ram is a *direct* call to the suspend mechanism. the best way to use s2ram in this case would be to change your /etc/acpi/sleep.sh file so that it uses s2ram instead of it's default. that can done by changing this line

```
echo -n $ACPI_SLEEP_MODE >/sys/power/state
```

to this

```
s2ram
```

then the normal ubuntu suspend command will trigger s2ram for sleep instead of its usual acpi method, but it will still run all your acpi scripts.

---

### Post by ResumeMan on 2007-11-29
OK thanks for that info.

Pardon me as I ask you to continue my education :)

Currently, per [this thread]("http://ubuntuforums.org/showthread.php?t=471855"), I have the file /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux with the contents:

```
#!/bin/sh

/sbin/s2ram --force 
```


Can you tell me how these two approaches differ? And will your approach either call the /etc/acpi/suspend.d scripts or avoid the breaking of the shares in the first place? Or is there another workaround?

Thanks!

---

### Post by reacocard on 2007-11-30
> **ResumeMan said:**
> OK thanks for that info.

Pardon me as I ask you to continue my education :)

Currently, per [this thread]("http://ubuntuforums.org/showthread.php?t=471855"), I have the file /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux with the contents:

```
#!/bin/sh

/sbin/s2ram --force 
```


Can you tell me how these two approaches differ? And will your approach either call the /etc/acpi/suspend.d scripts or avoid the breaking of the shares in the first place? Or is there another workaround?

Thanks!

ah that would be where the breakage is. if you have that modification, acpi is skipped entirely. revert to the old file and then make my modification to the acpi file. it has the same net effect, it just goes through the acpi scripts first, which is usually a good thing since they can help prevent problems and also allow customizations like your umount/mount.

of course probably the easiest, most flexible way to do things like unmount/mount/etc. with any sleep/hibernate method is via the hibernate script (package 'hibernate' in universe), but I see no reason to move to that if you already have most of this working. (if you want to try it anyway you'll have to revert the hal file)

---

### Post by ResumeMan on 2007-11-30
Hmmm...

Well, I changed my HAL files back to the originals, and I edited the sleep.sh file to replace the line you noted with s2ram -f, and what seems to have happened is the machine reverted to the old way of suspending -- which messes up the video (upon return various graphical features don't render right, and often don't show up at all till the cursor goes over them).

Any ideas what may have happened? Do I perhaps need to write add'l scripts to shut down and resume the video, or do you think that the replacing of the line in that script didn't actually call s2ram?

Perhaps I will try installing that Hibernate package, I didn't even know it existed...

Thanks again.

---

### Post by reacocard on 2007-11-30
> **ResumeMan said:**
> Hmmm...

Well, I changed my HAL files back to the originals, and I edited the sleep.sh file to replace the line you noted with s2ram -f, and what seems to have happened is the machine reverted to the old way of suspending -- which messes up the video (upon return various graphical features don't render right, and often don't show up at all till the cursor goes over them).

Any ideas what may have happened? Do I perhaps need to write add'l scripts to shut down and resume the video, or do you think that the replacing of the line in that script didn't actually call s2ram?

Perhaps I will try installing that Hibernate package, I didn't even know it existed...

Thanks again.

acpi is supposed to do that sort of thing automatically, maybe you have to set an option for it in /etc/default/acpi-support.

---

