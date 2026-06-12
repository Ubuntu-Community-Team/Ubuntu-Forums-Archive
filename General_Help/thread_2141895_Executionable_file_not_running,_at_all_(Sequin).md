---
title: "Executionable file not running, at all (Sequin)"
date: 2013-05-04
forum: General Help
---

### Post by alphaamanitin on 2013-05-04
Hi Guys,

I have downloaded the sequin.linux.tar.gz and the 64bit version.  Ran ```
tar -zxvf Downloads/sequin.linux.tar.gz -C ~/Sequin
``` Everything looked good; all was extracted properly, no warnings.  I have checked that the permisions on executable sequin file are set for my username as read/write/excute as program.  Double clicking the file does nothing, right clicking and choosing run as program (or execute as program cannot remember exact wording) does nothing, tried running it from the terminal, nothing.  I mean really nothing as well.  It is like I haven't even tried to run the program when I click on the icon or right click at tell it to execute.  

I am running Xubuntu 12.04 LTS on Panp9 System76.  I cannot use the sequin that is in the repos.  It is way out of date and does not work well for what I am doing.

Thanks for any help.

AlphaA

---

### Post by bluefrog on 2013-05-04
run the command in a terminal to see what error occurs, if any.

---

### Post by montag dp on 2013-05-04
Are you sure that you have the 64-bit version and that your machine is 64 bit? I ask because it kind of sounds like what happens when I try to run some 32-bit programs on my 64 bit machine. Usually, installing the ia32-libs package does the trick in that case.

---

### Post by alphaamanitin on 2013-05-06
> **bluefrog said:**
> run the command in a terminal to see what error occurs, if any.

As I said in my first post, "tried running from terminal nothing."  When I run it from the terminal nothing happens, I get no error, no msg of any kind, and I just end up with a new line waiting for me to put in a command.  


> **montag dp said:**
> Are you sure that you have the 64-bit version and that your machine is 64 bit? I ask because it kind of sounds like what happens when I try to run some 32-bit programs on my 64 bit machine. Usually, installing the ia32-libs package does the trick in that case.

I definitely have the AMD64 version of xubuntu 12.04 LTS.  Also, I do not think this can be the issue; As I said, I have tried both the 32 bit Sequin version and the 64 bit Sequin version and get the same response (or rather, non-response) to attempting to run the program.

I know this is a bit of a crappy thing and you guys are just trying to help.  It is frustrating because there is no error, it makes no sense.  

AlphaA

---

### Post by montag dp on 2013-05-06
That is strange.  Just curious, when you try to run from the terminal, does bash auto-complete the command?  (Hit tab while typing if you're not familiar with auto-completion.)  The only time I've seen something like this happen, when trying to run a 32-bit executable on a 64-bit machine, auto-completion wouldn't work.

In any case, it sounds like a problem with the program itself and not your hardware.  Since I'm not familiar with the program, could you give some more information about it?  Are there other people you know of running it on Linux, and is the source code available, or just binaries?

---

### Post by alphaamanitin on 2013-05-06
So I found the issue and the solution.  I will describe what was going on in case any others use Sequin.

Sequin: this is a software tool created and distributed by the USA governments NCBI, NIH, and NSF organizations for semi-automated DNA, RNA, and protein submission to the NCBI GenBank genetic sequence database that integrates with the other major sequence databases in the world (e.g. Japans sequence database).

So, the versions that I downloaded from this website [https://www.ncbi.nlm.nih.gov/projects/Sequin/download/seq_download.html](https://www.ncbi.nlm.nih.gov/projects/Sequin/download/seq_download.html) for whatever reason didn't work at all.  So, I went back to the core FTP site [ftp://ftp.ncbi.nih.gov/sequin/](ftp://ftp.ncbi.nih.gov/sequin/) and redownloaded both the 64 bit and 32 bit versions (sequin.linux-x86_64.tar.gz and sequin.linux.tar.gz respectively).  I deleted my previous installs and extracted both to their own path (~/Sequin_64/ and ~/Sequin/ respectively).  I tried running bot version through the command ```
 ~/Sequin_64/sequin
``````
~/Sequin/sequin
```
This time both gave the same error > could not find libjpeg.so.62, missing or wrong directorySo, I installed the library ```
 sudo apt-get install libjpeg62
```This fixed the issue and now both are running fine.  I do not know why the original installs produced no results when trying to run the command.  I assume that some sort of file damage or corruption occurred that I was unaware of and therefore prevented the programs for being able to be ran.  

As an FYI, I believe the source code is available somewhere, but I am not sure where.

Thanks for the help guys,

AlphaA

---

### Post by steeldriver on 2013-05-06
I couldn't find a 64-bit tarball (I guess it's in the anonymous ftp archive somewhere? I didn't check), however the 32-bit version from the download web page

[ftp://ftp.ncbi.nih.gov/sequin/sequin.linux.tar.gz](ftp://ftp.ncbi.nih.gov/sequin/sequin.linux.tar.gz)

worked on my 32-bit 12.04.02 laptop AFTER I installed libmotif5

```
~/Downloads$ mkdir ~/sequin
~/Downloads$ tar xzf sequin.linux.tar.gz -C ~/sequin
~/Downloads$ 
~/Downloads$ cd ~/sequin
~/sequin$ ./sequin
[B]./sequin: error while loading shared libraries: libXm.so.4: cannot open shared object file: No such file or directory
[/B]~/sequin$ 
~/sequin$ sudo apt-get install libmotif4
.
.
.
~/sequin$ ./sequin         # <-- this works

```

Maybe it's an issue with 64-bit motif libs?

---

### Post by alphaamanitin on 2013-05-06
I ended up requiring a different library.  Maybe because I am running Xubuntu?

AlphaA

---

### Post by montag dp on 2013-05-06
Glad you got it sorted out.  It could be that the original binaries were compiled a long time ago on an older machine and simply don't work on newer hardware, or there's just something else wrong with them.

---

### Post by alphaamanitin on 2013-05-06
Who knows.  I wish I wouldn't have deleted them using rm though.  I didn't think about it 'til now but I should have created a md5 hash of the non-working .tar.gz files and the working ones and compared them.  

Oh well. 

AlphaA

---

