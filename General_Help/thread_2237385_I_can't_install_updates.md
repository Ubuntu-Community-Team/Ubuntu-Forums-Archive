---
title: "I can't install updates"
date: 2014-08-01
forum: General Help
---

### Post by viriatovigo on 2014-08-01
I don't understand...
 

 As can be seen in the attached screenshots, I can't install the updates since 3 months ago because it says that there are not enough boot memory (What the hell is that?) but I have my HDD practically empty.
 

 If I open Properties I can see that there are more than enough memory in my HDD as can be seen in the attached screenshot.
 

 This trouble “thing” of boot memory and HDD memory only happens in Linux, not in AppleMac.
 

 Precisely I have nothing in my Linux PC because is impossible make business with it as I said many times before and why, then I have nothing to delete, move to other mysterious folder or compress. So... What the hell it wants me to delete or to move? I don't get it...
 

 Still I believe that Linux is the safest, faster and with more technical free ad-ons OS but very, very, very customer unfriendly, so I am keeping it with the hope that one day Linux would be as easy to use as AppleMac.
 

 Every time that I get a notification of updates, this is what happens and in the order of the attached  screenshots.
 

 Of course, because they couldn't be installed, any time that I do open it says that there are updates to install, but if I try to install them the full sequence stated above do happens again and again.
 

 Please advice, if possible without writing the history of my life in the terminal. Thank you.

---

### Post by mikewhatever on 2014-08-01
tl:dr
You probably need to remove some old kernels to free disk space of the boot partition. 
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by viriatovigo on 2014-08-01
Ta mikewhatever

The chap in the link says that "I know I can manually search through the installed packages and remove them.", but I am afraid that I am too thick and I don' know how to do it.

I would join his question: "Does Ubuntu provide any easier way to clean them up or keep them from showing in the boot list?".

---

### Post by coffeecat on 2014-08-01
There are several ways of removing old kernels, but perhaps the easiest is to download, install and run Ubuntu-Tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

When you run it, use the Janitor tab and then tick the old kernel box. It will list old kernel packages that can be uninstalled.

But before you do that, please satisfy my curiosity. Almost every day someone is posting a thread with the same problem as you, a full boot partition. There is no need for a separate boot partition for 99% of home installations. In fact a separate boot partition is likely to cause exactly the problem you are describing. I have no idea why people are installing Ubuntu with a separate boot partition. Please enlighten me.

---

### Post by Impavidus on 2014-08-01
If you tell it to autoremove some packages, does it remove something? You can do it in the gui (difficult to explain) or terminal:```
sudo apt-get --purge autoremove
```Else show us the output of this terminal command, so that we can tell you exactly how to remove some old kernels:```
dpkg --list linux-image* linux-headers*
```To be sure which kernel you're running now, also show the output of```
uname -a
```It can all be done in the GUI, but that's hard to explain in text.

---

### Post by ian-weisser on 2014-08-01
> **viriatovigo said:**
> I would join his question: "Does Ubuntu provide any easier way to clean them up or keep them from showing in the boot list?".

Filled /boot partitions are due to several known bugs, not lack of cleanup tools.
Most of those bugs were fixed in 13.10, and the rest are fixed in 14.04, *but* the system has no way to identify old kernels that were not autoremoved due to the bug(s) before they were fixed.

Nor does the system have any way to autoremove kernels that were installed manually, nor kernels that were installed due to...unwise user decisions.

Generally, as more and more users upgrade or reinstall their systems for other reasons, the number of filled /boot incidents should be declining. I see fewer "filled /boot error" threads (like this one) cropping up in this forum.

---

### Post by ajgreeny on 2014-08-01
> **ian-weisser said:**
> Filled /boot partitions are due to several known bugs, not lack of cleanup tools.
Most of those bugs were fixed in 13.10, and the rest are fixed in 14.04, *but* the system has no way to identify old kernels that were not autoremoved due to the bug(s) before they were fixed.

Nor does the system have any way to autoremove kernels that were installed manually, nor kernels that were installed due to...unwise user decisions.

Generally, as more and more users upgrade or reinstall their systems for other reasons, the number of filled /boot incidents should be declining. I see fewer "filled /boot error" threads (like this one) cropping up in this forum.
Agreed, but that still does not answer coffeecat's question of why so many desktop users seem to be installing with a separate /boot partition; it is simply not needed and is the main reason for this lack of space problem appearing.

---

### Post by ian-weisser on 2014-08-01
I wasn't trying to answer coffeecat's question. I'd love to know *that* answer.

---

### Post by mikewhatever on 2014-08-02
> **viriatovigo said:**
> Ta mikewhatever

The chap in the link says that "I know I can manually search through the installed packages and remove them.", but I am afraid that I am too thick and I don' know how to do it.

I would join his question: "Does Ubuntu provide any easier way to clean them up or keep them from showing in the boot list?".
There are other ways... I don't have a separate boot partition, but still use the following script to get rid of old kernels and headers:
<dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | \
cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | \
xargs sudo apt-get -y purge>


> **coffeecat said:**
> There are several ways of removing old kernels, but perhaps the easiest is to download, install and run Ubuntu-Tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

When you run it, use the Janitor tab and then tick the old kernel box. It will list old kernel packages that can be uninstalled.

But before you do that, please satisfy my curiosity. Almost every day someone is posting a thread with the same problem as you, a full boot partition. There is no need for a separate boot partition for 99% of home installations. In fact a separate boot partition is likely to cause exactly the problem you are describing. I have no idea why people are installing Ubuntu with a separate boot partition. Please enlighten me.
Looks like the installer is too easy, not enough to do, so people get bored.

---

### Post by viriatovigo on 2014-08-02
Ta Coffecat, Impavidus, ian-weisser, ajgreeny and mikewhatever.

Sorry but I am not being rude, ust that , as I said, I am workig from home using the MacBook Pro and in summer seem that everybody is in a hurry.

I will try all your advises and I will be cack to you with the results.

Thank you for your attention. Talk to you soon.

---

### Post by viriatovigo on 2014-08-02
Coffecat: The link that you did provide leads to the download of an application that is for Ubuntu 13.10 and before and I have 14.04.

mikewhatever: The result of running your script is as follows:
                        vigo@vigo-X50V3:~$ <dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | \cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | \xargs sudo apt-get -y purge> 
 bash: syntax error near unexpected token `newline' 
 vigo@vigo-X50V3:~$  
  
Impavidus: I did run your first script and still says that my boot memory is "0". Then I did run the other scripts with the following results.

                        The ressut of dpkg --list linux-image* linux-headers* is:
 

 vigo@vigo-X50V3:~$ dpkg --list linux-image* linux-headers* 
 Desired=Unknown/Install/Remove/Purge/Hold 
 | Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend 
 |/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
 ||/ Name           Version      Architecture Description 
 +++-==============-============-============-================================= 
 un  linux-headers  <none>       <none>       (no description available) 
 un  linux-headers- <none>       <none>       (no description available) 
 un  linux-headers- <none>       <none>       (no description available) 
 un  linux-headers- <none>       <none>       (no description available) 
 un  linux-headers- <none>       <none>       (no description available) 
 un  linux-headers- <none>       <none>       (no description available) 
 ii  linux-headers- 3.13.0-27.50 all          Header files related to Linux ker 
 ii  linux-headers- 3.13.0-27.50 amd64        Linux kernel headers for version  
 ii  linux-headers- 3.13.0-29.53 all          Header files related to Linux ker 
 ii  linux-headers- 3.13.0-29.53 amd64        Linux kernel headers for version  
 ii  linux-headers- 3.13.0-30.55 all          Header files related to Linux ker 
 ii  linux-headers- 3.13.0-30.55 amd64        Linux kernel headers for version  
 ii  linux-headers- 3.13.0-32.57 all          Header files related to Linux ker 
 ii  linux-headers- 3.13.0-32.57 amd64        Linux kernel headers for version  
 ii  linux-headers- 3.13.0.32.38 amd64        Generic Linux kernel headers 
 un  linux-image    <none>       <none>       (no description available) 
 un  linux-image-3. <none>       <none>       (no description available) 
 rc  linux-image-3. 3.11.0-12.19 amd64        Linux kernel image for version 3. 
 rc  linux-image-3. 3.11.0-17.31 amd64        Linux kernel image for version 3. 
 rc  linux-image-3. 3.11.0-18.32 amd64        Linux kernel image for version 3. 
 ii  linux-image-3. 3.11.0-19.33 amd64        Linux kernel image for version 3. 
 ii  linux-image-3. 3.13.0-27.50 amd64        Linux kernel image for version 3. 
 ii  linux-image-3. 3.13.0-29.53 amd64        Linux kernel image for version 3. 
 ii  linux-image-3. 3.13.0-30.55 amd64        Linux kernel image for version 3. 
 ii  linux-image-3. 3.13.0-32.57 amd64        Linux kernel image for version 3. 
 rc  linux-image-ex 3.11.0-12.19 amd64        Linux kernel extra modules for ve 
 rc  linux-image-ex 3.11.0-17.31 amd64        Linux kernel extra modules for ve 
 rc  linux-image-ex 3.11.0-18.32 amd64        Linux kernel extra modules for ve 
 ii  linux-image-ex 3.11.0-19.33 amd64        Linux kernel extra modules for ve 
 ii  linux-image-ex 3.13.0-27.50 amd64        Linux kernel extra modules for ve 
 ii  linux-image-ex 3.13.0-29.53 amd64        Linux kernel extra modules for ve 
 ii  linux-image-ex 3.13.0-30.55 amd64        Linux kernel extra modules for ve 
 ii  linux-image-ex 3.13.0-32.57 amd64        Linux kernel extra modules for ve 
 ii  linux-image-ge 3.13.0.32.38 amd64        Generic Linux kernel image 
 

 And the result of uname -a is:
 

 vigo@vigo-X50V3:~$ uname -a 
 Linux vigo-X50V3 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux 
 vigo@vigo-X50V3:~$

---

### Post by coffeecat on 2014-08-02
> **viriatovigo said:**
> Coffecat: The link that you did provide leads to the download of an application that is for Ubuntu 13.10 and before and I have 14.04.

No, it doesn't. Click on the download now button and you get the 0.8.7 version for Trusty/14.04. I did that yesterday and installed the downloaded deb - it works just fine in 14.04. I think you are being misled by the "* For Ubuntu 13.10 and before: old versions" link below the button. It is not very well phrased and simply leads you to downloads for earlier versions of Ubuntu Tweak.

13.10 is past end-of-life now anyway, so I'm not surprised Ubuntu Tweak is not offering a version for 13.10 on their front page.

---

### Post by 3rdalbum on 2014-08-02
Before reading this post, please keep in mind that I'm not angry at you and this isn't a rant. This is just some friendly comment.

This seems to be one of my favourite phrases at the moment:

"Linux is only difficult if you make it difficult".

You created an unnecessary partition for /boot, didn't know how to keep it clean and ran into problems, and then complained that Linux is difficult to use. Actually, if you let the Ubuntu installer make its own partitions automatically (the easy way), you wouldn't have this problem. The real cause of the problem was when you decided to do things a difficult way, as though you were a power user who knew what they were doing. You don't know what you are doing - some day you will, but today is not that day.

Another thing I see... some new users download the Nvidia graphics driver from the Nvidia site, try to install it in the terminal and then complain that it's giving them error messages and "Linux is too hard". Once again, it's only hard if you make it hard! Ubuntu can download and install the driver for you with just a couple of mouse clicks. No need for the terminal.

NASA's first manned mission lasted only 15 minutes. Michael Schumacher's first driving lesson wasn't in an F1 car. The first thing I ever cooked was baked beans, not Veal Cordon Bleu.

It's tragic when the person gets bad advice or outdated advice ("You need to remove Pulseaudio" instead of "Have you checked that the headphones aren't muted in Sound Settings?") and we all need to make sure our knowledge is current or else do not reply.

Once again, this isn't a rant at you, just a friendly comment. If you decide to reinstall Ubuntu, which may be the easiest option for you to stop this problem reoccurring, please remember that you are new to Ubuntu, and if things seem difficult then there's probably an easier way.

---

### Post by viriatovigo on 2014-08-02
Ta 3rdlbum.

It doesn't look to me lile a runt... Is just your honest opinion. Thank you.

Nop! I didn't any partition because I don't know how t do it. This problem did arise one month ago from the blue, without me doing anything especial.

Another member said in this Forum that I should not have the need to write in the terminal but in some rare cases, but the real thing is that any time that I ask for hell I need to write such amount of scripts (that I don't know were they are coming from) that look like to write again the War & Peace book.

In business things must done yesterday because if I can't someone else can, and in Europe the competence in my field of business is very, very, very tough, so I can't tell a custome "sorry, you need to hold for several minutes until I resolve a problem in Linux" because then the best thing that I can do is to close down the business.

I have not that problem with Apple Mac, where all is very fast just with a click, and to navegate among open applications and documents is as easy as with Linux since it has also a kind of screen split.

Thank you for your comments, I do appreciate.

---

### Post by viriatovigo on 2014-08-02
Ta Coffecat.

I did download and did install the application. Now... Where to click to clean the boot memory? Funny... the application says that my system is up to date...??????? But if any time that I try to update hapens what says in the screeshots that I did post!!!!!!!! Every second I understand less...

---

### Post by coffeecat on 2014-08-02
> **viriatovigo said:**
> Nop! I didn't any partition because I don't know how t do it.

Someone or something must have created a separate boot partition. If it wasn't you, what did? I am not aware of a situation where the Ubuntu installer creates a separate boot partition unless the user selects "something else" and sets one up. Because this is such a regular problem on this forum - a spurious boot partition where one is not needed - it would be very helpful if you would give us further information so that we can get to the bottom of this.

How did you install Ubuntu? Did you follow a howto that you found on the internet?

Just so that we can be sure that you do indeed have a separate boot partition - the 4th screenshot in your first post certainly suggests this - please post the output of the following terminal command:

```
mount
```

Sorry to ask you to run a terminal command, but it is the quickest and easiest way to get the information needed. You can right-click the output with your mouse -> copy and then paste it into your post.

If you followed a howto on official Ubuntu documentation that includes setting up a boot partition (I found one such yesterday) then we as the forum community need to look into this.

If the installer does indeed set up a boot partition in certain cases without you running the advanced "something else" option, then I would consider that a serious bug which we as the forum community need to bring to the attention of the developers.

Your assistance with whatever information you can provide would be appreciated.

---

### Post by coffeecat on 2014-08-02
> **viriatovigo said:**
> Ta Coffecat.

I did download and did install the application. Now... Where to click to clean the boot memory? Funny... the application says that my system is up to date...??????? But if any time that I try to update hapens what says in the screeshots that I did post!!!!!!!! Every second I understand less...

Did you read my post #4?

---

### Post by Impavidus on 2014-08-02
Part of the output is missing (your terminal wasn't wide enough), so I'm guessing some of the package names here, but I think this should solve your problem:```
sudo dpkg --purge linux-image-3.11.0-12-generic \
linux-image-3.11.0-17-generic \
linux-image-3.11.0-18-generic \
linux-image-3.11.0-19-generic \
linux-image-3.13.0-27-generic \
linux-image-3.13.0-29-generic \
linux-image-extra-3.11.0-12-generic \
linux-image-extra-3.11.0-17-generic \
linux-image-extra-3.11.0-18-generic \
linux-image-extra-3.11.0-19-generic \
linux-image-extra-3.13.0-27-generic \
linux-image-extra-3.13.0-29-generic \
linux-headers-3.13.0-27 \
linux-headers-3.13.0-29 \
linux-headers-3.13.0-27-generic \
linux-headers-3.13.0-29-generic
```Copy and paste in your terminal. This should remove old kernel images, remaining configuration and also old headers, which are not on /boot, but you won't need them. Several cleaning tools can do the same, but I always do it manually.

A /boot partition is automatically created when the user wants LVM or full disk encryption. Most people shouldn't need those, but many think it sounds interesting and check the box.

Aah! In the time I carefully prepare my post three more are posted.

---

### Post by coffeecat on 2014-08-02
> **Impavidus said:**
> A /boot partition is automatically created when the user wants LVM or full disk encryption. Most people shouldn't need those, but many think it sounds interesting and check the box.

Thanks, Impavidus. It was in the back of my mind, but I couldn't recall when I posted. I don't know whether it's worth raising a fuss in LP about this asking for some sort of health warning, but it would be interesting to hear what viriatovigo did.

---

### Post by viriatovigo on 2014-08-02
Coffecat.
 

 I did install it from the disc bought from Canonical, and I can't remember now what I did at that time.
 

 In the Lenovo I did install it from the net and I can't remember now what I did because all this things were done last year and 2 years ago. In the Lenovo 2 years ago sharing the PC with windows 8.1 -that comes with the Lenovo- but is not working properly at all and I blame the Lenovo since the Lenovo is giving me a lot of trouble in a lot of things so I using it only to teach job seekers to use a PC.  
 

 In the Shuttle X50V I did install it, as I said, with the CD bought from Canonical 1 year ago and, so far, was working without problems until one month ago.
 

 Certainly, as I said in my answer to 3rdalbum, I have not a clue about how to make a partition.
 

 The outcome of your script is as follows:
 

 vigo@vigo-X50V3:~$ mount 
 /dev/mapper/ubuntu--vg-root on / type ext4 (rw,errors=remount-ro) 
 proc on /proc type proc (rw,noexec,nosuid,nodev) 
 sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
 none on /sys/fs/cgroup type tmpfs (rw) 
 none on /sys/fs/fuse/connections type fusectl (rw) 
 none on /sys/kernel/debug type debugfs (rw) 
 none on /sys/kernel/security type securityfs (rw) 
 udev on /dev type devtmpfs (rw,mode=0755) 
 devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
 tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
 none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
 none on /run/shm type tmpfs (rw,nosuid,nodev) 
 none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) 
 none on /sys/fs/pstore type pstore (rw) 
 /dev/sda1 on /boot type ext2 (rw) 
 systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd) 
 gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=vigo)

---

### Post by viriatovigo on 2014-08-02
coffecat

I found out how to use the Ubuntu Tweak and it took a while to clean but in the end said "Cool, your system is clean!".

Thank you.

---

### Post by viriatovigo on 2014-08-02
Thank you to every one for your help. All the best.

---

