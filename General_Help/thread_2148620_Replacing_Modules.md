---
title: "Replacing Modules"
date: 2013-05-26
forum: General Help
---

### Post by lemonoid on 2013-05-26
Okay so I've had the problem for about a week. Long story short, I thought I was deleting some files out of my own /lib folder for building Android kernels, and I deleted my modules. I've looked around and gotten many different answers. Since I can't plug up my external where I backed them up to, and can't connect to the internet, my best way I've determined is to download them through a live session and either back them up somehow on the filesystem, or chroot into my current filesystem and install them that way. 
    Can anyone provide some guidance here? Which do you think is the best route, and could you possibly elaborate on how to perform the method that you believe is best. I've never had to chroot before, I'm sure I can find a guide but I figured I'd ask for any elaboration in case this could turn out to be a very easy process. Thank you.

---

### Post by lemonoid on 2013-05-26
Okay so I found my best guide so far to re-installing modules, or at least the most in-depth, which shows you how to mount your correct filesystem, and then chroot into it. However, it is saying to mount proc and sys, however, my modules are missing from /lib, so shouldn't I mount lib to reinstall my modules, or is moutning proc and sys for the sake of being able to apt-get install? If anyone could help me out with this question about what I need to mount I'm pretty sure I can get it from here. through ftp.kernel.org I found the package I need, I believe its the 3.2.41-generic-pae file. I'm not positive though. It says to use sudo apt-get install "linux headers package name" which I believe is "linux kernel headers 3.2.41-generic-pae". I don't want to try this other way and it be wrong and I mess up something else in my system.

---

### Post by lemonoid on 2013-05-26
this is an edited post.
I figured out how to chroot in, which was just the simply sudo chroot /mnt command I thought it was, and then mount proc and sys, and now all i need to do is download and install what I'm missing. I tried 'sudo apt-get install linux kernel headers 3.2.41-generic-pae', 'sudo apt-get install linux kernel headers 3.2.41', and sudo apt-get install linux-kernel-headers-3.2.41-generic-pae (and without the -generic-pae). So ALL I need is help figuring out what I need to download. I actually have the linux 3.2.41 downloaded on an external HDD, would it be easier to just use that to re-install the kernel? Or is there just a package to download that will install the modules back where they belong? Thank you very much. I haven't gotten any responses yet, I've tried to keep all this as simple as possible. I'm where I need to be, chroot'ed into my current Ubuntu filesystem where I'm missing /lib/modules, and all I need to do is replace those modules. If anyone can please respond and help me figure out how to do this now that I'm chroot'd and I have internet access, and USB access etc, it would really help me. Thank you so much in advance.

---

### Post by cariboo on 2013-05-26
> **lemonoid said:**
> also, I figured I'd just do the steps provided anyways, and for mounting and going into chroot, prior to going in and mounting proc & sys. it provided this command:
sudo mount --bind /dev/ /mnt/dev sudo chroot /mnt 

and this does not work. it returns me to the command line with help for mount command. can anyone tell me what is wrong with this command

You're missing a few commands. What works for me is the following:

```
sudo mount /dev/sdXx /mnt
sudo mount -o bind /sys /mnt
sudo mount -o bind /dev /mnt
sudo mount -o bind /proc /mnt
sudo chroot /mnt
```

Where /dev/sdXx is the partition you want to chroot

if you need network access use the following command before running the chroot command:

```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```

---

### Post by lemonoid on 2013-05-26
> **cariboo907 said:**
> You're missing a few commands. What works for me is the following:

```
sudo mount /dev/sdXx /mnt
sudo mount -o bind /sys /mnt
sudo mount -o bind /dev /mnt
sudo mount -o bind /proc /mnt
sudo chroot /mnt
```

Where /dev/sdXx is the partition you want to chroot

if you need network access use the following command before running the chroot command:

```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```

I used
sudo mount -t proc none /proc
and mounted that, sys, and dev/pts. So those are mounted I believe because I got returned to the command line as if I successfully mounted each,  now I just need to figure out what to download and install to replace my modules where they belong (/lib/modules) thanks for your response

---

### Post by lemonoid on 2013-05-26
> **cariboo907 said:**
> You're missing a few commands. What works for me is the following:

```
sudo mount /dev/sdXx /mnt
sudo mount -o bind /sys /mnt
sudo mount -o bind /dev /mnt
sudo mount -o bind /proc /mnt
sudo chroot /mnt
```

Where /dev/sdXx is the partition you want to chroot

if you need network access use the following command before running the chroot command:

```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```

I used
sudo mount -t proc none /proc
and mounted that, sys, and dev/pts. So those are mounted I believe because I got returned to the command line as if I successfully mounted each,  now I just need to figure out which headers to install. sudo apt-get install linux-headers brought up a whole list of different headers, and I know its 3.2.0-41 but there are a list such as 3.2.0-41.3 3.2.0-41.6 etc, does it matter which one of these I install as long as its 3.2.0-41.x ?

---

### Post by lemonoid on 2013-05-26
actually I tried one of them, linux-headers-3.2.0-41.66 and it said that it was already the newest version and wouldn't install it, so I don't think that it's the headers that I need to install, unless that WILL work, which would mean I need to uninstall the headers and reinstall them correct? but really wouldn't that just make everything stop functioning? I don't know that's why I'm asking.


UPDATE: So I hooked up my external HDD and found the entire 3.2.0-40-generic-pae that I had removed out of /lib/modules in the first place. I copied it into the home folder of my live session. However, in the terminal, I'm chroot'd into my old filesystem, and don't know how to copy from the live system to my filesystem, is there ANY way to copy these modules back into the /lib/modules folder?

---

### Post by lemonoid on 2013-05-27
anyone? please? all i need to know is what package to download and install to replace my modules, or if there's a way I can copy the modules I have on my external (the ones i deleted in the first place), to my chroot'd filesystem

---

