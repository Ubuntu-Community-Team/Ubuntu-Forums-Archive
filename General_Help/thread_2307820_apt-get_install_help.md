---
title: "apt-get install help"
date: 2015-12-28
forum: General Help
---

### Post by will95 on 2015-12-28
I have recently got Ubuntu as my main operating system. I am having some issues. The default location for the downloads which I download from using the command apt-get install downloads straight to my hard drive. I want things to download to my 200GB external drive. Any ideas or ways on being able to change the default location to my 200GB without destroying or ruining anything?

---

### Post by matt_symes on 2015-12-28
Hi

> **will95 said:**
> I have recently got Ubuntu as my main operating system. I am having some issues. The default location for the downloads which I download from using the command apt-get install downloads straight to my hard drive. I want things to download to my 200GB external drive. Any ideas or ways on being able to change the default location to my 200GB without destroying or ruining anything?

I'm rather confused by this as apt is used, amongst other things, to update your operating system and install new software.

These updates should be installed on your root partition which is usually the main drive in your computer. It will download the files to the root partition from which ever drive you booted into Ubuntu.

You can remove the older packages, after they have been installed, if you want.

Why do you want to download apt's packages to your external hard drive ?

Kind regards

---

### Post by will95 on 2015-12-28
Because I am going to get katoolin to download the tools from kali linux and the tools can  take up some space which i would prefer to be on my external drive

---

### Post by QIII on 2015-12-28
Hello and welcome to the Forums.

Were I you, I would leave well enough alone and allow the package manager to do what it is designed to do.  Unless you are very familiar with the filesystem, you are liable to break the package management system by doing something like that.

Furthermore, whatever tools you plan to install would best reside in your root partition.

Is your main OS drive terribly small?

---

### Post by matt_symes on 2015-12-28
Hi

> **will95 said:**
> Because I am going to get katoolin to download the tools from kali linux and the tools can  take up some space which i would prefer to be on my external drive

You want the *installed* packages on your external hard drive and not just the *downloaded package* files ?

This may not be easy as each packages metadata will instruct apt where on the file system the packages files should be installed.

It's going to want to install the package files in the default locations and this is usually in your root partition on Ubuntu.

Kind regards

---

