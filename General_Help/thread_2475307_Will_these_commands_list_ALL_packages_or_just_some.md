---
title: "Will these commands list ALL packages or just some?"
date: 2022-05-22
forum: General Help
---

### Post by sofasurfer on 2022-05-22
I am learning about listing packages on my system.  My goal is to simply list all installed on my system, no matter what package management tool they are installed by. I would also what to be able to grep specific packages. I am confused as to what apt, apt-get and dpkg do differently. Would the commands only list debian packages or would they also list rpms. I think Debian and rpm are the only ones that would be on a Ubuntu system...right or wrong?

---

### Post by sofasurfer on 2022-05-22
!!!

---

### Post by Impavidus on 2022-05-22
apt, apt-get and dpkg all deal with .deb packages, so they all list the same. Normally you won't find rpm packages on Ubuntu. There are also flatpack, appimage and snap packages, which use different tools. On recent Ubuntu releases, you're likely to find some snap packages installed.

---

### Post by Dennis N on 2022-05-22
There are also packages installed without the aid of a package manager. These include AppImages and applications distributed in archives. Firefox for example, can be installed from a .tar.bz archive without involving any package manager. So these things you cannot list with some terminal command.

---

### Post by Holger_Gehrke on 2022-05-22
'.deb' means Debian package. Ubuntu is based on Debian. '.rpm' is the **R**edhat **P**ackage **M**anager. It would be very unusual (read: an invitation to disaster) to have rpm running on Ubuntu. If a package is only available as an rpm you'd try to convert the package into a .deb by using 'alien' (and you'd probably have a lot of trouble getting it to work).

'dpkg*' (there are several tools whose names start with dpkg; they are related but all do slightly different things up to and including building your own packages) work on local files and the local database of installed packages. 'apt-*' adds the ability to install packages from remote repositories and handle package dependencies (dpkg recognizes dependencies and will tell you if you need some other package to be able to install and run a package, but it can't download and install them automatically like apt-* can). Finally 'apt' is a combination of some of the apt-* tools in one program. It's meant to have the most common tasks all in one tool for interactive use on the command line.

To get an idea of what tools there are, go to the command line, type 'dpkg' or 'apt' and hit the tabulator key twice. You'll get lists of all programs whose names start with 'dpkg' (or with 'apt'). Now that you have those names, you can read the respective manual pages with 'man *programname*'.

Similarly 'snap' is the tool to deal with snap-packages. This too has a manual page, as does 'flatpak'. The appimages Impavidus mentions are a special case; each is everything belonging to one program that would normally be spread out over dozens of file rolled into one executable file; just download, mark as executable and run - no package-management involved.

If you want a grep-able list of packages, 'dpkg-query --show --showformat '${Package}\n' will get you something usable. For snap the best I can come up is something like "snap list|tail +2|cut -d' ' --fields=1" or you could just look at the files in '/var/lib/snapd/snaps'.

Holger

---

