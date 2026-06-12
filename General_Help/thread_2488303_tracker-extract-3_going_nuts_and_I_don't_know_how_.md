---
title: "tracker-extract-3 going nuts and I don't know how to turn it off"
date: 2023-06-30
forum: General Help
---

### Post by Paddy Landau on 2023-06-30
Out of the blue, my CPU is going nuts with 100% usage (one core at a time).

The offending app is tracker-extract-3.

Looking this up, it appears to be a Gnome package run by tracker3. The advice is to turn off Search in Ubuntu.

I have gone to Settings > Search > turn it off, and then restarted the computer. But this hasn't helped; as soon as I log in, tracker-extract-3 gets going again.

How can I stop this, please? My fans are going to wear out!

---

### Post by deadflowr on 2023-06-30
Try masking the systemd services they use
from here: [https://www.linuxuprising.com/2019/07/how-to-completely-disable-tracker.html](https://www.linuxuprising.com/2019/07/how-to-completely-disable-tracker.html)
```
systemctl --user mask tracker-extract-3.service tracker-miner-fs-3.service tracker-miner-rss-3.service tracker-writeback-3.service tracker-xdg-portal-3.service tracker-miner-fs-control-3.service

```

---

### Post by Rubi1200 on 2023-06-30
A quick Google search shows you are not the only one reporting high/very high CPU or RAM usage from this service.

However, since a lot of things rely on it, removing seems not to be the best idea.

In this article, the author suggests a way to mask (disable) the service:
[https://www.linuxuprising.com/2019/07/how-to-completely-disable-tracker.html](https://www.linuxuprising.com/2019/07/how-to-completely-disable-tracker.html)

I have not tried this, so proceed with caution.

Hope this helps.

Edit: oops, while I was searching deadflowr already offered the solution.

---

### Post by Paddy Landau on 2023-07-01
Thank you. I ran:
```
tracker3 status
```
While the processes are running, this just hangs. After killing the processes, it claims, "Estimated less than one second left". But of course when I restart the machine, it just runs continuously again.

I couldn't find a bug report for Ubuntu, so I submitted [this one]("https://bugs.launchpad.net/ubuntu/+source/tracker-miners/+bug/2025523").

I've disabled tracker3 with systemctl as recommended, thank you for that.

Once the bug has been fixed, how do I re-enable it? I don't know the systemctl command, and I'd be loth to experiment.

---

### Post by MAFoElffen on 2023-07-01
Since you 'sudo systemctl mask xxx' to mask those, you would run the same except replace mask with unmask... Like this
```

systemctl --user unmask tracker-extract-3.service tracker-miner-fs-3.service tracker-miner-rss-3.service tracker-writeback-3.service tracker-xdg-portal-3.service tracker-miner-fs-control-3.service

```
What you did left the service files in /lib/systemd/system/, and removes the symlinks to them from /etc/systemd/system/ so nothing can act upon them. The command I posted above, tells systemd to create those symlinks again, to point back to the service files.

After doing that, then do
```

[s]sudo tracker3 reset -s -r[/s]
sudo systemctl daemon-reload

```
That last line will reload the systemd daemons without having to reboot.

---

### Post by Paddy Landau on 2023-07-01
> **MAFoElffen said:**
> Since you 'sudo systemctl mask xxx' to mask those, you would run the same except replace mask with unmask...
Thank you. I've made a note of that.

On another note, after I ran systemctl mask, I *didn't* run the command:
```
sudo tracker3 reset -s -r
```
Will that be problem? Is it important that I run that command?

Thank you

---

### Post by MAFoElffen on 2023-07-01
No... In fact, I looked at the man page for tracker3-reset, and edited my post...

The man page says that reset with those options does these
```

       -s, --filesystem
           Removes data stored by tracker-miner-fs(1). The miner will automatically recreate its
           cache from the filesystem when it restarts.

       -r, --rss
           Removes data stored by tracker-miner-rss(1).

```
Not running command that will leave the cache there. Since you are hoping to have it running again, there should be no problem with leaving it there... Although, if you did clear it, it says if it is flushed, once it starts again, it rebuilds the cache on it's own. So it looks like you are good either way.

---

### Post by Paddy Landau on 2023-07-01
> **MAFoElffen said:**
> No … So it looks like you are good either way.
That's great, thank you. I suspected as much, but as I know little about it, I needed to be sure!

---

### Post by angusk on 2023-12-01
In the last week or so (November 2023) tracker-miner-fs has had such an impact on my system performance and usability that I have uninstalled nautilus and hence tracker. I've been using Ubuntu for years and the last week or so it has become so painful to use that I've opted for another file manager (for the moment thunar). Rather than going through all the machinations of what might or might not work in my environment I've decided this is the best option for me. If there was (a) a foolproof way to reduce the performance impact of tracker and/or (b) an explanation why the performance impact has skyrocketed (hint: who changed what?) I'd swap back but for the moment out of frustration I'll avoid nautilus/tracker

---

### Post by Paddy Landau on 2023-12-01
> **angusk said:**
> &#8230; I have uninstalled nautilus and hence tracker.
You don't have to uninstall anything. The solution was given by deadflowr in [comment #2]("https://ubuntuforums.org/showthread.php?t=2488303&p=14148821&viewfull=1#post14148821"). Reinstall Nautilus, if that's what you want, and then disable tracker3 as follows.

**Step 1**
```
systemctl --user mask tracker-extract-3.service tracker-miner-fs-3.service tracker-miner-rss-3.service tracker-writeback-3.service tracker-xdg-portal-3.service tracker-miner-fs-control-3.service
```

**Step 2**
This step is optional, and you should skip it if you intend to use tracker3 again in future.
```
tracker3 reset --filesystem --rss
```

**Step 3**
Reboot.

As this bug affects you, please [vote for it]("https://bugs.launchpad.net/ubuntu/+source/tracker-miners/+bug/2025523") (sign in and select the green writing on the left near the top).

---

### Post by angusk on 2023-12-01
Paddy

Thank you for pointing me in the right direction. It was late last night and when uninstalling nautilus and tracker also uninstalled ubuntu-desktop :-) So had to reinstall it all. I've done (your) Step 2 and so far so good. 

As for tracker. I assume it performs some useful function, but perhaps a case of the tail wagging the dog. When I could get to see/run System Monitor I see/saw that it pretty well gobbles up all available memory making it impossible to do anything else. Perhaps if there was some way to limit its resource usage it would be more useful.

Once again, thank you

Angus

---

### Post by Paddy Landau on 2023-12-02
> **angusk said:**
> &#8230; when uninstalling nautilus and tracker also uninstalled ubuntu-desktop
I was wondering how you uninstalled Nautilus without uninstalling ubuntu-desktop! I'm glad that you managed to fix it.
> **angusk said:**
> As for tracker. I assume it performs some useful function
It does. When it works, it allows for rapid search of files in your system, including contents.
> **angusk said:**
> When I could get to see/run System Monitor I see/saw that it pretty well gobbles up all available memory making it impossible to do anything else.
In my case, it was CPU, not memory.

Hence the bug report; this is definitely a bug and not valid behaviour. Until the bug is fixed, we can't use tracker3.

EDIT: See [this page]("https://www.linuxuprising.com/2019/07/how-to-completely-disable-tracker.html") for information about the use of tracker.

---

### Post by dragonfly41 on 2023-12-02
Learning about role (and apparently impact) of tracker by reading this thread I found other tips here ..

[https://stackoverflow.com/questions/72827703/how-to-disable-file-indexing-in-ubuntu-22-04-tracker3](https://stackoverflow.com/questions/72827703/how-to-disable-file-indexing-in-ubuntu-22-04-tracker3)

But I use ripgrepall to search content of files.

---

### Post by Paddy Landau on 2023-12-02
> **dragonfly41 said:**
> Learning about role (and apparently impact) of tracker by reading this thread I found other tips here ..

[https://stackoverflow.com/questions/72827703/how-to-disable-file-indexing-in-ubuntu-22-04-tracker3](https://stackoverflow.com/questions/72827703/how-to-disable-file-indexing-in-ubuntu-22-04-tracker3)

But I use ripgrepall to search content of files.
Thank you. I fortunately didn't have a problem with disabling tracker, but maybe someone else does, and will see your comment.

I've installed ripgrepall on my system and forgotten ever to use it!

---

### Post by dragonfly41 on 2023-12-02
Note: Some of the tips address the mid option of keeping tracker .. but limiting its scope.

---

### Post by Paddy Landau on 2023-12-02
> **dragonfly41 said:**
> Note: Some of the tips address the mid option of keeping tracker .. but limiting its scope.
Thanks. I seem to be doing OK with it completely disabled, so I'll stick to that for now. With luck, the problem will be solved by 24.04, but I'm not holding my breath, because this problem has been around for a long time!

---

### Post by somshell on 2024-05-13
Ubuntu 24 has the same issue. In my case however a couple of weeks after installing ubuntu 24 the CPU started to stabilize. It wobbles about 80% for some 15 minutes after booting and then all cores flatline to some 10%. I guess waiting it out may be an option for some people (beginners like me) who don't want to meddle with the system.

---

### Post by Paddy Landau on 2024-05-13
> **somshell said:**
> I guess waiting it out may be an option…
The thing is that I tried it, but it just kept on going, and eventually I turned it off because my computer was getting too hot and the fans were blasting away!

The bug needs to be fixed.

Please vote for [the bug]("https://bugs.launchpad.net/ubuntu/+source/tracker-miners/+bug/2025523") (log in and select the green writing near the top left).

---

### Post by vanadium on 2024-05-16
I do not want to have Tracker running, so I disable it already several years this way. The result is a super light system that never starts to hog your processor and strains your drive on your back unless you cause it to.

Basic functionality remains: you still can search files by file name, the "starred files" feature works also without tracker running since Files version 46. If you turn "Application Search" on, various apps like clock, characters, settings, software, … continue to display results in the Application overview.

Disabled functionality: full name search in Files, Starred files (prior to version 46), any results of files in the Application Overview. In addition, some Gnome applications like Photos cannot work.

---

