---
title: "Free cell on a minimal install?"
date: 2023-06-13
forum: General Help
---

### Post by nowindows2 on 2023-06-13
I've been researching whether it's possible to download Free Cell as a standalone game. The research isn't promising so far, but I've only started with Ubuntu (Jammy Jellyfish) a few weeks ago so I'm hoping I might be missing something.  I did a minimal install and have only downloaded three programs (gimp, gnumerics, and smplayer) via sudo apt.

It looks like I can't get just Free Cell - I would have to download it as part of a package of hundreds of other games.  The two apps (?) that popped up in the search (and these forums) several times were Play on Linux and Aisle Riot. Both appear to need Wine installed first, which I'd rather not do.

If I can't get Free Cell, is it possible to get just Solitaire?  Thanks!

---

### Post by Rubi1200 on 2023-06-13
Am I right that you want to keep a minimal install?

This link seems to have what you want but then it involves installing Snaps and perhaps that is not what you are after?

[https://snapcraft.io/install/freecell-solitaire/ubuntu](https://snapcraft.io/install/freecell-solitaire/ubuntu)

---

### Post by Holger_Gehrke on 2023-06-13
PlayOnLinux is not a game, it's a frontend for wine which makes installing and running Windows programs a bit easier.

aisleriot is a collection of solitaire games for Gnome containing about 80 solitaire games. It's about 9 Megabyte installed and needs quite a few libraries beyond that (whether or not you already have those installed depends on what else you run; GiMP needs a lot of the same libraries).

For a more minimal approach there's ace-of-penguins. That's another collection of solitaire games, but it's only a dozen or so games and it weighs in at less than 800 kb.

Another option is PySol, but that's hard to get running (couldn't get it to run from the package in the repositories and got it from sourceforge instead; was quite a bit of trouble) but that's even bigger then aisleriot both in terms of number of games and in installed size.

Holger

---

### Post by nowindows2 on 2023-06-13
Thanks for the link. I had seen that page while searching, but wasn't really sure what would happen if I executed the "sudo apt install snapd"  command. I was concerned it would install something like the snap store that comes with a regular full install.

Do I need to implement  "sudo apt install snapd" , or will "sudo snap install freecell-solitaire" install the game?

Thanks again.

---

### Post by nowindows2 on 2023-06-13
Thanks for the suggestions, but I only want Free Cell or Solitaire. Free Cell is the only thing I miss about Windows :)

---

### Post by Dennis N on 2023-06-13
> **nowindows2 said:**
> Thanks for the link. I had seen that page while searching, but wasn't really sure what would happen if I executed the "sudo apt install snapd"  command. I was concerned it would install something like the snap store that comes with a regular full install.

Do I need to implement  "sudo apt install snapd" , or will "sudo snap install freecell-solitaire" install the game?

Thanks again.

Just open your terminal and run:
**snap install freecell-solitaire**
That's all.

Image attached.

---

### Post by ian-weisser on 2023-06-13
It seems like you have four options.

1. You can install the aisleriot deb package and dependencies from the Ubuntu repositories. This is the fastest, simplest, and easiest method. This is the best method for beginners. 'sudo apt install aisleriot'

2. You can install the freecell snap package `sudo snap install freecell-solitaire` . This is equally fast and easy, and equally recommended to beginners...UNLESS your "minimal" system does not include snapd (all full installs of Ubuntu include snapd). If you lack snapd, then you must install the 'snapd' package and learn how to use it.

3. You can install the aisleriot flatpak package, which should include all necessary dependencies. Requires that you use apt to install the 'flatpak' package, and that you learn how to use it.

4. You can get freecell someplace else and try to install it (somehow) yourself. This might get complex and difficult in some cases. Depends upon what you choose.

---

### Post by Holger_Gehrke on 2023-06-13
Just to add a bit of perspective: the default variant (latest/stable) of the freecell-solitaire snap is 44mb. That's due to a snap bringing along all the libraries it needs and never using libraries that are already on your system. There are other variants of the snap (candidate,beta,edge) which are "only" 11mb but those need the updated core_14946.snap (which normally isn't installed, there are smaller core_18(58mb) and core_20(66mb) snaps which are installed by default), which weighs in at ~120 MB. So the snap solution is anything but minimal.

Holger

---

