---
title: "Best way to install Firefox 1.5 Beta 1?"
date: 2005-09-09
forum: General Help
---

### Post by sk545 on 2005-09-09
How do i install this in hoary?  I mean, do i have to remove the old one (1.06) first?  But if i try to do that, it removes all of these too:

The following packages will be REMOVED:   firefox* firefox-gnome-support* mozilla-firefox*   mozilla-firefox-gnome-support* ubuntu-desktop* yelp*

Wouldn't that break the system?

Thx.

---

### Post by Ibuntu_52 on 2005-09-09
I had all kinds of problems installing it thru apt-get and synaptic.When I installed it It just wouldn't work.

So I just unistalled firefox with apt-get (apt-get remove firefox, apt-get remove mozilla-firefox) . then I downloaded it from the firefox webpage and installed that one.Now it works fine ;-)

btw the removal of those packages will not break your system.You can remove ubuntu-desktop and put it back on after installing firefox.

---

### Post by sk545 on 2005-09-10
How were you using apt-get?  I don't see FF 1.5B1 in the repository of Ubuntu... :confused: 

Also, if i install from the tar.gz, how do i point the mozilla path so that it finds the plugins in /usr/lib/mozilla-firefox/plugins? 

Plus, its weird that the instructions on the beta website state this:

```
Extract the tarball and run the installer like so: 

tar -xzvf firefox-1.5b1.installer.tar.gz
cd firefox-installer
./firefox-installer

```
But there is no such thing as 'firefox-installer' in the tar.gz archive.

---

### Post by mcmuffy on 2005-09-10
I found just extracting and running the 'firefox' script did the trick for me. Runs from whereever you put it on your HDD. All my bookmarks were picked up and I did not have to remove 1.0.6 which I have in reserve incase things go tango uniform.

---

### Post by sk545 on 2005-09-10
but did it pick up the plugins?  Check by typing 'about: plugins' in the address bar.

---

### Post by mikaoj on 2005-09-10
[QUOTE=sk545]
Plus, its weird that the instructions on the beta website state this:

```
Extract the tarball and run the installer like so: 

tar -xzvf firefox-1.5b1.installer.tar.gz
cd firefox-installer
./firefox-installer

```
But there is no such thing as 'firefox-installer' in the tar.gz archive.[/QUOTE]

If you browse the ftp archive you will find firefox-1.5b1.installer.tar.gz :)

---

### Post by sk545 on 2005-09-11
I see...so, anyone know how to set the path in firefox beta so that it will see the plugins in my /usr/lib/mozilla-firefox/plugin directory?

---

### Post by codejunkie on 2005-09-11
[QUOTE=sk545]I see...so, anyone know how to set the path in firefox beta so that it will see the plugins in my /usr/lib/mozilla-firefox/plugin directory?[/QUOTE]
go to the where you placed the beta version of firefox remove the plugins folder and then open a terminal and cd to that location and do 
```
sudo ln -s /usr/lib/mozilla-firefox/plugins
``` this just creates a symbolic link to your old firefox plugin dir but it should work just fine.

---

### Post by sk545 on 2005-09-11
thx, that worked.  Maybe a how-to should be put up about this, no?

---

### Post by pongster on 2005-09-28
[QUOTE=mcmuffy]I found just extracting and running the 'firefox' script did the trick for me. Runs from whereever you put it on your HDD. All my bookmarks were picked up and I did not have to remove 1.0.6 which I have in reserve incase things go tango uniform.[/QUOTE]

I did exactly what mcmuffy said and my deer park alpha 2 picks evrything up!  is there a way to actually install it and have it be part of the Applications-Internet Menu?

---

### Post by overgee on 2005-09-30
There is a Debian package at [http://packages.debian.org/experimental/web/mozilla-firefox]("http://packages.debian.org/experimental/web/mozilla-firefox"). It needs to be re-compiled since it does not work with ubuntu dependencies. May be someone having a little expirience compiling binaries from source can try.
Source packages can be found at [http://ftp.debian.org/debian/pool/main/m/mozilla-firefox/]("http://ftp.debian.org/debian/pool/main/m/mozilla-firefox/").
I think it has to be renamed so it replaces firefox 1.0.7 package.

---

