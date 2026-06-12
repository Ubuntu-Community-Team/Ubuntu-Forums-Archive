---
title: "Do Ubuntu software updates change or add files in the home directory?"
date: 2023-05-19
forum: General Help
---

### Post by Advait on 2023-05-19
If yes, is it common or rare for this to happen?

sudo apt update && sudo apt upgrade

I'm using Ubuntu 22.04 Gnome Wayland.

---

### Post by Holger_Gehrke on 2023-05-19
No, the updates themselves usually don't change or add things in $HOME. The archives inside .deb packages are meant to be unpacked in the root directory and the user name(s) and home directories aren't known to the packager, so putting files into $HOME is not trivial (unpacking is done as root - either through sudo or pkexec, so you can't use the environment variable HOME which at that point contains '/root'). But there are scripts inside the package which get called before and after unpacking and you could in theory put files in user's directories from those scripts. Normally changes in user's directories are done by the installed programs when they are run (writing a user specific configuration file into $HOME or $HOME/.config.

Holger

---

### Post by The Cog on 2023-05-19
Holger_Gehrke is absolutely right. I would add that this means that your personal settings for apps (browser settings, LibreOffice settings etc.) do not get removed by uninstalling and reinstalling an application. However, an updated application *may* choose to automatically update your personal settings for that application the first time you run the new version.

---

### Post by Advait on 2023-05-19
"No, the updates themselves usually don't change or add things in $HOME."

So you're saying that sometimes (maybe rarely) an update/upgrade will change something in home. I'm asking cuz in the future I plan to install Btrfs (with separate partitions for root and home). And I wanted to know if I needed to snapshot both root and home partitions before update/upgrade. Looks I will need to snapshot both before an update/upgrade.

---

### Post by ajgreeny on 2023-05-19
Newly installed packages never in my experience add any files or folders to the user's home
However, at first run of the new application by a user there will generally be additions made to home of the user who runs the software with their own cache and local configuration details.

For example, a computer with two separate users each with their own home.  The admin user installs an application, eg VLC multimedia player.
Each user will, once they have used VLC, have a folder in both .cache and .config with details of the use and configuration chosen for VLC.  If a user never opens VLC those folders will not exist in their home.

---

### Post by Advait on 2023-05-19
I'm a little confused. What do you mean by "newly installed packages"? How does that relate to the usual run of the mill update/upgrade? 

You mean a new package (app)? Or an update to an existing package? In my mind "package" = app. A package is just another name for some program on my system. Is that correct? A system program (like those in the OS) and user programs like LibreOffice, etc. 

Please clarify. Thanks.

---

### Post by ian-weisser on 2023-05-19
> **Advait said:**
> If yes, is it common or rare for this to happen?

sudo apt update && sudo apt upgrade

It is possible, but very rare. Rather like a meteor striking your home. Or like successfully changing somebody's mind on the internet.
Keep in mind that a properly-installed Ubuntu system will already run the equivalent commands twice daily for security updates *without telling you. *Completely in the background. Most folks never notice it at all.

Frequent snapshots are a good idea for lots of reasons. Regardless of the cause, nobody has ever complained about having a recent backup when they needed it.

---

### Post by Holger_Gehrke on 2023-05-19
> **Advait said:**
> In my mind "package" = app. A package is just another name for some program on my system.

That's right for snap, but for .deb packages it isn't ... quite. Debian packages are more granular. Even a comparably simple program might be made up of several packages, the actual program and the libraries it depends on. Let's take LibreOffice as an example: there is a (Meta-)package libreoffice, which depends on libreoffice-{base,calc,draw,impress,math,report-builder-bin,writer} plus libreoffice-core and python3-uno. Each of these packages again depends on other packages ... The ideas behind this are reuse of packages (why have each program install it's own libraries ? split the libraries into their own package) and minimising install size (I don't write in French, so why should my office package install dictionaries and message files for this and heaven knows how many other languages); also there are variants of programs compiled for many architectures, so binaries and non-architecture dependent data are put into their own separate packages.

Holger

---

### Post by Advait on 2023-05-20
> **ian-weisser said:**
> It is possible, but very rare. Rather like a meteor striking your home. Or like successfully changing somebody's mind on the internet.
Keep in mind that a properly-installed Ubuntu system will already run the equivalent commands twice daily for security updates *without telling you. *Completely in the background. Most folks never notice it at all.

Frequent snapshots are a good idea for lots of reasons. Regardless of the cause, nobody has ever complained about having a recent backup when they needed it.

Thanks. Very helpful. Presumably I could check the size and and file numbers of the home partition before and after an update to see if anything got changed.

---

### Post by Advait on 2023-05-20
> **Holger_Gehrke said:**
> That's right for snap, but for .deb packages it isn't ... quite. Debian packages are more granular. Even a comparably simple program might be made up of several packages, the actual program and the libraries it depends on. Let's take LibreOffice as an example: there is a (Meta-)package libreoffice, which depends on libreoffice-{base,calc,draw,impress,math,report-builder-bin,writer} plus libreoffice-core and python3-uno. Each of these packages again depends on other packages ... The ideas behind this are reuse of packages (why have each program install it's own libraries ? split the libraries into their own package) and minimising install size (I don't write in French, so why should my office package install dictionaries and message files for this and heaven knows how many other languages); also there are variants of programs compiled for many architectures, so binaries and non-architecture dependent data are put into their own separate packages.

After reading this I'm slightly less newbie. :P

---

