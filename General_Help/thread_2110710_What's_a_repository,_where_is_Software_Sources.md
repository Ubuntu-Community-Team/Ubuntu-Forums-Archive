---
title: "What's a repository, where is Software Sources?"
date: 2013-01-30
forum: General Help
---

### Post by GCbon on 2013-01-30
what is a repository? Is it on my computer?  Or on the Internet?
Where do I find "Software sources" and "other software" ?
(I know I've seen them - many many times - but I don't remember where.)
And to think that once upon a time, I could take equipment, assemble it without any instructions, figure out how it worked, and write operating manuals!

---

### Post by Petro Dawg on 2013-01-31
> **GCbon said:**
> what is a repository? Is it on my computer?  Or on the Internet?
Where do I find "Software sources" and "other software" ?
(I know I've seen them - many many times - but I don't remember where.)
And to think that once upon a time, I could take equipment, assemble it without any instructions, figure out how it worked, and write operating manuals!

Just for  the sake of covering all the bases, I will start by a recommending the program called "Ubuntu Software Center" which is installed on your computer or "Synaptic Package Manager" which might be installed on your computer.  The programs found here are from Canonical's standard repositories (as far as my understanding goes).

If you are looking for software not in the primary Canonical repositories, they are sometimes available on the web within a personal package archive (a.k.a. PPA),  If you find software you want outside of the standard software center, you may have to add the software PPA repository through terminal before you can install the program.  The PPA can also be added through the "Update Manager" program on you computer (you can also see which software sources you currently use from the settings menu of this program).  

Instructions for adding specific PPAs are usually included on the software's website installation page.

This is an example of a PPA site [https://launchpad.net/~stk/+archive/dev](https://launchpad.net/~stk/+archive/dev)

---

### Post by ibjsb4 on 2013-01-31
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by GCbon on 2013-02-02
What I was looking for was the answer to a problem with my updater, similar to problems seen by others. I appreciate the help. You've given me even more basic manuals and guides than I had already. I think by the time I digest them all, I might be ready to solve my own problems, or at least feel less incompetent. Now if I could just stay awake for more than 30 minutes (often less) at a time. Narcolepsy is such a fascinating disease, if I didn't  have to live with it.  zzzzzzzzzzz
Thank you, everyone.

---

### Post by Impavidus on 2013-02-02
Simply put, a repository is a collection of software available for your Ubuntu system. It's located on the internet.

A software source is an internet server providing a repository. There is a main ubuntu server, and there are many mirrors all over the world. A freshly installed ubuntu system should know the address of the main server and of a nearby mirror. Software from these dources is guaranteed to work on your system. There are also third-party software sources. Software from third-party sources is not guaranteed to work on your system.

"Other software" is software not coming from the Ubuntu repositories. It may be available in third-party repositories (ppa, personal package archive) or for download and semi-automatic or manual installation (.deb, .tar.gz, .tar.bz2 or other file formats).

---

### Post by col48 on 2013-02-02
Worth adding to Impavidus (post #5) that 

1. software from a Canonical repository or a mirror (see 3 below) will sometimes not be the latest version, although it would have been when the Ubuntu version was released.  BUT it has been tested against that release and will work.  Later versions may not have been Linux-tested or may be just Beta quality.

2. software in the "Other software" category should have full instructions on the source website for its installation (eg for uncompression or expanding an archive file) where you should also check carefully for compatibility.

3. a mirror repository is just a copy held by a responsible non-Canonical site (such as a university).  This can relieve congestion on the main site especially around the time of a new Ubuntu release and may also provide a faster service for, say, geographically nearby users.  A mirror will itself be updated from the Canonical repositories so it will be out-of-date by up to a few hours.  No big deal.

---

