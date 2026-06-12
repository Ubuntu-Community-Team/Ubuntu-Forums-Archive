---
title: "mednafen installation issue."
date: 2008-01-11
forum: General Help
---

### Post by Moonfrost on 2008-01-11
I just downloaded a .deb package containing mednafen 0.8.7-1 from the official website (I know they have mednafen on the repos but it's an older version), the package does not want to install because it says "dependency not satisfiable libc6", I tried ```
apt-get install libc6
``` but it told me it didn't install or upgrade anything...what is this library and why can't I install it?

EDIT: I checked Synaptic and it shows I already have "libc6" installed but the package still won't install giving me the same error "dependency not satisfiable libc6"...

EDIT #2: I tried cd ~/Desktop to go into the desktop on a command line, then I tried

```
sudo install mednafen_0.8.7-1_i386.deb
```

and that gave me the following error

```
missing destination file operand after `mednafen_0.8.7-1_i386.deb'
```

---

### Post by yabbadabbadont on 2008-01-11
It apparently requires a different version of libc6 than the one included in the repositories and currently installed on your system.  Your best bet would be to try building it from source.  In order to install the required development packages, I would try something like this:
```
sudo -i
apt-get install build-essential xorg-dev automake autoconf libtool flex bison
apt-get build-dep mednafen

```
That should probably install all of the dependencies required for building it from source.

You should also make sure that you have the linux-headers for your kernel installed.  I think that they are included by default in Feisty and Gutsy, but it doesn't hurt to check.

---

### Post by rubicon on 2008-01-11
First: Never heard that .deb packages could be installed by ```
sudo install mednafen_0.8.7-1_i386.deb
```

Have you forgot something? ;)

And second: if you use Gnome, then double-click on this package to open it in GDebi.

Third: If you cannot install newer libc6 for your Ubuntu version, then the library must be still unreleased for it.

Have you done ```
sudo apt-get update
sudo apt-get upgrade
```? If you have done it, then your system is up-to-date and installing something like newer libc may be risky, because of this lib's dependencies (90% of programs depend on this library, and if it is screwed...).

---

### Post by Moonfrost on 2008-01-11
> **rubicon said:**
> First: Never heard that .deb packages could be installed by ```
sudo install mednafen_0.8.7-1_i386.deb
```

Have you forgot something? ;)

And second: if you use Gnome, then double-click on this package to open it in GDebi.

Third: If you cannot install newer libc6 for your Ubuntu version, then the library must be still unreleased for it.

Have you done ```
sudo apt-get update
sudo apt-get upgrade
```? If you have done it, then your system is up-to-date and installing something like newer libc may be risky, because of this lib's dependencies (90% of programs depend on this library, and if it is screwed...).

Ok yeah I know that already, but the install manager wouldn't install it so I just tried whatever...and I already tried upgrade and it says it's up to date, I also tried ```
sudo apt-get install
```

but it told me that I already had it installed...

---

### Post by Moonfrost on 2008-01-11
[QUOTE=yabbadabbadont;4114472]It apparently requires a different version of libc6 than the one included in the repositories and currently installed on your system.  Your best bet would be to try building it from source.  In order to install the required development packages, I would try something like this:
```
sudo -i
apt-get install build-essential xorg-dev automake autoconf libtool flex bison
apt-get build-dep mednafen

```
That should probably install all of the dependencies required for building it from source.

You should also make sure that you have the linux-headers for your kernel installed.  I think that they are included by default in Feisty and Gutsy, but it doesn't hurt to check.[/QUOTE

When I try to fix some dependencies for mednafen this comes out

```
You must put some 'source' URIs in your sources.list
```

I already tried the first one and it installed quite a lot of libraries/files but when I try to install mednafen it's still the same error...

---

### Post by yabbadabbadont on 2008-01-11
Those commands are only to get your system in a state so that you can build the mednafen package from source that you download from their website.  You wanted a newer version, so download the source for that version from their site and try to build it.  They should provide instructions for building from source somewhere on their site.

---

