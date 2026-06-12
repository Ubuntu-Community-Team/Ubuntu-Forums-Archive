---
title: "Offline Ubuntu"
date: 2007-06-23
forum: General Help
---

### Post by Weaseal on 2007-06-23
Hi,

So at work we have 9 machines running Kubuntu 7.  However, we have no internet whatsoever, and there are occasionally packages that need to be installed.

Currently, this is the process: I go to another location (very far away, we're talking at least a day roundtrip), download all of the packages and their dependencies, and then install them by hand, starting with the dependencies and ending with the package itself, machine by machine.  This is obviously a huge headache, and makes it virtually impossible to get things done regarding software that is not in the default release.

So!  My question is, how does one run an offline Ubuntu efficiently?  I don't actually mind the daylong roundtrips, it's just the tedious collection and installation of dependencies (God help me if I forgot to download just one tiny dependency).

Are there any sort of download-generating scripts?  Is there any way to download a package-DVD or something, that just has tons and tons of the most frequently used packages?  We installed off of the Kubuntu 7.04 DVD, and that has a lot of packages, but not all of them (it does not have XMMS, MPlayer, or wine, for examples).

Suggestions, please!

---

### Post by corstar on 2007-06-23
I just done this  today as i reformated.

The process is easy.

Copy all the files from your source computer from the directory of /var/cache/apt/
then put them on a thumb drive.

On your other computers, either copy them to the same directory and do an update(even though it's offline). The other ways is open Synaptic >File>Add packages.

It's that simple.

Synaptic has a download script installer in the same menu, but I have never used it.

---

### Post by Weaseal on 2007-06-23
Unfortunately, Kubuntu uses Adept instead of Synaptic.

Are you saying, though, that Synaptic adds the packages in that directory to the list of available installs?  That is one of the biggest frustrations for me in Kubuntu -- I've added the .deb packages to that /var/cache/apt/archives/ directory and they still do not show in Adept.  It would be great if they did, because then I wouldn't have to manually install the dependencies.

However, even if I were to switch to Synaptic (I haven't even begun to look into the logistics of doing so yet) this still does not solve the problem of having to manually download each dependency for the packages I want.  This is honestly the biggest headache, because I occasionally miss/forget one, and then the whole project is debunked for a couple of weeks until I can get to internet again.

---

### Post by corstar on 2007-06-23
> **Weaseal said:**
> Unfortunately, Kubuntu uses Adept instead of Synaptic.

Are you saying, though, that Synaptic adds the packages in that directory to the list of available installs?  

Yes. Exactly.

I'm not sure if Adept uses the same repo's and directories. I would imagine it would though. maybe someone can expand on this.

Another option you can explore is using synaptic in Kubuntu, I know this works as I have done it before.

There are ways of making a OEM version of Ubuntu to create a mirror image of customised setups, applications and repos etc. I'm not sure how to accomplish this. 

Good luck

---

### Post by corstar on 2007-06-24
I found another solution for you.

It's called CloneIt. the link is [here]("http://www.ferzkopp.net/~aschiffler/Software/CloneIt/CloneIt.html")

It sounds to be what your after. Let us know if it goes well.

here is where i found it and there are other tools there too. [link]("http://www.linuxsoft.cz/en/sw_list.php?id_kategory=89")

---

### Post by mikewhatever on 2007-06-24
> So! My question is, how does one run an offline Ubuntu efficiently? I don't actually mind the daylong roundtrips, it's just the tedious collection and installation of dependencies (God help me if I forgot to download just one tiny dependency).
Pain in the back. Corstar is mixing two things. While it is easy to install the packages from /var/cache/apt/archives/, you still need to take care of the dependencies manually, and no, the packages do not show in the package manager. I think it is a good idea to get one of the computers to where there is internet, install all the packages via synaptic or apt-get, then bring it back and copy all the packages from /var/cache/apt/archives/ to install on other computers.

If you want the packages to show in Adept, add your own repository following this guide [https://help.ubuntu.com/community/Repositories/Personal?action=show&redirect=PersonalRepositories](https://help.ubuntu.com/community/Repositories/Personal?action=show&redirect=PersonalRepositories)

---

### Post by Weaseal on 2007-06-25
Thanks for the links to clone it and for creating a personal repository.  These seem like ideas that can take some serious time out of the process.

Unfortunately, transporting a computer is pretty much out of the question.  That would be pretty expensive (hire a driver for a round trip, find somewhere where someone will let me hook my comp into their network, etc).

---

