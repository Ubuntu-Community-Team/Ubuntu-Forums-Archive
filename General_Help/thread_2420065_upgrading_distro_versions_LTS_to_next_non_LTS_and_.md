---
title: "upgrading distro versions LTS to next non LTS and back to 20.04 LTS?"
date: 2019-05-29
forum: General Help
---

### Post by jebi on 2019-05-29
hi,

is it possible to upgrade from 18.04 lts to 19.04 then 19.10 then to 20.04 LTS?

also

what is the difference between running the software updater

and 

sudo apt update
sudo apt upgrade

this method seems to get newer updates on that the gui updater, as i ran the gui updater and then sudo upgrade and files this came?

on sudo apt upgrade will it tell you if you need a reboot?

thx

---

### Post by Autodave on 2019-05-29
You need to go to 18.10, then to 19.04 and then to 19.10 and 20.04.

If you are now on 18.04 (which is a long term service (LTS) release, you can stay there until 20.04 is released and upgrade straight from 18.04 to 20.04.  20.04 will be a LTS release.  Interim releases only have a little over 6 months of security updates.

I don't know about the GUI vs. the terminal: I would think that both are the same assuming that the GUI has updated itself before you used it.

---

### Post by deadflowr on 2019-05-30
In a few months you should be able to upgrade from 18.04 to 19.04 directly,
(going by Ubuntu's newer behavior for such things)
when 18.10 goes light outs.

This is because with the shorter support period people who decide to upgrade from the LTS releases could get caught up in a dead release if they kept allowing them to go to that first release after.
So now they reset which release will be offered when the last one goes night night. 
So when 18.10 goes bye the channel to upgrade from 18.04 should move to 19.04, and then 19.10 when 19.04 goes to sleep. And so on.

That make sense?

---

### Post by Impavidus on 2019-05-30
There are some differences between the software updater and apt upgrade. The most important is that the software updater supports [phased updates](https://wiki.ubuntu.com/PhasedUpdates). Another difference is that the software updater may propose to remove packages to be able to upgrade other packages, in case simply upgrading one package would lead to some conflict. In 12 years of using Ubuntu, this has never happened to me.

---

