---
title: "External Forum - Cannot Upload Images"
date: 2023-01-10
forum: General Help
---

### Post by electrosteam on 2023-01-10
Lubuntu 22.04 64 bit,
Firefox 108.0.2,
All upgrades to date,
No imported preferences.

On an external Forum, MetalworkForums, when uploading files, the File Manager Window to enable file selection does not appear when 'Browse' is selected.

This operation has been successful over several years with earlier versions of Lubuntu and Firefox.

I have opened a thread on this subject in the external forum.

Can anyone shed light on possible source of the problem ?

Keep well,
John.

---

### Post by ne29914 on 2023-01-10
Based on your several posts here, your Lubuntu 22.04 install does not seem to be a success.
Neither was mine.
I chose to go back to Lubuntu 20.04.5 which works a dream.
The issues seem to be a combination of 22.04 missing/changed functionality, plus some Qt5 issues, but it's damn hard to nail down. I suspect snaps also play a role.

---

### Post by guiverc on 2023-01-10
Firefox when run as a *snap* package, runs *confined* which means it has only limited access to your root file-system.

A *confined** snap* package should be able to access files in your user directory, but will see only its own *squashfs* for directories outside of that, though you can allow it to also access removable-media directories, ie. `/mnt/` and `/media/`  (or subdirectories inside of either of /mnt or /media).

You didn't give any details on what directories you cannot access, thus I can't know if this is your issue.

Example.  I use network shares on my own boxes & avoid typing when I can, so access them from the / directory (eg. `/pe2900` to access one server, `/de2900` to access another etc; however *snap* apps cannot use them as they're outside of $HOME or /mnt or /media. My own fix to this was to create a separate (*second*) mount in /mnt/ (eg. `/mnt/de2900/`) which is what I use when using a *snap* package (chromium or firefox). As I don't use browsers to download files, my *second* mount in /mnt only has read access, but it let me upload files when I need to.

---

### Post by electrosteam on 2023-01-11
Reluctant to go backwards with the release.
My experience is that others will have the same problem, and it will soon get fixed.
(am I too trusting ?)

I am attempting to upload an image from my User Account.

Tried a second laptop with Ubuntu Mate 22.04 LTS and the same Firefox.
Uploaded image to external forum no problem.

The Firefox About window states Snap, but the machine boots up with the Firefox icon selectable in the Menu line.
Seems it must be installed in some way.

I will research installation of the snap version as I know the Lubutu install does not have Firefox installed.
I have a shortcut link on the Desktop to launch Firefox.

Thanks to all who take the time to assist people like me.
Keep well,
John

---

### Post by dragonfly41 on 2023-01-12
I would try another browser - such as Brave - to see if the experience is the same.

---

### Post by guiverc on 2023-01-12
I'll just comment again, but sorry I'm not providing any answers.

**Lubuntu does include firefox by default**, a quick look at the latest *daily* ISO of *jammy* (22.04) will show you [https://cdimage.ubuntu.com/lubuntu/jammy/daily-live/current/jammy-desktop-amd64.manifest](https://cdimage.ubuntu.com/lubuntu/jammy/daily-live/current/jammy-desktop-amd64.manifest) as to what's included on it, and you can search for *firefox* and you'll note that it's included, and what version is included.

Lubuntu has included *firefox* on all released products as you'll find it in our seeds ([https://people.canonical.com/~ubuntu-archive/seeds/lubuntu.jammy/desktop](https://people.canonical.com/~ubuntu-archive/seeds/lubuntu.jammy/desktop) for *jammy or 22.04*).  Yes there are parts of cycles (eg. *cosmic* or 18.10 which was long ago now, where we experimented with replacing *firefox* with *falkon* as it's lighter, but the few times we've done this, there were always websites that didn't work as well as they did with *firefox*, thus we returned to *firefox* prior to actual release, thus *firefox *alternatives will only exist on QA intended *daily* ISOs (*of long ago now*) and not released products).

I'm not aware of any differences between Ubuntu-MATE 22.04 & Lubuntu 22.04 LTS with regards *firefox*, but you didn't specify any directories as per my prior comment, so I've not looked any further.  Personally I'd expect the same with all *flavors* and main Ubuntu with regards *firefox* as all use the same Ubuntu base, just using different *seed* files that alter some packages (eg. [https://people.canonical.com/~ubuntu-archive/seeds/ubuntu-mate.jammy/desktop](https://people.canonical.com/~ubuntu-archive/seeds/ubuntu-mate.jammy/desktop) will show Ubuntu-MATE's *jammy* file)

There are many posts about replacing the *default snap* version of *firefox* with the various *deb* packages; some even by Ubuntu *developers*, and you'll find at least one on the [Lubuntu discourse]("https://discourse.lubuntu.me/t/how-to-install-firefox-non-snap/3222") too (*jump to the end for one of the Ubuntu dev posts*), but without specifics as to what directories were being used for the problems I can't test or suggest anything specific.

---

