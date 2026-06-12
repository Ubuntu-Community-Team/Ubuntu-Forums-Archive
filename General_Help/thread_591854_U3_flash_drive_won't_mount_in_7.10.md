---
title: "U3 flash drive won't mount in 7.10"
date: 2007-10-25
forum: General Help
---

### Post by jlachovsky on 2007-10-25
Hi everybody I have a Sandisk U3 Flash drive that for some reason won't mount in 7.10.  I don't remember having any issues in 7.04 or before.  With the U3 flash drives it generally mounts two drives, one that resembles a CD drive, and one that actually has your data stored on it.  When I plug it in the one that resembles the CD drive shows up, but the drive with my data never shows up.  I don't get any error messages, it just doesn't pop up.  Any suggestions?

---

### Post by Qwerty_ on 2007-10-26
Is it a ntfs drive?

If so you will have to install ntfs-config

```
sudo apt-get install ntfs-config
```

Then run

```
sudo ntfs-config
```

And select your required options.

---

### Post by PmDematagoda on 2007-10-26
But before you install the GUI, you will need the core, first install ntfs-3g using:-

```
sudo apt-get install ntfs-3g
```

And then you can install ntfs-config.

---

### Post by Qwerty_ on 2007-10-26
Are you sure?

when I freshly installed Gutsy I just ran ntfs-config (without installing anything else) and I was up and away.

---

### Post by por100pre1 on 2007-10-26
Try taking a look at it using Gparted.

---

### Post by PmDematagoda on 2007-10-26
> **Qwerty_ said:**
> Are you sure?

when I freshly installed Gutsy I just ran ntfs-config (without installing anything else) and I was up and away.

Gutsy already has ntfs-3g built-in, then ofcourse you can just install ntfs-config, but this does not apply for 7.04 users. But like por100pre1 said, we better check the drive to see what filesystem it actually is using. You can install Gparted using:-

```
sudo apt-get install gparted
```

---

### Post by jlachovsky on 2007-10-26
Yeah I already have a two NTFS formatted partitions that I can read and write to fine.  I think it is an issue with U3.

---

### Post by PmDematagoda on 2007-10-26
Not necessarily, try mounting the device manually using:-

```
sudo ntfs-3g /dev/locationofdrive /media/mountpoint -o rw
```

---

### Post by jlachovsky on 2007-10-28
I don't know the location of the drive.  I tried checking it using Partition Editor and the drive didn't show up either.

---

### Post by PmDematagoda on 2007-10-29
You are right, it is an issue with U3 itself. I tried my mom's Kingston U3 drive as well, but it only read the initial part of the drive containing the launcher, but not the data part.

---

### Post by jlachovsky on 2007-10-29
> **PmDematagoda said:**
> You are right, it is an issue with U3 itself. I tried my mom's Kingston U3 drive as well, but it only read the initial part of the drive containing the launcher, but not the data part.

Yeah I was checking on Google to see if anyone else was having issues with it, but I didn't find anything.  Very interesting I wonder how many other people are having this issue?

---

### Post by jlachovsky on 2007-11-20
Anybody get any farther with this?  I really hate having to boot into Windows just to access my files on my flash drive and I don't want to wipe the U3 part.

---

### Post by PmDematagoda on 2007-11-21
There maybe one way you can access your U3 drive on Ubuntu by disabling the password prompt on the insertion of the USB drive through Windows. This did work when one of my friends used his U3 drives on Ubuntu without any access problems, and when I asked him if he had put any password protection on the drive, he said there wasn't any, that maybe the same issue with yours.

---

### Post by mike555 on 2007-11-21
A lot of people are having problems with U3 software (on Linux or Mac) ... I just went to Sandisk site (in Windows) and downloaded the little U3 uninstaller , use it to get rid of U3 and the thumbdrive should work ..... if not format it Fat32 , then it should work just fine , without U3 .........

---

### Post by jlachovsky on 2007-11-26
> **mike555 said:**
> A lot of people are having problems with U3 software (on Linux or Mac) ... I just went to Sandisk site (in Windows) and downloaded the little U3 uninstaller , use it to get rid of U3 and the thumbdrive should work ..... if not format it Fat32 , then it should work just fine , without U3 .........

I appreciate the the suggestions, but I want to figure out what is really going on here and not just doing a workaround.  It has worked in every other instance of Ubuntu before 7.10 (and a couple of other distros) so I am thinking it is something they changed in 7.10.  I really don't care if the actual U3 functionality works in Ubuntu, I just want to be able to access my data on the flash drive. II like having the U3 functionality (Avast comes in handy with virus/spyware removals for work) so I don't necessarily want to get rid of it.  I also don't want to downgrade to fat32, because I am pretty sure this isn't an issue with the fact that it's NTFS (I have three other partitions on my HD and an external backup drive all formatted NTFS).  It's not a huge issue, because I still have to boot into Windows for games and I can take the files from the flash drive and throw them on a separate partition that I store all my data on, I would just like to be able to access it in Ubuntu, especially when I never had an issue in the past.

Edit:PmDematagoda I'll give that a try and see if it works, even though I also don't have it password protected.

---

