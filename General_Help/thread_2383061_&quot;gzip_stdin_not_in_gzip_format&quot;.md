---
title: "&quot;gzip: stdin: not in gzip format&quot;"
date: 2018-01-20
forum: General Help
---

### Post by sks24 on 2018-01-20
I would appreciate some help with installing GuaPDF - or any other PDF password utility which gives me to option to remove password permissions or determine the password - on my Ubuntu installation on my i7/8gb Dell XPS laptop. 

GuaPDF was the only utility which started running on the Windows partition on this laptop, but I would prefer to perform this operation in Ubuntu. 

The specific problem I'm having with the GuaPDF Ubuntu installation has to do with the following error message: "gzip: stdin: not in gzip format"

It's been literally years since I've installed packages in Ubuntu, and so I apologize if I'm missing something very elementary.

Thanks in advance,
Scott

see: 

```
scott@scott-Dell-System-XPS-L702X:~$ cd Desktop
scott@scott-Dell-System-XPS-L702X:~/Desktop$ tar xvfz guapdf-3.3-free-linux.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now
scott@scott-Dell-System-XPS-L702X:~/Desktop$ ls
csv file contacts.csv         teamviewer_12.0.85001_i386
guapdf-3.3-free-linux.tar.gz  teamviewer_12.0.85001_i386.deb
scott@scott-Dell-System-XPS-L702X:~/Desktop$ guapdf
guapdf: command not found
scott@scott-Dell-System-XPS-L702X:~/Desktop$ guapdf-align
guapdf-align: command not found
scott@scott-Dell-System-XPS-L702X:~/Desktop$ tar xvfz guapdf-3.3-free-linux.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now
scott@scott-Dell-System-XPS-L702X:~/Desktop$ file guapdf-3.3-free-linux.tar.gz
guapdf-3.3-free-linux.tar.gz: POSIX tar archive (GNU)
scott@scott-Dell-System-XPS-L702X:~/Desktop$ sudo apt update
[sudo] password for scott: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease                    
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                    
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [62.7 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [71.2 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [51.3 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [226 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [185 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [268 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [4,712 B]
Fetched 1,578 kB in 1s (1,440 kB/s)                                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
scott@scott-Dell-System-XPS-L702X:~/Desktop$ sudo apt install guapdf-3.3-free-linux.tar.gz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package guapdf-3.3-free-linux.tar.gz
E: Couldn't find any package by glob 'guapdf-3.3-free-linux.tar.gz'
E: Couldn't find any package by regex 'guapdf-3.3-free-linux.tar.gz'
scott@scott-Dell-System-XPS-L702X:~/Desktop$ sudo apt install guapdf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package guapdf
scott@scott-Dell-System-XPS-L702X:~/Desktop$ cd /home/scott/Desktop/guapdf
scott@scott-Dell-System-XPS-L702X:~/Desktop/guapdf$ sudo apt install guapdf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package guapdf
scott@scott-Dell-System-XPS-L702X:~/Desktop/guapdf$ ^C
scott@scott-Dell-System-XPS-L702X:~/Desktop/guapdf$ 

```

---

### Post by steeldriver on 2018-01-20
What does

```

file guapdf-3.3-free-linux.tar.gz

```

say? Sometimes the issue with downloads is that they actually save a web page rather than a file

---

### Post by sks24 on 2018-01-20
Thanks steeldriver

POSIX tar archive (GNU)

```
scott@scott-Dell-System-XPS-L702X:~$ cd Desktop
scott@scott-Dell-System-XPS-L702X:~/Desktop$ file guapdf-3.3-free-linux.tar.gz
guapdf-3.3-free-linux.tar.gz: POSIX tar archive (GNU)
scott@scott-Dell-System-XPS-L702X:~/Desktop$ mv guapdf-3.3-free-linux.tar.gz
mv: missing destination file operand after 'guapdf-3.3-free-linux.tar.gz'
Try 'mv --help' for more information.
scott@scott-Dell-System-XPS-L702X:~/Desktop$ mv guapdf-3.3-free-linux.tar.gz guapdf-3.3-free-linux.tar # optional
scott@scott-Dell-System-XPS-L702X:~/Desktop$ tar xvf guapdf-3.3-free-linux.tar
guapdf/
guapdf/pdfcrypt-cl.dll
guapdf/readme
guapdf/restricted.pdf
guapdf/encrypted.pdf
guapdf/guaPDF.txt
guapdf/changes.txt
guapdf/guapdf
guapdf/guapdf-ocl
scott@scott-Dell-System-XPS-L702X:~/Desktop$ 
```

---

### Post by steeldriver on 2018-01-20
OK so issue solved? 

FWIW, modern GNU tar is usually capable of figuring out the type of compression (or none) so the explicit z,j,J etc.  are often omitted nowadays

---

### Post by sks24 on 2018-01-21
I'm not sure. I didn't realize that the Linux application was terminal-only, and I'm not sure that I'm entering the commands correctly. I'm gonna hafta buy the program to get support. 

Thanks for you help steeldriver.

---

