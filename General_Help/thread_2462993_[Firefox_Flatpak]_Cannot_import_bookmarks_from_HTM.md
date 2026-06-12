---
title: "[Firefox Flatpak] Cannot import bookmarks from HTML file"
date: 2021-05-31
forum: General Help
---

### Post by ardouronerous on 2021-05-31
I'm running Xubuntu 20.04.

I've installed Firefox Flatpak from [here]("https://flathub.org/apps/details/org.mozilla.firefox") and I cannot import bookmarks from my HTML file. When I click on "Import and  Backup" then "Import Bookmarks from HTML...", nothing happens.

---

### Post by monkeybrain20122 on 2021-06-01
Maybe some kind of permission issue? Install flatseal from flatpak and adjust what firefox can access.

---

### Post by dddman on 2021-06-01
Never ran xubuntu, a while back when I explored different desktops xubuntu was left out.  Wasn't an intentional thing but an oversite on my part.  In ubuntu firefox can be installed from the software store, you have such a thing?  That would get you on either snaps or deb and I think a better match for Ubuntu.  I had one and only one flatpac installed (gimp), when I removed it and flatpac software I gained 1.2G of space!  Snaps installed gimp using about 200M and deb used 80M.  I can live with 200M, so using snaps for it.

Flatpaks are a bi product for Ubuntu

---

### Post by ardouronerous on 2021-06-01
> **monkeybrain20122 said:**
> Maybe some kind of permission issue? Install flatseal from flatpak and adjust what firefox can access.

[ATTACH=CONFIG]288593[/ATTACH]

Didn't work, I scrolled down to "Filesystem", then I selected "All user files (filesystem=home)", same result, cannot import bookmarks from my HTML file, I even selected All system files (filesystem=host), same result.

---

### Post by Dennis N on 2021-06-01
> When I click on "Import and Backup" then "Import Bookmarks from HTML...", nothing happens.
By "nothing happens", are you implying that the window to browse to your bookmarks.html file doesn't open?

---

### Post by ardouronerous on 2021-06-01
> **Dennis N said:**
> By "nothing happens", are you implying that the window to browse to your bookmarks.html file doesn't open?

Yes. Also, "Open File" and "Save Page As" doesn't work either, the window to open or save file doesn't open.

---

### Post by him610 on 2021-06-01
My four installations of Xubuntu 20.04 included Firefox from the official Ubuntu repository. Did yours not get installed, or did you remove yours in order to install a flatpak version?

---

### Post by ardouronerous on 2021-06-01
> **him610 said:**
> My four installations of Xubuntu 20.04 included Firefox from the official Ubuntu repository. Did yours not get installed, or did you remove yours in order to install a flatpak version?

I have two Firefoxes installed, the one from the official Ubuntu repository and flathub. I installed the flathub version so I can test newer versions of Firefox because flathub gets updated sooner, for example, the version from the official repository is at 88.0.1, while the flathub version is at 89.0.

---

### Post by him610 on 2021-06-01
> ...so I can test newer versions of Firefox
Well, if you are testing software, you can expect a few issues once in awhile. Did you report it using a discrepancy report to the developers, or whoever is tracking the DRs? It is the responsibility of the developers to fix it once it gets properly reported by the software tester. At least, that's the way it worked when I tested software in my previous life..

---

### Post by ardouronerous on 2021-06-01
> **him610 said:**
> Well, if you are testing software, you can expect a few issues once in awhile. Did you report it using a discrepancy report to the developers, or whoever is tracking the DRs? It is the responsibility of the developers to fix it once it gets properly reported by the software tester. At least, that's the way it worked when I tested software in my previous life..

This isn't because of Firefox Flatpak, how do I know this, because I've tested another browser from flathub, [LibreWolf]("https://flathub.org/apps/details/io.gitlab.librewolf-community"), same experiences, unable to import bookmarks. So, it' something to do with permissions.

---

### Post by Dennis N on 2021-06-02
I tried the "import bookmarks from HTML.." on Firefox Flatpak 89.0 to see if any problem arose, and the import worked correctly. 
The bookmarks.html was saved to my home folder from the Ubuntu repository version of Firefox for importing to the Flatpak version. I had previously used Flatseal to allow Firefox access to all user files.

---

### Post by dragonfly41 on 2021-06-02
Users trying to import bookmarks will find that Albert is very useful. Not only for bookmarks but many other uses.
Looking at Firefox bookmarks (although I use Chrome and not Firefox) I can see multiple Firefox profiles.

---

### Post by ardouronerous on 2021-06-02
> **Dennis N said:**
> I tried the "import bookmarks from HTML.." on Firefox Flatpak 89.0 to see if any problem arose, and the import worked correctly. 
The bookmarks.html was saved to my home folder from the Ubuntu repository version of Firefox for importing to the Flatpak version. I had previously used Flatseal to allow Firefox access to all user files.

As I test, I installedKdenlive from Flathub and I cannot open files with it, when I click on "Open", nothing happens, so there's a problem with my permissions. I've tried to allow Kdenlive access to user files with Flatseal, but it didn't work.

I installed Flatseal from Flathub too: [https://flathub.org/apps/details/com.github.tchx84.Flatseal](https://flathub.org/apps/details/com.github.tchx84.Flatseal)

---

### Post by &amp;KyT$0P# on 2021-06-02
Please post the output from running this command in Terminal -
```
apt-cache policy flatpak 'xdg-desktop-portal*'
```

---

### Post by ardouronerous on 2021-06-02
> **halogen2 said:**
> Please post the output from running this command in Terminal -
```
apt-cache policy flatpak 'xdg-desktop-portal*'
```

Here's the output:

```
apt-cache policy flatpak 'xdg-desktop-portal*'
flatpak:
  Installed: 1.6.5-0ubuntu0.3
  Candidate: 1.6.5-0ubuntu0.3
  Version table:
 *** 1.6.5-0ubuntu0.3 500
        500 http://ph.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
        500 http://ph.archive.ubuntu.com/ubuntu focal-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.6.3-1 500
        500 http://ph.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
xdg-desktop-portal-dev:
  Installed: (none)
  Candidate: 1.6.0-1
  Version table:
     1.6.0-1 500
        500 http://ph.archive.ubuntu.com/ubuntu focal/main amd64 Packages
        500 http://ph.archive.ubuntu.com/ubuntu focal/main i386 Packages
xdg-desktop-portal-backend:
  Installed: (none)
  Candidate: (none)
  Version table:
xdg-desktop-portal-gtk:
  Installed: (none)
  Candidate: 1.6.0-1build1
  Version table:
     1.6.0-1build1 500
        500 http://ph.archive.ubuntu.com/ubuntu focal/main amd64 Packages
xdg-desktop-portal-kde:
  Installed: (none)
  Candidate: 5.18.5-0ubuntu0.1
  Version table:
     5.18.5-0ubuntu0.1 500
        500 http://ph.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
     5.18.4.1-0ubuntu2 500
        500 http://ph.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
xdg-desktop-portal-tests:
  Installed: (none)
  Candidate: 1.6.0-1
  Version table:
     1.6.0-1 500
        500 http://ph.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
xdg-desktop-portal:
  Installed: (none)
  Candidate: 1.6.0-1
  Version table:
     1.6.0-1 500
        500 http://ph.archive.ubuntu.com/ubuntu focal/main amd64 Packages 
```

---

### Post by &amp;KyT$0P# on 2021-06-03
Try
```
sudo apt-get install xdg-desktop-portal-gtk
```

If that does not resolve the issue, try also using the official flatpak PPA per [flatpak setup instructions]("https://www.flatpak.org/setup/Ubuntu/").

---

### Post by ardouronerous on 2021-06-03
> **halogen2 said:**
> Try
```
sudo apt-get install xdg-desktop-portal-gtk
```

If that does not resolve the issue, try also using the official flatpak PPA per [flatpak setup instructions]("https://www.flatpak.org/setup/Ubuntu/").

Thank you, that worked! I can now import bookmarks into Firefox Flatpak.

---

### Post by Dennis N on 2021-06-03
It's surprising you didn't have the xdg-desktop-portal. It's a dependency of flatpak.

```
dmn@Sydney:~$ apt depends flatpak
flatpak
  Depends: adduser
  Depends: xdg-desktop-portal (>= 0.10)
  Depends: libappstream-glib8 (>= 0.6.1)
  Depends: libarchive13 (>= 3.0.4)
  Depends: libc6 (>= 2.28)
  Depends: libcap2 (>= 1:2.10)
<list cut>
```

Do you use the PPA to get the **flatpak** package? That may make the difference.
[https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak](https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak)

---

### Post by &amp;KyT$0P# on 2021-06-03
> **Dennis N said:**
> It's surprising you didn't have the xdg-desktop-portal. It's a dependency of flatpak.

The [FONT=Courier New]flatpak[/FONT] package from the PPA Depends on [FONT=Courier New]xdg-desktop-portal[/FONT] and Recommends [FONT=Courier New]xdg-desktop-portal-gtk[/FONT], but the standard Ubuntu repository version only Recommends both those packages.

@ardouronerous You're welcome. :KS

---

### Post by ardouronerous on 2021-06-03
[LEFT][FONT=arial]> **Dennis N said:**
> It's surprising you didn't have the xdg-desktop-portal. It's a dependency of flatpak.[/FONT][/LEFT]
[FONT=arial]
```
dmn@Sydney:~$ apt depends flatpak
flatpak
  Depends: adduser
  Depends: xdg-desktop-portal (>= 0.10)
  Depends: libappstream-glib8 (>= 0.6.1)
  Depends: libarchive13 (>= 3.0.4)
  Depends: libc6 (>= 2.28)
  Depends: libcap2 (>= 1:2.10)
<list cut>
```

Do you use the PPA to get the **flatpak** package? That may make the difference.
[https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak](https://launchpad.net/~alexlarsson/+archive/ubuntu/flatpak)

Yeah, I installed flatpak from the Ubuntu repos. I didn't even know there was a PPA of flatpak.

> **halogen2 said:**
> The flatpak package from the PPA Depends on xdg-desktop-portal and Recommends xdg-desktop-portal-gtk, but the standard Ubuntu repository version only Recommends both those packages

@ardouronerous You're welcome. :KS

Thanks again hallgen2.[/FONT]

---

