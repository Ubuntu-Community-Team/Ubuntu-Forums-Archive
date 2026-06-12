---
title: "ubuntustudio-audio problem"
date: 2008-05-05
forum: General Help
---

### Post by gbrannan on 2008-05-05
I had a problem installing ubuntustudio-audio, I got this error message:

dpkg:  dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg:  error processing ubuntustudio-audio (--install):
 dependency problems - leaving unconfigured

I tried to re-install and I got this message:

Please insert the disk labeled:
Ubuntu-Studio 8.04 _Hardy Heron_ - Release amd64 (20080423.1)
in drive /cdrom/

The DVD was in the drive and I could see it in file browser.  I could access the readme file and all, but I still got this message even after multiple attempts and being sure the DVD was in and mounted before I ran SPM

When I cancelled I got this message:

W: Failed to fetch cdrom:[Ubuntu-Studio 8.04 _Hardy Heron_ - Release amd64 (20080423.1)]/pool/universe/u/ubuntustudio-meta/ubuntustudio-audio_0.28_amd64.deb

So, I went to the DVD, went to /pool/universe/u/ubuntustudio-meta/ and clicked on ubuntustudio-audio_0.28_amd64.deb and it opened with GDebi Package Installer.  I got the same message as the first time I installed it when I installed everything through SPM.


TIA

PS, yes, I'm a n00b to Linux, but I used to be very proficient in MS-DOS 3.2 and MS-DOS 5.0 back in the day, so I'm not afraid of terminal, I just haven't learned even the basics yet.

---

### Post by perlluver on 2008-05-05
> **gbrannan said:**
> I had a problem installing ubuntustudio-audio, so I tried to re-install and I got this message:

Please insert the disk labeled:
Ubuntu-Studio 8.04 _Hardy Heron_ - Release amd64 (20080423.1)
in drive /cdrom/

The DVD was in the drive and I could see it in file browser.  I could access the readme file and all, but I still got this message even after multiple attempts and being sure the DVD was in and mounted before I ran SPM

When I cancelled I got this message:

W: Failed to fetch cdrom:[Ubuntu-Studio 8.04 _Hardy Heron_ - Release amd64 (20080423.1)]/pool/universe/u/ubuntustudio-meta/ubuntustudio-audio_0.28_amd64.deb

Is there another way to install this?

The title of the DVD seems to be "Ubuntu-Studio 8.04 amd64".  How can I make it look there instead of "Ubuntu-Studio 8.04 _Hardy Heron_ - Release amd64 (20080423.1)"?

TIA

PS, yes, I'm a n00b to Linux, but I used to be very proficient in MS-DOS 3.2 and MS-DOS 5.0 back in the day.

If you are connected to the internet, turn off the CD-ROM in system>administration>software sources.

---

### Post by gbrannan on 2008-05-05
> **perlluver said:**
> If you are connected to the internet, turn off the CD-ROM in system>administration>software sources.

When I do that SPM can find nothing with ubuntustudio.  I have universe, multiverse, and restricted all selected.

---

### Post by perlluver on 2008-05-05
> **gbrannan said:**
> When I do that SPM can find nothing with ubuntustudio.  I have universe, multiverse, and restricted all selected.

Did you update the repos, after you de-selected the CD-ROM?

Edit: Run these two commands in terminal together, ```
sudo apt-get update && sudo apt-get install ubuntustudio-audio
```

---

### Post by gbrannan on 2008-05-05
> **perlluver said:**
> Did you update the repos, after you de-selected the CD-ROM?

Edit: Run these two commands in terminal together, ```
sudo apt-get update && sudo apt-get install ubuntustudio-audio
```

I tried both of those things and I did find ubuntustudio-audio, reinstalled it both ways and I still get the error.  Is the problem with timidity?  It says

dpkg:  error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg:  dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg:  error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured.

---

### Post by perlluver on 2008-05-05
> **gbrannan said:**
> I tried both of those things and I did find ubuntustudio-audio, reinstalled it both ways and I still get the error.  Is the problem with timidity?  It says

dpkg:  error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg:  dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg:  error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured.

Run these one at a time, ```
sudo apt-get install timidity
``` then ```
sudo apt-get install ubuntustudio-audio
```.  I was having trouble with this yesterday.

---

### Post by gbrannan on 2008-05-05
> **perlluver said:**
> Run these one at a time, ```
sudo apt-get install timidity
``` then ```
sudo apt-get install ubuntustudio-audio
```.  I was having trouble with this yesterday.

I tried it once and it didn't work, so I uninstalled both packages, then re-installed using terminal.  It didn't give me any error messages this time, but I need to try it out.

Thanks!

---

