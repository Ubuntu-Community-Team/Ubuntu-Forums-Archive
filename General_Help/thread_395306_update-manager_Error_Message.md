---
title: "update-manager Error Message"
date: 2007-03-28
forum: General Help
---

### Post by nervt0xin on 2007-03-28
For the past two days, I have been getting the following error when attempting to run update-manager:

E:Malformed line 5 in source list /etc/apt/sources.list (dist parse),
E:The list of sources could not be read.

It doesn't update and I am unable to install any new applications nor update any existing ones. The first few lines of that file are this:

# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.2)]/ feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted #Added by software-properties

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.2)]/ feisty
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

I never manually edited it, so it is as made by the application.
Is there any way to quickly fix this?

---

### Post by Mr. C. on 2007-03-28
From the command line, try:

```
sudo apt-get install -f
```

Then try your updates again.
MrC

---

### Post by nervt0xin on 2007-03-28
The command line kicks back the exact same message after I entered that:

E: Malformed line 5 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

---

### Post by Mr. C. on 2007-03-28
Can you post line 5 of that file ?

MrC

---

### Post by nervt0xin on 2007-03-28
Here's the first 20:

# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.2)]/ feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted #Added by software-properties

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.2)]/ feisty
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

---

### Post by hikaricore on 2007-03-28
I'm going to go out on a limb here and guess this is line 5:

> deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.2)]/ feisty

Try putting a # in front of that line like this

> #deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.2)]/ feisty

---

### Post by nervt0xin on 2007-03-28
That allowed the update-manager to run, thanks a lot!

---

### Post by hikaricore on 2007-03-28
Np, that line is for the software repos (default stuff mostly) on the feisty beta cd, you don't specifically need it, but it can make reinstallation of some packages faster.

I'm not familiar with the cdrom apt read methods, so I don't know how to go about correcting it.

But as long as you can update, it shouldn't be an issue.

---

### Post by Mr. C. on 2007-03-28
Sorry for the delay in responding nervt0xin.

The problem line doesn't match the sources.list spec

```
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.2)]/ feisty
```

From man sources.list:

> 
The format for a sources.list entry using the deb and deb-src types are:

          deb uri distribution [component1] [component2] [...]

The URI for the deb type must specify the base of the Debian distribution,
from which APT will find the information it needs.  distribution can specify
an exact path, in which case the components must be omitted and distribution
must end with a slash (/).  This is useful for when only a particular sub-section
of the archive denoted by the URI is of interest. If distribution does not specify
an exact path, at least one component must be present.

The URI is **cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.2)]/** and the distribution is **feisty**.  Since the distribution "feisty" does not end in a slash (/), it is not an exact path, therefore at least one component must be present, but there is none.  This is the error.

Commenting out the line is fine.

MrC

---

