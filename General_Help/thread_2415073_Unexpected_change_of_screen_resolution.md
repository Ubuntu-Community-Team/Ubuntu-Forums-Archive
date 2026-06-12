---
title: "Unexpected change of screen resolution"
date: 2019-03-19
forum: General Help
---

### Post by jayhawker2 on 2019-03-19
Please, I have an old version of Ubuntu which I don't remember, say around ten years ago. I'm just a user with no great Linux technical knowledge. Reason the version is so much old is the computer wouldn't be suitable for any upgrade any longer. Some day, it opened with a  resolution say 300 x 200 or the like. Things in the screen are so big that I don't know how to open the resolution window in order to get back to a more common screen size. The desktop only offers a very little portion and it's quite impossible to find anything. Sliding bars up and down the screen (remember it is an old version) are so big too that it is not possible to open any scroll down satisfactorily. 

In the up bar, on the left, it appears an Ubuntu symbol. When clicking it, it appears a scroll down with accessories, system tools, graphics and so on. When clicking on System tools, expecting to find "Monitors", it only appears "Bacula Administration Tool, Bacula Monitor and Dolphin (two first to my astonishing surprise: never saw them before, at least in a conscious manner) where it is supposed to find far more possibilities, as "monitors" and the like. 

Please, any idea in order to solve this very annoying, irritating circumstance?

Thank You very much.

---

### Post by QIII on 2019-03-19
Hello!

Without a release number and some information about your computer specs, it would be impossible for us to help you any further than this:

If you are running a 10 year old release of Ubuntu, then it is certainly past its End Of Life, it is receiving no updates of any kind -- including security, and it is unsafe to have it connected to the internet.  Thus, any support we were to provide would be irresponsible because it would allow you to continue to be vulnerable.

My suggestion is that you let us know your computer specs and we see if a current release of one of the official Ubuntu Flavors will run comfortably on your hardware.

---

### Post by jayhawker2 on 2019-03-19
Thanks for your concern. If you can say me how to get this information I'll be very grateful. It is so difficult to get to the system information that I feel quite unable to know the computer specs. I only remember it has a 80 gigabytes Hard Disk, which gives a notion how old is this computer, but it is still useful to me... so far. Thanks

---

### Post by Impavidus on 2019-03-20
Can you get to the console? Try hitting [s]ctrl+shift+F2[/s]ctrl+alt+F2 ([s]ctrl+shift+F7[/s]ctrl+alt+F7 to get back to the gui) and login using your username and password. Or boot using recovery mode from the grub menu and drop to a root shell. Then try a few commands for more information:```
lsb_release -a
free -m
sudo lshw -sanitize -c cpu
sudo lshw -sanitize -c display
```
If using the root shell, you can skip the sudo part of the final two commands.

---

### Post by jayhawker2 on 2019-03-20
Thank you for your concern and help. I'm afraid I am not very familiar with Linux tech vocabulary. When you say "console", must I infer it is the keyboard? On the other hand, when must I to type Ctrl+shift+F2? When into the giant desktop or before entering it? Besides, how I get the "recovery mode from the grub menu"? As a matter of fact, what&#8217;s the grub menu and how I get it? Thanks again. Very grateful.

---

### Post by Impavidus on 2019-03-20
If you graphical user interface is not usable, try the command line interface. That's what I mean by console. At any time after bootup, you can hit ctrl+alt+F2 to get to the command line interface. There should be 6 of them, accessible with ctrl+alt+F1-6. You can't copy-paste anything from there, but there shouldn't be too much output and we don't need all of it. It is possible to redirect the output from those commands to a file on an external drive to allow you to copy it to a forum post via a different computer, but let's do that some other time.

The grub menu is the menu that you may see when you boot the computer, after the screen for the hardware manufacturer and before the Ubuntu splash screen. grub is the bootloader and allows you to choose different operating systems, kernels and recovery mode. The grub menu may be hidden, but with a bit of luck you can open it by hitting shift at the right moment, when the menu should show. The Ubuntu installer makes it that way if you don't dual boot. It only takes one change in a configuration file and a single command to make the menu visible, if you like it.

---

### Post by jayhawker2 on 2019-03-20
I've got to reach "to drop to a root shell" .... lsb_release -a is not avalaible. The other commands did really work. But now, which one is the appropiate way to exit and get in anew?

Please, is it Ctrl+shift+F2 or ctrl+alt+F2? After entering "drop to a root shell" it doesn't work. 

Thank You

Is there any way to recover login and password? I've quite forgotten the first one. The second, the password, I do remember because it is required in order to begin every day.

---

### Post by Impavidus on 2019-03-21
> **jayhawker2 said:**
> I've got to reach "to drop to a root shell" .... lsb_release -a is not avalaible. The other commands did really work. But now, which one is the appropiate way to exit and get in anew?I thought that command has been around for a long time. Anyway, what output did they give you? It should contain information on your hardware and the version of Ubuntu currently installed. Try this one instead of the lsb_release command:```
cat /etc/lsb-release
```To get out of the root shell, just use the exit command.

> **jayhawker2 said:**
> Please, is it Ctrl+shift+F2 or ctrl+alt+F2? After entering "drop to a root shell" it doesn't work. 

Thank Youctrl+alt+Fn. I fixed the command in my earlier post. After dropping to a root shell there's no need, as you already have a command line interface.

> **jayhawker2 said:**
> Is there any way to recover login and password? I've quite forgotten the first one. The second, the password, I do remember because it is required in order to begin every day.
See [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword). In most cases **ls /home** will print the login names of all users. It's possible to configure the system otherwise, but if you had, you'd remember.

We're now trying to get some information on your hardware, so that we know what Ubuntu flavour would be best to install. Using a 10 year old version is no option.

---

### Post by jayhawker2 on 2019-03-22
FInally, I've got the Ubuntu release: 9.04. Thanks to the cat /etc/lbs-release. There are other information like distrib_ID=Ubuntu; distrib_CODENAME=jaunty and distrib-DESCRIPTION=Ubuntu 9.04.
 
Is this useful?

Thank You 

> **Impavidus said:**
> I thought that command has been around for a long time. Anyway, what output did they give you? It should contain information on your hardware and the version of Ubuntu currently installed. Try this one instead of the lsb_release command:```
cat /etc/lsb-release
```To get out of the root shell, just use the exit command.

ctrl+alt+Fn. I fixed the command in my earlier post. After dropping to a root shell there's no need, as you already have a command line interface.


See [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword). In most cases **ls /home** will print the login names of all users. It's possible to configure the system otherwise, but if you had, you'd remember.

We're now trying to get some information on your hardware, so that we know what Ubuntu flavour would be best to install. Using a 10 year old version is no option.

---

### Post by jeremy31 on 2019-03-22
jayhawker2, 9.04 has been unsupported for almost 10 years now

---

### Post by jayhawker2 on 2019-03-22
> **jeremy31 said:**
> jayhawker2, 9.04 has been unsupported for almost 10 years now

Yes, I know, but I'm trying to get back to an optimal resolution in order to recover some information in my computer. All the problem, as I said days before, begun when some day, when opening, the screen appeared in a very low resolution, say 300x200. All what is seen is so big than I can not come back to the previous resolution, because it has disappeared "Monitor" from System.

Please, what kind of information as for the computer itself would be required? I have a list of other specs after applying the other commands suggested, but frankly there are so many than I need some guidance. Thanks a lot.

---

### Post by Impavidus on 2019-03-22
The useful stuf to know would be RAM, the CPU and the graphics. That tells us what flavour of Ubuntu you can install. Once you have created a live disk with the appropriate flavour, you can use that to get any files from the hard drive and onto a usb drive before you begin installation. There should be no need to run the old system.

I don't know why anything would have changed a few days ago. It is surprising everything worked more or less until that time.

---

### Post by jayhawker2 on 2019-03-22
I'm afraid this information is not here. It only says tha the CPU IS Logical. If you can teach me some specific commands, now I know how to get to "go to a roll shell", I'll try to get this information.

Root shell, not roll shell, sorry.

Must I infer that if we are trying to know all those computer specs and Ubuntu releases is because there is no way to recover the previous release screen, and the only solution is to reinstall some fitting old Ubuntu release?

---

### Post by Impavidus on 2019-03-24
> **jayhawker2 said:**
> I'm afraid this information is not here. It only says tha the CPU IS Logical. If you can teach me some specific commands, now I know how to get to "go to a roll shell", I'll try to get this information.The command line interface rarely changes, but your release is so old that things may have changed. So I'm guessing some commands and hope they work on your system.

Another way to get some information on your cpu is from the proc filesystem. Try```
less /proc/cpuinfo
```That should open a text viewer with information on your cpu. Use the arrow keys to scroll and q to exit. On my computer I get, amongst other things, this:```
processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
stepping    : 7
microcode    : 0x2e
cpu MHz        : 837.398
cache size    : 3072 KB

```That's on an 8 year old laptop more than capable of running the latest Xubuntu.

The **free** command has been around for ages as well. On my computer I get```
free -m
              total        used        free      shared  buff/cache   available
Mem:           7910        1395        5226         130        1288        6113
Swap:          8667           0        8667
```telling me I've got 8GB of ram, most of which is available, and a little over 8GB of swap, unused.

> **jayhawker2 said:**
> Must I infer that if we are trying to know all those computer specs and Ubuntu releases is because there is no way to recover the previous release screen, and the only solution is to reinstall some fitting old Ubuntu release?
It may be possible to get your 9.04 system working again, but using 9.04 really is no option. It has been unsupported for 8½ years and there are known security risks. Furthermore, the software is so old that it will struggle with modern file formats. Actually, forum policy is to provide no help running dead Ubuntu releases, but to provide help to get on supported releases instead.

The goal is not to install some other old Ubuntu release. It's probably best to try the latest LTS release, but use a light flavour. Maybe that will turn out to be Lubuntu 18.04 LTS 32 bit, but without any specs, I can't say for certain.

If you want to recover some files, you can do that using the command line interface. Plug in a usb drive, mount it, copy your files, umount it and unplug it. I do all my file management on the command line. You may also be able to take the harddrive out of the computer, put it in an enclosure and plug it into a different computer using usb, then copy the files.

---

### Post by jayhawker2 on 2019-03-25
Thank You for your concern and advice. I'll inform.

---

