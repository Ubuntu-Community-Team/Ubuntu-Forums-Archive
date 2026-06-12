---
title: "bash: &quot;executable&quot;: No such file or directory"
date: 2008-06-27
forum: General Help
---

### Post by Max Spain on 2008-06-27
Hi, I have been using Ubuntu happily for quite some time now, but I have been running into this problem occasionally on fresh installs.  It goes away eventually, but I never remembered what I did to fix it.  I already searched the forums and google, but I couldn't find anything.

What happens is that when I try to execute certain files, I get the "No such file or directory" error in bash.  This happens despite the fact that I used tab completions to insert the file name.  Also the files are set to be executable in their permissions.  Here's an example using ET:QW

```
max@GamingBox:~/.phoronix-test-suite/installed-tests/etqw/data$ ls
base            etqw-rthread      libgcc_s.so.1       readme_1_5_patch.txt
copyrights.txt  etqw-rthread.x86  libjpeg.so.62       README.txt
etqw            etqwtv.txt        libSDL-1.2.id.so.0  sdl.1.2.12.patch
etqw-dedicated  etqw.x86          libstdc++.so.6      server_readme.txt
etqwded.x86     EULA.txt          openurl.sh
etqw_icon.png   libCgx86.so       pb
max@GamingBox:~/.phoronix-test-suite/installed-tests/etqw/data$ ./etqw-rthread.x86 
bash: ./etqw-rthread.x86: No such file or directory
max@GamingBox:~/.phoronix-test-suite/installed-tests/etqw/data$ 

```

Any help would be appreciated.

---

### Post by ChameleonDave on 2008-06-27
Hmm.  Not sure.  Perhaps that happens if the file is sitting on a partition with a filesystem not marked in fstab as supporting executable files.

---

### Post by Max Spain on 2008-06-27
It is on my root partition, but thanks for the suggestion.

---

### Post by ChameleonDave on 2008-06-27
If you become root first with "sudo -i", is the behaviour the same?

---

### Post by VMC on 2008-06-27
Type this in that Terminal directory:

```
ls -l etqw-rthread.x86
```

And see who owns it and is it executable.

---

### Post by Max Spain on 2008-06-28
Output of "ls -l etqw-rthread.x86"

```
max@GamingBox:~/.phoronix-test-suite/installed-tests/etqw-demo/data$ ls -l etqw-rthread.x86 
-rwxr-xr-x 1 max max 6696668 2008-01-16 12:19 etqw-rthread.x86

```

As for running as superuser, that shouldn't be necessary for a game ;)

---

### Post by Max Spain on 2008-06-28
I have also tried linking to the executables and using taskset to launch them.  I might just try a reformat because I have no idea what's going wrong :confused:

---

### Post by ChameleonDave on 2008-06-28
> **Max Spain said:**
> 

As for running as superuser, that shouldn't be necessary for a game ;)
I didn't ask you for your opinion on whether it was necessary; I asked you whether the output was the same.  ;-)

---

### Post by charanpreethu on 2008-06-28
its simple jus got to synaptic manager and install "sudo"....your problem will be solved

---

### Post by Max Spain on 2008-06-28
> **ChameleonDave said:**
> I didn't ask you for your opinion on whether it was necessary; I asked you whether the output was the same.  ;-)

```
max@GamingBox:~/.phoronix-test-suite/installed-tests/etqw-demo/data$ sudo -i
root@GamingBox:~# cd /home/max/.phoronix-test-suite/installed-tests/etqw-demo/data/
root@GamingBox:/home/max/.phoronix-test-suite/installed-tests/etqw-demo/data# ls
base            etqw_icon.png     EULA.txt            libstdc++.so.6
copyrights.txt  etqw-rthread      libCgx86.so         openurl.sh
etqw            etqw-rthread.x86  libgcc_s.so.1       pb
etqw-dedicated  etqwtv.txt        libjpeg.so.62       README.txt
etqwded.x86     etqw.x86          libSDL-1.2.id.so.0  sdl.1.2.12.patch
root@GamingBox:/home/max/.phoronix-test-suite/installed-tests/etqw-demo/data# ./etqw-rthread.x86 
-bash: ./etqw-rthread.x86: No such file or directory
root@GamingBox:/home/max/.phoronix-test-suite/installed-tests/etqw-demo/data# 

```
Output is the same :(  Ty all for the suggestions, but this is not an easy one :confused:

---

### Post by ChameleonDave on 2008-06-28
If you boot from the Ubuntu live CD (or any Linux live CD) and try to execute those files, does it work?

---

### Post by Max Spain on 2008-06-28
With Live CD:
```
ubuntu@ubuntu:/media/disk/home/max/.phoronix-test-suite/installed-tests/etqw-demo/data$ ./etqw-rthread.x86 
./etqw-rthread.x86: error while loading shared libraries: libSDL-1.2.id.so.0: cannot open shared object file: No such file or directory

```
Works fine.

---

### Post by Max Spain on 2008-06-28
Thanks to everyone for your help, but this issue is a difficult one.  I am just going to reformat and reinstall.  I am quite used to this after several failed attempts at getting the latest Nvidia driver to install manually ;)  Fortunately for me, I wrote down the steps I took last time so this one should be a cakewalk.

---

### Post by Max Spain on 2008-06-29
Well, I reformatted and reinstalled, and I'm getting the same thing :confused:  This is getting really annoying, however, I think I've discovered a connection.  All of the executable files I am having problems running were self-extracted from ".run" files.  All of the files that were extracted from zips and tars are working fine.  Does anybody have any ideas why that might be???

---

### Post by bobyy on 2008-06-29
Hy ...maybe you alredy try this :
 
$sudo chmod +x etqw-rthread.x86
$sudo ./etqw-rthread.x86

but is just a sugestion.

---

### Post by cariboo on 2008-06-29
You don't have to extract a .run file, just make it executable if it isn't already eg:

```
chmod +x *run
```

Then run it as it is:

```
sudo ./*run
```

if you are in the same directory

Jim

---

### Post by Max Spain on 2008-06-29
Thanks for the replies, but no joy so far :(  I did find out that I cannot execute those *.run files.  They were extracted using "unzip -o *.run".  I am going to try downloading them fresh and seeing if that does anything.  Before I reformatted and installed this Nvidia card, they were all working :confused:  I just checked the zerowing.idsoftware.com site and the md5sum's match too :confused:  I think this might be worthy of a bug report.

---

### Post by Max Spain on 2008-06-30
This issue has been SOLVED:KS  I checked the launchpad and came across [this]("https://answers.launchpad.net/ubuntu/+question/11491") person having the same problem.  It turns out that I didn't have the 32-bit libs installed.  Thanks to everyone for their help.

---

### Post by joelwhitehouse on 2009-11-04
Yes -- running > sudo apt-get install ia32-libs did it for me.  I wanted to reply because it took me WAY too long to find this and I want to boost the relevance for others.


Is there anyway to get Bash to generate a more helpful error -- perhaps by mentioning what file is missing?

---

### Post by suryasaha on 2009-11-09
You would think this library would be installed by default.

---

### Post by arch0njw on 2011-06-07
> **Max Spain said:**
> This issue has been SOLVED:KS  I checked the launchpad and came across [this]("https://answers.launchpad.net/ubuntu/+question/11491") person having the same problem.  It turns out that I didn't have the 32-bit libs installed.  Thanks to everyone for their help.

Holy smokes... 3 years later and running into the same issue!  I'm glad you posted the resolution!

---

