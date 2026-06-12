---
title: "can't download"
date: 2008-04-12
forum: General Help
---

### Post by badhabit on 2008-04-12
Ok I'm having some trouble downloading Opera Web Browser. When I got to download it it tells me I don't have enough disk space. Here's the error I get.There is not enough room on the disk to save /tmp/qixhkxIP.deb.part.
Odd thing is I have 171 GB of  free space. 
I'm running 8.04 Hardy. 
Thank you very much for any help you can give.

---

### Post by wormser on 2008-04-12
Try installing from the repositories.

```
sudo apt-get install opera
```

---

### Post by polmir on 2008-04-12
Type in terminal:
```
sudo apt-get clean
sudo apt-get autoclean
```
and try installing opera.

---

### Post by badhabit on 2008-04-12
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_hardy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
I also did the clean and auto clean. Neither worked.

---

### Post by wormser on 2008-04-12
I am not sure if this will work but it is worth a shot.

```
sudo apt-get install -f
```still not working then try
```
sudo dpkg --remove --force-remove-<packagename>
```

---

### Post by brian_p on 2008-04-12
> **polmir said:**
> Type in terminal:
```
sudo apt-get clean
sudo apt-get autoclean
```
and try installing opera.

Those two commands produce entirely different results. I would suggest that the OP may find the first one undesirable.

Too late! I see he has done it.

---

### Post by Tyke91 on 2008-04-12
taken from the apt-get man page

```

clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

``````

 autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.


```

oh no :(

---

### Post by brian_p on 2008-04-12
> **badhabit said:**
> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_hardy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
I also did the clean and auto clean. Neither worked.

That looks like a packages file is missing. Have a look in  var/lib/apt/lists to see if is there.

```
ls -l var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_hardy_main_binary-i386_Packages
```

Correct the situation with

```
apt-get update
```

---

### Post by brian_p on 2008-04-12
> **Tyke91 said:**
> oh no :(

it's not a disaster but keeping current packages is generally a good idea in my opinion.

---

### Post by polmir on 2008-04-12
[QUOTE=''brian_p'']
...
Too late! I see he has done it.[/QUOTE]

```
apt-get -h
...
clean - Erase downloaded archive files
autoclean - Erase old downloaded archive files
...
```
**badhabit** --- >>[Red this](http://qref.sourceforge.net/Debian/reference/ch-package.en.html#s-apt-trouble)<<

---

### Post by Nameless_one on 2008-04-12
From what you mentioned in the opening post, I suppose you try to download it to the default location. Try right clinking and saving to a different location and install from there, by double clicking on the .deb.

---

