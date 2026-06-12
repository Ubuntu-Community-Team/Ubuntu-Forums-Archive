---
title: "Problems with upload download via internet browser 22.04 Firefox and Brave"
date: 2022-12-21
forum: General Help
---

### Post by ironarjen2 on 2022-12-21
I have a rather annoying problem with up and downloading. It does not depend on the browser but different browsers have different problems. If I download a file Brave crashes (the download works), same for for instance attaching a doc to a mail. I need to kill Brave, restart it and then the browser responds again, the file is attached. In firefox I can download only to the Download folder, which I really dislike since it results in a mess of files. When I try to attach a file in firefox, it does not crach but I do not get the dialogue for attachment  (gmail). The same goes for Whatsapp, Brave crashes, Firefox does not allow me to attach anything.

Dropbox is working fine, SSH is functioning.

Anybody any idea?

---

### Post by TheFu on 2022-12-22
22.04 firefix is a snap package with snap constraints.  Part of those constraints limits where files can be saved and read.  That's the nature of snap packages and why you may have seen that some people strongly dislike snap packages.  There is no way to locally override these constraints, unless the snap packaging for that specific program/suite decided it should be allowed.  Still, most GUI program are limited to accessing specific "approved by Canonical" locations, since they hard-coded the locations into the snapd code.

There are options.  Install firefox from a non-Snap source and use firejail to setup constraints that meet your local requirements.  Mozilla makes an ESM version of firefox which is not a snap package.  Their might be a flatpak and an AppImage version too, if you like the idea of single-file, run anywhere, packaging.

I know nothing about Brave.

Of course, it could be simple file and directory permissions too.  If you'll state the exact directory locations for uploads and downloads, someone may know something specific.

---

### Post by mIk3_08 on 2022-12-24
> **ironarjen2 said:**
> I have a rather annoying problem with up and downloading. It does not depend on the browser but different browsers have different problems. If I download a file Brave crashes (the download works), same for for instance attaching a doc to a mail. I need to kill Brave, restart it and then the browser responds again, the file is attached. In firefox I can download only to the Download folder, which I really dislike since it results in a mess of files. When I try to attach a file in firefox, it does not crach but I do not get the dialogue for attachment  (gmail). The same goes for Whatsapp, Brave crashes, Firefox does not allow me to attach anything.

Dropbox is working fine, SSH is functioning.

Anybody any idea?
Did you try to use the compress tar.bz firefox. I've have been using this firefox starting I use 22,04 lts. So far so great I haven't experiencing any trouble or any issue same as yours. Regards and cheers.

---

### Post by dragonfly41 on 2022-12-24
We each have different ways of trying to troubleshoot freezing problems.
It helps to know what memory you have.
8GB, 16GB, 32GB?
Browsers consume memory for each tab which is open.
I use Stacer GUI to inspect memory usage per process but you can do this with command line.


I did find a relevant thread to read.

Based on your statement of problem (clues) I did quickly find one relevant discussion.

[https://community.brave.com/t/bug-unable-to-download-save-anything-browser-freezes/277404/22](https://community.brave.com/t/bug-unable-to-download-save-anything-browser-freezes/277404/22)

Brave is a good, secure browser.

---

### Post by ironarjen2 on 2022-12-26
I uninstalled Firefox, which indeed was installed via snap. I then installed the old fashioned apt way and at least in gmail I can attach stuff. So thumbs up and thanks!

But I do wonder what's at the heart of this. If this is simply like that with snap, everybody would have that problem and that is clearly not the case, So something must have been wrong with my snap install. I do remember some strange messages related to snap when starting firefox, except that I do not recall the exact message. I will figure this out when I have more time.

---

