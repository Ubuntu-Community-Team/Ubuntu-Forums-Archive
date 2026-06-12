---
title: "all snaps get unstable Ubuntu 22.04"
date: 2022-11-12
forum: General Help
---

### Post by rebecca58 on 2022-11-12
Since I've migrated to Ubuntu 22.04, most snaps packages don't work properly. A window will popup, saying the program isn't responding... I had this on musescore. Had to remove it. Same with audacity when I export a file as a MP3... It just did with telegram app too. There is something wrong with most snaps and I want to find out why.  Laptop Dell Vostro 4GO RAM. Ubuntu 22.04.

---

### Post by TenPlus1 on 2022-11-12
It would probably be easier to install gnome-software with it's flatpak plugin and use the flatpak versions of the software you need.

---

### Post by ian-weisser on 2022-11-12
If programs aren't responding, regardless of package, jump into a terminal and check `top` and `free`.

See if there is a resource constraint or a runaway process or some other easy-to troubleshoot cause.

For example, it might be a Gnome issue or a disk issue instead of a snap issue. Real data will help you look in the right place.

---

### Post by mIk3_08 on 2022-11-12
> **rebecca58 said:**
> Since I've migrated to Ubuntu 22.04, most snaps packages don't work properly. A window will popup, saying the program isn't responding... I had this on musescore. Had to remove it. Same with audacity when I export a file as a MP3... It just did with telegram app too. There is something wrong with most snaps and I want to find out why.  Laptop Dell Vostro 4GO RAM. Ubuntu 22.04.
I experienced this snap too since 18.04. the application works fine from the moment you install but after the upgrade snaps application begins to struggle, other apps from snap won't start and while the others have errors too. I prefer to use the repo via terminal than using snap package. Sad to say but I already experienced it. That is why I remove all the snap application as possible and choose the repo via terminal to install a packages or using some package manager will be more efficient, reliable than snap packages manager. Regards and cheers.

---

