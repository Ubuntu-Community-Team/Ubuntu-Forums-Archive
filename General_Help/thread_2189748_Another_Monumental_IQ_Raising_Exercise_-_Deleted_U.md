---
title: "Another Monumental IQ Raising Exercise - Deleted Ubuntu Firefox and..."
date: 2013-11-23
forum: General Help
---

### Post by Wroger on 2013-11-23
How I got into this. Had not updated a system for 3 or 4 months. Big update and a few extras. Moved 1800 TTF fonts into font directory. Did the restart - though not necessarily in the order described. (it was late - I was tired)

    Started up Firefox and click boxes were clear, auto-completion was happening with ONE letter entered, with neither the letter displaying, nor the results of the auto-search / auto completion displaying. Installed two other browsers - they worked fine. Decided that the browser was defective. Commenced the uninstall - and after reading the WARNING that removing FIREFOX, would also delete many parts of the system files like startxfce4, thunar etc., etc., etc., knowing that it would probably lead to major issues - I went and uninstalled it anyway.

        Then while it was all still running I downloaded a NON Ubuntu version of Firefox.... and it appears that in the Ubuntu system - no longer means actually uninstalling the actual program, because when I installed the Linux version of Firefox, Firefox-25.0.1.tar.bz2, it seemed to be an exact copy of the version I had deleted seemingly complete with all the formers settings.

    So where am I at now. I can boot up into Xubuntu - but because startxfce4 had been deleted, it defaulted to a desktop with no menus.

    Hmmm genius move thinks I. 

Here in lies the issue. I want to fix my system.

I still have access to the filing system - Nautilus.

By searching for TERMINAL, I can find the executable link for Xterminal.

The system is encrypted, so I can log in, but I can't or don't know how to insert the any files into it via a running copy of Xubuntu from a USB stick

I have done an apt-get update of the system - which seemed to install some things, but did not restore the system.

It is auto logging into the internet connection when I hook that up - but I can't see any panels to gain control over it.

Alt-F2 does not run. 

Using Nautilus - I got "System Monitor" + "Chromium" working by Open With

   
IS there a LOG of the messages that have been displayed - that would show exactly what files have been removed when firefox was uninstalled? 

I found this in the .var/backups/dpkg.status.0 
These are the ones that I think are connected with the startxfce4 file - in ****-***

    ~~~~~~~~~~~~~~~~

    Package: *****xfce4-utils****
    Status: install ok installed
    Priority: optional
    Section: xfce
    Installed-Size: 2469
    Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
    Architecture: amd64
    Version: 4.8.3-1ubuntu2
    
*****Depends: libc6 (>= 2.3.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libglib2.0-0 (>= 2.18.0), libgtk2.0-0 (>= 2.16.0), libxfce4ui-1-0, libxfce4util4 (>= 4.3.99.2), xterm | x-terminal-emulator, x11-xserver-utils, xinit, exo-utils, procps

    Pre-Depends: dpkg (>= 1.15.7.2)
    Recommends: xfwm4, xfce4-panel, thunar, xscreensaver | xlockmore | xlockmore-gl, dbus-x11, xinput, xdg-user-dirs*********

    Suggests: xfce4-session
    Conffiles:
    /etc/xdg/xfce4/xinitrc 9ea339d739a2175d086caf103c3ec3d5
    /etc/xdg/xfce4/Xft.xrdb be007703931906a013b32f3d96cd31b2
    Description: Various tools for Xfce
    This package contains xfrun4, xfterm4, xflock4, xfmountdev4, xfbrowser4,
    startxfce4, xfhelp4, xfce4-about, eight tools for Xfce. Xfce is a desktop
    environment that uses the GTK+ library and isn't resource-hungry.
    .
    If you want to use xfmountdev4, be sure to install Thunar before because it's
    called by it.
    Homepage: [http://www.xfce.org/](http://www.xfce.org/)
    Original-Maintainer: Debian Xfce Maintainers <pkg-xfce-devel@lists.alioth.debian.org>

    ~~~~~~~~~~~~~~~~

    So I am thinking 

A. The system files have been restored and the links to the programs needs to be established... or

B. The whole program group needs to be extracted from a live version running from a USB stick, copied to a drive and then when the encrypted filing system is running, it can be transplanted across.

Can help me find the message log that MIGHT have the list of files that uninstalling Firefox created?

And or can someone running Xubuntu - begin the process of uninstalling Firefox - without actually completing it - to see get a list of the files that will be affected / deleted - and then post them here - prior to cancelling the removal?

Overall. 

Am I going about this the right way or ways?

Any thoughts on the subject?

Meaningful help would be appreciated.

---

### Post by Impavidus on 2013-11-24
There's hardly any difference between the Ubuntu version of firefox and the normal version. Just a few tweaks, like to put the menus in the top bar in Unity I think. Uninstalling firefox and reinstalling the different version did not clean the configuration files, especially your profile, which you must delete (or rename) yourself. That could have solved your original problem.

You can always access the command line by hitting ctrl-alt-F1 (or F2...F6). This will give you the console. Hit ctrl-alt-F7 to get back to the GUI.

---

### Post by Wroger on 2013-11-24
Hmm.

Thanks for that.....

Still have lots to do though.

I mean I love doing the exploring and finding out stuff, and I do want to restore my system without trashing it...

This means IQ raising by smarts, hard work, some (tolerable) mistakes and lots of time, reading and research.

I just don't have infinite amounts of them.

Any helps on this would be appreciated.

---

