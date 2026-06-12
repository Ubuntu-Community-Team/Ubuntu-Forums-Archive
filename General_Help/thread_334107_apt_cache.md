---
title: "apt cache"
date: 2007-01-08
forum: General Help
---

### Post by artinla on 2007-01-08
If I wanted to throw a bunch of .debs into /var/cache/apt/archives and then update the package list so that apt-get could see them, how might I accomplish that?

Note that I already know how to create a repository, that is not what I wish to know.  I want to know where the "package lists" are that tell apt what is in the local cache, and if it is possible to update them to reflect new stuff thrown into the cache.

Thanks,

Art

---

### Post by Ramses de Norre on 2007-01-08
/var/cache/apt/pkgcache.bin seems like a candidate, depending on the filename, but it's a binary...

---

### Post by artinla on 2007-01-08
I tried deleting it, and it gets recreated when I do an apt-get upgrade.. but it still doesn't show the new packages that exist in /var/cache/apt/archives.   I also looked at /var/lib/apt/Extended_states and it was incomplete.  

I created a Packages.gz file with sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz.  I then extracted its contents to Packages (a text file).

I then used "dselect update Packages" to regenerate /var/lib/apt/Extended_states and now that file shows the new packages, but apt-get update doesn't add them to the package list.  Somewhere there must be a file that only apt uses to identify available packages but I can't find it.

For example, I have the most current bison package in the cache, but apt-get install bison says that the package is not avaiable.  

I tried setting /var/cache/apt/archives as a source in /etc/apt/sources.list with the following line:

deb file: /var/cache/apt/archives  as instructed in a howto, but apt gripes the line no matter what syntax that I try to use.   I tried adding "main" to the end of the line and moving the packages to /var/cache/apt/archives/main (and then recreating the Packages.gz using the sudo line above) but it still refuses to see them.   I also made a repository CDROM by copying all the .deb's to it and generating Packages.gz, but when I try to add it in synaptic the system locks up at "Unmounting CDROM".  I can remount the CDROM and use "sudo apt-get cdrom add" to get it to work, but I am trying to script this install and Synaptic is not the answer.  If I can get the list to work from Synaptic (albeit a pain in the rear end) I should be able to do it from the command line (apt-get) as well.

I wish there was a place to read about the inter-workings between synaptic, apt-get and dpkg.  

If there are any experts on the way apt-get stores available (local) package lists, I would sure like to hear from you.

Thanks,

Art

---

### Post by llamakc on 2007-01-08
Why not just install them with `dpkg -i nameof.deb` and then use apt-pinning?

---

### Post by artinla on 2007-01-08
Because when I try that, dpkg bitches about dependencies that are actually satisfied if it would just look in the cache.  I may just be doing it wrong, but apt-get seems to do a much better job of intelligently satisfying dependencies.  

I have 611 packages in the cache that I want to install, and I have already created a script using apt-get.  It works if I fiddle with it and do apt-cdrom add.  The problem is that I want to create a liveCD with all the packages pre-installed in the cache so that I can have them auto install after booting.  I have tried reconstructor but it just doesn't handle permissions or export variables such as HOME properly.   I have burned 20 or more DVD coasters trying to get that program to work.

My last hope to get this idea to work is for the packages to be available and install them in some automatic way after booting the new systems.

I can say with authority that the procedures on the internet for creating local apt caches just don't work.  It wouldn't seem to be such a difficult thing to do.

Thanks,

Art

---

### Post by llamakc on 2007-01-08
611 packages? Are you trying to copy a previously installed package situation from another machine to this one? DPKG has a process for that: --get-selections and --set-selections.

---

### Post by llamakc on 2007-01-08
So the way this works is you get all of the packages from one cache say on TARGET_A with:

dpkg --get-selections > package.list

Then move package.list to the 2nd, new machine.

Now,

dpkg --set-selections < package.list

apt-get dselect-upgrade

That way has certainly worked for me. Perhaps you could fold this into your script in some fashion? If I'm offbase, my apologies.

---

### Post by artinla on 2007-01-08
No, that isn't what I need to do.  Actually, wajig does a nice job of that.

The problem with doing it that way is that it also marks system critical files such as the kernel, driver modules, etc.   I am trying to make this project "machine independent" so that it will install and run on most any computer.  The livecd uses a generic kernel, which I don't want to immediately replace.  I know that I could go in and manually remove each package that might cause trouble, but I am afraid that I would miss something important.  I am not a Linux expert by far, but I am learning.  I have become intimately familiar with creating liveCD/DVD's and there are problems with trying to pre-install packages.  It is becoming apparent that a post-install script that adds the stuff that I want to add is probably the best way to go, but apt-get and dpkg don't really fit the bill unless I can learn a little more about the way they handle local caches.

My goal is to be able to create a liveDVD (about 2 gigs) with the package cache pre-loaded.  Then after installing on a new machine, have the additional stuff installed without needing an internet connection.  I can make the liveDVD, the only trouble that I am having is to get the packages installed after setting up the Ubuntu initial environment.

Like I said,  I can do it with my custom repo CD using "apt-cdrom add", but I would much rather have a working local cache built into the liveDVD where no additonal work is required by the person who may be installing from my DVD.

Mr. Bass used to make some custom repo/auto installing disks that were outstanding.  Unfortunately he doesn't do it anymore.

Thanks,

Art

---

### Post by artinla on 2007-01-09
I finally got it.  Here is what I found:

These instructions apply to my personal cache of .debs, so some steps such as the msttcorefonts might not apply to you.  If you don't have a package such as that, ignore that line.  Also, I chose "ubuntu-art" as my distribution name, but you can call yours anything you want.  Just replace all the "ubuntu-art's" in these instructions with whatever name you want.  By following these instructions exactly, your local apt cache will be up and running in no time.  This can be especially valuable to someone who has dialup, or no internet connection at all.  Just download the debs that you want with:

sudo apt-get install -d (package names)

Your packages will be saved in /var/cache/apt

Falcon is a great program that can help you create local, http, and CD repositories.  I have had much trouble trying to follow instructions from the internet to create good (especially local) repositories.

To create a WORKING local apt repository:

1.  Install falcon*.deb and python-cheetah  (I got the v1.5 .deb from the internet, and apt-get installed python-cheetah)
2.  browse /usr/share/doc/falcon and read the .pdf
3.  follow instructions to create .ini file and required folders.
4.  sudo chown -R (username) /var/www/falcon
5.  sudo chmod -R 777 /var/www/falcon
6.  copy debs into /var/www/falcon/pool/ubuntu-art/main
7.  falcon update
8.  copy all package lists from /var/www/falcon/dists/ubuntu-art/main/binary-i386 to /var/www/falcon/pool/ubuntu-art
9.  add the following line to your /etc/apt/sources.list
10. deb file:/var/www/falcon ubuntu-art main
11. sudo apt-get update
12. run synaptic to see the packages under "not installed" status
13. sort available packages by "version" and don't select anything that has a blank version. Uninstall those completely.
14. don't select msttcorefonts unless you have a working internet connection established (has to d/l some fonts)
15. mark all the other packages and right-click
16. select "mark for installation"
17. click apply

That should do it.  

If you add any new packages to the local repository, just repeat steps 7 and 8.

To create a repository CD, just copy the pool folder to a CD and copy the package index files from /var/www/falcon/ to the root of the CD.

sudo apt-cdrom add will add the CDROM to your sources.list

Art

---

