---
title: "Removal of Inkscape from Ubuntu22.04"
date: 2024-06-19
forum: General Help
---

### Post by grey1beard on 2024-06-19
Having found the problem that the latest version of Inkscape(ver. 1.3.2) that I had installed would not export png files, I want to go back to an earlier version.
How do I make a clean removal of the software, so that I can make a clean install of an earlier version ?
MTIA,
John
EDIT I tried using the Ubuntu Software in Activities, where it says that Inkscape is installed, but clicking on the uninstall button returns > 'Cannot remove Inkscape: cannot perform the following tasks:' with no further explanation !
EDIT 2 Tried Terminal  **> sudo apt remove --autoremove inkscape**
> Package 'inkscape' is not installed, so not removed


---

### Post by dragonfly41 on 2024-06-20
I have not used Inkscape for a while.
I launched it and clicked on the debug icon (ladybird image bottom right) and this was returned.
You might compare.

Inkscape 1.1.2 (0a00cf5339, 2022-02-04)
    GLib version:     2.72.4
    GTK version:      3.24.33
    glibmm version:   2.66.2
    gtkmm version:    3.24.5
    libxml2 version:  2.9.13
    libxslt version:  1.1.34
    Cairo version:    1.16.0
    Pango version:    1.50.6
    HarfBuzz version: 2.7.4
    Poppler version:  22.02.0
    OS version:       Ubuntu 22.04.4 LTS

---

### Post by Dennis N on 2024-06-20
I use the Flatpak of Inkscape, and it has multiple export options, with .png as default. The Flatpak is also version 1.3.2. Please see the screenshot of export menu options. I'd be surprised if the .deb wasn't the same, but maybe its not.

It's possible you have a snap package of Inkscape if apt doesn't show it as installed.

---

### Post by grey1beard on 2024-06-20
Dragonfly - first problem is that I can't launch Inkscape.
Dennis - I went to Activities/Ubuntu Software (Is this the same as going to the 'Snap Store' ?) where it said it was installed, and got the message as in #1.
Can I install inkscape via Flatpack if there are bits of my original inkscape version still present ?

Tried Terminal - see #1
John

---

### Post by dragonfly41 on 2024-06-20
inkscape --debug-info
shows nothing?

---

### Post by grahammechanical on 2024-06-20
The 22.04 App Centre (Ubuntu Software) may have installed Inkscape as a snap packaged app.

```
snap list
```

If it is a snap application, then

```
sudo snap remove <package name>
```

Will remove it. I might be wrong, but I think that Ubuntu Software in 22.04 LTS was in fact, the snap store by another name and could not install deb packaged apps.

I am on 24.04 LTS and a recent update has improved the App Centre so that it offers both snap packaged and Debian (deb) packaged versions if both are available. It certainly offers both a snap and a deb packaged version of Inkscape.

[https://www.omgubuntu.co.uk/2024/06/deb-installer-in-ubuntu-app-center-coming-soon](https://www.omgubuntu.co.uk/2024/06/deb-installer-in-ubuntu-app-center-coming-soon)

Regards

---

### Post by grey1beard on 2024-06-20
Yes, snap list showed it present, but 'disabled' (?)
Tried  [B]sudo snap remove inkscape
[/B] and got - 
> [sudo] password for john: 
error: cannot perform the following tasks:
- Remove data for snap "inkscape" (10555) (failed to remove snap "inkscape" base directory: remove /home/john/snap/inkscape: directory not empty)

---

### Post by grey1beard on 2024-06-21
>  inkscape --debug-info

Is this a terminal command ? I tried it, as is, but got nothing.
Regards 
John

---

### Post by Dennis N on 2024-06-21
I would check if the snap application is still there or not. Just run in terminal **snap list**
The output would include inkscape IF it's still there.

If it's gone, you can go ahead and install the .deb version or the Flatpak version. But the .deb version in 24.04 is 1.2.2, not the latest. If you want to have version 1.3.2 (the latest), you can install the Flatpak package. As I said previously, it definitely has all the export options.

---

### Post by #&amp;thj^% on 2024-06-21
I ran into this on 23.10, it is clear by now I'm not a snap user period....Dennis N has a good suggestion (Flatpak)

But there is another way for a current .deb: [https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable](https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable)

This won't fix snap, but it will solve your problem:

    Uninstall the snap package of Inkscape:

```
    sudo snap remove inkscape
```

    Install the official Ubuntu package from Inkscape's ppa at [https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable:](https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable:)

  ```
  sudo add-apt-repository ppa:inkscape.dev/stable
    sudo apt-get update
    sudo apt-get install inkscape

```
```
inkscape --debug-info
Inkscape 1.3.2 (091e20ef0f, 2023-11-25, custom)

    GLib version:     2.80.3
    GTK version:      3.24.42
    glibmm version:   2.66.7
    gtkmm version:    3.24.9
    libxml2 version:  2.13.0
    libxslt version:  1.1.40
    Cairo version:    1.18.0
    Pango version:    1.54.0
    HarfBuzz version: 8.5.0


```
Good luck though on any path you choose.

---

### Post by grey1beard on 2024-06-21
> 
This won't fix snap, but it will solve your problem:

    Uninstall the snap package of Inkscape:

```
    sudo snap remove inkscape
```


Still run into brick wall, as #7 !
> sudo snap remove inkscape
error: cannot perform the following tasks:
- Remove data for snap "inkscape" (10555) (failed to remove snap "inkscape" base directory: remove /home/john/snap/inkscape: **directory not empty**)

---

### Post by grey1beard on 2024-06-21
DennisN, I went to the Flathub page, but I'm a bit concerned about para 2. ->  Install the Software Flatpak plugin

The Flatpak plugin for the Software app makes it possible to install apps without needing the command line. To install, run:
sudo apt install gnome-software-plugin-flatpak
Note: the Software app is distributed as a Snap since Ubuntu 20.04 and does not support graphical installation of Flatpak apps. **Installing the Flatpak plugin will also install a deb version of Software and result in two Software apps being installed at the same time**.

Question - do I need the plugin ? (I'm happy with using Terminal for app installations)
Regards
John

---

### Post by #&amp;thj^% on 2024-06-21
Xubuntu here:
```
apt policy gnome-software-plugin-flatpak
gnome-software-plugin-flatpak:
  Installed: (none)
  Candidate: 46.2-1
  Version table:
     46.2-1 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
```
I use Topgrade to update everything on all my systems:
```
&#9472;&#9472; 13:22:13 - Summary &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
System update: OK
config-update: OK
Firmware upgrades: OK
Flatpak: OK
cargo: OK

```
Flatpak version:
```
flatpak list | grep inkscape
Inkscape	org.inkscape.Inkscape	1.3.2	stable	flathub	system

```
Both seem to work on my end.
```
apt policy inkscape
inkscape:
  Installed: 1:1.3.2+202404261509+091e20ef0f~ubuntu24.04.1
  Candidate: 1:1.3.2+202404261509+091e20ef0f~ubuntu24.04.1
  Version table:
 *** 1:1.3.2+202404261509+091e20ef0f~ubuntu24.04.1 100
        100 /var/lib/dpkg/status
     1.2.2-2ubuntu12 500
        500 http://archive.ubuntu.com/ubuntu oracular/universe amd64 Packages

```

And you might have to first back-up:
```
mv  /home/john/snap/inkscape /Documents
```
For a backup.
Then:
```
rm -rf  /home/john/snap/inkscape
```
To see if that fixes the .deb version

---

### Post by Dennis N on 2024-06-21
> Question - do I need the plugin ? (I'm happy with using Terminal for app installations)
Regards
John
The plugin only works with Gnome Software. Not Ubuntu Software, nor the App Center. If you install the plugin, you also get Gnome Software.

It's not required, but I install it because it installs, removes, and automatically checks for and installs updates to Flatpaks as well as .deb packages (and optionally snaps, if you install the gnome-software-plugin-snap as well).  Ubuntu Software and App Center do not manage Flatpaks. Otherwise, Gnome Software (a .deb package) looks and works like Ubuntu Software (a snap package). If you use Gnome Software with its plugins, you don't need Ubuntu Software and can uninstall it. 

The App Center is the new software manager that comes with a new install of Ubuntu 24.04.

```
dmn@tyana:~$ apt search gnome-software-plugin*
Sorting... Done
Full Text Search... Done
gnome-software-plugin-flatpak/noble 46.0-1ubuntu2 amd64
  Flatpak support for GNOME Software

gnome-software-plugin-snap/noble 46.0-1ubuntu2 amd64
  Snap support for GNOME Software
```

---

### Post by grey1beard on 2024-06-21
Entered *apt search gnome-software-plugin**, and got the same result as you show, viz both Flatpak and Snap support Gnome.

> If you use Gnome Software with its plugins - not a question I've ever needed to ask myself, so I've no idea !

Thanks for your help thus far. I have a sense I'm creeping forwards.
Regards
John
ps Hope you're keeping cool - only 95F in Corinth !

---

### Post by Dennis N on 2024-06-21
If you plan to use the terminal to manage flatpaks, that is easy enough. But you need to remember to run flatpak update occasionally to keep them up-to-date - they don't automatically update themselves like snaps do.

I am in the habit of installing and uninstalling flatpaks with the terminal myself. One reason I have gnome software as the "software store" is that it 's a .deb package. Ubuntu's two "stores" are both snaps.

---

### Post by grey1beard on 2024-06-21
I think familiarity with 'package' types is a deeper level than I need to go ! 
This 85yo brain is overloaded already ! :rolleyes:
John

---

### Post by grahammechanical on 2024-06-21
This thread is moved on to a different subject. Here are the instructions for installing and running Flatpaks in Ubuntu.

[https://www.omgubuntu.co.uk/how-to-install-flatpak-on-ubuntu](https://www.omgubuntu.co.uk/how-to-install-flatpak-on-ubuntu)

[https://docs.flatpak.org/en/latest/using-flatpak.html](https://docs.flatpak.org/en/latest/using-flatpak.html)

@grey1beard

Stick with it. A lot of developers are unable to look at things from the ordinary users point of view. Documentation is often comprehensive. Which developers need to produce but which is far to much for the ordinary user. Identify to few commands you need.

Regards

---

### Post by grey1beard on 2024-06-21
> This thread is moved on to a different subject
No, I don't think so. My original question was referencing the need to remove Inkscape because of its inability to export .png files. That the thread has now expanded to the use of Flatpack is surely a suggestion of how to deal with problem by an alternative route, though not specifically answering the original.
Regards
John

---

### Post by grey1beard on 2024-06-22
My grateful thanks to Dennis and Graham for guidance and encouragement. I now have a working installation of Inkscape. 
I will post a confirmation and 'thread solved' in a couple of days, when I've had a chance to test it out.
Regards,
John

---

