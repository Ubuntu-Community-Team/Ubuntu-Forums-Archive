---
title: "Changing path in Nautilus sidebar"
date: 2020-04-23
forum: General Help
---

### Post by Brunty on 2020-04-23
Hi, I've been unable to find a way around this - 

I have a relatively small SSD with Ubuntu 20.04 installed and a large HDD that I use for storage (also with my Windows partition). 

I'd like to change the path in the sidebar for Music, Videos, etc. 

I mount the Storage HDD at startup so it appears in /mnt and I see it correctly at boot, so I edited user-dirs.dirs to point at the correct directories but on a reboot the file has changed back to default.

Any help out there?

Cheers,

Brunty

---

### Post by CatKiller on 2020-04-23
The easy way to do it would be to symlink ~/Music to /mnt/whatever/Music and so on.

---

### Post by Holger_Gehrke on 2020-04-23
Editing ~/.config/user-dirs.dirs should work. Are you sure you saved the changes you made and that the values you entered are correct ? During start up 'xdg-user-dirs-update' should get run and this will reset any invalid settings to the default values. If you have some typos in the file or the file system mounted in /mnt/ is not (yet) available at the time this happens, then you should see exactly the kind of effect you describe.
   
Holger

---

### Post by Brunty on 2020-04-24
> **Holger_Gehrke said:**
> Editing ~/.config/user-dirs.dirs should work. Are you sure you saved the changes you made and that the values you entered are correct ? During start up 'xdg-user-dirs-update' should get run and this will reset any invalid settings to the default values. If you have some typos in the file or the file system mounted in /mnt/ is not (yet) available at the time this happens, then you should see exactly the kind of effect you describe.
   
Holger

Thanks

That's the only thing I could come up with - the mnt not being there at the right time.

---

### Post by Brunty on 2020-04-24
> **CatKiller said:**
> The easy way to do it would be to symlink ~/Music to /mnt/whatever/Music and so on.

Cheers, I'll look into this.

---

