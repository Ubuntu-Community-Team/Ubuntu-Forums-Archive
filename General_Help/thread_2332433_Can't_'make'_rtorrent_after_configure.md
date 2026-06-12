---
title: "Can't 'make' rtorrent after /configure"
date: 2016-07-31
forum: General Help
---

### Post by corbula on 2016-07-31
I don't know if anyone here will be able to help me but this is more difficult than I thought and more difficult than it should be.

I've downloaded rtorrent 0.9.2 (yes it needs to be this version) in a tar.gz format. I've extracted that and read the install file which say's you should run './configure' followed by 'make' and then 'make install'

I did the './configure and every time it gave an error about dependencies, so I installed the dependencies (I think I got all of them) and tried the 'make' command. When I do this though it doesn't work. I'm not sure what the actual error is as it doesn't make it clear but it does say 'makefile:383: recipe for target 'all' failed at the end. 

I don't know what causing this or where to go from here. 

I never knew installing something on linux that you download in a tar.gz was so difficult.

Any ideas anyone? Anyone seen this before?

Thanks

---

### Post by ajgreeny on 2016-07-31
You may need to install build-essentials package to do that, but before you start messing about installing packages that way, you should understand that we do not normally do things that way in Linux  and certainly not in Ubuntu.

We use a package manager system to install packages from repositories where they are stored and updated for us, and in that way we can install an application one time and it will then be automatically updated along with all the other installed packages in the system.

Try running terminal command ```
sudo apt-get install rtorrent
``` and you should install rtorrent of a version correct for your Ubuntu version, which in 14.04 is 0.9.2-1.  If you really must run a different version of rtorrent you could end up with problems installing and running it as a result of conflicts of various library file versions.

---

### Post by corbula on 2016-08-01
Thanks. I've been informed that I can use the latest version so I can just do a apt-get rtorrent like you've stated. I will try and prevent it from updating though just incase a newer version causes issues.

I will mark this as solved now.

---

