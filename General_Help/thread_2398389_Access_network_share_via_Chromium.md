---
title: "Access network share via Chromium"
date: 2018-08-11
forum: General Help
---

### Post by Thomas_E._Haynes on 2018-08-11
Here is a puzzling problem.

I have 18.04 installed. From Firefox I can download and upload pictures from a network share. So this would be something like moving pictures to and from Google Photos. 

From Chromium I can't. It does not see the share. The share is a computer on the network running 16.04 LTS.

Additional data - I have a Debian Sid installation on the same computer that does this with no problem via Firefox and Chromium. Previous versions of Ubuntu did not have issues with this. I would be tempted to call this a Chromium issue and try to resolve it there, but it only seems to be a problem with this particular version of Ubuntu.

Anyone have any ideas?

---

### Post by TheFu on 2018-08-11
Is it a snap? [https://discourse.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987](https://discourse.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987)

Snaps provide additional security by preventing undesirable behaviors,  I'm guessing, and it is only a guess, that this undesirable behavior is something you would prefer remain?

---

### Post by Thomas_E._Haynes on 2018-08-12
> **TheFu said:**
> Is it a snap? [https://discourse.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987](https://discourse.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987)

Snaps provide additional security by preventing undesirable behaviors,  I'm guessing, and it is only a guess, that this undesirable behavior is something you would prefer remain?

I would prefer to be able to upload from and download to the share from Chromium.

---

### Post by TheFu on 2018-08-12
> **Thomas_E._Haynes said:**
> I would prefer to be able to upload from and download to the share from Chromium.

Is it a snap?

I asked that question because I'm guessing at the problem. If you don't answer, then we are done.

---

### Post by Thomas_E._Haynes on 2018-08-12
$ snap list
Name                  Version       Rev   Tracking  Publisher  Notes
chromium              68.0.3440.84  396   stable    canonical  -
core                  16-2.34.3     5145  stable    canonical  core
gnome-3-26-1604       3.26.0        70    stable/&#8230;  canonical  -
gnome-calculator      3.28.2        180   stable/&#8230;  canonical  -
gnome-characters      3.28.2        103   stable/&#8230;  canonical  -
gnome-logs            3.28.2        37    stable/&#8230;  canonical  -
gnome-system-monitor  3.28.2        51    stable/&#8230;  canonical  -


Yes - it is a snap.

---

### Post by TheFu on 2018-08-12
If my guess is correct, it is the "snap" which is causing the problem.  Remove the snap chromium and install a non-snap version. See if that fixes the issue.

And if it does, please open a bug with the snap version in the Ubuntu bug system so the snap team learns about it.

---

### Post by Thomas_E._Haynes on 2018-08-13
That seems to have fixed it. I appreciate the help. I was totally unfamiliar with the snap.

---

### Post by TheFu on 2018-08-13
> **Thomas_E._Haynes said:**
> That seems to have fixed it. I appreciate the help. I was totally unfamiliar with the snap.

It was a lucky guess on my part.  If it is solved, please mark this thread as solved (thread tools near the top). This helps others in the community looking for solutions AND people trying to help solve issues.

I think snaps are a great idea, but because they fence-off programs and limit access to other parts of the system, some formerly-fine interactions won't be possible. 

I also think that Canonical pushed out something that wasn't ready too soon into an LTS. Bad idea. Snaps have been around over 2 yrs, but making them the default installation for commonly used tools was a bad idea.  My newest Ubuntu is 16.04 and I've removed all snaps and the snap tools from my systems to avoid them until I'm ready.

VLC is also pushed as a snap which seems to break DVD playback, BTW. Access to the external library needed to decrypt the DRM for DVDs isn't allowed under the snap.

If you want to put chromium into a similar, but integrated container, you can use **firejail**.  It is good to know the limits of what these containers provide. I have a few scripts to startup chromium with different options and firejail.
```

alias firechrome='firejail chromium-browser '
alias firepchrome='firejail --private chromium-browser '
```
The first one uses a profile shipped with firejail and allows access to ~/Download/ and a few other directories.
The 2nd one blocks all file system access to the browser. Nothing is left behind after the run.  Anything saved isn't accessible.
You can create a custom profile to allow access to specific location, while retaining most of the blocking. Just look at the /etc/firejail/ directory for examples.  I'd start by copying the chromium.profile into a new name.  The firejail manpage will explain more. It has many capabilities around network controls too.

---

