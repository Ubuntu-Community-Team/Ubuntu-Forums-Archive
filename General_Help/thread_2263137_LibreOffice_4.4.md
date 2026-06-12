---
title: "LibreOffice 4.4"
date: 2015-01-29
forum: General Help
---

### Post by rbengr on 2015-01-29
Hi,

This should be easy but apparently it's not.

I have Ubuntu 14.04.  It comes with a version of LibreOffice.  LibreOffice 4.4 has just been released and I would like to upgrade.  You are supposed to be able to do this from within the program but the upgrade tab is missing.  I tried to download from the LibreOffice site, but that didn't work either.

Perhaps I shouldn't even bother with the program but I'll try one more time.

Any suggestions?  Thanks.

[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]This should be easy but apparently it's not.[/COLOR]

[COLOR=#000000]I have Ubuntu 14.04. It comes with a version of LibreOffice. LibreOffice 4.4 has just been released and I would like to upgrade. You are supposed to be able to do this from within the program but the upgrade tab is missing. I tried to download from the LibreOffice site, but that didn't work either.[/COLOR]

[COLOR=#000000]Perhaps I shouldn't even bother with the program but I'll try one more time.[/COLOR]

[COLOR=#000000]Any suggestions? Thanks.[/COLOR]

---

### Post by ajgreeny on 2015-01-29
There is a ppa at [https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases) with the 4.4 version which you may like to try.

Instructions are available on the ppa site about how to add and use the repository.

---

### Post by ajgreeny on 2015-01-29
There is a ppa at [https://launchpad.net/~libreoffice/+...ce-prereleases]("https://launchpad.net/%7Elibreoffice/+archive/ubuntu/libreoffice-prereleases") with the 4.4 version which you may like to try.

Instructions are available on the ppa site about how to add and use the repository.

---

### Post by rbengr on 2015-01-29
That page only seems to deal with pre-releases.

---

### Post by ajgreeny on 2015-01-29
Yes, they are pre-releases of the 4.4 ubuntu versions because the stable 4.4 versions are not yet built for Ubuntu.  That is what ppa repos are often used for, ie, packages for applications that are not yet officially available for Ubuntu.

You could always use the 4.4 version direct from the [libreoffice]("http://www.libreoffice.org/download/libreoffice-fresh/") website, unpack the archive, and install all the .deb packages from that with dpkg.

I would use the ppa then the packages will be updated as you do normal updates.

Actually, thinking about it, that is not what I would do; I would stick with the stable ppa version from [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=precise](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=precise)

---

### Post by rbengr on 2015-01-29
Thanks for the response but I guess I don't understand.  On the official website, they announced a stable release of 4.4 on January 29.  It is available for Linux, Windows and OS X.  What am I missing?  Thanks.

I just clicked on the main download tab on the LibreOffice Site.  This time it downloaded.  I opened a Readme file.  Among other things it said the version for Ubuntu should be downloaded through the Ubuntu Software Center.  The 4.4 version is not in the Software Center.  Does Ubuntu have to perform an update?  Thanks.

---

### Post by ian-weisser on 2015-01-29
There are two things you are missing.

First, you are thinking perhaps that compatibility is automatic. It's not.
Just because it works for the upstream developer doesn't mean it will work in Ubuntu.

The dependencies may be different. It may assume window manager features that, say, Unity or LXDE does not provide. It may assume graphics your system cannot provide. It may crash. It may crash the entire system. So volunteers test it, discover and work out the bugs, before it reaches you. That's why it works for you. All that testing and work takes time.

Second, you are assuming the Windows or OSX model of applications: OS and Applications are upgraded independently. Not true here.
14.04 will have late-2013 software for all five years of it's existence. Almost nothing will get newer versions. The kernel, firefox, and a few other bits will get upgrades.

That's the Debian and Ubuntu model: A snapshot of the then-current art.
The way you get supported, updated applications in Ubuntu is by upgrading the entire system every six months to the next snapshot. Rather like upgrading your entire phone instead of individual apps. Look for a fully-supported version of LibreOffice to land soon in 15.04 (the pre-release version), which will be released, of course, in April 2015.

If you want, you can use the upstream installer.
But if you do, and something is broken, we probably can't help you much beyond 'uninstall it and use the Ubuntu version.' You'll need to look for upstream support...from upstream.

---

### Post by rbengr on 2015-01-29
Thanks for that good explanation.  Apparently, I will have to download an updated Ubuntu each 6 months.  That's ok.

---

### Post by grahammechanical on 2015-01-29
For information

Vivid Vervet (the development version of 15.04) got Libreoffice upgraded from 4.3 to 4.4 with today's updates. I think that Libreoffice is another of those few applications that get upgraded through Software Updater but stability has priority over the latest in Ubuntu LTS releases. Ubuntu 14.04 may yet get Libreoffice 4.4 but the developers will not be rushing to push it out.

To give an example of what can go wrong. Last week using Libreoffice 4.3 in Vivid Vervet every time I tried jumping from the beginning to the end of a Writer document (Ctrl+End) the Libreoffice window froze and it froze the user interface as well. I could select 10 or 12 lines of text for copying and pasting but every time I tried to select more than that the application window froze and froze the user interface as well. This required a power off to get things going again. 

Linux will survive a power off but do it three or four times in a row like I did and Linux most definitely gets upset. I no longer have a shut down splash screen. A couple of days later an update to Libreoffice fixed the problem. But for a while I had to go into Ubuntu 14.04.1 to use Libreoffice.

Regards.

---

### Post by QIII on 2015-01-29
Threads merged.

---

### Post by rbengr on 2015-01-30
Thanks

---

### Post by sgage on 2015-01-30
For what it's worth, I just installed 4.4 in Trusty using the binary installer from the site - everything seems to be working fine.

---

### Post by rbengr on 2015-01-30
Thanks.  With your method of installation, can you place an icon in the left-hand bar?

---

### Post by sgage on 2015-01-30
> **rbengr said:**
> Thanks.  With your method of installation, can you place an icon in the left-hand bar?

Yes, at least in Gnome Shell. I'm sure it would be just easy in Unity.

Here's how I did it:

First, remove your currently installed LibreOffice, including the uno and ure bits - they will conflict. I use Synaptic, search for libreoffice, sort on 'installed' and there you go.

Then, extract the tarball. Fire up a terminal, go to the DEBS directory, and do this:

```
sudo dpkg -i *.deb
```

That's really it.

---

### Post by rbengr on 2015-01-30
LibreOffice comes standard in the Ubuntu package.  I assume if you remove it, it will reappear with the next auto upgarde of Ubunto?  Thanks.

---

### Post by monkeybrain20122 on 2015-01-30
Look, just use the LO ppa. I just upgraded to LO4.4. The advantage of the ppa is that it is packaged for Ubuntu and therefore integrate well with the DE, it will keep up to date when a new version is available and totally trustable because these are the same people who package LO for Ubuntu's official releases.

 [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty)

---

### Post by sgage on 2015-01-30
> **rbengr said:**
> LibreOffice comes standard in the Ubuntu package.  I assume if you remove it, it will reappear with the next auto upgarde of Ubunto?  Thanks.

No - using the download from the LO site (and I incorrectly referred to it as a 'binary installer' - it's not, it's a collection of .deb files in a tarball), you will use dpkg to install it, so it will be in the installed-software database. And as a higher version number, it will not get upgraded. Until and unless a higher version number comes to the official repos, which is unlikely.

---

### Post by monkeybrain20122 on 2015-01-30
> **ian-weisser said:**
> There are two things you are missing.


That's the Debian and Ubuntu model: A snapshot of the then-current art.
The way you get supported, updated applications in Ubuntu is by upgrading the entire system every six months to the next snapshot. Rather like upgrading your entire phone instead of individual apps. Look for a fully-supported version of LibreOffice to land soon in 15.04 (the pre-release version), which will be released, of course, in April 2015.

.

I get up to date applications with ppas and compiling. PPas is a reason why I use Ubuntu instead of Debian. Despite all the doom and groom to scare beginners I have never experienced any issue with ppa that I cannot fix (and only very very rarely anyhow)  Installing system components with ppas (e.g graphic stack) is a bit tricky, but for applications such as LO there is rarely any issue.

The model of having to upgrade the whole system every 6 months just to get the latest of one piece of software is crazy and Ubuntu is actually trying to move away from that according to Shuttleworth's talks.

---

### Post by rbengr on 2015-01-30
Ok, thanks.

---

### Post by monkeybrain20122 on 2015-01-30
> **rbengr said:**
> That page only seems to deal with pre-releases.

For LO the last pre-release is exactly the same as the stable release but in name. So in the LO Ppa you get 4.4rc3, but that is the same as 4.4

---

### Post by rbengr on 2015-01-30
Thanks.  I didn't know you could make a change to, and 'override', the LO version supplied in the Ubuntu package.

---

### Post by rbengr on 2015-01-30
Thanks

---

### Post by monkeybrain20122 on 2015-01-30
If you want nice integration with Ubuntu desktop don't install from download. Use the ppa. See screenshot (and note the version) Once the ppa is added, LO will get updated through the normal software channel whenever a newer version is available.

---

### Post by sgage on 2015-01-30
> **monkeybrain20122 said:**
> If you want nice integration with Ubuntu desktop don't install from download. Use the ppa. See screenshot (and note the version) Once the ppa is added, LO will get updated through the normal software channel whenever a newer version is available.

The PPA didn't upgrade me to 4.4 (in Trusty). Just brought in a few components, but 'held back' most of the components.

The download from the official LO site is the whole collection of deb files, so it is in the apt database and will be updated as available. I mistakenly referred to it as a 'binary installer', which it is not.

---

### Post by monkeybrain20122 on 2015-01-30
> **sgage said:**
> The PPA didn't upgrade me to 4.4 (in Trusty). Just brought in a few components, but 'held back' most of the components.

The download from the official LO site is the whole collection of deb files, so it is in the apt database and will be updated as available. I mistakenly referred to it as a 'binary installer', which it is not.

Not sure why that is the case with you. All my LO componenets are upgraded. I think may be because you tried it too early when not all the components have been pushed to the server. It was built only 6 hours ago. 

I used to download from OO before there was a ppa (around 10.04?) In those days there were no debs. I had to dl a whole bunch of .rpms and then converted them with alien before doing dpkg -i *.deb. :)

Edited: there was no LO back in 10.04, I meant OO.

---

### Post by rbengr on 2015-01-30
Thanks.  I'll give it a try after dinner.  Making Italian chicken tonight, lol.

---

### Post by sgage on 2015-01-30
> **monkeybrain20122 said:**
> Not sure why that is the case with you. All my LO componenets are upgraded. I think may be because you tried it too early when not all the components have been pushed to the server. It was built only 6 hours ago. 

I used to download from  LO before there was a ppa (around 10.04?) In those days there were no debs. I had to dl a whole bunch of .rpms and then converted them with alien before doing dpkg -i *.deb. :)

Happily nowadays they offer the debs. It could be that I tried too early with the PPA. In any case, LO 4.4 is running fine using the debs from LO.

---

### Post by ian-weisser on 2015-01-30
> **sgage said:**
> Just brought in a few components, but 'held back' most of the components.

'Held back' usually means a dependency package has a version conflict or a filename conflict.
Happens with some non-Ubuntu packages. That 'compatibility' issue. Usually easy to resolve...if you know how.
Another reason we recommend new users stick to the Ubuntu Repos and the better PPAs.

---

### Post by deadflowr on 2015-01-30
> **rbengr said:**
> LibreOffice comes standard in the Ubuntu package.  I assume if you remove it, it will reappear with the next auto upgarde of Ubunto?  Thanks.

Do you mean release-upgrade?
(The method of moving from something like 14.04 to 14.10 without reinstalling?)
I really don't know if it does.

If you remove a package, then normally no new packages for that remove package will be installed.
I've removed base packages before and then done a release-upgrade before, but I do not remember if it re-installed those packages.

On a normal update any removed package will not, nor will ever be, updated.

On a sidenote, +1 to using the ppa to upgrade the libreoffice packages, and also to only using the update manager (or whatever updating method you want to use) to upgrade the packages.

I feel I will come off as a broken record, as I've tried to make a point of this over and over, but Ubuntu does not install libreoffice.
But rather it installs a base of a few libreoffice packages. Like writer, calc, impress, draw, the starter(Do not know what it is really called off the top of my head) and I think a few under the hood packages.
So if you add the ppa and run apt-get install libreoffice, you will actually install far more than what you really should.
Which is just adding bloat.

The update manager, method, will only update what ever packages you have already installed.
Adding no extra bloat then necessary.

Hope this helps.

---

### Post by ian-weisser on 2015-01-30
> **rbengr said:**
> LibreOffice comes standard in the Ubuntu package.  I assume if you remove it, it will reappear with the next auto upgarde of Ubunto?  Thanks.


No, it won't.
You told the package manager you didn't want LibreOffice packages.
It remembers that.

It's possible to *accidentally* change that setting, usually by installing another package that depends on LibreOffice (like the ubuntu-desktop metapackage). Try to avoid that: 
- The LibreOffice package install will fail because LibreOffice files are already installed in the expected location.
- The package manager will stop working until you diagnose and resolve the broken-package problem.
- That means no updates, no security updates, cannot install or remove software, etc.

Best practice for a fast, easy migration to the next release of Ubuntu includes *uninstalling all software from Non-Ubuntu sources*.
That includes PPAs, upstream debs, everything. 
You reinstall after the release-upgrade is complete.
Lots of help requests in this forum from people who broke their systems trying to do a release-upgrade with long-forgotten PPAs and random debs.

---

### Post by monkeybrain20122 on 2015-01-30
> **ian-weisser said:**
> 'Held back' usually means a dependency package has a version conflict or a filename conflict.
Happens with some non-Ubuntu packages. That 'compatibility' issue. Usually easy to resolve...if you know how.
Another reason we recommend new users stick to the Ubuntu Repos and the better PPAs.

With due respect I cannot disagree more. What worst things ppas can do than to make you reinstall the whole  system, which you tell new users to do anyway every 6 months just tp  upgrade a few pieces of software??

The solution to fix a ppa problem is usually a lot easier than working around bugs for every new OS release after 6 months and not to mention blotched 'upgrades'. The forum is full of new releases breaking x y z and upgrade woes. For non system component ppas (i.e, not something like graphic drivers, which would require more caution) the worst case scenario is editiing sources list or ppa purge provided that not too many ppas with  overlapping packages are added. 

In this case I am almost 100% sure that the problem is simply that sgage tried to update LO too soon and the packages were not all there yet. Waiting for a few hours would have sorted it out. The team that maintain the LO ppa are the same developers who package Ubuntu's official version.

Either ppa or use old software,--the Debian approach, --upgrading every 6 months just to get the  latest LO or gimp makes no sense IMO (some sofware like LO provides .debs but most doesn't, one can also compile of course, but  it wouldn't be appropriate advice to new users)

---

### Post by rbengr on 2015-01-30
Hi,

I am working through thr processing a ppa for the latest LibreOffice release:

The ppa is here: [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty)

and here: [https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-4-4](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-4-4)

I followed the instructions to the end but I'm not sure that I'm done.  The end of step 3 says: [COLOR=#000000][FONT=Times]Now you're ready to start installing software from the PPA!
[/FONT][/COLOR]
What should I do now?

Thanks

---

### Post by ian-weisser on 2015-01-30
> **monkeybrain20122 said:**
> In this case I am almost 100% sure that the problem is simply that sgage  tried to update LO too soon and the packages were not all there yet.  Waiting for a few hours would have sorted it out. The team that maintain  the LO ppa are the same developers who package Ubuntu's official  version.

Totally agree. The LO PPA is one of the better ones that doesn't break systems. I recommend it.

> **monkeybrain20122 said:**
> The forum is full of new releases breaking x y z and upgrade woes.

I think the forum has just as many this-PPA-or-random-deb-broke-my-system threads. Both LTS+PPA and semiannual-new-release are ways people use to get newer software. And both have users who break their systems. I have used both at various times.
Glass half empty / glass half full?

---

### Post by deadflowr on 2015-01-30
***Threads Merged***

Please do not start new thread on the same subject.

Having said that.
To install the new packages from the ppa, simply run an update.
I'd use the software updater/update manager.

---

### Post by rbengr on 2015-01-30
Thanks

---

### Post by monkeybrain20122 on 2015-01-30
> **rbengr said:**
> Hi,

I am working through thr processing a ppa for the latest LibreOffice release:

The ppa is here: [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty)

and here: [https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-4-4](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-4-4)

I followed the instructions to the end but I'm not sure that I'm done.  The end of step 3 says: [COLOR=#000000][FONT=Times]Now you're ready to start installing software from the PPA!
[/FONT][/COLOR]
What should I do now?

Thanks

Use the first one. The second one would only give you 4.4, so it won't upgrade if 4.5 comes out. 

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get upgrade


```

This will upgrade all your installed LibreOffice packages

To remove the second ppa

```
sudo add-apt-repository --remove ppa:libreoffice/libreoffice-4-4 
sudo apt-get update
```

You can manage your packages (update, install, remove) and ppas easily with synaptic (a gui much faster and have more optopns than the Software Centre). Install it with the Software Centre or 
```
sudo apt-get install synaptic
```

---

