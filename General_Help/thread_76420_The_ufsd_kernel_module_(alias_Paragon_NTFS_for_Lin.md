---
title: "The ufsd kernel module (alias Paragon NTFS for Linux)"
date: 2005-10-15
forum: General Help
---

### Post by drigloi on 2005-10-15
Paragon's NTFS for Linux is an NTFS file system driver for Linux. The demo version mounts NTFS in read-only mode while the full version is capable of reliable and fast NTFS write operation.

I'm experiencing with the demo version which worked under Hoary but now in Breezy I can compile the module but can't insert it. This is how far I got with ufsd:

1. grab the ufsd source code from Paragon:
```
wget http://download.paragon.ag/demo/ntfslin_drv.tgz
```

2. untar it under let's say /usr/src/ufsd

3. prepare the build environment. We'll need the current kernel headers, the build-essential package and gcc-3.4 (as far as I understand Breezy packages are made with gcc-4.02 while the kernel still needs gcc-3.4):
```
sudo apt-get install linux-headers-386 build-essential gcc-3.4
```

4. create some symlinks to let ufsd's install.sh to find kernel and module stuff and awk
```
sudo ln -s /usr/src/linux-headers-2.6.12-9-386 /usr/src/linux
sudo ln -s /lib/modules/2.6.12-9-386 /lib/modules/2.6.12
sudo ln -s /usr/bin/awk /bin/awk
```

5. run ufsd's install script
```
cd /usr/src/ufsd
sudo sh install.sh
```

The result is: compilation successful but the resulting ufsd module is incompatible with Breezy's kernel The operation was successful but the patient died :(.
```
root@ubuntu:/usr/src/ufsd# sh install.sh
configure kernel
scripts/kconfig/conf -s arch/i386/Kconfig
#
# using defaults found in .config
#
  CHK     include/linux/version.h
ufsd driver can be compiled for kernel 2.6.12(2.6.12)
We can build module only for 2.6.x kernels
Ufsd module was build and will be installed for kernel 2.6.12 but current kernel in 2.6.12-9-386.
Moving module in destination directory...
`./objfre/ufsd.ko' -> `/lib/modules/2.6.12/kernel/fs/ufsd/ufsd.ko'
Finding module dependencies...
I think you are using a Debian-like system
can't load ufsd module
root@ubuntu:/usr/src/ufsd# modprobe ufsd
FATAL: Error inserting ufsd (/lib/modules/2.6.12-9-386/kernel/fs/ufsd/ufsd.ko): Invalid module format
```

---

### Post by Polo_Talnir on 2005-12-15
>> while the full version is capable of reliable and fast NTFS write operation.
Really? did you try this reliable and fast capability?
I bet you didn't, because if you did, and had a bad time
recovering the ruined NTFS partition, you would write otherwise.

With this driver, whose installation is not exactly as the readme file,
written in poor English, describes, you can not perform reliably even
the simplest operations without corrupting the filesystem.

Furtunately, several of the corruptions that it the NTFS for Linux
crap generates, can be corrected by the elementary Windows chkdsk.

For example, I challenge you to use the reliable and capable NTFS
for Linux driver to create a small file in the drive, then edit it with
'vi' and try to save it. That is
$ cat > file1
line 1 for edit
line 2 perhaps also for edit
^D
$ vi file1
.... do some changes ... and save the file --> 

A copy test: I tried to copy over a large file: my
Registry SOFTWARE hive ~87MB.
root@0[testdir]# cp /win2Ke/WINNT/system32/config/software software1
root@0[testdir]# cp software1 software2
root@0[testdir]# ls -l
total 36
-rwxr-xr-x 1 root root 19 Dec 13 01:07 file1
-rwxr-xr-x 1 root root 86556672 Dec 13 01:13 software1
-rwxr-xr-x 1 root root 86556672 Dec 13 01:31 software2
root@0[testdir]# sync
root@0[testdir]# cmp software1 software2
software1 software2 differ: char 49659905, line 49343
root@0[testdir]#

Copying the file from another partition (a FAT32 partition)
produced a correct, identical copy of the file.

The sequence:
$ rm file2
$ cp file1 file2
resulted in both files become unreachable.
Later, back in Windows, I run chkdsk and fixed the "disappeared"
files, but GIMME A BREAK!

This product claims to be a commercial product and it
does not even pass the most basic sanity checks. So
much so, that the seriousness of Paragon as a software
developer can be doubted. How they dare to call this
thing a complete, commercial product?! I guess that the
draconic software licenses that we grew to accept without
thinking allows for any crap to be sold to us.

The results with NTFS for Linux were pathetic. Really PATHETIC.

Summarizing, NTFS for Linux by Paragon, as far as the
version I checked goes (v3, reasonably recent) may
be ready for alpha testing, but is NOT a commercial product
ready for production/prime-time. Using it in any
form of a production environment without taking
backups prior to doing it, is, without any doubt,
a stupid thing to do. NTFS for Linux probably can help
to do some elementary things, without trusting it too
much to work well and not to corrupt the NTFS filesystem.
For example, if you have to edit a file, do it in an ext2
or ext3 partition, then copy the edited result to the
NTFS partition, and COMPARE the files, as they may get
corrupted in-transit. It probably can copy over an existing
file with identical size, but again, also the Linux built-in
NTFS driver can do that - no need to risk to use not-tested
features of a dubious driver by a dubious company.

Paragon clearly does not have their QA act put together
in a manner that will uncover the most elementary,
close to your eyes, bugs. Will you trust your data to
their driver?. You must have very little self-respect if you
do.

In short, a mildy useful piece of crap, dangerous enough
to make you think 5 times about using it, and that after
you took a full image backup of the disk that you are
going to touch with NTFS for Linux.

Hope this helps you decide what to do. Unfortunately,
there are no real solutions to the problem of
accessing transparently NTFS from Linux, so that
even this piece of crap can help in a pinch.

For all I can see in the NTFS-write-access-from-Linux
scene right now, the only decent solution, which seems
to work for all versions of NTFS requires some workaround
to work with Windows XP SP2 drivers/ntoskrnl.exe, is
Captive NTFS, which, alas is not supported anymore by
the author, and nobody else picked it up.

-Polo

---

### Post by zoiks on 2005-12-15
So exactly what are you trying to say, Polo?  ;)

---

### Post by Polo_Talnir on 2005-12-25
I don't think that it is so complicated to figure out what I was "trying" to
say.

I actually said everything that I tried, and what I wrote should be clear
for most average readers. But I will translate this for you to fewer words
if I can. I will add some more comments, as I feel inspired to write right now.

Of course, in spite of having provided specific examples where this piece of
crap will corrupt your NTFS filesystem, I have, for the sake of humbleness,
to write the following caveat: this is my (educated, but only my) opinion.

Summary for folks with short patience:

Paragon NTFS for Linux, version 3, which I tested very basically, is a piece
of crap, will corrupt your filesystem and is not even close to being a
production-strength product. The fact that Paragon, whoever they might
be, sells and advertises this junk as a product you can use, only reminds me
about how stupid all of us, users of commercial software, are, by accepting
those user-agreements that in one-sentence say "this thing I am selling to
you, in spite of me taking money from you, may not do what I am
advertising it does, may or may not be of any use to you, and best-of-all,
it may or may not ruin your system and your life, and in any case "we" are
not liable". And we keep accepting this. Therefore, this NTFS for Linux
garbage, can and will ruin your NTFS partition, and you have no basis to
sue Paragon or anybody else for that. Those that posted reviews from which
it can be understood that this garbage works, were probably the Paragon
folks in desguise, or someone that did not care to actually test minimally
the "product". Or may be someone that because he/she paid the $70
to Paragon and feels horribly for that, wants others to get screwed too.
Don't know the reason, but that is what it seems to me. I can't imagine
anyone in his/her sane mind to honestly recommend this pile of .... to
others. (did you notice the quotes surrounding "product"?).

For all the more Linux savvy folks out there, if you absolutely need to
access an NTFS partition in r/w mode, I whole-heartedly would
recommend to use the (currently unsupported, but that will probably
change ...) Captive NTFS. It is free, uses the native Windows software
to access the NTFS partition, and is therefore a safer choice than any
other implementation of NTFS-r/w-access for Linux. By *far* so.

Now, as I don't want to sound too biased in my opinions, Captive,
in addition to being not-currently-supported/updated, has its own
problems. Mainly in the area of performance, but there are some
other little problems that stem from the fact that it is not supported.

For example, as of kernel 2.6.10, the latest LUFS doesn't compile.
Captive leverages LUFS to work (which is also one of the reasons
for Captive's poor performance, in addition to using CORBA for certain
buffering/sandboxing internal functions).

Not a great problem, and it is easily solved, but needs to be solved,
by you.

Another one: Captive 1.1.5 (the latest at the time of writing) does
not recognize Windoze drivers/software other than WinXP SP1.
This requires an update, but these SP1 drivers work just fine as far
as I (and others) could test/see. There are also a couple of compilation
errors in Captive, which show if you don't use the "standard"
./configure parameters. But all this is for a separate thread. I
only wanted to give you and others a more complete picture.

There is currently no full solution to the problem of r/w access
to NTFS partitions from Linux. "Full solution" means, in my dictionary:
safe+stable, transparent and with acceptable throughput/performance.
We may be getting there some day with either the Linux-NTFS project,
or with Captive, if Captive gets a new boost/new developer that knows
what to do.

My opinion is that anything but a Captive-like solution (use of
native Windows software) requires quite a bit of accepting a statement
like "trust me ... I know" to be used. That is because the Linux-NTFS
drivers work based on reverse-engineering NTFS, which is hard (and that
is also where the arrogant Paragon folk failed, in addition to not having
the minimal honesty to test their product before releasing it).

Captive does not require that, as it uses the working-and-tested Windows
software at its interface. Plain brilliant! Kudos to Jan Kratochvil !! magnificent
job!.

OK. This was not short either ... but thank you for giving me a reason
to explain myself better (perhaps).

Shortest line: visit your psychiatrist before you buy Paragon NTFS for Linux.

-Polo

---

### Post by zoiks on 2005-12-25
Sarcasm doesn't go through well in text-based forums.  I guess the winky-smiley wasn't enough, I should have put <sarcasm> tags.  Anyhoo, I am sure I won't be rushing out to buy Paragon's products, if that makes you feel better.  ;)

---

