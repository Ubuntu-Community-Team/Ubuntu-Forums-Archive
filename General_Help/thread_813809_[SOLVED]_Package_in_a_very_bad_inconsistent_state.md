---
title: "[SOLVED] Package in a very bad inconsistent state"
date: 2008-05-31
forum: General Help
---

### Post by abujenin on 2008-05-31
I am having a problem with a package that was not fully installed and now i cannot remove it nor reinstall it, nor install any other package. 
Package is libvlc0. I running Hardy.

I tried:
```
sudo apt-get remove libvlc0 

dpkg: error processing libvlc0 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing: libvlc0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And when I try reinstalling it again:
```
sudo apt-get -f --reinstall install libvlc0

Errors were encountered while processing:
 /var/cache/apt/archives/libvlc0_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried deleting it from the archive, and downloading it again from different source, but faced the same problem. Running dpkg gives similar errors, and also Synaptic gives similar errors (on reinstalling gives: files list file for package `libvlc0' is missing final newline).

How can I fix this?

---

### Post by abujenin on 2008-06-01
I found the solution [http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html)

1st: I must delete all relevant files in /var/lib/dpkg/info 
```
sudo rm /var/lib/dpkg/info/libvlc* 
```

2nd: Force remove with dpkg
```
 sudo dpkg -r --force-depends --force-remove-reinstreq libvlc0 
```

---

### Post by mirage on 2009-11-09
Thanks, that helped!

---

### Post by fluffydanoob on 2009-12-22
I'm having a very similar problem which cropped up during an automatic update, but instead of fixing anything, the above solution added an extra error or two. First, I get this:

```
Setting up jockey-common (0.5.5-0ubuntu3) ...
Killed
dpkg: error processing jockey-common (--configure):
 subprocess installed post-installation script returned error exit status 137
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on jockey-common (= 0.5.5-0ubuntu3); however:
  Package jockey-common is not configured yet.
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 jockey-common
 jockey-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Deleting all jockey* files lets me reinstall jockey-gtk without any error messages. However, if I now reinstall jockey-common again, I get back to the original error I was getting at the start:
```
E: jockey-common: subprocess installed post-installation script returned error exit status 137
```
I've tried completely removing it and then installing it anew. Nothing seems to work.

In related news, Movie Player suddenly does not work, also as of this broken update. "Ubuntu Software Center" likewise. And the update icon in the corner doesn't do anything anymore. I can right-click on it and give it commands, but nothing happens. EDIT: Huh, rebooted and everything is fine now. Weeeird.

---

