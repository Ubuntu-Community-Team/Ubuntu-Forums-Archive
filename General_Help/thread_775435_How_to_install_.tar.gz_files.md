---
title: "How to install .tar.gz files?"
date: 2008-04-30
forum: General Help
---

### Post by chiku on 2008-04-30
Help required.
Some how my computer is not able to connect to the repositeries.
How do i install .tar.bz2 files?

---

### Post by chiku on 2008-04-30
also i get 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by descentspb on 2008-04-30
2. Exit all the applications, that are using the repositories (synaptic or update manager), then try to install again.

---

### Post by chiku on 2008-04-30
Okay I had synaptic working. But otherwise I get following error
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

---

### Post by ryanhaigh on 2008-04-30
Can you please post the command that you are using to do that?
If it is something like apt-get install packagename you need to use **sudo** apt-get install packagename.

---

### Post by ryanhaigh on 2008-04-30
Can you please post the command that you are using to do that?
If it is something like apt-get install packagename you need to use **sudo** apt-get install packagename.

Generally it is better to use software available in ubuntu before installing from the source code (which is what is likely in that tar.bz2 archive you have) what application/software are you trying to install.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by MaindotC on 2008-04-30
That's usually related to running the apt-get or synaptic under non-root privileges.  For apt, try:

```

sudo apt-get update

```

And if you need to search for a program try:
```

sudo apt-cache search <filename>

```

where <filename> is the actual name of the file you're trying to find.

---

### Post by MaindotC on 2008-04-30
As for tar.bz2 files, they are compressed files.  You can uncompress them by typing the following in a command prompt (be sure you are in the directory where you want the files uncompressed):

```

tar xvf <filename>.tar.bz2

```

That should create a folder usually named the same as the filename without the .tar.bz2 extension.  Enter the folder, and then what you do depends on what you have in the folder.  Let us know if you wish to proceed.

---

### Post by chiku on 2008-04-30
Whenever i try using 
sudo apt-get update

I get 

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by chiku on 2008-04-30
On the website:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

some instructions were given on installing .tar.gz files

I am trying to install latest gcc 4.3.0

sudo aptitude install gcc-4.3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "gcc-4.3.0"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

---

### Post by ryanhaigh on 2008-04-30
Searching packages.ubuntu.com ([http://packages.ubuntu.com/search?keywords=gcc&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=gcc&searchon=names&suite=hardy&section=all)) indicates that no gcc-4.3 package is available, the latest is gcc-4.2 which is why the package can't be found. 

For you lock issue perhaps you should try rebooting the machine, maybe an application opened the lock file and crashed and the system still thinks the file is open due to some handler remaining after the crash.

---

### Post by defmomo on 2008-04-30
Why don't you try to open a root shell session:
```
 sudo -s 
```
Enter your password then start the installation:
```
aptitude install gcc-4.3.0
```
Although I should warn you, gcc-4.3.0 doesn't seem to be available in the repos.

---

### Post by MaindotC on 2008-04-30
Definitely either a permissions issue or some other program is accessing the lock file such as Synaptic or Software updater.  They have to be closed and nothing else can be accessing that file to do the apt-get update or upgrade.

---

