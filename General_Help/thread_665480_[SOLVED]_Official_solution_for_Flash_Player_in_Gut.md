---
title: "[SOLVED] Official solution for Flash Player in Gutsy 7.10?"
date: 2008-01-12
forum: General Help
---

### Post by narf y akim on 2008-01-12
Hi, I have read quite a lot about the flashplugin-nonfree in Gutsy 7.10 and possible solutions. But, anyone knows when the official solution will be released by Update Manager? If I have to wait too long I'll have to use an alternative install (other than Synaptic or Add/Remove) of Flash Player, but I dislike this way.:(

---

### Post by luisromangz on 2008-01-12
Ummm I have been using the flashplayer-nonfree from the repositories since I installed Gutsy with no problems, what problem do you have?

---

### Post by dabang on 2008-01-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I don't know, if there's an official bugfix, but if you do not depend on konqueror and don't want to wait you could build your own flash-nonfree package with flash version 9.0.115. This is what I did, work's great and it's closest to an "official" bugfix I guess. Be aware, that the new flash plugin does not work with konqueror, firefox is fine though.

Get the hardy source for the flash package from here:
[http://packages.ubuntu.com/hardy/source/flashplugin-nonfree](http://packages.ubuntu.com/hardy/source/flashplugin-nonfree)

Then
```
sudo apt-get build-dep flashplugin-nonfree
tar xvf flashplugin-nonfree_9.0.115.0ubuntu2.tar.gz
cd flashplugin-nonfree-9.0.115.0ubuntu2
dpkg-buildpackage -b -r fakeroot
cd ..
sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_<i386/amd64>.deb
```

---

### Post by narf y akim on 2008-01-12
Thanks very much, I'm not sure about one thing, in the command:

sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_<i386/amd64>.deb

Have I to choose between i386 and amd64? That's right isn't it?

---

### Post by ominousluv on 2008-01-12
I get this error:

dpkg-buildpackage: unknown option or argument fakeroot

---

### Post by iris-n on 2008-01-12
There's a official bugfix, [_[U][COLOR="Orange"]here.[/COLOR]_[/U]]("http://ubuntuforums.org/showthread.php?t=636397&highlight=flash+gutsy+support+thread")

---

### Post by erfahren on 2008-01-12
that bug has been fixed from what I understand

the issue seems to still be creeping up for some users

is it possible that some may have the bad (buggy) package archived in /var/cache and if they try to uninstall and reinstall they just reinstall the bad package from their /var/cache ?

if anyone experiences the problem with Firefox saying Flash needs to be installed after they have installed Flash from the repos (through Synaptic or apt-get) maybe they could see if they have the package archived in /var/cache 

- they could try uninstalling, delete the archived package and try reinstalling from the repos

---

### Post by dabang on 2008-01-13
> Thanks very much, I'm not sure about one thing, in the command:

sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_<i386/amd64>.deb

Have I to choose between i386 and amd64? That's right isn't it?
No, it depends on your architecture and the package will be named automatically after it. So you'll end up either with "...i386.deb" or "...amd64.deb".


> I get this error:

dpkg-buildpackage: unknown option or argument fakeroot
Sorry, my mistake, supposed to be:
```
dpkg-buildpackage -b -rfakeroot
```
No blank between "-r" and "fakeroot". Or: are you sure fakeroot package is installed?

---

