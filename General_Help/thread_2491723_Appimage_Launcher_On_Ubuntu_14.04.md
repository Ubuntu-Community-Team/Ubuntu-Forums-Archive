---
title: "Appimage Launcher On Ubuntu 14.04?"
date: 2023-10-18
forum: General Help
---

### Post by irJvX7xo on 2023-10-18
Still using 14.04 here on an old computer. I need to use the development edition of Firefox, as Proton Mail won't run on the old version, 65 or so. But it's a bit cumbersome to open Files, then Firefox, then right-click on the app image - well, you get the idea. but I'm not sure I can use appimage launcher on 14.04, and if so, where to find the right version of it to install. Git hub seems not to have it, or at least I can't find it. I think I need the Xenial or Bionic version. "It'sfoss" said something about backward compatibility being broken with Bionic, and from Trusty on you need the Bionic package. but the ones listed all are newer. Is this possible?

---

### Post by irJvX7xo on 2023-10-19
Not really solved, but I decided it's not worth pursuing. I just moved the Firefox Developer folder onto the desktop. Two clicks get it to open so that works well.

---

### Post by Holger_Gehrke on 2023-10-19
'14.04' ? Unless you're using ESM you've been out of support for 5 years. Not good. If at all possible you should update to something current.

You should be able to use the snap package of Firefox, but for such an old system installing the snapd package is probably not trivial - you'd at the very least need to change the repositories for package download to the archive server were they were moved when support ended.

For an appimage you should be able to just set up a [.desktop file]("https://specifications.freedesktop.org/desktop-entry-spec/latest/") so the new firefox would show up in the menus or the application overview.

Holger

---

### Post by ajgreeny on 2023-10-19
Please do not continue to use Ubuntu 14.04 on a network as it has not received any security updates or upgrades for at least 5 years and will be a danger not only to you and your OS but also potentially to everyone else on the internet by being used by hackers as a bot thus causing problems for other internet users.

I would recommend that you try version 22.04 and if the newer version of Ubuntu is too resource hungry try a different DE version such as Lubuntu, Xubuntu, Kubuntu, etc etc.

---

### Post by irJvX7xo on 2023-10-19
This is just on an old desktop I use to stream music stations, and check out a few forums. not an enterprise situation. Also, I am indeed on ESM. I plan to use it until April when it finally is out of support.

Addendum: I actually only go on it now and then, basically to let ESM update. I activated ESM as soon as I installed it a few months back. I also have Ubuntu 16.04 on this computer, and it also has ESM. So when April comes, I still have two more years for that.

As time goes on, current distros  are getting to be too much for this system. It works best with Nvidia drivers, and 304 is the last one that works on the primitive 6150se graphics. And the 4.4 kernel is the last that will run 304. (I've heard someone made a patch, and you can install 304 on Ubuntu 18, but I don't like Gnome 3. also, systemd starts getting in the way with its bloat. 

Distros with Windows managers work well, but I don't care for them. I ran Bunsen for awhile, also Mabox, but couldn't deal with the degree of difficulty in doing things. Bodhi works best of all current distros, and I have Bodhi 7 on a SSD. so far that is working fine. but I like having U14 & 16 as backups, and also for the retro experience. 14 is actually my favorite distro of all time. Part of that is that I retired in 2014, and installed it, so it was really my gateway into the Linux world. Now, 9.5 years later, I have completely left Windows behind, even doing my music composition solely on Linux (Mint 21). But Ubuntu 14 will always have a special place in my heart.

---

### Post by irJvX7xo on 2023-11-01
Just wanted to tie a ribbon around this, and put to rest any concerns anyone might have about my using an unsafe system. After a few weeks of using Bodhi 7, I am so impressed that I must conclude it is the best light distro on the planet. It runs so smoothly, quietly and efficiently that it's like I have a brand-new machine (it's 14 years old). It runs better on nouveau drivers than Ubuntu 14 on Nvidia drivers. And systemd doesn't slow it down in the least. Si, I have found the distro for this old AMD Dual core with primitive graphics. and I could not be more emphatic about it being number one for light distros. And very little is needed for customizing. none, really, but I do a little anyway. If you're looking for a really light system that still looks great, give it a try.

---

