---
title: "Clean autoclean and autoremove...Please HELP???"
date: 2016-02-29
forum: General Help
---

### Post by wyattwhiteeagle on 2016-02-29
man apt-get

       clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed.


Is there a way to have sudo apt-get to not "clean, autoclean, or autoremove" those things which we actually need or use?

I use BleachBit which is actually in one of the directories set for "apt-get clean" so right now if I run "sudo apt-get clean" guess what will happen to my BleachBit.

In autoclean it says the configuration option will prevent installed packages from being erased if it is set to off. How can I know which ones are set to off and how do I set one to off?

Last time I ran autoremove...some automatically installed packages that I actually use were removed. How can I prevent autoremove from removing the ones I actually use?

---

### Post by papibe on 2016-03-01
Hi wyattwhiteeagle.

When you install or upgrade a package, it is downloaded in /var/cache/apt/archive as a .deb file. Then, it is extracted and installed, or use to upgrade a previous version of the package.

Once that is done, the .deb file is kept there as a cache/backup in case you want to reinstall, or reconfigure it to defaults. However, it does not have any interaction with the system. You could (not recommended) delete that cache by hand.

Both clean, and autoclean delete files on that cache, and don't do anything with the currently install packages. It is a good tool to free space on the root partition, and it does no mess up any installed packages.

Autoremove is different in the sense that remove programs already installed. In my experience it is pretty safe to use. I can't think on an scenario in which would remove BleachBit. What it does is remove packages, usually libraries, that no other program is using. The typical example you would find in a run of autoremove would be: old kernels, and old headers.

If you have any doubt on any command, you could run a 'simulated' run. This way apt-get would print all as if it were deleting things, but it actually it is not doing anything. For example, all this command are synonymous of a fake run:
```
apt-get -s autoremove

apt-get --simulate clean

apt-get --just-print autoclean
```
You can also simulate an installation. For instance, to see how much dependencies a package would install:
```
apt-get --dry-run install kodi
```
Hope that helps. Let us know how it goes.
Regards.

---

### Post by deadflowr on 2016-03-01
Clean and autoclean simply clear the same debian installer packages out of the system.
These are the packages you download for updates or when you install something with apt-get, or through a package manager frontend like the software center or synaptic.

The difference is that clean clears out the archived cache folder wholesale, and autoclean only clears out older versions of installer packages, which may have newer versions you can or are using.
An example would be firefox. Every time firefox updates on Ubuntu you download a full installer package for it, from which the new firefox version gets installed.
Every new firefox version is a new version on the system, but the archive still holds the old one.
Autoclean will remove the old versions in the archive cache, but keep the installer package latest or newest version.

Neither or these commands will remove or uninstall any program.
They only clear the installer packages archives.

The default is set to on for the APT:clean-installed because that means it won't remove those older archives if it is set to off.
So leave it as is.


Now as for autoremove, let us say you installed a program-1, but that program-1 needs another program-2 installed first in order to work, but then you remove the 
program-1 but program-2 is still installed, autoremove will think that since program-1 is no longer installed, then there will be no need for program-2 and ask for it's removal. These are what are known as dependencies, but sometimes, these dependencies are full programs on their own.

One thing to note would be the autoremove does not simply start the removal process without user confirmation.
So whenever invoking autoremove, it is always best to review the programs that are marked for removal.
If in that step you notice a program you want to keep, you can then go with a more manual removal method, such as a standard apt-get remove package command.


Does any of that makes sense or did it add to the confusion.

Also this:
> I use BleachBit which is actually in one of the directories set for  "apt-get clean" so right now if I run "sudo apt-get clean" guess what  will happen to my BleachBit.
If you could follow the above, then the answer would be, *nothing.*
Bleachbit is already installed so running bleachbit on the archive won't do anything to the already installed bleachbit.
It'll only make so that if you need to reinstall bleachbit, you'll need to download the installer package for it all over again.

Partial ninja'd

---

