---
title: "steps in bisecting the kernel"
date: 2012-10-31
forum: General Help
---

### Post by Lars Noodén on 2012-10-31
I am trying to track down a [trackpad bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/881830) that started after the 2.6.35-22 kernel in 10.10 and before the 2.6.38-8 kernel in 11.04.  I am told that to [bisect the kernel](https://wiki.ubuntu.com/Kernel/KernelBisection) is the way to go.  

In the bisection instructions an example is given:

```

git log --oneline Ubuntu-2.6.35-24.42..Ubuntu-2.6.35-25.43

```

How do I calculate the right values for git based on the two known kernels (2.6.35-22 and 2.6.38-8****) I have?

---

### Post by Doug S on 2012-10-31
Hi Lars,
 
I think before you go to the git step. you want further isolate where the issue got introduced by testing more kernels from [https://launchpad.net/ubuntu/maverick/+source/linux](https://launchpad.net/ubuntu/maverick/+source/linux)
and /or
[https://launchpad.net/ubuntu/natty/+source/linux](https://launchpad.net/ubuntu/natty/+source/linux) (scroll down to the "Releases in Ubuntu" section)
 
Oh, I see similar notes have been added to lauchpad bug report you linked to above. I was gone for quite some time trying to figure out this reply, and I guess you made progess in the meantime. Myself, I find this stuff a little slow and tedious to try to find and follow. Hope you get it isolated.

---

### Post by Lars Noodén on 2012-10-31
Thanks.  

I think I've found how to navigate [https://launchpad.net/ubuntu/maverick/+source/linux](https://launchpad.net/ubuntu/maverick/+source/linux) through to the versions of the kernel I need to test.

---

### Post by Lars Noodén on 2012-10-31
I've gotten through the kernels that were available for download.  

2.6.35-32.67, if it overwrote 2.6.35-32.64 when I installed it, was good.

2.6.38-10.44 was definitely bad.

What is the next step in the bisect?  I've tried followng the [example](https://wiki.ubuntu.com/Kernel/KernelBisection#Take_a_look_first_to_see_what_you_can_learn), but get the error below.

```

$ git log --oneline Ubuntu-2.6.35-32.67..Ubuntu-2.6.38-10.44
fatal: ambiguous argument 'Ubuntu-2.6.35-32.67..Ubuntu-2.6.38-10.44': unknown revision or path not in the working tree.
Use '--' to separate paths from revisions

```

---

### Post by Doug S on 2012-10-31
Wouldn't you switch to the natty kernels and continue to try to isolate?
I would start with 2.6.36-0.1 as a starting point for the natty successive approximation. If that works then 2.6.37-8.21 as an approximate mid-point of the 42 or 43 kernels in between, and so on...

---

### Post by Lars Noodén on 2012-11-02
Thanks.  I've gotten it narrowed down to the last good one as 2.6.38-7.39 and the first bad one as 2.6.38-8.40.  

 [https://wiki.ubuntu.com/Kernel/KernelBisection#Commit_bisecting_Ubuntu_kernel_versions](https://wiki.ubuntu.com/Kernel/KernelBisection#Commit_bisecting_Ubuntu_kernel_versions)

I'm able to clone the branch:

 [font=Courier New]git clone git://kernel.ubuntu.com/ubuntu/ubuntu-natty.git[/font]

and create a bisect

 [font=Courier New]git checkout -b mybisect origin/master[/font]

However, I can't get through the next step.

[s] [font=Courier New]git bisect start Ubuntu-2.6.38-8.40..Ubuntu-2.6.38-7.39[/font][/s]
 [font=Courier New]git bisect start Ubuntu-2.6.38-8.40 Ubuntu-2.6.38-7.39[/font]

It should say something about bisecting and the number of revisions left.  But it produces no output or anything like in the instructions.  If I try the statement again, it replies with, "[font=Courier New]Already on 'mybisect'[/font]"

Edit: It was the double dots that were wrong.

---

### Post by Lars Noodén on 2012-11-02
Now the output diverges from the guide:

$ git bisect start Ubuntu-2.6.38-8.40 Ubuntu-2.6.38-7.39
Switched to branch 'mybisect'
Bisecting: a merge base must be tested
[521cb40b0c44418a4fd36dc633f575813d59a43d] Linux 2.6.38

Where in the guide it should say the number of revisions and steps left.  How do I test a merge base?

---

### Post by Doug S on 2012-11-03
I think, but am not sure, that you are supposed to test the point that git has suggested. Git can not exactly "bisect" yet, and needs to know the answer if the point it selected is good or bad. For example (and since I can not actually test the kernel for your problem, I just made a "good" answer for this example):```
doug@s15:~/temp-lars/ubuntu-natty$ git bisect start Ubuntu-2.6.38-8.40 Ubuntu-2.6.38-7.39
Bisecting: a merge base must be tested
[521cb40b0c44418a4fd36dc633f575813d59a43d] Linux 2.6.38
doug@s15:~/temp-lars/ubuntu-natty$ git bisect good
Bisecting: 351 revisions left to test after this (roughly 9 steps)
[516b498acc786576d4dd4238f7d67812a5c5df86] UBUNTU: SAUCE: hid: ntrig: New ghost-filtering event logic
```I'll put this same info in the bug report, in case you don't see this.

---

### Post by Lars Noodén on 2012-11-03
Thanks, Doug.  How did you find out which option to add to git to go forward?

---

### Post by Lars Noodén on 2012-11-03
Ok, inching slowly forward, I've gotten to the stage where I need to build the kernel.  However, again the instructions don't match with what I have.

The instructions on [building a kernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) say

```

fakeroot debian/rules clean
fakeroot debian/rules binary-headers binary-generic

```

But there is no directory "debian" among the material I've cloned/checked out using git.

 ```

$ ls
[COLOR="Blue"]arch[/COLOR]     [COLOR="Blue"]debian.master[/COLOR]  [COLOR="Blue"]fs[/COLOR]       Kconfig      [COLOR="Blue"]mm[/COLOR]              [COLOR="Blue"]scripts[/COLOR]   [COLOR="Blue"]usr[/COLOR]
[COLOR="Blue"]block[/COLOR]    [COLOR="Blue"]Documentation[/COLOR]  [COLOR="Blue"]include[/COLOR]  [COLOR="Blue"]kernel[/COLOR]       [COLOR="Blue"]net[/COLOR]             [COLOR="Blue"]security[/COLOR]  [COLOR="Blue"]virt[/COLOR]
COPYING  [COLOR="Blue"]drivers[/COLOR]        [COLOR="Blue"]init[/COLOR]     [COLOR="Blue"]lib[/COLOR]          README          [COLOR="Blue"]sound[/COLOR]
CREDITS  dropped.txt    [COLOR="Blue"]ipc[/COLOR]      MAINTAINERS  REPORTING-BUGS  [COLOR="Blue"]tools[/COLOR]
[COLOR="Blue"]crypto[/COLOR]   [COLOR="Blue"]firmware[/COLOR]       Kbuild   Makefile     [COLOR="Blue"]samples[/COLOR]         [COLOR="Blue"]ubuntu[/COLOR]

```

Nor is there a 'debian' in any of the subdirectories.  Running "find" doesn't show any files named "rules" either.  :confused:

My own notes are not much better, it being 10 years since I last had to make a custom kernel.

---

### Post by Doug S on 2012-11-03
> **Lars Noodén said:**
> Thanks, Doug. How did you find out which option to add to git to go forward?Hi Lars, I didn't add any option to git. I Think git figured it out based on my answer for the "test this merge point" request above. Note that I didn't list it above but I also tried an answer of```
git bisect bad
```and git replied with a range of commit numbers. I suppose if that avenue needs to be pursued, a new bisection would be started with those good /bad points.
 
On your next posting, "no debian" sub-directory: On my computer, I have the debian sub-directory. I have no clue why I have it and you do not. However, it might be because I got to the next step, and you did not. Even though I did a "git bisect reset" and then the "git bisect start ..." again, maybe the debian directory is left over. 
 
I also tried to compile (before I did the "git bisect reset" stuff), and it errors out right at the start. If I am even able to figure it out, it tends to take me forever at the best of times. However, I can not work on it right now. 
 
I have been compiling the kernel a lot over the last year (mainly from Ubuntu, but also from Kernel.org), but not for a couple of months now. However, when things don't work, I tend to end up in some blackhole of getting lost and frustrated.

---

### Post by Lars Noodén on 2012-11-03
I did "git bisect reset" and, after it ran for about a minute, I got a debian directory where before I had none.  

Taking the next step in the [kernel build instructions](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) gives a mess of errors, again about missing directories:

```

$ fakeroot debian/rules clean
/bin/bash: debian/debian.env: No such file or directory
sed: can't read /changelog: No such file or directory
/bin/bash: debian/debian.env: No such file or directory
sed: can't read /changelog: No such file or directory
/bin/bash: debian/debian.env: No such file or directory
sed: can't read /changelog: No such file or directory
/bin/bash: debian/debian.env: No such file or directory
sed: can't read /changelog: No such file or directory
debian/rules.d/0-common-vars.mk:10: *** first argument to `word' function must be greater than 0.  Stop.

```

and

```

$ fakeroot debian/rules binary-headers binary-generic/bin/bash: debian/debian.env: No such file or directory
sed: can't read /changelog: No such file or directory
/bin/bash: debian/debian.env: No such file or directory
sed: can't read /changelog: No such file or directory
/bin/bash: debian/debian.env: No such file or directory
sed: can't read /changelog: No such file or directory
/bin/bash: debian/debian.env: No such file or directory
sed: can't read /changelog: No such file or directory
debian/rules.d/0-common-vars.mk:10: *** first argument to `word' function must be greater than 0.  Stop.

```

Edit: It builds on another machine even though I have followed the same steps.  Strange.

---

### Post by Lars Noodén on 2012-11-04
git bisect seems not to advance to the next case.  When I enter 'git bisect bad' there is no output.  Shouldn't it say something about the number of revisions and steps left?

```

$ git bisect bad
$ git bisect log
git bisect start
# bad: [6c417a4e4d15e4a77e299f5f41df24211a879dd4] UBUNTU: Ubuntu-2.6.38-16.67
git bisect bad 6c417a4e4d15e4a77e299f5f41df24211a879dd4

```

---

### Post by Lars Noodén on 2012-11-04
The [instructions](https://wiki.ubuntu.com/Kernel/KernelBisection#Start_the_bisection) don't work at all.  The directories debian and debian.master and their contents are needed to build the kernel, but doing a **git bisect start ...** removes them.  **git bisect reset** creates them, but leave me (I think) unable to go forward with the bisect.  How do I really get going with a bisect?

```

[COLOR="Red"]$ time git clone git://kernel.ubuntu.com/ubuntu/ubuntu-natty.git
[/COLOR]Cloning into 'ubuntu-natty'...
remote: Counting objects: 1985139, done.
remote: Compressing objects: 100% (324883/324883), done.
remote: Total 1985139 (delta 1658653), reused 1967904 (delta 1641721)
Receiving objects: 100% (1985139/1985139), 500.91 MiB | 476 KiB/s, done.
Resolving deltas: 100% (1658653/1658653), done.
Checking out files: 100% (36408/36408), done.

real	20m46.517s
user	2m23.980s
sys	0m54.610s


[COLOR="red"]$ cd ubuntu-natty
[/COLOR]

[COLOR="red"]$ time git checkout -b mybisect origin/master
[/COLOR]Branch mybisect set up to track remote branch master from origin.
Switched to a new branch 'mybisect'

real	0m0.288s
user	0m0.190s
sys	0m0.100s


[COLOR="red"]$ git log --oneline Ubuntu-2.6.38-7.39..Ubuntu-2.6.38-8.40  | wc -l
[/COLOR]704


[COLOR="red"]$ git bisect start Ubuntu-2.6.38-8.40 Ubuntu-2.6.38-7.39
[/COLOR]Bisecting: a merge base must be tested
[521cb40b0c44418a4fd36dc633f575813d59a43d] Linux 2.6.38
# no debian or debian.master directory

[COLOR="red"]$ git bisect reset
[/COLOR]
# debian and debian.master directories created


[COLOR="red"]$ git bisect start Ubuntu-2.6.38-8.40 Ubuntu-2.6.38-7.39
[/COLOR]Bisecting: a merge base must be tested
[521cb40b0c44418a4fd36dc633f575813d59a43d] Linux 2.6.38
# now debian and debian.master directories disappear

[COLOR="Red"]$ fakeroot debian/rules clean[/COLOR]
/usr/bin/fakeroot: line 178: debian/rules: No such file or directory


```

---

### Post by Doug S on 2012-11-04
Hi Lars,
I am finding the same as you. I thought, perhaps, this part:> Bisecting: a merge base must be tested
[521cb40b0c44418a4fd36dc633f575813d59a43d] [COLOR=red]Linux 2.6.38[/COLOR]
# no debian or debian.master directory
might mean the raw kernel as from kernel.org before any changes to the Ubuntu way, which is compiled a different way. So, I thought maybe GIT set it up that way. However, I was still unable to compile, I tried two methods. One of those methods actually got about 5 minutes into the compile, which on my i7 computer is typically about 42% of the way.
 
By the way, I time my steps also.
 
My continued interest in this thread and your launchpad bug are because I have never actually manged to get this stuff work. I have had to switch to manually applying patches and backedits and such, which ends up very tedious. I was hoping to learn something.
 
<Begin rant:>Sometimes it seems to be very hard to try to help. It get s so frustrating and if anything goes out of the ordinary, the reference materials don't seem to cover the senario. The hours pile up, with little or no progress made.
<End rant>

---

### Post by Doug S on 2012-11-04
> **Lars Noodén said:**
> git bisect seems not to advance to the next case. When I enter 'git bisect bad' there is no output. Shouldn't it say something about the number of revisions and steps left?
 
```

$ git bisect bad
$ git bisect log
git bisect start
# bad: [6c417a4e4d15e4a77e299f5f41df24211a879dd4] UBUNTU: Ubuntu-2.6.38-16.67
git bisect bad 6c417a4e4d15e4a77e299f5f41df24211a879dd4

```Lars, I get this when I enter "bad" at the first step:```
doug@s15:~/temp-lars/ubuntu-natty$ git bisect reset
Previous HEAD position was 521cb40... Linux 2.6.38
Switched to branch 'mybisect'
doug@s15:~/temp-lars/ubuntu-natty$ git bisect start Ubuntu-2.6.38-8.40 Ubuntu-2.6.38-7.39
Bisecting: a merge base must be tested
[521cb40b0c44418a4fd36dc633f575813d59a43d] Linux 2.6.38
doug@s15:~/temp-lars/ubuntu-natty$ git bisect bad
The merge base 521cb40b0c44418a4fd36dc633f575813d59a43d is bad.
This means the bug has been fixed between 521cb40b0c44418a4fd36dc633f575813d59a43d and [36bb4f292ae74227c1ff4dc8b160781c0d02a0ae].
```I assume in that senario we would start a new bisection with those parameters:```
doug@s15:~/temp-lars/ubuntu-natty$ git bisect reset
Previous HEAD position was 521cb40... Linux 2.6.38
Switched to branch 'mybisect'
doug@s15:~/temp-lars/ubuntu-natty$ git bisect start 521cb40b0c44418a4fd36dc633f575813d59a43d 36bb4f292ae74227c1ff4dc8b160781c0d02a0ae
Some good revs are not ancestor of the bad rev.
git bisect cannot work properly in this case.
Maybe you mistake good and bad revs?

```Oh, that seems to have issues also. I'm lost.

---

### Post by Doug S on 2012-11-04
I continued to try compile, and continue fail. The most recent thing I did was to just check out 521cb40b0c44418a4fd36dc633f575813d59a43d by itself and try to compile that:```
git checkout -b dougbasetest 521cb40b0c44418a4fd36dc633f575813d59a43d
make clean
make oldconfig
... answer a bunch of question, accepting defaults ...
time make -j8 deb-pkg
... which eventually errors out, but doesn't tell me why (annoying).
make[1]: *** [deb-pkg] Error 2
make: *** [deb-pkg] Error 2
real    1m24.808s
user    9m58.337s
sys     0m38.462s
```If instead, I check out, say:```
git checkout -b dougbisect Ubuntu-2.6.38-7.39
```Then I should be able to use the Ubuntu compile instructions, but the compile also failes.
I also followed a git bisection, giving guessed answers just to see where it lead:```
doug@s15:~/temp-lars/ubuntu-natty$ git bisect start Ubuntu-2.6.38-8.40 Ubuntu-2.6.38-7.39
Bisecting: a merge base must be tested
[521cb40b0c44418a4fd36dc633f575813d59a43d] Linux 2.6.38
doug@s15:~/temp-lars/ubuntu-natty$ git bisect [COLOR=red]good[/COLOR]
Bisecting: 351 revisions left to test after this (roughly 9 steps)
[516b498acc786576d4dd4238f7d67812a5c5df86] UBUNTU: SAUCE: hid: ntrig: New ghost-filtering event logic
doug@s15:~/temp-lars/ubuntu-natty$ head -1 debian.master/changelog
linux ([COLOR=red]2.6.37-3.11[/COLOR]) natty; urgency=low
doug@s15:~/temp-lars/ubuntu-natty$ git bisect [COLOR=red]good[/COLOR]
Bisecting: 175 revisions left to test after this (roughly 8 steps)
[5a5f7782e0ab5d5c93bc77179e4b471aa85abd60] UBUNTU: ubuntu: ndiswrapper -- fix interaction between __packed and packed
doug@s15:~/temp-lars/ubuntu-natty$ head -1 debian.master/changelog
linux ([COLOR=red]2.6.37-13.27[/COLOR]) UNRELEASED; urgency=low
doug@s15:~/temp-lars/ubuntu-natty$ git bisect [COLOR=red]good[/COLOR]
Bisecting: 87 revisions left to test after this (roughly 7 steps)
[538b2ab8ca9fca3eb02209cd6ad09724607dab99] UBUNTU: rebase fixes Bug #722689
doug@s15:~/temp-lars/ubuntu-natty$ head -1 debian.master/changelog
linux ([COLOR=red]2.6.38-5.32[/COLOR]) UNRELEASED; urgency=low
doug@s15:~/temp-lars/ubuntu-natty$ git bisect [COLOR=red]good[/COLOR]
Bisecting: 43 revisions left to test after this (roughly 6 steps)
[84a78d3f5a9132a3693cbe80a55b5d4cfa2f4a9d] UBUNTU: Enable common packages for armhf
doug@s15:~/temp-lars/ubuntu-natty$ head -1 debian.master/changelog
linux ([COLOR=red]2.6.38-7.36[/COLOR]) UNRELEASED; urgency=low
doug@s15:~/temp-lars/ubuntu-natty$ git bisect [COLOR=red]good[/COLOR]
Bisecting: 21 revisions left to test after this (roughly 5 steps)
[1018ae2e394feb81b9884178b35132a34944f7ba] UBUNTU: [Config] update configs after v2.6.38.1 rebase
doug@s15:~/temp-lars/ubuntu-natty$ head -1 debian.master/changelog
linux ([COLOR=red]2.6.38-8.40[/COLOR]) UNRELEASED; urgency=low
doug@s15:~/temp-lars/ubuntu-natty$ git bisect [COLOR=red]bad[/COLOR]
Bisecting: 10 revisions left to test after this (roughly 4 steps)
[7778de98450721faff3500a264aa2ccda9eb36cf] UBUNTU: Ubuntu-2.6.38-7.39
doug@s15:~/temp-lars/ubuntu-natty$ head -1 debian.master/changelog
linux ([COLOR=red]2.6.38-7.39[/COLOR]) natty; urgency=low
doug@s15:~/temp-lars/ubuntu-natty$ git bisect [COLOR=red]good[/COLOR]
Bisecting: 5 revisions left to test after this (roughly 3 steps)
[4a051c3c21a7e0276baba305f9ecbc377875a278] (drop after v2.6.38) HID: ntrig: apply NO_INIT_REPORTS quirk
doug@s15:~/temp-lars/ubuntu-natty$ head -1 debian.master/changelog
linux ([COLOR=red]2.6.38-8.40[/COLOR]) UNRELEASED; urgency=low
```I also tried:```
doug@s15:~/temp-lars/ubuntu-natty$ git bisect reset
Previous HEAD position was 4a051c3... (drop after v2.6.38) HID: ntrig: apply NO_INIT_REPORTS quirk
Switched to branch 'mybisect'
doug@s15:~/temp-lars/ubuntu-natty$ git checkout -b dougbisect Ubuntu-2.6.38-7.39
Switched to a new branch 'dougbisect'
doug@s15:~/temp-lars/ubuntu-natty$ git bisect start Ubuntu-2.6.38-8.40 Ubuntu-2.6.38-7.39
Bisecting: a merge base must be tested
[521cb40b0c44418a4fd36dc633f575813d59a43d] Linux 2.6.38
```

---

### Post by Lars Noodén on 2012-11-04
I tried most of today also.  I have a lot of notes but not luck in compiling.  Eventually one of the changes (or something on the partition) went wrong and I could not delete files or remove subdirectories.  I lost a lot of time restoring the partition from backup.  

There is a new comment on the bug report, I will get to that soon.

---

### Post by Doug S on 2012-11-04
I tried the instructions/comment from the problem report. I got nothing:```
doug@s15:~/temp-lars/ubuntu-natty$ git rev-list Ubuntu-2.6.38-8.40 | grep $(git log --pretty=oneline -1 Ubuntu-2.6.38-7.39 | cut -d' ' -f1)
doug@s15:~/temp-lars/ubuntu-natty$

```Leaving the other stuff out of the above command, gives a complete list of commit numbers. Refering to the new link in the problem report and correlating, if we could get compiles to work, I would be tempted to jump directly to these two:```
63e248e086e8a80b7345982d22d83b56d4986532
d139156bc7b509b78e9fb254c16dd2fa8d3d7f82
e6b8d2b77c7cc690015f97c771cbe9b6d1d6ef57
0ad40e118007ff770e2479f5afcdb9103782b4ba
ffaee98cdff45f84d43bd6ca0b016464cfd42984
[COLOR=red]04e8a8adfbebfab3762e494bee98521a01d10ef7[/COLOR]
[COLOR=red]219c03274bb3ec6c74c714996461d6be4f9a8df3[/COLOR]
7c4cec7209ffb6a718e6f15400437c0e2123127a

```Because 04e8a8 is "add touchpad sysfs file".
Lars, you had mentioned in an earlier post that you did have a successful compile. Are you still able to compile on that computer?

---

### Post by Lars Noodén on 2012-11-04
I can still compile on it, but the kernel won't build without debian/rules and 'git bisect start' seems to remove that directory's  contents.  'git bisect reset' seems to create the needed files.  I'm not sure how to resolve that.

---

### Post by Doug S on 2012-11-04
The git bisect start step gives the confused state, that I am pretty sure is a kernel.org kernel, which wouldn't have the ./debian/rules file and needs to be compiled via different methods (not working for me). However, if you just tell it "git bisect good", it will proceed to the next step, and the ./debian/rules file will be there. If that could be made to compile, then contining should be possible. Yes, it is unclear if that is the actual correct direction to proceed, but it wouldn't take long to try the end points (i.e. good, good, good ... from this point only building the last one and bad, bad, bad... from the same point, only building the last one)
 
Edit: As a sanity check I downloaded and compiled 3.2.0-32.51, the current 12.04 kernel. It compiled fine, although it took a few minutes longer than in the past.

---

### Post by Lars Noodén on 2012-11-05
> **Doug S said:**
> ... However, if you just tell it "git bisect good", it will proceed to the next step, and the ./debian/rules file will be there. If that could be made to compile...

That does indeed add the rules and other files, but the actual compilation has a metric buttload of y/n/m queries and then ultimately fails to compile and aborts with an error.

```

make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/home/foo/ubuntu-natty'
make: *** [/home/foo/ubuntu-natty/debian/stamps/stamp-build-generic] Error 2

```

---

### Post by Lars Noodén on 2012-11-05
Grrr.

/home/foo/ubuntu-natty/arch/x86/pci/xen.c:428:1: fatal error: closing dependency file arch/x86/pci/.xen.o.d: No space left on device
compilation terminated.

That's all the space I have on that machine.  The only other partition is a smallish swap partition.

---

### Post by Doug S on 2012-11-05
> **Lars Noodén said:**
> That does indeed add the rules and other files, but the actual compilation has a metric buttload of y/n/m queries and then ultimately fails to compile and aborts with an error.
 
```

make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/home/foo/ubuntu-natty'
make: *** [/home/foo/ubuntu-natty/debian/stamps/stamp-build-generic] Error 2

```I get the same as you. I tried both accepting defaults for the tons of configure questions and answering "no" to all of them. What I do not like with the compile method is that the error exit doesn't really tell us anything about why.

---

