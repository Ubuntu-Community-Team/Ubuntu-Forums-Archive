---
title: "Shotwell not finding pictures after transferring profile"
date: 2012-10-19
forum: General Help
---

### Post by x-shaney-x on 2012-10-19
So in 12.04, shotwell was working fine, I could view all my photos and everything was tagged and just great.
The photos and profile used was copied over from another 12.04 install and I simply ran shotwell and everything was there, tags and all.

During 12.10 testing, I copied over the .shotwell from 12.04 again, along with all my photos but it finds nothing, says nothing is in my library.
Since it was in the testing phase, I left things alone.
I then copied the photos and .shotwell from 12.04 into a new Fedora install and then again into a Kororaa install and after launching shotwell, everything was there once again.

So after installing 12.10 final, I tried again, copied over that same profile and the same photos but nothing found.
I deleted the profile and started from scratch, and imported the photos.
It finds them ok but screws up all the tags and I have to start from scratch (or restore from a backup).

Why will shotwell in 12.10 not just re-use the profile 12.04?

<EDIT>
I noticed that not only is it not finding the photos and tags, it is not bringing over any of the preferences either (plugins etc).

Has the profile location moved or something in 12.10?

---

### Post by hwttdz on 2013-07-13
Shotwell moved from keeping things in ~/.shotwell to ~/.cache/shotwell and ~/.local/share/shotwell.  There's a possibility you confused it by importing in a strange way.  Since you have a good backup I might recommend deleting ~/.shotwell,  ~/.cache/shotwell, and ~/.local/share/shotwell and then copying over ~/.shotwell from the old machine.  This should trip the upgrade scripts and it should migrate to keeping the prefs in the new locations.  Let us know if that works for you.

---

