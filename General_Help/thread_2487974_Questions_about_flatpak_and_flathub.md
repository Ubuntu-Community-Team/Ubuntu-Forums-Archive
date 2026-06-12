---
title: "Questions about flatpak and flathub?"
date: 2023-06-19
forum: General Help
---

### Post by SpaceManJack on 2023-06-19
So I'm a newb here so bear with me.

So this right here is flathub yes? See picture, you see the folder that says software, that's flathub right? I just wish it would say that, it should say "Flathub", and even when you open it up it doesn't say flathub anywhere. You know you'd think the developers would title it "Flathub" but I guess they were too lazy do do that. Instead of saying "Software" it really should say "Flathub".
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292401&stc=1[/IMG]

So it looks like I could install the VLC player from the Ubuntu Software store or flathub, which one should I use, should I install VLC player on Ubuntu Software or flathub? They both work the same way right? Uh, Ubuntu Software is the snap store yes? Like I said I'm a newb.

Also check this out please, so I used flathub to install TOR, if you follow this link you'll see "manual install" at the bottom of the page, this is the method I used to install TOR [https://flathub.org/apps/com.github.micahflee.torbrowser-launcher](https://flathub.org/apps/com.github.micahflee.torbrowser-launcher) 

So TOR is only supposed to be 8Mb right? Well like I said previously, I installed TOR using the manual method on flathub, and it looks to me like it installed way more than just 8Mb, look 

```

computer1@Computer:~$ flatpak install flathub com.github.micahflee.torbrowser-launcher
Looking for matches…
Required runtime for com.github.micahflee.torbrowser-launcher/x86_64/stable (runtime/org.kde.Platform/x86_64/5.15-22.08) found in remote flathub
Do you want to install it? [Y/n]: y

com.github.micahflee.torbrowser-launcher permissions:
    ipc                   network       fallback-x11       pulseaudio
    wayland               x11           dri                file access [1]
    dbus access [2]

    [1] xdg-config/kdeglobals:ro, xdg-download
    [2] com.canonical.AppMenu.Registrar, org.freedesktop.Notifications,
        org.kde.KGlobalSettings, org.kde.kconfig.notify


        ID                                                  Branch      Op Remote  Download
 1. [&#10003;] org.freedesktop.Platform.GL.default                 22.08       i  flathub 142.8 MB / 143.1 MB
 2. [&#10003;] org.freedesktop.Platform.GL.default                 22.08-extra i  flathub  16.2 MB / 143.1 MB
 3. [&#10003;] org.freedesktop.Platform.openh264                   2.2.0       i  flathub   1.2 MB / 944.3 kB
 4. [&#10003;] org.gtk.Gtk3theme.Yaru                              3.22        i  flathub 328.6 kB / 191.5 kB
 5. [&#10003;] org.kde.Platform.Locale                             5.15-22.08  i  flathub  18.0 kB / 355.0 MB
 6. [&#10003;] org.kde.PlatformTheme.QGnomePlatform                5.15-22.08  i  flathub  10.6 MB / 10.6 MB
 7. [&#10003;] org.kde.WaylandDecoration.QGnomePlatform-decoration 5.15-22.08  i  flathub   6.8 MB / 11.1 MB
 8. [&#10003;] org.kde.Platform                                    5.15-22.08  i  flathub 340.3 MB / 323.9 MB
 9. [&#10003;] com.github.micahflee.torbrowser-launcher            stable      i  flathub   9.6 MB / 8.1 MB

Installation complete.
computer1@Computer:~$ 


```

Yeah it looks to me like it installed hundreds of megabytes. I mean, everything's ok right? Thanks you for your time.

---

### Post by deadflowr on 2023-06-19
No, Software is gnome-software.

---

### Post by SpaceManJack on 2023-06-19
> **deadflowr said:**
> No, Software is gnome-software.

Ok so when I went through the flathub installation process it installed gnome-software? I'm confused.

---

### Post by Frogs Hair on 2023-06-19
There is a plugin for gnome software that is used to install flatpaks from flathub. This is no longer a default on new Ubuntu releases as of April 2023. There are 3 package types that can be available in gnome-software on Ubuntu and they are flatpak, .deb, and snap. The origin of those packages are not well marked in gnome-software regardless of Linux distribution. This is why the application may appear more than once in gnome-software. My experience with flatpaks varies depending on who packaged and uploaded the application. Flatpak quality can't be verified by Ubuntu developers and has become a user choice.

---

### Post by Dennis N on 2023-06-19
> So TOR is only supposed to be 8Mb right? Well like I said previously, I installed TOR using the manual method on flathub, and it looks to me like it installed way more than just 8Mb
The Tor package is item #9 in the list of installed packages. It alone was a 9.6 mB download. Items 1-8 are the supporting libraries needed to run it. Once you download them, next time these same support packages are required, you don't need to download them again since they are already on your system and will be shared.

flathub is a website that is a repository for Flatpak packages. 
You can install Flatpak packages found on the flathub website in two ways: with the flatpak command in the terminal or by using the gnome-software package + its plugin for Flatpaks. gnome-software installs an application named 'Software' on your computer. Ubuntu Software cannot install Flatpak packages and they are not shown in it.

---

### Post by SpaceManJack on 2023-06-20
> **Dennis N said:**
> The Tor package is item #9 in the list of installed packages. It alone was a 9.6 mB download. Items 1-8 are the supporting libraries needed to run it. Once you download them, next time these same support packages are required, you don't need to download them again since they are already on your system and will be shared.

flathub is a website that is a repository for Flatpak packages. 
You can install Flatpak packages found on the flathub website in two ways: with the flatpak command in the terminal or by using the gnome-software package + its plugin for Flatpaks. gnome-software installs an application named 'Software' on your computer. Ubuntu Software cannot install Flatpak packages and they are not shown in it.

So the gnome-software package was installed by flathub correct?

---

### Post by Dennis N on 2023-06-20
> **scott130 said:**
> So the gnome-software package was installed by flathub correct?

No, gnome-software is a package in the Ubuntu repository:

```
dmn@Tyana-vm:/etc/default$ apt show gnome-software
Package: gnome-software
Version: 44.0-1ubuntu1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 3,107 kB
<snip>
Recommends: fwupd, **gnome-software-plugin-snap**
Suggests: apt-config-icons-hidpi,** gnome-software-plugin-flatpak**


```

It looks and works the same as Ubuntu Software but supports both Flatpak and Snap packages if you also install the two plugins indicated in the display above. Use apt to install all of them.

---

### Post by SpaceManJack on 2023-06-28
> **Dennis N said:**
> No, gnome-software is a package in the Ubuntu repository:

```
dmn@Tyana-vm:/etc/default$ apt show gnome-software
Package: gnome-software
Version: 44.0-1ubuntu1
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 3,107 kB
<snip>
Recommends: fwupd, **gnome-software-plugin-snap**
Suggests: apt-config-icons-hidpi,** gnome-software-plugin-flatpak**


```

It looks and works the same as Ubuntu Software but supports both Flatpak and Snap packages if you also install the two plugins indicated in the display above. Use apt to install all of them.

The thing is I never saw the "gnome-software" in my list of apps til I went through with the flathub installation (and I've explained above). Once I went through the flathub installation that's when I saw gnome-software appear in my apps.

---

### Post by MAFoElffen on 2023-06-29
'gnome-software' has not been a default installed pacakge in new installations since 20.10. Now if you did do-release-upgrade to upgrade the release to current, that package would carry over from a previous release.

If you run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info")... Near the end are sections for User installed packages, Snaps, and Flatpak applications... In that report, you can see what is there, and where they are from. That report would tell us which ISO your system was originally installed from, and if a do-release-upgrade was ver done from a previous release.

To answer your question on the difference in size of the applications... For Snap Apps and Flatpak Apps, they are 'packaged' with all the dependencies they need to run. The problem of this, is that, after a while of installing those types of packages, then you end up with multiple copies (and sometimes multiple versions) of some dependancy types of packages, duplicated many times between those apps. But since they run inside sandboxes, there are no problems encountered between them. This does add up fast in taking up storage resources

---

### Post by grahammechanical on 2023-06-29
I would like to add something to this discussion.

I was using the snap version of zoom-client happily until the zoom host application refused to log me in because the zoom-client version I was using was not the latest version. For some strange reason the system could not update the snap version even though Ubuntu software indicated the latest version as available.

I went through the process of installing the flatpak version. At the end of this process I ended up with two app stores. One app store had an icon of a white and blue suit case - that is Gnome Software with the flatpack extensions. The other app store had an orange suitcase icon. That is Ubuntu Software (also called Software or snap store). It will install both deb and snap packed apps. Whereas, Gnome-software will install both deb and flatpack apps.

Flathub is the official repository of flatpak apps. Gnome Software will access this as well as the normal Ubuntu deb software repositories. The Flathub repository is not in our sources.list file. So, it address must be stored in the Gnome Software Extension.

Regards

---

### Post by SpaceManJack on 2023-08-08
> **grahammechanical said:**
> I would like to add something to this discussion.

I was using the snap version of zoom-client happily until the zoom host application refused to log me in because the zoom-client version I was using was not the latest version. For some strange reason the system could not update the snap version even though Ubuntu software indicated the latest version as available.

I went through the process of installing the flatpak version. At the end of this process I ended up with two app stores. One app store had an icon of a white and blue suit case - that is Gnome Software with the flatpack extensions. The other app store had an orange suitcase icon. That is Ubuntu Software (also called Software or snap store). It will install both deb and snap packed apps. Whereas, Gnome-software will install both deb and flatpack apps.

Flathub is the official repository of flatpak apps. Gnome Software will access this as well as the normal Ubuntu deb software repositories. The Flathub repository is not in our sources.list file. So, it address must be stored in the Gnome Software Extension.

Regards

Well you see the picture as the top yes? That's Gnome Software yes? I didn't see that till I went through the flathub installation steps. I just wish it would say "Gnome Software" to avoid any confusion!!!

---

