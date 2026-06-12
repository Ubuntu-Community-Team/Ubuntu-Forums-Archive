---
title: "flatpak and other means to install package"
date: 2024-05-05
forum: General Help
---

### Post by ValentynPrumers on 2024-05-05
A few months ago i installed mednaffe (a program to emulate old game consoles and play games). I totally forgot i installed it (and which way i used). But today i installed mednaffe using flatpak (first time i used flatpak btw, seems nice). So no there are 2 versions of this program. I know how to remove the one i installed with flatpak. But is there a way to search for the other version of mednaffe? I really dont remember how i installed it...

Thanks :)

---

### Post by Holger_Gehrke on 2024-05-05
Actually mednaffe is just a frontend for the mednafen emulator. If mednaffe works then you obviously have both of them installed.

I can think of five ways to install a program: .deb package, snap package, flatpak, AppImage, and from source. 

Check for a .deb with 'apt list mednaf'. If mednaffe and mednafen are installed they will be marked with '[installed]' in the list this command shows. You can remove them with 'apt remove mednafen mednaffe'.

Check for a snap with 'snap list'. AFAIK there's no such thing as a mednaffe snap, but if there were, the command to remove a snap is 'snap remove "package-name"'.

Since you know what to do about a flatpak (and I don't; haven't used flatpaks for a few years), I'll leave that to you.

An AppImage is somewhat problematic: it's a single file that you just execute. Integration into a desktop environment is usually done by hand by creating your own .desktop file for it and you can put it basically anywhere. So uninstalling an AppImage consists of just deleting the .desktop file and the AppImage; the problem is finding them.

If you installed from source, you would probably remember ... mednafen uses GNU automake and it's Makefile should define an 'uninstall'-target, so 'make uninstall' should work.

Holger

---

### Post by ValentynPrumers on 2024-05-05
Thanks!

The apt list mednaf* did indeed return mednafen but also mednaffe. So thats def a different mednaffe than I installed with flatpak today, You think i can safely remove
the mefnaffe entry with apt remove mednaffe? 

I thought mednaffe had all the mednafen stuff packed inside it. But you say its only a front end and i do need the mednafen package?

Thanks :)

To remove a flatpak app:# [COLOR=#000000]flatpak uninstall &#8211;delete-data <package ID>[/COLOR]

---

### Post by Holger_Gehrke on 2024-05-05
If the flatpak you installed is [this one]("https://flathub.org/apps/com.github.AmatCoder.mednaffe"), then it includes mednafen and you can remove both mednafen and mednaffe that you installed with apt. And yes, they are separate projects by different authors. If you install mednaffe through apt, the separate mednafen package gets pulled in as a dependency. Or you can install just mednafen and use it from the command line.

Holgeer

---

### Post by ValentynPrumers on 2024-05-05
Thanks a lot!

---

