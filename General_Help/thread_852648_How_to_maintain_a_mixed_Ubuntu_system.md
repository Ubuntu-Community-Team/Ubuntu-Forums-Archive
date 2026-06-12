---
title: "How to maintain a mixed Ubuntu system"
date: 2008-07-07
forum: General Help
---

### Post by _alterego on 2008-07-07
Disclaimer: This guide involves making configuration changes that modify apt's behavior. I have only tested it for simple operations such as upgrading Firefox and Subversion to new versions. While I consider it to be generally safe, remember that its your system and there is no warranty.  Hopefully others can improve on my methodology here.

I recently figured out how to mix packages from Ubuntu Intrepid Ibex and Hardy Heron using apt-get. You can mix and match any packages from any future or prior distribution by modifying just a couple of files and specifying a simple command-line parameter. The benefits to this are pretty cool. Subversion 1.5 was released very recently, for example (it contains support for automatic merge tracking), and you can already find it packaged in Intrepid Ibex (what Debian would consider "unstable"). Or maybe you want a recent Firefox 3, or in my case, an SoQt linked against Qt 4, all of which is available in Intrepid. In many cases paid developers that work for Canonical are creating these packages so they are actually quite stable.

First, create the file */etc/apt/apt.conf* and put the following in it:

```
APT::Default-Release "hardy";
```

Replace hardy with the distribution that you want to be the default.

Then create the file */etc/apt/preferences* and add the following:

```

Package: *
Pin: release a=intrepid
Pin-Priority: 50

```

This Pin-Priority basically says, make Intrepid packages the lowest priority. Other priorities are much higher, for example 400, 500 or 600. This makes sure that when you do *apt-get upgrade* you don't grab every single package that has been updated in Intrepid.

Finally, go into your */etc/apt/sources.list* and create a copy of it at the end of itself, and replace all instances of *hardy* in that second copy with *intrepid*. Then run *apt-get update* to get all the meta-data. 

Now all you have to do to download a package from Intrepid Ibex is specify the -t parameter when installing a package, like so: *apt-get install -t intrepid package_name*

Time for some examples. We'll play with GNU Hello to start with and make a few points:

Running *sudo apt-get -d install hello* should download but not install GNU Hello from Hardy (since we are just playing around right now):

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  hello
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.6kB of archives.
After this operation, 606kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main hello 2.2-2 [20.6kB]
Fetched 20.6kB in 0s (303kB/s)
Download complete and in download only mode

```

Now what if we run *apt-get install -d -t intrepid hello* (after running *apt-get clean* to delete our downloaded package) it should download but not install Hello from Intrepid, right? Wrong! It grabs it from Hardy since, as you can see on [http://packages.ubuntu.com,](http://packages.ubuntu.com,) they are the exame same version and we have given Intrepid a lower pin priority than Hardy. So it just ignores the *-t intrepid* and downloads it from Hardy.

What about Subversion though? Let's start with the vanilla *apt-get install -d subversion*:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  db4.6-util subversion-tools
The following NEW packages will be installed:
  subversion
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 254kB of archives.
After this operation, 3543kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main subversion 1.4.6dfsg1-2ubuntu1 [254kB]
Fetched 254kB in 0s (3411kB/s)
Download complete and in download only mode
```

It grabbed it from Hardy, cool. Now what about *sudo apt-get install -d -t intrepid subversion* (after an *apt-get clean*):

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libneon27-gnutls libsvn1
Suggested packages:
  subversion-tools db4.6-util
The following NEW packages will be installed:
  libneon27-gnutls subversion
The following packages will be upgraded:
  libsvn1
1 upgraded, 2 newly installed, 0 to remove and 970 not upgraded.
Need to get 1226kB of archives.
After this operation, 4731kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libneon27-gnutls 0.28.2-2 [119kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main libsvn1 1.5.0dfsg1-1ubuntu2 [788kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main subversion 1.5.0dfsg1-1ubuntu2 [319kB]
Fetched 1226kB in 2s (548kB/s)
Download complete and in download only mode

```

And there you have it.. Ubuntu Nirvana!

---

### Post by bodhi.zazen on 2008-07-07
Nice one. It is "generally safe" for "simple operations".

If you try something complex (apt-get update && apt-get dist-upgrade OR adding debian repos into the mix), be prepared for breakage.

---

### Post by _alterego on 2008-07-09
Hi, does this forum have a place where they sticky how-to guides?

---

### Post by kostkon on 2008-07-09
> **_alterego said:**
> Hi, does this forum have a place where they sticky how-to guides?
Although it is a very nice guide, I don't think it can be put as a sticky (if this is the thing you are asking for). It is not 100% safe, since it may not allow for future upgrades and it may lead to serious breakage when someone tries to upgrade to the next version of Ubuntu.

---

### Post by _alterego on 2008-07-09
Hi, I don't think "100% safe" is a reasonable requirement for a how-to guide. This guide is actually "100% safe" anyway since it has a fair warning and reverting the changes just involves going through the guide and reversing a few changes. People are much better off doing it this way than manually downloading packages from newer distributions and installing them using dpkg -i, which I have been doing for years until I figured this out.

Anyway, I wasn't asking it to be stickied in a main forum, just whether you had a sticky where you list how to guides such as many other forums have.

---

### Post by _alterego on 2008-07-09
I would just like to add one more comment about this not being "100% safe." 

This guide is based on the Debian documentation, specifically the "[APT HOWTO - Managing packages - How to keep a mixed system](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)" section.

So I think its reasonable, and I think its something people would like to know how to do. And my guide includes examples, which the documentation doesn't.

---

### Post by bodhi.zazen on 2008-07-09
On these forums we have this section :

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

The criteria for posting in that section are here :

[http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396)

The criteria for a sticky would include those criteria but in addition it would have to be something that applied to most users and answer a FAQ. In the case of this how to my guess would be a minority of users would use this information.

For example of a sticky look at this :

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Now to give you and idea , first look at the number of views / responses on that thread and then do a search on these forums and you will see just how common vmware questions actually are :)

If you are interested in documentation I suggest you become active with the wiki team

> **_alterego said:**
> I would just like to add one more comment about this not being "100% safe." 

This guide is based on the Debian documentation, specifically the "[APT HOWTO - Managing packages - How to keep a mixed system]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html")" section.

So I think its reasonable, and I think its something people would like to know how to do. And my guide includes examples, which the documentation doesn't.

Break you system via pinning and then fix it, then we can talk about "safety" :twisted:

Most users on these forums will have no idea how to fix packages, let alone X, gcc mis-matches, or APT. You may need to "fix" the problem by re-installing Ubuntu. Right now there is not all *that* much difference between the 8.04 and 8.10 repos, that will change. In addition the 8.10 repos are for developers and there are many known and unknown bugs. Do you know how people will use your how to ? Do you know what pachages they will pull in with your how-to or how stable those packages are ? Do you know how to fix a broken system? If not, how can you know if this how-to is safe ?

I can tell you from experience, following this how to may often work just fine, but it may also result in a broken system that may or may not be recoverable.

---

### Post by koenn on 2008-07-09
> **_alterego said:**
> 
This guide is based on the Debian documentation, specifically the "[APT HOWTO - Managing packages - How to keep a mixed system](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)" section.

So I think its reasonable, and I think its something people would like to know how to do. And my guide includes examples, which the documentation doesn't.
Apt pinning is indeed a neat feature, and works well on Debian, although even on Debian it's kind of a freak feature, since Debian recommends to always use the stale release (for production systems). 
Compaired to Debian, Ubuntu has a faster release cycle, with lots of ubuntu-specific modifications that trigger version-specific dependencies, and as far as I can tell, these are meant to  resolve within a given release, but usually don't resolve *across* releases.This means that if you try to install a pinned package, you probably get one of the following 2 scenarios :
a/ the package does not install because it can't satisfy the dependencies of that package (typical error: " ... depends on ... version 2.0 but version 1.7 is (going to be) installed")

b/ the package pulls in a lot of dependencies, to the extend that you actually do half a release upgrade. And a half upgrade practically guaranties at least some buggy behaviour in random applications, and general breakage in most cases.

If none of this happens, you're extremely lucky but will most likely face trouble when the next release-upgrade comes along. 


It's a nice thing to play with, but not something to advertise, imo.

---

### Post by koenn on 2008-07-09
> **_alterego said:**
> and reverting the changes just involves going through the guide and reversing a few changes.
"Downgrading" is notoriously difficult in apt-based systems (Debian, Ubuntu) because the system was designed to facilitate version upgrades of packages, not for downgrades (and the associated dependencie changes that would require additional packages to be downgraded as well, etc).
So reverting the preferences file and sources list to its previous state is easy, "undoing" installed packages from a newer release to fix breakage, is not.

---

### Post by _alterego on 2008-07-09
I was curious about what could possibly go wrong, so I installed Feisty Fawn and followed my guide, and then attempted to install Subversion from Intrepid Ibex. I only tested this on Hardy previously. As you can see from the attached image, I am happy to report that it went really, really well!

---

