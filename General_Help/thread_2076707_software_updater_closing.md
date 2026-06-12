---
title: "software updater closing"
date: 2012-10-26
forum: General Help
---

### Post by jmore9 on 2012-10-26
Hello

I am running 12.10 and have the following problem:

When i start the software updater it opens and displays some software to update.  I click update now and then it asks for password.  As soon as i have typed 2 or 3 letters it closes.

Software to be updated was mplayer and some codecs

Anyone got any ideas ?

---

### Post by Bashing-om on 2012-10-26
well, What I would do in this case :
start with terminal codes
```
sudo apt-get update
sudo apt-get upgrade
```take action on the errors generated and  heed  dpkg's advise .

Depending on this, is what to do next .
[INDENT]hth <==BDQ
[/INDENT]

---

### Post by cstoh on 2012-10-27
when i click on Software Update icon, it spends some time searching then get this error message

Failed to download repository information
check your internet connection

I have very good internet connection. About 28 Mbps.
In the detailes box I ge this

W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by plucky on 2012-10-27
@cstoh
You should start your own thread instead of hi-jacking another users thread.


> W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Disable the CDrom as a sources using the **Settings** button for the Update Manager.

> W:Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_source _Sources Hash Sum mismatch

Open a terminal and run ```
sudo rm /var/lib/apt/lists/partial/* -vf
``` and then run ```
sudo apt-get update
``` again and see if you get the same error.


Good Luck

---

### Post by cstoh on 2012-10-28
I followed your instructions but at the end of "apt-get update" I get this bunch of error messages. What does it mean and how do I fix it?

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by cstoh on 2012-10-28
I clicked on the Spftware Updater and got similar error messages except for the earlier lines which mentions the CDROM.

W:Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by plucky on 2012-10-28
Can you see if the directory is empty ```
ls /var/lib/apt/lists/partial/
```

Then run the "sudo rm" command again and then check the directory is now empty.There should be nothing in that directory.

If it still gives you the same error,try changing the Download server to the main server using Software Sources and try again.

Good Luck

---

### Post by aabed91 on 2012-10-28
This problem appear when some repository are not exist.

---

### Post by cstoh on 2012-10-28
ls /var/lib/apt/lists/partial/
gave this result, so its obviously not empty

archive.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages.decomp.FAILED
archive.ubuntu.com_ubuntu_dists_quantal_main_source_Sources
archive.ubuntu.com_ubuntu_dists_quantal_main_source_Sources.decomp.FAILED
archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-amd64_Packages.decomp.FAILED
archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-i386_Packages.decomp.FAILED
archive.ubuntu.com_ubuntu_dists_quantal_multiverse_source_Sources
archive.ubuntu.com_ubuntu_dists_quantal_multiverse_source_Sources.decomp.FAILED
archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-amd64_Packages.decomp.FAILED
archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages.decomp.FAILED
archive.ubuntu.com_ubuntu_dists_quantal_universe_source_Sources
archive.ubuntu.com_ubuntu_dists_quantal_universe_source_Sources.decomp.FAILED
extras.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages
extras.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages.decomp.FAILED
extras.ubuntu.com_ubuntu_dists_quantal_main_source_Sources
extras.ubuntu.com_ubuntu_dists_quantal_main_source_Sources.decomp.FAILED

---

### Post by cstoh on 2012-10-28
After running "rm /var/lib/apt/lists/partial/* -vf" I verified that it was empty. But after running "apt-get update" I got the same error messages as the upper post. I had changed the server to Main Server is the Software Soources. So it looks like that doesn't help.

---

### Post by plucky on 2012-10-28
> archive.ubuntu.com_ubuntu_dists_quantal_main_binar y-i386_Packages

Check out the space between the r and y in binar y and all the other lines also have a space in them.

If you are still on the main server run ```
sudo rm /var/lib/apt/lists/partial/* -vf
sudo rm /var/lib/apt/lists/* -vf
``` as it could be the .list files are corrupt.

Then run ```
sudo apt-get update
``` and see what happens.

Good Luck

---

### Post by cstoh on 2012-10-29
> **plucky said:**
> Check out the space between the r and y in binar y and all the other lines also have a space in them.

If you are still on the main server run ```
sudo rm /var/lib/apt/lists/partial/* -vf
sudo rm /var/lib/apt/lists/* -vf
``` as it could be the .list files are corrupt.

Then run ```
sudo apt-get update
``` and see what happens.

Good Luck

I did what you suggested. It still doesn't work

---

