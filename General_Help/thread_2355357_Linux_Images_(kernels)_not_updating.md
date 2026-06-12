---
title: "Linux Images (kernels) not updating"
date: 2017-03-12
forum: General Help
---

### Post by rogertx2 on 2017-03-12
I've been running Ubuntu for a long time; I updated to 16.04.02 last fall... but once I did so, the "Software Updater" is no longer finding/installing new kernel versions.  It is installing the headers, which I'm currently using as my clue to go grab the latest kernel. I searched the forums, but didn't see anything about this, so I'm hoping someone may have some ideas.  I've not run into this problem before.

An example: This morning, I was running kernel version 4.4.0[COLOR=#ff0000]-66[/COLOR] -- the Software Update popped up with several updates, including the headers for 4.4.0[COLOR=#ff0000]-71[/COLOR], but NOT the actual linux-image-generic-4.4.0-71. I'm having to manually run the update command to get these updates.

---

### Post by DuckHook on 2017-03-12
Please post output from the following:```
cat /etc/apt/sources.list
``````
dpkg --get-selections | grep linux
```…and please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by rogertx2 on 2017-03-12
I haven't (to my knowledge) touched the sources.list, but here it is (cut off commented-out lines at end of file):

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

```


Output of dpkg --get-selections | grep linux:

```

console-setup-linux                install
libselinux1:amd64                install
libselinux1:i386                install
linux-base                    install
linux-firmware                    install
linux-headers-4.4.0-65                install
linux-headers-4.4.0-65-generic            install
linux-headers-4.4.0-66                install
linux-headers-4.4.0-66-generic            install
linux-headers-generic                install
linux-image-4.4.0-65-generic            install
linux-image-4.4.0-66-generic            install
linux-image-extra-4.4.0-65-generic        install
linux-image-extra-4.4.0-66-generic        install
linux-libc-dev:amd64                install
linux-signed-image-3.13.0-100-generic        deinstall
linux-signed-image-4.4.0-47-generic        deinstall
linux-signed-image-4.4.0-51-generic        deinstall
linux-sound-base                install
pptp-linux                    install
syslinux                    install
syslinux-common                    install
syslinux-legacy                    install
util-linux                    install

```

---

### Post by DuckHook on 2017-03-12
Please do:```
sudo apt install linux-image-generic
```…then reboot, then```
sudo apt update && sudo apt full-upgrade && sudo apt autoremove && sudo apt clean
```

---

### Post by ajgreeny on 2017-03-12
I don't think 16.04.02 was released last fall, depending on where you are in the world, but it looks as if you are in USA? It was released in mid January 2017.

Are you sure it was not the 16.04.1 point version you installed rather than 16.04.2?
That would explain why you are still using the 4.4.0-66 kernel which is the original kernel series for xenial which is still supported and will continue t6o be so for the full life of xenial support.

Is there a really good reason or need for the upgrade of your kernel version, eg to get better wifi support, or are you just wanting to have the latest  version of everything including the kernel? If you really do want to move to the later kernel version you can see all the info and commands to use [here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").

---

### Post by DuckHook on 2017-03-12
+1 to ajgreeny's observations.

@rogertx2

If you want to install 16.04.2, then follow the instructions that ajgreeny links to. However, in my opinion, that would be putting the cart in front of the horse. First things first. Your system is not installing new kernels that match your *linux-headers-generic* for the simple reason that *linux-image-generic* is not installed. If you want these, then follow my instructions in post #4 above. In my opinion, get that working first. You can install the HWE stack that takes you to the 4.8 kernel afterwards and only after enough research to see if you really need it.

It bears noting that a few people have reported breakage after installing the HWE stack. Not many&#8212;I don't want to be alarmist&#8212;but a few. If your system is stable on 4.4, then ajgreeny's advice (sticking with 4.4) is something you should seriously consider.

---

### Post by Bucky Ball on 2017-03-12
```
sudo apt update
sudo apt full-upgrade
```

... will get you to 16.04.2 :)

---

### Post by ajgreeny on 2017-03-14
> **Bucky Ball said:**
> ```
sudo apt update
sudo apt full-upgrade
```

... will get you to 16.04.2 :)
However, it will still not pull in the 4.8.0-xx kernel series which was the reason for rogertx2's original query; for that you have to use the HWE upgrade commands shown in the link I provided or install from the 16.04.2 iso image.

Command **lsb_release -a** on my system shows 16.04.2 as it should if fully updated, even though I have not updated the HWE enablement and am still using the 4.4 kernel.
The kernel version is independent of the OS version shown by that command, and vice-versa; only by updating the HWE or by installing a new iso of the 16.04.2 point version will you get the 4.8 kernel series.

---

### Post by rogertx2 on 2017-04-02
> **DuckHook said:**
> Please do:```
sudo apt install linux-image-generic
```…then reboot, then```
sudo apt update && sudo apt full-upgrade && sudo apt autoremove && sudo apt clean
```

I did the first one, and once again, if found that the kernel was out of date, and updated from -65 to -71

> **ajgreeny said:**
> I don't think 16.04.02 was released last fall, depending on where you are in the world, but it looks as if you are in USA? It was released in mid January 2017.

Are you sure it was not the 16.04.1 point version you installed rather than 16.04.2?
That would explain why you are still using the 4.4.0-66 kernel which is the original kernel series for xenial which is still supported and will continue t6o be so for the full life of xenial support.

Is there a really good reason or need for the upgrade of your kernel version, eg to get better wifi support, or are you just wanting to have the latest  version of everything including the kernel? If you really do want to move to the later kernel version you can see all the info and commands to use [here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").

I'm in the USA; the /etc/issue shows I'm running 16.04.2 LTS. I know that it took me a while to go to 16.04, because the earlier releases had some issue with my NFS mounts. I'm not exactly sure when I updated to 16.04.

I'm used to security patches that change the final -nn number, and I normally update as they come out.  My irritation is that now the updates install the header files for the new kernel, but not the kernel itself.  Getting the image manually via the sudo apt-get install linux-image works, but the Updated GUI has always worked fine in the past.

To repeat: Earlier today, I did an update via the Graphical Updater, and it updated the header files to -71, but the kernel itself stayed at -66; once I manually ran the "sudo apt-get install linux-image", it updated to -71.

> **DuckHook said:**
> +1 to ajgreeny's observations.

@rogertx2

If you want to install 16.04.2, then follow the instructions that ajgreeny links to. However, in my opinion, that would be putting the cart in front of the horse. First things first. Your system is not installing new kernels that match your *linux-headers-generic* for the simple reason that *linux-image-generic* is not installed. If you want these, then follow my instructions in post #4 above. In my opinion, get that working first. You can install the HWE stack that takes you to the 4.8 kernel afterwards and only after enough research to see if you really need it.

It bears noting that a few people have reported breakage after installing the HWE stack. Not many—I don't want to be alarmist—but a few. If your system is stable on 4.4, then ajgreeny's advice (sticking with 4.4) is something you should seriously consider.

I'm NOT trying to do an kind of major upgrade; I'm talking about (for the most part) the security patches that increment the -nn number; for example, this morning, I was running kernel 4.4.0-[COLOR=#ff0000]66[/COLOR]-generic; the GUI updater indicated several updates, including linux-headers-4.4.0-71 (and linux-headers-4.4.0-71-generic), but it did **NOT** list (or install, naturally) "linux-image-4.4.0-71" & "linux-image-extra-4.4.0-71-generic" until I had manually ran the "sudo apt-get install linux-image-generic"

I'm just trying to figure out why the updater tool refuses to update the kernel

> **ajgreeny said:**
> However, it will still not pull in the 4.8.0-xx kernel series which was the reason for rogertx2's original query; for that you have to use the HWE upgrade commands shown in the link I provided or install from the 16.04.2 iso image.

Command **lsb_release -a** on my system shows 16.04.2 as it should if fully updated, even though I have not updated the HWE enablement and am still using the 4.4 kernel.
The kernel version is independent of the OS version shown by that command, and vice-versa; only by updating the HWE or by installing a new iso of the 16.04.2 point version will you get the 4.8 kernel series.

No, that wasn't my original query - see other posts; I apologize for being unclear.  Since I've been on the 16.04 LTS version (not sure if I started with 16.04.2 or 16.04.1, but /etc/issue says I have 16.04.2), the minor kernel updates don't show up in the software updater.

---

### Post by rogertx2 on 2017-04-02
> **DuckHook said:**
> +1 to ajgreeny's observations.

@rogertx2

First things first. Your system is not installing new kernels that match your *linux-headers-generic* for the simple reason that *linux-image-generic* is not installed. If you want these, then follow my instructions in post #4 above. In my opinion, get that working first.


This may well be it -- I didn't notice that linux-image-generic was missing. It is present now, and well see when the next set of patches come out.


> 
You can install the HWE stack that takes you to the 4.8 kernel afterwards and only after enough research to see if you really need it.

It bears noting that a few people have reported breakage after installing the HWE stack. Not many—I don't want to be alarmist—but a few. If your system is stable on 4.4, then ajgreeny's advice (sticking with 4.4) is something you should seriously consider.

I'm happy with 4.4; I have no particular need to upgrade; I stick with the LTS versions and test new ones in a virtual environment before I put them on my "important" machine.  Thanks! I don't know how the linux-image-generic managed to go missing.

---

