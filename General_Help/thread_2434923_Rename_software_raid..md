---
title: "Rename software raid."
date: 2020-01-13
forum: General Help
---

### Post by Weidbrewer on 2020-01-13
Let me preface this by saying that I have no idea how this happened, and terminal did not retain the command, so I wasn't able to go back and see if I'd made a typo.  Over the weekend, I was setting up a software RAID on a machine, left it to do its thing and went off to do some weekend chores.  I came back later and saw that my kid must have flipped the power strip off.  I have no idea if it happened while the RAID was creating or not, but upon rebooting, the RAID was successfully created and working...but the name of it was WAY off.

Assuming there were no typos, I created it with:

```
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-device=2 /dev/sda /dev/sdb
```

...but somehow - I and I have no idea how - it created the RAID as "/dev/md/[name of computer]:0"

How would I go about renaming it what it *should* be (md0)?

Again, it works and I was able to mount it where I wanted and everything...I just don't want to have to deal with typing out that clumsy name any time I need to do some sort of maintenance on it.

---

