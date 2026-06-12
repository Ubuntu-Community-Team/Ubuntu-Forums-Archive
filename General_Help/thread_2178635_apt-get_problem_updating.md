---
title: "apt-get problem updating"
date: 2013-10-04
forum: General Help
---

### Post by Claude_Sutton on 2013-10-04
When updating with apt-get, I get the following at the end of the output.

I have no idea how to resolve this.

```
14 B]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en [26.7 kB]
100% [59 Translation-en bzip2 0 B] [Waiting for headers]            130 kB/s 0s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [1,175 kB]            
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,306 B]       
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [6,239 kB]        
100% [48 Translation-en gzip 715 kB] [Waiting for headers]         93.6  kB/s 0sE: Unable to parse package file  /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en.decomp  (1)
Fetched 27.2 MB in 5min 50s (77.6 kB/s)                                        
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Bad header line [IP: 91.189.91.13 80]

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en  

W: Failed to fetch  gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en   Encountered a section with no Package: header

W: Failed to fetch  gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en   Encountered a section with no Package: header

W: Failed to fetch  gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en   Encountered a section with no Package: header

W: Failed to fetch  gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en   Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I also have the following problem:

```
[Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

---

### Post by ibjsb4 on 2013-10-04
Try cleaning out your /apt/lists.

```
sudo rm -r /var/lib/apt/list

sudo mkdir -p /var/lib/apt/list/partial

sudo apt-get clean

sudo apt-get update
```

---

### Post by Claude_Sutton on 2013-10-04
Did not help.

Got the same results.

---

