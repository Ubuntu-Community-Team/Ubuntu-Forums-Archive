---
title: "Tumbler keeps crashing, how to prevent please"
date: 2023-03-04
forum: General Help
---

### Post by andrew-q2 on 2023-03-04
hi, I keep getting "sorry ubuntu has experienced an internal error" shortly after ubuntu has booted up.
The executable is ..tumbler-1/tumblerd    package tumbler 0.2.8-1
"tumbler crashed with SIGSEGV"

From a previous thread here, I've already set all the plugins to "Disabled=true" but this has not fixed it.

I'm using ubuntu 20.04.5 with Gnome 3.36.8.  For a file manager, I generally use thunar 1.8.14.  "Files" 3.36.3-stable is also present from the original 20.04 install.

Apologies for the previous test post but a previous attempt with a small jpeg attached failed and I lost all my typing.

Thanks for reading

---

### Post by DuckHook on 2023-03-04
> **andrew-q2 said:**
> …From a previous thread here, I've already set all the plugins to "Disabled=true" but this has not fixed it.
Please post link to the thread. It is not possible to understand the context without more info.
> I'm using ubuntu 20.04.5 with Gnome 3.36.8.  For a file manager, I generally use thunar 1.8.14.  "Files" 3.36.3-stable is also present from the original 20.04 install
Is there a reason you are using Thunar in a vanilla Ubuntu install? Not that there is anything wrong with doing so, but giving your reasons might make it easier to understand your larger goals. Again, that all&#8209;important context.

Vanilla Ubuntu does not come with Thunar by default. Installing Tumbler on top of a "foreign" file manager makes an already unusual setup even more brittle. If you are trying to disable this plugin (an action implied by your previous reference), then why not just remove/purge Tumbler altogether? For that matter, why not just stick with Nautilus?

This is another illustration of my adage: "leave the system as close to its default state as possible." The more "customizations" and cruft that we add to an install, the more that will eventually go wrong.

---

### Post by #&amp;thj^% on 2023-03-04
> **DuckHook said:**
> 
Is there a reason you are using Thunar in a vanilla Ubuntu install? Not that there is anything wrong with doing so, but giving your reasons might make it easier to understand your larger goals. Again, that all&#8209;important context.


Here's a good reason: [https://docs.xfce.org/xfce/tumbler/start](https://docs.xfce.org/xfce/tumbler/start)
Tumbler is used by Thunar, Ristretto, Xfce. 
For the OP, I use this in my .bashrc
```
export XDG_CACHE_HOME=$HOME/.my_new_cache
```
you can change "my_new_cache" to something useful for yourself
I do agree with Duck Hook on adding different DE environments, do add challenges to your DE
```
apt policy tumbler
tumbler:
  Installed: 4.18.0-1
  Candidate: 4.18.0-1
  Version table:
 *** 4.18.0-1 990
        990 http://deb.debian.org/debian sid/main amd64 Packages
        990 http://ftp.us.debian.org/debian sid/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by DuckHook on 2023-03-04
> **1fallen said:**
> Here's a good reason: [https://docs.xfce.org/xfce/tumbler/start](https://docs.xfce.org/xfce/tumbler/start)
:-k
I may be denser than normal today, but I still don't understand. This shows that Tumbler is needed to make Thunar complete, but why Thunar at all? My Nautilus shows thumbnails, so I don't understand why the OP doesn't just use Nautilus.

---

### Post by #&amp;thj^% on 2023-03-04
> **DuckHook said:**
> :-k
I may be denser than normal today, but I still don't understand. This shows that Tumbler is needed to make Thunar complete, but why Thunar at all? My Nautilus shows thumbnails, so I don't understand why the OP doesn't just use Nautilus.

I just can't argue that kind of wisdom DH
If you seen my set-up you would kick my Butt from here to Sunday..:lolflag:

---

### Post by andrew-q2 on 2023-03-04
Thanks all for the replies.

@DuckHook -
The previous thread I referred to is [https://ubuntuforums.org/showthread.php?t=2461302&highlight=tumbler.rc+thunar](https://ubuntuforums.org/showthread.php?t=2461302&highlight=tumbler.rc+thunar)

I started using Thunar simply because I prefer the interface as compared to Files.  I have no special interest in having thumbnails shown, quite happy if there are none.

Removing Tumbler is perhaps the best course of action for me.  Does
sudo apt-get remove tumbler
followed by a restart sound ok?

I didn't think installing Thunar might make anything "brittle".  The "Ubuntu Software" app seems quite happy to offer it up.

@1fallen -
What is the idea behind moving the cache please?

---

### Post by #&amp;thj^% on 2023-03-04
> **andrew-q2 said:**
> 
@1fallen -
What is the idea behind moving the cache please?
If you stick with Thunar it helps smooth environment clash's
> 
Configuration

You can override the default cache directory $HOME/.cache in which, besides other non-essential files, thumbnails are stored:

    D-Bus/ systemd
        create a file below ~/.config/environment.d/ and inside set XDG_CACHE_HOME. E.g:
        XDG_CACHE_HOME=$HOME/.my_new_cache

    Other
        Extend $HOME/.profile, $HOME/.bash_rc or similar
        export XDG_CACHE_HOME=$HOME/.my_new_cache

After that, re-login, make sure the variable is set, and check if it works fine.

Tumbler has a configuration file tumbler.rc described in a dedicated page. 

This has been an on going problem with tumbler in a mixed mode.
Works perfectly fine in my XFCE4 desktop.

---

### Post by DuckHook on 2023-03-04
> **andrew-q2 said:**
> &#8230;Does:
```
sudo apt-get remove tumbler
```
&#8230;followed by a restart sound ok?
First, try 1fallen's tweak. I don't like nuking dependency elements any more than I like cruft.
> I didn't think installing Thunar might make anything "brittle".  The "Ubuntu Software" app seems quite happy to offer it up.
*sigh*

The Ubuntu Software app.

That's another story in and of itself. More on that later.

As for your query, nothing wrong with installing alternate file managers provided one is familiar with the pitfalls. They key is: "familiar with the pitfalls".

Consider: the file manager operates at a pretty basic level. It must manage stuff like file ownerships, permissions, etc, so it has to be a gut&#8209;level utility. This means that it has to have hooks deep into your system. If any of those hooks are not *exactly* right, then the consequences are more severe than those of, say, that game you installed.

This is why I tend to shy away from running system utilities that the devs didn't include with my install. This is not a hard and set rule, just my rule of thumb that many years of experience has taught me for staying out of trouble. I used to do all sorts of tweaks and customizations to my new installs. Not any more. It's not worth my time and aggravation trying to chase down all the little breakages and inconsistencies that my tinkering used to cause.

You've just been instructed by 1fallen on one such pitfall. I didn't know about that one either. But why would I even want to risk any unknowns? For the sake of appearances? When the utility is just the same? That's a poor trade in my books. But that's just me.

As for the Ubuntu Software app&#8230;

I don't like it. At all. It gives just enough info to be dangerous without enough info to mitigate that danger. For example, it doesn't warn unwary users that an app made for KDE will drag in hundreds of dependencies in a GTK environment. This would not only create a huge additional attack surface, but it bloats up your install and increases the chance of system breakage, sometimes in very subtle ways that are hard to trace. In your case, it didn't warn you that Thunar needs a separate cache to avoid the risk of conflicts.

In short, it has the same shortcomings as proprietary app stores&#8212;a pretty face but insufficient info to make informed decisions. This is not due to malice or neglect on the devs part; it is because if they want the Ubuntu experience to go down easy for new users, they have to dumb it down to the point where anything that smacks of complexity is left out.

I never use the Software app. Instead, I do things from the CLI. Here's a comparison using Thunderbird as an example:

[list=1]
[*]Software app:> 
Description:
Thunderbird is a free and open source email, newsfeed, chat, and calendaring client, that&#8217;s easy to set up and customize. One of the core principles of Thunderbird is the use and promotion of open standards - this focus is a rejection of our world of closed platforms and services that can&#8217;t communicate with each other. We want our users to have freedom and choice in how they communicate.
Download Size: 106.8 MB
Version: 102.8.0
Source: Snap Store (it doesn't even offer the choice of the .deb version). For those not in the know, the snap version may cause problems.

My biggest beef with this Software "store" is that it has ratings and reviews that are divorced from reality, posted by tourists and dilettantes who don't know how to use the app, then blame it for their own shortcomings. I nuked my Gmail account recently, but while I had it, I had no problems getting it to work with T&#8209;bird. The process was involved, but this is not Mozilla's fault; the fact is that Google makes it as hard as possible to use email clients other than their own. Yet, the reviews would have one believing that T&#8209;Bird doesn't work with Gmail. These reviews/ratings are useless and misleading, skewed by ignorance and ineptitude, so why are they even there?

---versus---

[*]```
duckhook@Zeus:~$  apt show thunderbird
Package: thunderbird
Version: 1:102.7.1+build2-0ubuntu0.22.04.1
Priority: optional
Section: mail
Origin: Ubuntu
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 240 MB
Provides: mail-reader
Depends: libasound2 (>= 1.0.16), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.35), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdbus-1-3 (>= 1.9.14), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.12.6), libfreetype6 (>= 2.10.1), libgcc-s1 (>= 4.0), libgdk-pixbuf-2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.37.3), libgtk-3-0 (>= 3.13.7), libharfbuzz0b (>= 0.6.0), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libstdc++6 (>= 12), libx11-6, libx11-xcb1 (>= 2:1.7.5), libxcb-shm0, libxcb1, libxcomposite1 (>= 1:0.4.5), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxi6, libxrandr2 (>= 2:1.4.0), libxrender1, libxtst6
Recommends: myspell-en-us | hunspell-dictionary | myspell-dictionary, libcanberra0, libdbusmenu-glib4, libdbusmenu-gtk3-4
Suggests: thunderbird-gnome-support, ttf-lyx, libotr5
Conflicts: mozilla-thunderbird
Breaks: enigmail (<< 2:2.2), jsunit (<< 0.2.2-2ubuntu1), thunderbird-gnome-support (<= 3.0.4+nobinonly-0ubuntu3), tinyjsd (<< 1.2+git1-1ubuntu1)
Replaces: mozilla-thunderbird, thunderbird-gnome-support (<= 3.0.4+nobinonly-0ubuntu3)
Task: ubuntu-desktop, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-default-languages, ubuntu-desktop-raspi, kubuntu-desktop, kubuntu-full, xubuntu-desktop, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-budgie-desktop, ubuntu-budgie-desktop-raspi
Download-Size: 62.4 MB
APT-Manual-Installed: no
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
Description: Email, RSS and newsgroup client with integrated spam filter
 Thunderbird is a full-featured email, RSS and newsgroup client that makes
 emailing safer, faster and easier than ever before. It supports different mail
 accounts (POP, IMAP, Gmail), has a simple mail account setup wizard, one-
 click address book, tabbed interface, an integrated learning spam filter,
 advanced search and indexing capabilities, and offers easy organization
 of mails with tagging and virtual folders. It also features unrivalled
 extensibility.

N: There is 1 additional record. Please use the '-a' switch to see it
```
This is more like it.

I get dependencies, recommends, suggests, conflicts and apps it will break. It tells me the repository source and that it's not a manual install (in other words, it came with the system). The description is the least of its offerings and the silly misleading ratings/reviews are nowhere to be seen (yay!). Factual, complete and filled with actually useful info, there is no comparison between this and the pointless marketing fluff that I get on the Software app.
[/list]
You don't have to be a power user to appreciate the value of good, genuinely useful info.

---

### Post by #&amp;thj^% on 2023-03-05
> **andrew-q2 said:**
> 
I didn't think installing Thunar might make anything "brittle".  The "Ubuntu Software" app seems quite happy to offer it up.



Along with what DuckHook has offered, I don't think it makes it  "brittle" per say but it dose clash with how smoothly Gnome DE behaves:
```
 >> apt depends tumbler
tumbler
  Depends: tumbler-common (= 4.18.0-1)
  Depends: libc6 (>= 2.34)
  Depends: libcairo2 (>= 1.2.4)
  Depends: libfreetype6 (>= 2.2.1)
  Depends: libgdk-pixbuf-2.0-0 (>= 2.22.0)
  Depends: libglib2.0-0 (>= 2.67.1)
  Depends: libgstreamer-plugins-base1.0-0 (>= 1.0.0)
  Depends: libgstreamer1.0-0 (>= 1.4.0)
  Depends: libjpeg62-turbo (>= 1.3.1)
  Depends: libpng16-16 (>= 1.6.2-1)
  Depends: libpoppler-glib8 (>= 0.85.0)
  Depends: libtumbler-1-0 (>= 4.17.2)
  Depends: libxfce4util7 (>= 4.17.1)
  Suggests: tumbler-plugins-extra


me on Sun Mar 05 at 09:34 AM in ~ branch: (HEAD) 
>> apt depends thunar
thunar
  Depends: desktop-file-utils
  Depends: exo-utils
  Depends: shared-mime-info
  Depends: thunar-data (= 4.18.4-1)
  Depends: libatk1.0-0 (>= 1.12.4)
  Depends: libc6 (>= 2.34)
  Depends: libcairo2 (>= 1.14.0)
  Depends: libexo-2-0 (>= 4.17.0)
  Depends: libgdk-pixbuf-2.0-0 (>= 2.22.0)
  Depends: libglib2.0-0 (>= 2.65.1)
  Depends: libgtk-3-0 (>= 3.21.5)
  Depends: libgudev-1.0-0 (>= 146)
  Depends: libice6 (>= 1:1.0.0)
  Depends: libnotify4 (>= 0.7.0)
  Depends: libpango-1.0-0 (>= 1.44.6)
  Depends: libsm6
  Depends: libthunarx-3-0 (>= 1.7.0)
  Depends: libxfce4ui-2-0 (>= 4.17.6)
  Depends: libxfce4util7 (>= 4.17.2)
  Depends: libxfconf-0-3 (>= 4.6.0)
  Breaks: thunar-data (<< 1.2.3-3)
 |Recommends: <default-dbus-session-bus>
    dbus-user-session
  Recommends: <dbus-session-bus>
    dbus-user-session
    dbus-x11
  Recommends: gvfs
 |Recommends: policykit-1-gnome
  Recommends: <polkit-1-auth-agent>
    gnome-flashback
    gnome-shell
    lxpolkit
    lxqt-policykit
    mate-polkit
    phosh
    policykit-1-gnome
    polkit-kde-agent-1
    ukui-polkit
  Recommends: thunar-volman
  Recommends: tumbler
  Recommends: udisks2
  Recommends: xdg-user-dirs
  Recommends: libxfce4panel-2.0-4 (>= 4.13.0)
  Suggests: thunar-archive-plugin
  Suggests: thunar-media-tags-plugin
  Suggests: gvfs-backends
  Replaces: thunar-data (<< 1.2.3-3)

```
This might help visualize possible hiccup's.

---

### Post by andrew-q2 on 2023-03-06
Big thanks @DuckHook and @1fallen for explaining the above and taking the time.  I shall be more wary of the "app store" in future.  "apt show" looks extremely useful.
You mentioned KDE apps dragging in masses of dependencies - is there an APT SHOW type of command which for a given app will list all NEW dependencies, i.e. ones which you don't currently have but which will be dragged in?

---

### Post by DuckHook on 2023-03-06
> **andrew-q2 said:**
> …is there an APT SHOW type of command which for a given app will list all NEW dependencies, i.e. ones which you don't currently have but which will be dragged in?
The easiest way to guard against unintended dependency bloat is again to use the command line. When you install an app using the command line, it actually pauses to tell you what dependencies will be dragged in before you choose to go ahead. Even better is to use the -s swtich. The following example is what happens when I try to install the Dolphin file manager in a vanilla Ubuntu instance:```
duckhook@Zeus:~$  apt install -s dolphin
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  baloo-kf5 catdoc ffmpegthumbs gamin kactivities-bin kactivitymanagerd kded5 kdegraphics-thumbnailers keditbookmarks
  kimageformat-plugins kinit kio kio-extras kio-extras-data kpackagelauncherqml kpackagetool5 kuserfeedback-doc
  kwayland-data kwayland-integration libappimage0 libavif13 libcddb2 libdbusmenu-qt5-2 libdc1394-25 libdca0 libdolphinvcs5
  libdvbpsi10 libebml5 libepub0 libfaad2 libgamin0 libgav1-0 libhfstospell11 libilmbase25 libixml10 libkate1 libkdsoap1
  libkf5activities5 libkf5activitiesstats1 libkf5archive5 libkf5attica5 libkf5auth-data libkf5auth5 libkf5authcore5
  libkf5baloo5 libkf5balooengine5 libkf5baloowidgets-bin libkf5baloowidgets-data libkf5baloowidgets5 libkf5bookmarks-data
  libkf5bookmarks5 libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5 libkf5config-bin
  libkf5config-data libkf5configcore5 libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5 libkf5coreaddons-data
  libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5 libkf5declarative-data
  libkf5declarative5 libkf5dnssd-data libkf5dnssd5 libkf5doctools5 libkf5filemetadata-bin libkf5filemetadata-data
  libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5
  libkf5guiaddons-bin libkf5guiaddons-data libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin
  libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data
  libkf5jobwidgets5 libkf5kcmutils-data libkf5kcmutils5 libkf5kdcraw5 libkf5kexiv2-15.0.0 libkf5kiocore5
  libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiontlm5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff-data
  libkf5newstuff5 libkf5newstuffcore5 libkf5notifications-data libkf5notifications5 libkf5package-data libkf5package5
  libkf5parts-data libkf5parts-plugins libkf5parts5 libkf5quickaddons5 libkf5service-bin libkf5service-data libkf5service5
  libkf5solid5 libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5syndication5abi1
  libkf5syntaxhighlighting-data libkf5syntaxhighlighting5 libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin
  libkf5wallet-data libkf5wallet5 libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5
  libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libkuserfeedbackcore1
  libkuserfeedbackwidgets1 libkwalletbackend5-5 liblua5.2-0 libmad0 libmatroska7 libmpcdec6 libopenexr25
  libopenmpt-modplug1 libpackagekitqt5-1 libphonon4qt5-4 libphonon4qt5-data libplacebo192 libpolkit-qt5-1-1
  libpoppler-qt5-1 libprotobuf-lite23 libproxy-tools libqmobipocket2 libqt5printsupport5 libqt5qml5 libqt5qmlmodels5
  libqt5qmlworkerscript5 libqt5quick5 libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5sql5
  libqt5sql5-sqlite libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5 libqt5xml5 libresid-builder0c2a
  libsdl-image1.2 libsdl1.2debian libsidplay2 libsndio7.0 libspatialaudio0 libsquashfuse0 libupnp13 libvlc-bin libvlc5
  libvlccore9 libvoikko1 libyuv0 libzip4 phonon4qt5 phonon4qt5-backend-vlc qml-module-org-kde-kirigami2
  qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff qml-module-org-kde-userfeedback
  qml-module-qtgraphicaleffects qml-module-qtqml-models2 qml-module-qtquick-controls2 qml-module-qtquick-layouts
  qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2 qtspeech5-speechd-plugin qtwayland5
  sonnet-plugins vlc-data vlc-plugin-base vlc-plugin-video-output
Suggested packages:
  tk | wish dolphin-plugins qt5-qmltooling-plugins sndiod voikko-fi phonon4qt5-backend-gstreamer hspell libdvdcss2
The following NEW packages will be installed:
  baloo-kf5 catdoc dolphin ffmpegthumbs gamin kactivities-bin kactivitymanagerd kded5 kdegraphics-thumbnailers
  keditbookmarks kimageformat-plugins kinit kio kio-extras kio-extras-data kpackagelauncherqml kpackagetool5
  kuserfeedback-doc kwayland-data kwayland-integration libappimage0 libavif13 libcddb2 libdbusmenu-qt5-2 libdc1394-25
  libdca0 libdolphinvcs5 libdvbpsi10 libebml5 libepub0 libfaad2 libgamin0 libgav1-0 libhfstospell11 libilmbase25 libixml10
  libkate1 libkdsoap1 libkf5activities5 libkf5activitiesstats1 libkf5archive5 libkf5attica5 libkf5auth-data libkf5auth5
  libkf5authcore5 libkf5baloo5 libkf5balooengine5 libkf5baloowidgets-bin libkf5baloowidgets-data libkf5baloowidgets5
  libkf5bookmarks-data libkf5bookmarks5 libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5
  libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5
  libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5
  libkf5declarative-data libkf5declarative5 libkf5dnssd-data libkf5dnssd5 libkf5doctools5 libkf5filemetadata-bin
  libkf5filemetadata-data libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5
  libkf5globalaccelprivate5 libkf5guiaddons-bin libkf5guiaddons-data libkf5guiaddons5 libkf5i18n-data libkf5i18n5
  libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kcmutils-data libkf5kcmutils5 libkf5kdcraw5 libkf5kexiv2-15.0.0
  libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiontlm5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff-data
  libkf5newstuff5 libkf5newstuffcore5 libkf5notifications-data libkf5notifications5 libkf5package-data libkf5package5
  libkf5parts-data libkf5parts-plugins libkf5parts5 libkf5quickaddons5 libkf5service-bin libkf5service-data libkf5service5
  libkf5solid5 libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5syndication5abi1
  libkf5syntaxhighlighting-data libkf5syntaxhighlighting5 libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin
  libkf5wallet-data libkf5wallet5 libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5
  libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libkuserfeedbackcore1
  libkuserfeedbackwidgets1 libkwalletbackend5-5 liblua5.2-0 libmad0 libmatroska7 libmpcdec6 libopenexr25
  libopenmpt-modplug1 libpackagekitqt5-1 libphonon4qt5-4 libphonon4qt5-data libplacebo192 libpolkit-qt5-1-1
  libpoppler-qt5-1 libprotobuf-lite23 libproxy-tools libqmobipocket2 libqt5printsupport5 libqt5qml5 libqt5qmlmodels5
  libqt5qmlworkerscript5 libqt5quick5 libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5sql5
  libqt5sql5-sqlite libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5 libqt5xml5 libresid-builder0c2a
  libsdl-image1.2 libsdl1.2debian libsidplay2 libsndio7.0 libspatialaudio0 libsquashfuse0 libupnp13 libvlc-bin libvlc5
  libvlccore9 libvoikko1 libyuv0 libzip4 phonon4qt5 phonon4qt5-backend-vlc qml-module-org-kde-kirigami2
  qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff qml-module-org-kde-userfeedback
  qml-module-qtgraphicaleffects qml-module-qtqml-models2 qml-module-qtquick-controls2 qml-module-qtquick-layouts
  qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2 qtspeech5-speechd-plugin qtwayland5
  sonnet-plugins vlc-data vlc-plugin-base vlc-plugin-video-output
0 upgraded, 203 newly installed, 0 to remove and 17 not upgraded.

```
Scary, eh? This would all be hidden from you if you used Ubuntu Software. The problem here is that Dolphin uses Qt whereas vanilla Ubuntu is GTK. Therefore, for the system to install Dolphin, it must also drag in a bunch of Qt libraries.

I don't want to be an alarmist. I'm sure there are people who use Dolphin in a vanilla Ubuntu environment and don't run into trouble. But I can't help asking "why"? Isn't this risking big exposure for minuscule gain? What fundamental feature does Dolphin offer that Nautilus does not? And if it's so important to you, why not just install Kubuntu in the first place as a flavour that is built to work with Dolphin?

In your case, the question would be, why not just use Xubuntu instead of Ubuntu? Thunar is native to Xubuntu but not to Ubuntu. Just food for thought.

---

### Post by ajgreeny on 2023-03-06
Iv you simply run ***sudo apt install app-name*** the package will be installed immediately only if there are no dependencies pulled in with it.
If there are any dependencies which need to be installed you will be shown a list of packages and how large the total download will be with a n/Y (no or Yes) request, the upper case Y being default and actioned simply by hitting Enter. To stop the installation just hit n and the process will immediately be aborted.

Simple and effective with all the details you need to make such a decision. It's what I always use though occasionally I find it easier to search for packages using synaptic, the only GUI package manager worth using in my opinion.

EDIT:
DuckHook was quicker than me but largely gave you the same information!

---

