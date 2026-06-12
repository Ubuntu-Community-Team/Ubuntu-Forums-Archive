---
title: "(Solved}Snap Store No Longer Starts"
date: 2020-10-11
forum: General Help
---

### Post by exploder on 2020-10-11
Went to open the Snap Store this morning and it refuses to start. Anyone know what's going on?

Edit: Just tried it on another machine. It appears an update broke it.

---

### Post by deadflowr on 2020-10-11
> **exploder said:**
> Went to open the Snap Store this morning and it refuses to start. Anyone know what's going on?

Edit: JUst tried it on another machine. It appears an update broke it.

As long as you haven't removed old revisions you can revert back to an older version.
[https://snapcraft.io/docs/getting-started#heading--revert]("https://snapcraft.io/docs/getting-started#heading--revert")

---

### Post by exploder on 2020-10-11
Thanks! The apps themselves are fine, it's the Snap Store app itself that no longer works. It used to be Ubuntu Software or something like that. After the update it's now the Snap Store, even the icon was changed. The now, Snap Store refuses to launch on two machines...

---

### Post by deadflowr on 2020-10-11
Doesn't sound like it's fine if it doesn't work.
Snap store is a snap which is why I posted the howto for reverting to older versions.

Fwiw, you can launch snaps from a cli by run the snap run command
like
```
snap run snap-store
```
> It used to be Ubuntu Software or something like that
As far as I remember Ubuntu Software on 20.04 (and only on 20.04) used a specific snap-store version.
that version allowed installing deb packages from the normal repositories.
I haven't kept up with what changes have been made recently,
so not sure what may have changed.

I had removed it some time ago, but reinstalled to see if it ran and it did perfectly fine.
(Or at least snap-store ran fine)

(I normally use gnome-software (called Software in menu listings), because it handles flatpaks as well as snaps and deb packages.
Ubuntu Software/Snap store does not, or did not initially, handle those)

---

### Post by exploder on 2020-10-11
Thanks deadflower! I reverted the snap store to the previous version and it's working fine now.

---

### Post by deadflowr on 2020-10-12
I guess there's been an on going issue this weekend with it, see the discourse discussion here:
[https://discourse.ubuntu.com/t/is-ubuntu-software-going-to-be-remove-for-snap-snap-store/14542/186]("https://discourse.ubuntu.com/t/is-ubuntu-software-going-to-be-remove-for-snap-snap-store/14542/186")

---

