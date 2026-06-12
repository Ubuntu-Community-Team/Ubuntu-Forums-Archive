---
title: "Automatically revert users?"
date: 2007-09-26
forum: General Help
---

### Post by timelord726 on 2007-09-26
I have been tasked with setting up several guest laptops for use in a hotel lobby.  For many reasons, I decided that it would be a good idea to run Ubuntu on them.

I am wondering if there is a way that I can have the guest user account automatically (either upon logout or at some predetermined interval) "revert" to a base setup.  I ask this because it's inevitable that people will save files to this account, build up a web history, etc.  I am looking for a way to have everything cleared so that each time the guest account logs in they are working from a totally clean slate.

Is there a good way to accomplish something similar to this?

Thanks in advance!

---

### Post by bodhi.zazen on 2007-09-26
Well, I assume users will not be able to access anything outside of the /home directory.

So, make an archive of an empty (default) /home/username (using tar)

Now add a command to extract you archive to */etc/gdm/PostSession/Default*

---

### Post by timelord726 on 2007-09-26
> **bodhi.zazen said:**
> Well, I assume users will not be able to access anything outside of the /home directory.

So, make an archive of an empty (default) /home/username (using tar)

Now add a command to extract you archive to */etc/gdm/PostSession/Default*
That's close to what I was thinking.

Would this also take care of *clearing* what was already in the user's profile?

---

### Post by mcduck on 2007-09-26
It's also possible to disable ability to write to disk on those guest accounts..

You might want to take a look at Pessulus & Sabayon, those are the Gnome tools for configuring & locking user accounts.

---

### Post by bodhi.zazen on 2007-09-26
> **timelord726 said:**
> That's close to what I was thinking.

Would this also take care of *clearing* what was already in the user's profile?

Well, if you overwrite /home/username with a default setup, like say a firefox set up with default extensions and security (Adblock for example) this will overwrite the profile with what you want.

---

