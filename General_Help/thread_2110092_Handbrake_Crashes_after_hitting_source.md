---
title: "Handbrake Crashes after hitting source"
date: 2013-01-29
forum: General Help
---

### Post by jlabomb on 2013-01-29
I use handbrake to rip DVD's for my Plex Media Server. All of a sudden Handbrake is crashing when I hit the source  button or when I click on File source. I can select a DVD from file and choose the device but I can not convert other files. When I hit source the window comes up and says ghb and then both windows close with no error. It was working last week. What can I do to troubleshoot this issue? Thanks.

---

### Post by SeijiSensei on 2013-01-29
First, if you're not using Handbrake from [John Stebbins PPA]("https://launchpad.net/~stebbins/+archive/handbrake-releases"), I suggest you make the switch:

```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake

```

See if that fixes the problem.

If you are using the handbrake-releases repository, maybe you encountered a bug that is fixed in the version available in [handbrake-snapshots]("https://launchpad.net/~stebbins/+archive/handbrake-snapshots").

---

### Post by JohnAStebbins on 2013-01-29
Or maybe you are using the snapshots on ubuntu 12.10 and encountered a problem with the gtk3 port I just did.  

But we are all just guessing since you provided no information about what HandBrake version you are using or what ubuntu version you are using.

---

### Post by ravensqu on 2013-01-29
I have just encountered this same error. Handbrake was working just fine for me but after going into the handbrake preferences, I can no longer open any sources through the source button. I can still access and use handbrake through the auto-run on a dvd.

The only thing I changed in the handbrake settings before I noticed this problem was I unchecked and checked the "Use automatic naming" option. After rechecking this though, I would assume everything would work again. Any help to solve this problem would be great.

I am running Ubuntu 12.04.1 LTS with the current handbrake from the handbrake-snapshots ppa.

---

### Post by JohnAStebbins on 2013-01-30
> **ravensqu said:**
> I have just encountered this same error. Handbrake was working just fine for me but after going into the handbrake preferences, I can no longer open any sources through the source button. I can still access and use handbrake through the auto-run on a dvd.

The only thing I changed in the handbrake settings before I noticed this problem was I unchecked and checked the "Use automatic naming" option. After rechecking this though, I would assume everything would work again. Any help to solve this problem would be great.

I am running Ubuntu 12.04.1 LTS with the current handbrake from the handbrake-snapshots ppa.

Could you make a backup copy of the file "~/.config/ghb/preferences" then delete the file and restart HandBrake?  If that "solves" the problem, could you post the preferences file here so I can have a closer look?

---

### Post by jlabomb on 2013-01-31
Thanks that fixed it. Here is the old preferences file. I also am running 12.04 and the latest handbrake-snapshots ppa. Thanks again.

---

### Post by JohnAStebbins on 2013-02-01
> **jlabomb said:**
> Thanks that fixed it. Here is the old preferences file. I also am running 12.04 and the latest handbrake-snapshots ppa. Thanks again.

Perfect! I am now able to reproduce the problem and can work on a more general fix. Thanks.

---

### Post by JohnAStebbins on 2013-02-01
> **JohnAStebbins said:**
> Perfect! I am now able to reproduce the problem and can work on a more general fix. Thanks.

This problem is fixed now and the fix should be available in the next (snapshots) nightly build.

---

