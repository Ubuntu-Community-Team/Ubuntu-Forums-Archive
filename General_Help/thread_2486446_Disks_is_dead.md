---
title: "Disks is dead"
date: 2023-05-01
forum: General Help
---

### Post by stanfl on 2023-05-01
In Ubuntu 20.04, also previous versions, Disks does not respond.  When clicking the icon, it just gives me the timing icon for about a minute, which then disappears.  Nothing else happens.  I have the latest updates to this version, but it has been happening for many previous updates as well, I just never reported it.

---

### Post by deadflowr on 2023-05-01
Open a terminal and try
```
gnome-disks
```
Post the output.

---

### Post by MAFoElffen on 2023-05-01
Thinking about this...

I would post the output of
```

gnome-disks --display=$(w | grep -v 'USER\|users' | head -n 1 | awk '{print $3}')
ps -e | grep -i 'gnome-disks'

```
...just in case it is starting, but for some reason, not on the same display.

...because in the options of gnome-disks, it has the ability to start on other displays than just the current display.

---

### Post by stanfl on 2023-05-03
gnome-disks says timeout, waiting for udisks, or something to that effect.

---

### Post by MAFoElffen on 2023-05-03
Last time I have seen a timeout error on udisk was Ubuntu 16.04. There was a bug for it... It took that to get it resolved.

Please report this as a bug to Launchpad.
```

ubuntu-bug gnome-disks

```

---

### Post by aug7744 on 2023-05-04
The replies not means being an disk with problems.
Try run HDAT2 in machine startup. HDAT2 not run in OS.

---

### Post by ActionParsnip on 2023-05-04
Does gparted work OK? (May need installing)

---

### Post by MAFoElffen on 2023-05-04
I can see where my choice of wording for that might have been a bit confusing. Let me explain my last reply a little better... I'm not young, and have been around Ubuntu a while. I remember way too much.

On an error starting gnome-disks, when the error displays as "timeout error on udisk"... It's a deeper problem than just gnome-disks. udisks is an API to do things with disks and storage.

RE: [https://manpages.ubuntu.com/manpages/jammy/man8/udisks.8.html](https://manpages.ubuntu.com/manpages/jammy/man8/udisks.8.html)

This is the last time I have seen that error with those circumstances:
[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1575336](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1575336)

Which was on Ubuntu 16.04.

If it is a problem not being able to communicate with the udisks API, there is something deep under the covers wrong. Something we cannot diagnose here, without system traces and dumps that they would guide you through at launchpad.

But an afterthought, reinstalling gnome-disks may just fix the wiring between that(?) Just a guess with that.

But what do I know, right?

---

### Post by stanfl on 2023-05-09
Thanks to everyone for thinking about this.  I will follow the advice of MAFOFELFFEN, and report it as a bug.  I haven't reported a bug for many years, so this is surprising.

---

### Post by stanfl on 2023-05-09
Thanks for the advice MAFOELFFEN, but it failed.  I terminaled ubuntu-bug gnome-disks and it says "The problem cannot be reported: This report is about a package that is not installed.", but then when I terminal gnome-disks, it gives me a long wait and then the failure message GNOME-Disks-ERROR **" ...Error getting udisks client: Timeout was reached.

I don't know what to do next.

---

### Post by MAFoElffen on 2023-05-09
After doing an Ubuntu package search, the utility application gnome-disks comes from package gnome-disk-utility
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list gnome-disk* --installed
Listing... Done
gnome-disk-utility/jammy,now 42.0-1ubuntu1 amd64 [installed,automatic]

```
(Sorry. I should have done that first.)

Please report it against that package name.
```

ubuntu-bug gnome-disk-utility

```
--As an aside, I was wondering if reinstalling that package might help rewire what might be wrong? Something like
```

sudo apt install --reinstall gnome-disk-utility

```

---

### Post by stanfl on 2023-05-10
Curiosity.  I did a cold reboot and Disks came back to life.  I have done many reboots before, but always 'Restart', and that did not restore Disks.  This means my problem was probably with some variable overflow or other garbage-collecting failure, and so I am not able to address this bug, as it is probably more generic than just for Disks.  THANKS to all the people who took the time to advise me.  Now I know that cold reboots and warm reboots do not do exactly the same thing and if my Disks ever stops opening up again, I can get it back with a cold reboot.

---

### Post by MAFoElffen on 2023-05-10
LOL!!!

I went back to College to document my past Computer Science skills. There was a sign on the wall that said "#1. Did you tun off the computer, and turn it back on again?"

It seems so basic, but is often overlooked.

That was the answer to many questions, asked many times during many of their IT Courses.

So this is solved now? If so, please mark it as such so others may find your solution.

---

