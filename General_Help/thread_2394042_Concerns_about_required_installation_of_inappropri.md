---
title: "Concerns about required installation of inappropriate microcodes"
date: 2018-06-11
forum: General Help
---

### Post by &amp;KyT$0P# on 2018-06-11
The latest kernel update is [requiring installation of both amd64-microcode and intel-microcode]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259").  Both microcode packages are being required even in my VirtualBox VMs.  But according to the description in that bug, VMs **should not** have either microcode package installed.

Because the implementation is not working as intended, I am very concerned about upgrading the kernel on my 18.04 host, which has Intel CPU and already installed intel-microcode.  amd64-microcode is not appropriate for this machine.  I am concerned that a forced installation of amd64-microcode could potentially cause stability issues resulting from the wrong microcode being used.  Is this a fair concern?  Or is there something in the way microcode works that would make that situation impossible, regardless of what microcodes are installed?

Second question, is there a good way to prevent the installation of the microcode packages in my VMs?  I can think of some not-so-good ways, including holding back the kernel packages, but would prefer a proper solution if it exists.

---

### Post by mc4man on 2018-06-11
Do you have any known occurrences of wrong microcodes ever being used?

---

### Post by &amp;KyT$0P# on 2018-06-11
> **mc4man said:**
> Do you have any known occurrences of wrong microcodes ever being used?
No, I just don't know whether installing a wrong microcode package could result in wrong microcode being used.

---

### Post by crip720 on 2018-06-11
I think they ship both microcodes and your computer uses the right one.  This way you can take the hard drive from an intel machine and put it in an amd machine and be happy.

---

### Post by &amp;KyT$0P# on 2018-06-11
> **crip720 said:**
> I think they ship both microcodes and your computer uses the right one.
If more than one microcode package is installed, how does it determine which microcode is the right one?

---

### Post by QIII on 2018-06-12
The kernel is aware of which CPU it is running on.

You may see this by issuing the command

```
cat /proc/cpuinfo
```

If you really want to read it all in chunks, issue

```
cat /proc/cpuinfo | less
```

but there is more in there than you will probably be interested in.

The /proc directory is a virtual directory full of a lot of files that are empty until the instant you make a query, such as the command above.  Invoking that command creates ephemeral content in the cpuinfo file.  Everything your kernel knows about the CPU will get dumped in there.  You will notice that there is a lot of information about your CPU that the kernel is aware of.

---

### Post by &amp;KyT$0P# on 2018-06-12
So to be clear, are you saying that the microcode to be used is determined based on the info I see in [FONT=Courier New]cat /proc/cpuinfo[/FONT] output, and this detailed info prevents muddling of microcodes, regardless of which microcode packages are installed on the system?

---

### Post by mc4man on 2018-06-12
If you run this it'll show  what happened during boot
```
dmesg | grep -i microcode
```
For intel cpu's this shows basically how
```
/usr/sbin/iucode_tool -tb -lS /lib/firmware/intel-ucode/*
```

So no way to load microcode not matching your cpu's sig.

---

### Post by &amp;KyT$0P# on 2018-06-12
Thanks all for the replies!  So I did some searching and learned that CPU signature is derived from the CPU family & model & stepping.  [FONT=Courier New]cat /proc/cpuinfo[/FONT] shows my Intel CPU has family 6, and some more searching indicates AMD CPUs are family 15.  On this basis I figured that no AMD CPU could have a signature matching my Intel CPU's signature, so I went ahead with the kernel update on my bare-metal machine.  And the output from mc4man [FONT=Courier New]dmesg[/FONT] command is identical before & after the installation of amd64-microcode (+ reboot), which means I'm running the same (Intel) microcode as before.  So part 1 of my concerns is resolved. :KS

---

### Post by mc4man on 2018-06-12
Re: 2
Do you have a particular reason to be using linux-image-generic in your vm?

---

### Post by &amp;KyT$0P# on 2018-06-12
> **mc4man said:**
> Re: 2
Do you have a particular reason to be using linux-image-generic in your vm?
Yes and no -

1) It's just what was installed by the Xubuntu 18.04 ISO, and I never had any reason to pay much attention to this until now.

2) Since I use the VM for testing stuff that I may later use on my host, I would like both to run the same kernel, so that they're as close as possible.  But in theory this wouldn't necessarily require the kernel metapackages to be the same, right?

---

### Post by mc4man on 2018-06-12
I've no experience with virtual installs but would expect there are virtual  versions of the various linux meta packages. ( and these wouldn't depend on the microcode packages.

In general the linux metapackages are a convenience for kernel upgrades, not a requirement for using or upgrading.
So for instance here removing either or both the microcode packages would remove 
linux-generic 
linux-image-generic 
linux-signed-generic
Nothing would change other than a future upgrade wouldn't be as easy as simply upgrading the meta packages when available.

I'd guess on your vm you could remove the mc packges, note which meta packages are being removed, then install their virtual counterparts..??

---

### Post by &amp;KyT$0P# on 2018-06-13
> **mc4man said:**
> I'd guess on your vm you could remove the mc packges, note which meta packages are being removed, then install their virtual counterparts..??
```
$ sudo apt-get purge amd64-microcode intel-microcode
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  iucode-tool linux-headers-generic thermald
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  amd64-microcode* intel-microcode* linux-generic* linux-image-generic*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 1,672 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```

So I think I would need to A) mark linux-headers-generic as manually installed, and B) replace linux-image-generic.  Of the kernel metapackages [listed here]("https://packages.ubuntu.com/source/bionic/linux-meta"), none of them are quite what's needed.  linux-image-virtual is close, but it doesn't have a dependency on the latest linux-modules-extra package which is apparently necessary - as a test, removing the linux-modules-extra packages resulted in no audio, and reinstalling it brought audio back.

---

### Post by &amp;KyT$0P# on 2018-06-15
Since I couldn't find a good kernel metapackage for my VirtualBox VM, and no other ideas, I take it there isn't an ideal solution for my VirtualBox VM, so marking this solved.  Thanks again to all who replied :KS

---

