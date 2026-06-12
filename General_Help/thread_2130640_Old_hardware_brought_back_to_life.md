---
title: "Old hardware brought back to life"
date: 2012-12-12
forum: General Help
---

### Post by mörgæs on 2012-12-12
*Contents: A long, but hopefully easy to read collection of advice for beginners and intermediate users. *Don't get scared by the volume: The fact that the text is long is not an indication that the process is difficult, it's just a result of trying to deal with many different problems, also some which are fairly unlikely to encounter. Though the guide was born in 2012 it is receiving steady updates, latest 2025-01-07.


Various Linux distros are known as a good option for bringing old hardware back to life and the forum is receiving many questions on the topic. The thread is created in order to keep the experience and advice regarding old hardware in one place. Many of the considerations, recommendations and warnings from one problem can and should be reused by other people.

The main release, Ubuntu, used to be lightweight and suitable for old hardware, but recent releases are targeting new systems with more graphics horsepower.

Lighter derivatives like [Lubuntu]("http://www.lubuntu.me") and [Xubuntu]("https://www.xubuntu.org") are a somewhat better option for semi-old hardware. Both of them use the shared Ubuntu software repository so applications known to run on Ubuntu can also be used on Lubuntu/Xubuntu. 

However, there is a lot of hardware around which would benefit from something even lighter. For example, Snap (discussed later) adds a big workload so neither Lubuntu nor Xubuntu can be described as light today. This might not be relevant for recent hardware but one clearly feels the difference using older gear. 

[Fun OS]("https://www.funos.org/") seems like promising offspring within the Buntu family. The ads on their website are quite annoying but the distro itself looks fine - and free from Snap.

However, nothing in the Buntu family supports 32 bit CPU's so in this case other distros must be considered. The focus of this paper is Debian.



**1) Which distro to install?**
Ubuntu is built on [Debian]("https://www.debian.org/") and broadly speaking Debian of today can be compared to Buntu ten years ago. According to some, Buntu has drifted away from the roots but this space is now taken over by Debian. Some of the advantages regarding old hardware are:


[LIST]
[*]Debian supports 32 bit hardware
[*]Debian offers a small [Netinstall]("https://www.debian.org/distrib/netinst") image suitable for older equipment. Most of the packages are being downloaded during the installation so they don't have to be packaged in the installation file itself. The installation file fits to a CD.
[*]Debian manages packages using the DEB format which is as lightweight as can be. Various middle tiers like Snap and Flatpak are not needed here.
[*]There is no push towards buying a 'pro' subscription and the commands retain their original and intended function. For example, the **apt** command in Debian is only used for package management, not for additional marketing of the 'pro' option.
[/LIST]
 

When viewed using the command **df -hT**, a typical Debian installation running the XFCE desktop environment with Libreoffice and Firefox installed looks like this:

```
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.7G     0  1.7G   0% /dev
tmpfs          tmpfs     352M  1.2M  351M   1% /run
[COLOR=#ff0000]/dev/sda1      ext4      284G  4.1G  265G   2% /[/COLOR]
tmpfs          tmpfs     1.8G     0  1.8G   0% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     352M   60K  352M   1% /run/user/1000
```

A size around 4 GB is about as small as one can get. 

Later zram can be added (explained below). 


In the following guide we first test the hardware capabilities before deciding what and how to install but if you can't wait or if it's not possible to run a live boot you can just take the chance and go straight to the install described in **3)**.


**2) Hardware**
The main rule is that software in the Debian world works more or less everywhere. Some exceptions apply, though.

[TABLE="class: grid, width: 1000, align: left"]
[TR]
[TD]**Hardware**[/TD]
[TD]**Age (approx.)**[/TD]
[TD]**Occurrence**[/TD]
[TD]**Remarks**[/TD]
[/TR]
[TR]
[TD]32 bit without SSE2[/TD]
[TD] - 2002[/TD]
[TD]Rare[/TD]
[TD]See post 3 in the thread[/TD]
[/TR]
[TR]
[TD]32 bit without PAE[/TD]
[TD]2003-4[/TD]
[TD]Rare[/TD]
[TD]Debian is recommended. It comes with Firefox in stead of Chrome/Chromium which has abandoned 32 bit hardware.[/TD]
[/TR]
[TR]
[TD]32 bit with SSE2 and PAE[/TD]
[TD]A) General availability 2000 - 2008
B) Intel Atom notebooks from the years 2009-11 famous for having very low power consumption, for example discussed in a 2.000 post long thread [here]("https://ubuntuforums.org/showthread.php?t=2254322").[/TD]
[TD]Common[/TD]
[TD]Debian is recommended. It comes with Firefox in stead of Chrome/Chromium which has abandoned 32 bit hardware.[/TD]
[/TR]
[TR]
[TD]64 bit[/TD]
[TD]2003 -[/TD]
[TD]Common[/TD]
[TD]Though Ubuntu installs fine the performance under Debian is likely better.[/TD]
[/TR]
[/TABLE]


These restrictions are good to remember when reading the thread. 

Let's begin with a simple test to see if the hardware in question is fairly old but straightforward to deal with or very old and needs some tricks. 

Using any Linux distro, installed or from a live boot, please copy the following command one at a time into the terminal and run. 
```

sudo apt update
sudo apt dist-upgrade
sudo apt install lshw dmidecode
```

It installs the programs lshw (an abbreviation for *list hardware*) and dmidecode if they are not already present. We are going to use them a lot to look inside the computer.

After this, run
```
sudo lshw -C cpu | grep -i sse2
```

It takes some seconds to complete.

If you get a line full of abbreviations everything is good. Chances are that the install is simply next, next, next, finish.

If the command doesn't yield an output please see post #3 'really old hardware' in the thread. It's questionable if the computer will be of any practial use. 

(Details: The command above checks if the processor has the SSE2 instructions set. In the [Intel]("http://en.wikipedia.org/wiki/Comparison_of_Intel_processors") family the oldest member with SSE2 is a Pentium 4 and for [AMD]("http://en.wikipedia.org/wiki/Comparison_of_AMD_processors") the oldest is a K8. Though SSE2 is not necessary for a Debian install it still serves as a baseline for reasonable performance.)

The command
```
sudo lshw -C cpu | grep -i width
```
tells if you have a 32 or 64 bit processor. If it's 64 bit and you have more than 2 GiB of memory then a 64 bit ISO is recommended.

For people wanting to investigate CPU properties in depth this [link]("https://www.binarytides.com/linux-cpu-information/") gives inspiration.

*Memory:* The command
```
sudo dmidecode -t memory | grep -i 'ddr\|size'
```
shows the size of the present memory, for example 2*1 GB. It also shows empty slots ready for additional memory.

```
sudo dmidecode -t memory | grep -i max
```
shows the maximum size of memory that the motherboard supports.

If you (like me) end up with hardware not worth salvaging these commands are helpful when deciding how and where to recycle the memory. I often see a big improvement when an old computer receives one or two memory sticks from a donor.


The graphics processor has its own memory modules. Here is a guide for [finding out how much memory the graphics processor has]("https://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/").

[I]Drives
[/I]```
sudo lshw -short -C disk
```
shows the drives of the system, including CD/DVD drives. You can see the size of the hard disk and decide if it's big enough for the intended use. Later in the thread we shall investigate the health of the hard disk.

If Gparted or the **df** command show some strange partitions or don't show any at all it could be due of [Fake-RAID]("http://skrypuch.com/raid/"). If that's the case and if you don't want to keep Windows which may be installed here I suggest that Fake-RAID be disabled so the disks are functioning independently. The text in the hyperlink explains why. 

[I]Network
[/I]```
sudo lshw | grep -i '00bt'
``` shows the speed of the wired (ethernet) connector, often 100 or 1000 Mbit/s. If Wifi is slow then this is an alternative. 


*Display server*
You might have heard that some Linux distros are slowly switching from X11 to Wayland as a display server. Debian/XFCE stays for the time being with the dated but highly stable X11. One can see which server is in use by running the command 
```
echo $XDG_SESSION_TYPE
```
If the output is x11 then there's no need to worry about people posting this-and-that about Wayland. 

*Hardware modifications*
The older and hence slower the hard disk the more important is *zram *and/or *swappiness*, as explained in a later post. 2,5" disks used in portables are generally worse than 3,5" disks in stationary computers.

Adding memory is the single most efficient step one can take. 


If the hardware does not meet these requirements one should consider if it's worth the effort to carry on. There is so much used (say, 4-12 years of age) gear around that one can get for free or cheap. The ever-increasing system requirements of Windows are pushing more and more computers into the &#8216;old&#8217; category even though they are in good working order. 

Though, if the graphics performance in an old computer is too weak for daily use it can still be of value as a file server for back-ups. Just check that the hard disk is in good condition (see next post in the thread) but consider the power consumption if it's intended to be always running. 

On a home network with only trusted clients **Vsftpd** is a fine FTP server package for backup purposes. The otherwise popular client Filezilla has been terminated for 32 bit systems so here one has to use alternatives like Gftp. 

An interesting blog about [old hardware and realistic expectations]("http://www.alandmoore.com/blog/2011/08/21/reviving-your-old-pc-with-linux-part-i-defining-expectations/").


**3) Installing the operating system**
First of all: The solution to getting old hardware into usable condition is not old software. When software has reached end of life and is abandoned by the developers no security fixes are provided, and for obvious reasons people should not run such a system. Don't use it, no matter how fast it runs or how much you like the user interface. Here we focus on the latest Debian.

Installation files are normally packaged in a file with the .ISO extension, in daily speak just referred to as 'an ISO'. 

If the computer is one you have salvaged from a dumpster or which has been given to you I suggest that you begin with [completely erasing the hard disk]("https://ubuntuforums.org/showthread.php?t=2358582"). My preferred command is

```
sudo shred -f -z -v -n 2 /dev/sdX
```

where sdX refers to your hard disk, often sda. It must be run from a live boot.

Nwipe is another good candidate for sanitising a hard disk.

More about [hard disk management]("https://www.youtube.com/watch?v=gdqlPDIXkOw").



Installation should be done from a USB stick, if the computer is young enough to support it, or else from a CD or DVD. If the install hangs at the very end with no explanation given just push Return.


If booting from USB does not work and if the CD/DVD drive is on the brink of failing it's worth trying the minimal Debian ISO as opposed to the full-size one. Often a semi-working CD drive will accept a small ISO file like this one.

Regardless of which ISO you choose one should (if possible) use wired internet access while installing, during the first boot and when applying the first batch of bug fixes.


A number of background processes called *daemons* are created automatically. They often serve a useful purpose, for example taking care of the network connection, but not all are needed by all users.

If one doesn't have a printer then *cups* could and should be removed. It can be temporarily disabled by the command ```
sudo systemctl stop cups
```

After that ```
sudo apt --purge remove cups cups-common cups-filters cups-pk-helper
``` followed by ```
sudo apt autoremove
``` removes cups-related packages. 

In general software should be removed if there is no clear need for it - this is especially important for software that communicates with the outside world like a printer. [CUPS has a history of security related bugs and maintainers which are reluctant to listen to warnings]("https://www.evilsocket.net/2024/09/26/Attacking-UNIX-systems-via-CUPS-Part-I/") so let's celebrate that we use an OS where we have the power to uninstall packages which we don't use.

One or both of the commands ```
sudo systemctl --type=service
service --status-all
``` will shows all daemons running (press *q* for quitting after seeing the output). If one wants to harden the system and remove other unneeded daemons, for example Bluetooth, then this can be used as inspiration. 


**3 B) Security matters**
It's a well-known fact that software bugs are used for gaining access to a target computer. 

Maybe less known is that hardware, especially CPU's, also can have [security related bugs]("https://en.wikipedia.org/wiki/Transient_execution_CPU_vulnerability#Vulnerabilities_and_mitigations_summary"). Good news is that many of them can be solved by software, often in the form of processor microcode.

The topic is only discussed briefly here. Suffice to say that the command **lscpu** gives an overview of how well the CPU is protected - normally one will see that the general status is fine when using the latest release of Debian.

The standard user only has to deal with the question of [hyperthreading]("https://en.wikipedia.org/wiki/Hyper-threading#Security"). My advice is to disable it. 

If the command ```
lscpu | grep 'per core'
``` returns 1 then hyperthreading is not present, if 2 then reboot, go to BIOS/UEFI and turn it off.


**3 C) Distros other than Debian**
GNU/Linux is about choice, and other light distros than Debian are also worth a try. 

[Puppy]("http://www.puppylinux.org/") (which comes in many versions), [Knoppix]("http://www.knoppix.org/") and  [Bodhi Linux]("http://www.bodhilinux.com/") are good options. More distros are listed [here]("https://itsfoss.com/lightweight-linux-beginners") and [here]("http://ubuntuforums.org/showthread.php?t=1582027") if people want to experiment, but before choosing one of the minor distros remember to check how well it is maintained. Never use an unsupported distro or a distro where bug fixes are released so slowly that it's almost unsupported. This excludes for example Damn Small Linux, which is sadly still mentioned in Ubuntuforums. Please let it rest in peace.


**3D) BIOS**
If the install still does not work you could try resetting BIOS to default values and / or upgrade the BIOS to a later version. Before upgrading remember to search the web and see if people have bad experiences with this *for your particular hardware*. Don't be afraid of general warnings which may not apply to your machinery.

Some advice for [updating BIOS and other kinds of firmware]("https://fwupd.org/lvfs/docs/users").

A working BIOS can sometimes be tuned to yield a better performance, for example by disabling options which are not needed.


**4) Snap**
The traditional package format for Debian is a *deb* package. Lately at least three alternative package formats have been introduced: Snap, Flatpack and AppImage.

For a number of reasons I recommend to stay with deb packages only,  especially for old hardware. First and foremost the other package formats add a  significant workload to the system. 

The people behind Linux Mint have posted [this statement]("https://linuxmint-user-guide.readthedocs.io/en/latest/snap.html") about Snap explaining why they try to avoid it, and the same goes for [Bodhi Linux]("https://www.bodhilinux.com/w/snap/"). Since the purpose of this thread is to get old hardware functioning we will do the same. 

To check if you have snap installed run the command ```
snap list
``` 
It has three possible outcomes:

[LIST=1]
[*]An error appears
[*]The user is encouraged you run the command **snap install hello-world**
[*]The user gets a list of installed snap packages, for example
[/LIST]
```
Name               Version          Rev    Tracking         Publisher   Notes
bare               1.0              5      latest/stable    canonical&#10003;  base
core22             20230801         864    latest/stable    canonical&#10003;  base
firefox            118.0.1-1        3216   latest/stable/&#8230;  mozilla&#10003;    -
gnome-42-2204      0+git.ff35a85    141    latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes  0.1-81-g442e511  1535   latest/stable/&#8230;  canonical&#10003;  -
snapd              2.60.3           20092  latest/stable    canonical&#10003;  snapd

```

If 1: Everything is good.
If 2:  The snap daemon is present but inactive. To avoid using it by accident just  remove it with the command **sudo apt remove snapd**. It can take a while to  finish.
If 3: Some applications are present in snap format. Consider if you need all of them or if they can be replaced by applications in deb packages.

To remove a snap package run
```
sudo snap remove <package>
```
for each package, for example 
```
sudo snap remove firefox 
```
It might take some attempts because packages have to be removed in the right order.

Now 
```
snap list
```
should display the empty list.
Finally 

```
sudo apt remove snapd
```
removes the mothership. All clear.

Now comes the tricky part. One would expect that the command ```
sudo apt install chromium-browser --dry-run
``` would warn the user about all packages about to be installed but that's not the case. Should one be mislead to executing 

```
sudo apt install chromium-browser
```

then a subsequent

```
snap list
```

will show that the command silently has triggered a full Snap reinstall including packages unrelated to Chromium. We are back to start, only with *cups* added to the list. Oh, snap.

```
Name               Version          Rev    Tracking       Publisher      Notes
bare               1.0              5      latest/stable  canonical&#10003;     base
chromium           118.0.5993.117   2673   latest/stable  canonical&#10003;     -
core22             20230801         864    latest/stable  canonical&#10003;     base
cups               2.4.6-4          980    latest/stable  openprinting&#10003;  -
gnome-42-2204      0+git.ff35a85    141    latest/stable  canonical&#10003;     -
gtk-common-themes  0.1-81-g442e511  1535   latest/stable  canonical&#10003;     -
snapd              2.60.4           20290  latest/stable  canonical&#10003;     snapd
```


The Buntu roadmap indicates that more and more packages are to be transferred to Snap. If that's not your liking then it's worth the while trying Debian or Linux Mint.

For more information about Snap see the thread [here]("https://ubuntuforums.org/showthread.php?t=2429978").
 

**5) Applications**
&#8216;Light applications&#8217; is a neverending topic. Only brief advice is given here, otherwise I leave it to the user to experiment.

Trying a lighter browser like Pale Moon, Xombrero / Xxxterm or Epiphany may or may not speed things up. The packages are small so it&#8217;s an easy test to do. The even lighter browser **links2** gives a crude text display with embedded images but nothing more - no pop-ups, no animated GIF's and no video ads (scrolling is done with right mouse button or with Page Up/Down). After years of exposure to pages bloated with irrelevant ads and animations it's a joy to see only plain text. The command for installing is 
```
sudo apt install links2
```


**6) Maintenance**
An often overlooked part of getting an old computer into a useable condition is cleaning the interior dust build-ups, especially around the fan and heatsink. Take care not to damage the fans by forceful vacuuming and remember to only vacuum in the reverse direction of the normal air flow. Best is to block the fan with a tooth pick or piece of wire while cleaning to prevent it from spinning too fast. If we are dealing with a desktop remember that it likely has several fans (for CPU, GPU, power supply and more).

Short bursts of compressed air also helps. Again, only in the reverse direction of the normal air flow. 

Remember to check that the fan is turning freely after cleaning. 

Many good guides are available describing how to take hardware apart. Here's for example a list for [Toshiba]("http://www.irisvista.com/tech/").


On the software side the only maintenance needed is 

```
sudo apt update
sudo apt dist-upgrade
<maybe reboot here>
sudo apt clean
sudo apt autoremove
```

once in a while. The last command comes in handy because it removes old kernels and saves hard disk space. 

If the computer does not automatically ask for updates shortly after the install it's especially important to run the commands. 

A file system needs some free space to perform well. The command 
```
df -Th
```
shows in percent how much space is used for various mounts. A good rule of thumb is never letting any of the measures exceed 75%.

The similar command ```
df -i
``` shows the number of available inodes. There are many explanations for inodes on the web, for now it will be enough to know that the percentages shown should be as low as possible. If you see high numbers just run the *autoremove* command mentioned above.

The command 
```
sudo find /home -name '*' -size +50M
```
tells which files in the /home directory are more than 50 MB of size. It's useful for cleaning if space is getting tight. Remember to empty the trash can afterwards.

Some advice on [file system maintenance]("https://ubuntuforums.org/showthread.php?t=2494771").


**7) Environmental impact**
It is a widely held belief that old hardware shouldn&#8217;t be used because of power consumption. This is not necessarily true: [Old hardware is sometimes less greedy than new]("http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html"), if one compares within the same category (desktop versus desktop, for example). The power consumption of newer machines per unit of calculation is lower, but not the total power consumption of the machine.

However, the biggest benefits from using an old computer as long as possible is less production of new hardware and less e-waste to be handled, both of which are causing serious environmental problems. Add to  this the joy of using hardware without a software vendor trying to force people to pay for a pre-installed operating system.

If you have managed to bring an old computer back to usable life you should not be ashamed for being out of sync but proud of taking care of the environment. 


**8) Further improvement**
Third post in the thread gives some suggestions for what to trim and adjust after install.


**9) Still in doubt? **
If this does not answer all your questions you are of course welcome to post but please read [#4]("http://ubuntuforums.org/showthread.php?t=2130640&p=12580294&viewfull=1#post12580294") first.

= = =
Thanks to MG&TL for proof-reading.

---

### Post by mörgæs on 2013-03-14
One question when dealing with old hardware is whether or not it's fast enough for the intended purpose. Post 1 and 4 discuss this topic and provide ideas for getting a higher performance. Another question is whether or not it's safe to store data on an old hard disk. 

In mechanical equipment errors often appear in the shape of the [bathtub curve]("https://en.wikipedia.org/wiki/Bathtub_curve"). Since this is about old gear the left hand part of the bathtub is not a concern; the only question is how long we can use the hard disk before the right hand increase appears - if it ever does.

I am often surprised how long a hard disk can live on in an error-free state, some of mine now celebrating 20 years birthday after being exposed to a lot of distrohopping and reinstalling. 

However, **if** a sign of malfunction appears then one has to heed the warning and take action right away. This applies to hard disks in general and not only recycled gear. There may not be a second chance.  



A hard disk can fail in various ways; here we focus on **bad sectors** which can develop over time. Fortunately they tend to appear in clusters and not randomly distributed over the disk.

Error-handling routines in the hard disk firmware are expected to take care of the individual sectors when an error occurs. They are often quite efficient and many well-behaving hard disks have a few bad sectors unbeknownst to the user. 

However, when resurrecting old hardware one should at least do a little testing before installing.

If the hard disk is dubious then one can simply choose not to use it, expecting that more errors are coming up. When discarding a hopeless computer remember to keep the hard disk so there always is a stack of spares available. 

Another option is to keep using the damaged disk, directing the installation to the intact parts. This is what we are going to discuss here. If one decides to store all user files in Google Drive or another cloud service then there's no risk associated with a failing hard disk.

As always: Regardless of the hard disk condition always back up to a physically and digitally separated location. If your important data are not backed up they are obviously not important to you.


Let's take an example. The commands can be run in a live boot or in an  already installed Buntu / Debian. 

First we execute 
```
sudo fdisk -l

```

The top line of the output could look like

```
Disk /dev/sda: 74.6 GiB, 80060424192 bytes, 156368016 sectors

```

It tells us the number of sectors and that the hard disk is mounted as /dev/sda.

We would like to investigate /dev/sda further. Next command is 
```
sudo badblocks -v /dev/sda
```which can take long time to run. It searches the entire /dev/sda hard disk for bad sectors and writes their location if any are found. 

From an installed system the command can also be executed as```
sudo badblocks -v /dev/sda > badblocks.txt
``` which saves the output as a text file. An empty file indicates that no errors are found.

When the command has finished (for a large disk it might need to run the whole night) investigate the output. Say it looks like 

```
3040076
3040077
3040078
3040079
3040548
3040549
3040551
12558888
12558889
12559356
12559357
12559358
12559359
(and 58 more 125xxxxx-numbers)

```

In other words we have one cluster with sector numbers 304xxxx and another with numbers 125xxxxx.

The larger of the numbers is 125xxxxx. Let's define an area up to and including this sector (and a part more for safety) from which we are keeping the installation away. 

Since the total disk size is 156368016 sectors we have to let go of at least 12600000 / 156368016 = 8 % of the disk capacity. This equals 6 GiB lost. 

A basic Debian install takes around 4 GiB so we have plenty of room (remember, we have already decided to store all files in Google Drive). For safety we decide to skip the first 20 GiB. 

There  will still be 74.6 GiB - 20 GiB = 54.6 GiB left as useable space. 


We decide to erase the hard disk completely before installing. From a live boot run the command 
```
sudo dd if=/dev/zero of=/dev/sda bs=1M
```
again assuming that the hard disk is sda. Also this command can take a long time and only the hard disk indicator light shows that something is proceeding. 

When finished the message *no space left on device* will appear. Though it might sound like an error it only indicates that the process is complete. 

Some consider the command overkill but at least one should erase the master boot record and the partitioning scheme. This is done by the (quick) command 
```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

After this 
```
sudo fdisk -l /dev/sda
```
shows an empty (unpartitioned) disk as expected. 


During the Debian installation one is offered an automatic partitioning. Normally this is a good option but here we are going to take control and create our own.

First a partition of around 20 GiB should be created and marked *do not use*.

After this a swap partition. I prefer to have it double the size of RAM but other people might have different opinions.

The remainder is used as the / (root) partition formatted as ext4. I don't see the purpose of having a separate /home partition but if this is desired now is the time for creating it.

A simple partitioning scheme could be done using only primary partitions but if you are planning to do many experiments then extended partitions might be necessary.
Rest of the installation is standard. 


Now 
```
sudo fdisk -l
```
should show something (more or less) like

```
Disk /dev/sda: 74,6 GiB, 80060424192 bytes, 156368016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: *

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1  *         2046 156366847 156364802 74,6G  5 Extended
/dev/sda5            2048  39061503  39059456 18,6G 83 Linux
/dev/sda6        39063552 136912895  97849344 46,7G 83 Linux
/dev/sda7       136914944 156366847  19451904  9,3G 82 Linux swap / Solaris
```

and
```
df -hT
```
shows
```

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1,9G     0  1,9G   0% /dev
tmpfs          tmpfs     379M  1,2M  377M   1% /run
[COLOR=#ff0000]### notice that /dev/sda5 is not mentioned here ###[/COLOR]
/dev/sda6      ext4       46G  3,9G   40G   9% /
tmpfs          tmpfs     1,9G     0  1,9G   0% /dev/shm
tmpfs          tmpfs     5,0M  8,0K  5,0M   1% /run/lock
tmpfs          tmpfs     379M   64K  379M   1% /run/user/1000
```

We see that sda5 spans 39.059.456 sectors (12.600.000 required) and is unused; only sda6 stores data for the operative system. The usable hard disk size is now 46 GB.

Finally, the command ```
sudo badblocks -v /dev/sda6
```
should yield a clean log like 
```
Checking blocks 0 to 48924671
Checking for bad blocks (read-only test): done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)
```


Once in a while people discuss which [file system]("https://www.howtogeek.com/33552/htg-explains-which-linux-file-system-should-you-choose/") to use. I would go for ext4 unless there are strong reasons for doing otherwise.

---

### Post by mörgæs on 2013-03-19
The original post dealt with fairly old hardware. Here are some additions for really old stuff.

**32 bit CPU's with or without PAE**
All of these are supported by Debian in a standard installation. No tweaking needed.
Firefox [Extended Support Version]("https://www.mozilla.org/en-US/firefox/all/#product-desktop-esr") comes by default in a Debian install. Chrome and Chromium won't run.

**32 bit CPU's without ****SSE2**
A CPU uses a number of instruction sets to execute orders from the outside world. The instruction set SSE has been around for ages, so all recent software packages can expect SSE to be available. 

However, the later standard SSE2 was introduced with Pentium 4 which leads to special considerations for older gear. It is not known whether or not Firefox still supports non-SSE2 equipment, but maybe it's too slow anyway to be of any use.

---

### Post by mörgæs on 2013-03-30
Until now we have focused on getting a light and fast (that is, lightning fast) operating system by selecting the most efficient software to install. After the install is completed it's worth the while to test the system to see if some parameters should be adjusted in order to further speed up things. Don't jump to conclusions and begin tweaking the system before you know A) where the bottleneck is *for your particular combination of hard- and software* and B) if there's anything to do about it.

Many good workload monitors are available. One of the options is Gkrellm which can easily be configured to show various factors relevant to performance. Give it a corner of the screen and keep an eye on it during different kinds of tasks.


**Slow boot**
Though Debian is considered a fast operating system the boot itself is sometimes slow. Here is a discussion of processes which can be disabled, [speeding up boot time]("https://ubuntuforums.org/showthread.php?t=2496312").

The command ```
more /var/log/dmesg
``` shows in detail what goes on during boot. The number in [ ] at the beginning of each line is the time stamp so when there's a big difference in the number something is taking a long time. One can view the entire log screen for screen using the command above or use ```
awk -F'[][] *' '$2-ts>0.3{printf "%s\n%s\n---\n",l,$0}{ts=$2;l=$0}' /var/log/dmesg
``` which shows only the records in the log file where there's a delay longer than 0.3 seconds. Thanks to **schragge** for the command.


[HR][/HR]This section is only relevant if you have too much hard disk activity.

**Swappiness **
The *swappiness* setting determines when a system begins swapping data to the hard disk. A low value makes more use of memory and less use of the swap partition.

As memory storage is many times faster than hard disk storage this is what we want. 

The default setting is 60, which makes swapping begin early. Lowering to, say 10 sometimes makes a significant improvement in speed, dependent on the hard disk type and workload.

To test it (for the present session only, permanent settings are unchanged) one simply does the following: 


[LIST=1]
[*]Copy the command ```
cat /proc/sys/vm/swappiness
``` to the terminal and press Enter. You will now see the present value of swappiness.
[*]Spend some minutes browsing Ubuntuforums or another web site. Notice the speed (or lack thereof).
[*]After that run the command ```
sudo sysctl vm.swappiness=10
```
[*]Continue browsing. Do you now have a faster system with less hard disk activity?
[/LIST]

If one wants to make the setting permanent the line *vm.swappiness = 10* has to be added to */etc/sysctl.conf*. It's done with the command ```
sudo sed -i '$ a\vm.swappiness = 10' /etc/sysctl.conf
```

The new setting is activated in next boot. In effect it moves workload from a slow, rotating hard drive to the memory modules, which are faster than a solid state drive, and it could be referred to as the poor man's SSD.


**Zram**
is another module which can speed up a system by lowering the swap activity on the hard disk. The command ```
cat /proc/swaps
``` lists the swap areas in use; for a standard Lubuntu installation the results could look more or less like 
```

Filename        Type         Size      Used   Priority
/dev/sda1       partition    4882428   0      -2
```
which indicates that only a hard disk swap partition is used. After executing ```
sudo apt install zram-tools
``` the command now displays 
```

Filename        Type         Size      Used   Priority
/dev/sda1       partition    4882428   0      -2
/dev/zram0      partition    262140    0      100
```indicating that a new swap area with higher priority (that is, will be used first) has been added. The sizes shown will differ according to the hardware on which zram runs.

It's recommended to experiment with swappiness and zram alone and in combination. On some computers it gives a significant boost, on some there's only a minimal change

---

### Post by mörgæs on 2013-03-30
[COLOR=#ff0000]**A) I have a question**[/COLOR]
If the posts above do not solve your problem feel free to post here. Remember to state everything you know about the computer.

If you have the option please run 
```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags. Can be done in a live boot using any version of Buntu.

An example of the output is shown at the bottom of the post.


[COLOR=#ff0000]**B) I would like to provide an answer**[/COLOR]
Many users in Ubuntuforums have experience in old hardware and are eager to help. Thanks, that&#8217;s what keeps the forum running. However, a few guidelines should be observed before posting:

[LIST]
[*]Please don&#8217;t provide an answer based only upon searching the web. We are happy for contributions but a lot of dubious advice exists and quoting it does not help anyone. Please only post if you have hands-on experience with something close to the hardware and software in question.
[*]Don&#8217;t take for granted that there is a solution and don't give the person asking a false hope. Not every old computer can be brought into usable condition, so *sorry, you have to recycle this dinosaur* might be the only sensible answer. If you never post this regardless of the hardware in question you are probably too lenient.
[*]Corrections to the posts are welcome.
[/LIST]


```
computer
    description: Desktop Computer
    product: OptiPlex 745 ()
    vendor: Dell Inc.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=desktop power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0MM599
       vendor: Dell Inc.
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: 2.6.6
          date: 06/26/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 2133MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1,5 ns)
             product: M3 78T2953EZ3-CE6
             vendor: Samsung
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1,5 ns) [empty]
             vendor: FFFFFFFFFFFFFFFF
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_3
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 667 MHz (1,5 ns)
             product: M3 78T2953EZ3-CE6
             vendor: Samsung
             physical id: 2
             serial: [REMOVED]
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 667 MHz (1,5 ns) [empty]
             vendor: FFFFFFFFFFFFFFFF
             physical id: 3
             serial: [REMOVED]
             slot: DIMM_4
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: 82Q963/Q965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82Q963/Q965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fe900000-feafffff ioport:d0000000(size=268435456)
           *-display:0
                description: VGA compatible controller
                product: RV516 [Radeon X1300/X1550 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:16 memory:d0000000-dfffffff memory:fe9e0000-fe9effff ioport:dc00(size=256) memory:fea00000-fea1ffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV516 [Radeon X1300/X1550 Series] (Secondary)
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:fe9f0000-fe9fffff
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff00(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:22 memory:febfbc00-febfbfff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:43 memory:febfc000-febfffff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:fe800000-fe8fffff ioport:f0000000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:fe700000-fe7fffff ioport:f0200000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.132 duplex=full firmware=5754-v3.15 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:44 memory:fe7f0000-fe7fffff
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff80(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff60(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ff980800-ff980bff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fec0(size=16) ioport:ecc0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:febfbb00-febfbbff ioport:ece0(size=32)
        *-ide:1
             description: IDE interface
             product: 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe40(size=8) ioport:fe50(size=4) ioport:fe60(size=8) ioport:fe70(size=4) ioport:fed0(size=16) ioport:ecd0(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD800JD-75MS
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 10.0
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00000b01
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 72GiB
                capacity: 72GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-10-14 21:23:38 filesystem=ext4 lastmountpoint=/ modified=2014-06-16 17:27:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-06-16 17:27:40 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2044MiB
                capacity: 2044MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2044MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: CDRWDVD TS-H493A
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: D200
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc

```

---

### Post by venice vet clinic on 2013-03-30
hi there,
I hope you could help me. i've a very old Pc . it comes with pentium(R) 4 cpu 1.8Ghz and 1.79Ghz,1.96 Gb of Ram . it also have 80 Gb of hard disc.

i've try installing the latest ubuntu 12.1 but it is very slow.. I use it for my clinic daily record patients detail and some video that i play for my client.


pls advice

---

### Post by carl4926 on 2013-03-30
Try xubuntu
It should be much better

---

### Post by black veils on 2013-03-30
yes try xubuntu, should be just right.

if you want something faster than that though, you could use lubuntu.

---

### Post by 3rdalbum on 2013-03-30
If you're using Ubuntu in a business setting, you should be using an LTS version - Ubuntu 12.04 is the most recent LTS version, and it runs better on old hardware than 12.10.

Ubuntu 12.10 requires good 3D graphics support, but 12.04 can work with 2D graphics if your system isn't powerful enough for the 3D. If you try to use 12.10 on a computer with bad 3D support or an old graphics card, it will be horribly slow.

Xubuntu or Lubuntu would also work (even 12.10), but I'm unsure about how long Xubuntu and Lubuntu 12.04 are supported for. It might just be 18 months.

---

### Post by kc1di on 2013-03-30
Try LXLE it's Lubuntu long term support. 
you can get a copy [here. ]("http://www.lxle.net/index.php?showimage=10")

---

### Post by sudodus on 2013-03-30
I suggest that you download Xubuntu 12.04.2 LTS which has long time support until April 2015.[URL="http://cdimage.ubuntu.com/xubuntu/releases/12.04.2/release/"][COLOR=#ff0000]
[/COLOR][/URL][COLOR=#ff0000][http://cdimage.ubuntu.com/xubuntu/releases/12.04.2/release/](http://cdimage.ubuntu.com/xubuntu/releases/12.04.2/release/)
[/COLOR]
The current Lubuntu versions have only 18 months support.

*Edit*: Maybe I should explain why Xubuntu 12.04.2 LTS.

- enough RAM
- a business application, so official LTS (long time support) is preferred.

---

### Post by sudodus on 2013-03-30
If you want to play video, you might install ***openbox*** into your Xubuntu system (any time after installation of Xubuntu)
```
sudo apt-get install openbox
``` which gives you a very simple window manager (no full desktop environment), and it will be faster for playing video than with the default Xubuntu desktop. I think openbox has LTS thanks to Kubuntu 12.04.2, where it is included.

Select which desktop environment to run at the log in screen. Simply right-click on the dark grey background to start a terminal window in openbox.

---

### Post by ibjsb4 on 2013-03-30
I use to be an advocate of Xubuntu for older machines, but these days even XFCE seems to run slower.  I guess it should now be considered a middleweight, making Lubuntu the better choice.

---

### Post by amjjawad on 2013-03-30
I honestly couldn't read your thread because I have a toothache and I can't focus :(

Can you please add the link of my page: [https://wiki.ubuntu.com/amjjawad](https://wiki.ubuntu.com/amjjawad) and this link too: [https://wiki.ubuntu.com/Lubuntu/ContactUs](https://wiki.ubuntu.com/Lubuntu/ContactUs)

If anyone has any doubt, I'll be more than glad to help :)

I'm having some projects in mind these days but I can't do anything unless I get rid of this silly pain.

I promise to read it and get back to you!
Thank you so much :)

---

### Post by venice vet clinic on 2013-03-30
hi thanks to all the replies. i'm thinking does  Xubuntu 12.04.2 LTS  come with something like ms office or words??cos i need those to do my daily report.

---

### Post by venice vet clinic on 2013-03-30
hi i've a pentium(R) 4 cpu 1.8Ghz and 1.79Ghz,1.96 Gb of Ram . it also have 80 Gb of hard disc. do you think  Xubuntu 12.04.2 LTS is suitable for me?? and i also need something like ms exel and ms word to do my daily report.

---

### Post by sudodus on 2013-03-30
> **venice vet clinic said:**
> hi thanks to all the replies. i'm thinking does  Xubuntu 12.04.2 LTS  come with something like ms office or words??cos i need those to do my daily report.

Yes, ***Libre Office*** with a word processor 'Writer', a spreadsheet program 'Calc', a presentation creator 'Impress', a drawing program 'Draw' and a database program 'Base' are easy to install and fully compatible with Xubuntu either via the Software Center or via the terminal command

```
 sudo apt-get install libreoffice
```

---

### Post by black veils on 2013-03-30
you will want to either install libreoffice from the software center, or [openoffice]("http://www.openoffice.org/download/") depending on your need for compatibility or general preference.

---

### Post by amjjawad on 2013-03-30
Hi,

I'd like to explain something important. I have done it yesterday on Lubuntu Mailing List ([Contact Lubuntu]("https://wiki.ubuntu.com/Lubuntu/ContactUs")) and I guess I have to re-do it again here :)

What is the difference between Lubuntu and Ubuntu?
Answer is here: [https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu](https://wiki.ubuntu.com/Lubuntu#Lubuntu_VS_Ubuntu)

What are the things in common between Ubuntu and Lubuntu?
Answer is on the above link as well.

[B]Both L and U are sharing the same Core System. Of course, same repositories as well.
[/B]
Having that said, Lubuntu 12.04 is actually unofficial LTS version. You will be able to download and install all the security updates for 5 years for the core system.


Why then Julien ([Head of Lubuntu Devs]("https://wiki.ubuntu.com/Lubuntu/Developers")) can't call it an LTS?
Well, because we don't have enough developers (man-power) to have such commitment. LXPanel, PCManFM, etc ... are all Lubuntu Packages which are not supported for 5 years. That is why we can't call Lubuntu 12.04 an LTS.


Now, if you are:
- Average User
- Advanced User
- Someone who is keen to learn

This will change nothing for you. If you know what you are doing, you will be able to survive with Lubuntu 12.04 for 5 years. 


Thank you!

P.S.
Check my signature for more links.

---

### Post by venice vet clinic on 2013-03-30
can you give me one clear cut of solution base on my specification on my PC? my question is just which os is you think more/most suitable for me to install and my needs. just give me one.

---

### Post by sudodus on 2013-03-30
We give advice according to our experience and preferences, so different persons might give different advice. But if you have a reasonably fast internet connection, you can easily download a couple of 32-bit iso files, for example Lubuntu 12.10 and Xubuntu 12.04.2 LTS and try both (booted and running from the installation media, CD/DVD/USB drive). Do not install until you have found ***your*** favourite.

*Edit*: My advice is in post #8

---

### Post by mörgæs on 2013-03-30
> **venice vet clinic said:**
> can you give me one clear cut of solution base on my specification on my PC? my question is just which os is you think more/most suitable for me to install and my needs. just give me one.

The idea behind a megathread is that all necessary advice is written in the first post. If you read that and keep in mind you have a Pentium 4 (but one of the weaker 4's) you will see that Lubuntu 12.10 is recommended.

---

### Post by venice vet clinic on 2013-03-30
thank you so much. i'll try Lununtu 12.10. yap it is one of the weaker 4's

---

### Post by Mesozoic on 2013-03-31
Similar experience here.  Trying to install Ubuntu Servre 64-bit 12.04.2 LTS on an old eMachines K8M-800 mobo and 3300+ Sempron processor.  System boots and runs the USB bootloader, but detecting hardware fails, I believe.  Going to try the 32-bit version next.

---

### Post by lincoln32 on 2013-03-31
might also check non-PAE older cpu's do not support PAE adressing. Not a  real issue just use a non PAE kernal but when Ubuntu was trying to make everything fit on a cd they had to leave some things out---nonPAE was one of them. Download the mini.ISO it has it along with the ability to install all versions of ubuntu

[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html)
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by TenPlus1 on 2013-03-31
Bodhi LInux 2.2 (non-pae) will install on it and that is built from ubu 12.04 lts...

---

### Post by sudodus on 2013-03-31
> **Mesozoic said:**
> Similar experience here.  Trying to install Ubuntu Servre 64-bit 12.04.2 LTS on an old eMachines K8M-800 mobo and 3300+ Sempron processor.  System boots and runs the USB bootloader, but detecting hardware fails, I believe.  Going to try the 32-bit version next.

Welcome to the Ubuntu Forums :-)

1. Please explain what you want to do with the computer!

2. In the title you wrote about Lubuntu and Mint. In the text you wrote about Ubuntu server. Which ***versions*** did you try?

3. Also let us know the amount of RAM: (512, 768, 1024, ... MB?)

Knowing about the CPU but not knowing which versions you tried and not knowing about the RAM, I suggest a 32-bit OS, Lubuntu 12.10, Xubuntu 12.04.2 LTS or Ubuntu server 12.04.2 LTS. If less than 768 MB RAM, get the ***alternate*** iso file.

---

### Post by starlyte2 on 2013-03-31
LucidPup and PrecisePup are both Ubuntu based, and run anything, nearly, PII, PIII, Duron800. Believe me, I dunnit. ;)

---

### Post by OrangeCrate on 2013-03-31
> **mörgæs said:**
> Before posting in this thread: 

**A) I have a question**
If the post above does not solve your problem feel free to post here. Remember to state everything you know about the computer.

If you have the option please run 
```
sudo lshw > lshw.txt
```

and **post lshw.txt in code tags**. 


**B) [B]I want to provide an answer**[/B]
Many users in Ubuntuforums have experience in old hardware and are eager to help. Thanks, that&#8217;s what keeps the forum running. However, a few guidelines should be observed before posting:

[LIST]
[*]Please don&#8217;t provide an answer based only upon searching the web. We are happy for contributions, but a lot of dubious advice exists, and quoting it does not help anyone. Please only post if you have hands-on experience with something close to the hardware and software in question.
[*]Don&#8217;t take for granted that there is a solution. Not every old computer can be brought into usable condition, so *sorry, you have to recycle this dinosaur* might be the only sensible answer.
[*]Contributions to the original post are welcome.
[*]If you see a post somewhere which should be merged into this thread please send me a message and I shall take care of it.
[/LIST]

Proactive advice for people who like older IBM ThinkPads...

I just cleaned up and donated two T42s, and am currently using this T43, which was basically new when I got it. It sat on the desk of the owner, and it's workload consisted of light emails, and Solitare. I took it apart, cleaned it up, bumped the RAM from 512MB to the maximum of 2GB, and I liked it so much when I was done, that it is now my everyday laptop. I run Xubuntu 12.04.2 on this one, and it's very quick and solid.

**My only problem, is that I can not figure out how to get the sound working. I am suffering from the well documented "Dummy Output" issue. If anyone can supply an answer to this, it would be highly appreciated.**

The future of X/L/Ubuntu on these machines...

T42s and earlier models will not take a PAE kernel, so, 12.04 is your last shot for Ubuntu or Xubuntu (not sure about Lubuntu). T43s and newer, will take the PAE kernel, and I've had both 12.10 and 13.04 installed on this computer. They both worked fine. The added RAM makes a big difference, and is highly recommended for these notebooks to stuff them as full as you can with additional memory. One caution though - you will discover, that adding the second stick of RAM, is not for the weak of heart (it's under the keyboard).

```

laptop
    description: Notebook
    version: ThinkPad T43
    width: 32 bits
    capabilities: smbios-2.33 dmi-2.33
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=431E7E81-47D1-11CB-AC2A-A0190BCE89CD
  *-core
       description: Motherboard
       product: 18714AU
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: VJ0PG5AN2EY
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 70ET69WW (1.29 )
          date: 05/29/2007
          size: 144KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.86GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.13.8
          slot: None
          size: 800MHz
          capacity: 1866MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:90080000-900fffff ioport:1800(size=8) memory:b0000000-bfffffff memory:90000000-9003ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:80000000-8007ffff
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress cap_list
             configuration: latency=0
             resources: memory:d000c000-d000ffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:7000(size=4096) memory:90100000-901fffff ioport:80100000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 11
                serial: 00:10:c6:d0:fc:48
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5751m-v3.46a latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 memory:90100000-9010ffff
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:90200000-902fffff ioport:c0000000(size=1048576)
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:90040000-900403ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:3000(size=16384) memory:90300000-9fffffff ioport:c8000000(size=134217728)
           *-pcmcia
                description: CardBus bridge
                product: PCI1510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:c80000000-c7fffffff irq:16 memory:90300000-90300fff ioport:3400(size=256) ioport:3000(size=256) memory:c8000000-cbffffff memory:94000000-97ffffff
           *-network
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:04:02.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:83:6f:b5
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.2 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 memory:90301000-90301fff
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-disk
                description: ATA Disk
                product: HTS541080G9AT00
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MB4I
                serial: MPB4LAX6KLV8DM
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000004e4
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 2c0cf07a-dc3c-4e6e-ae2f-b139a5834955
                   size: 72GiB
                   capacity: 72GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2013-03-28 09:36:00 filesystem=ext4 lastmountpoint=/ modified=2013-03-28 09:46:03 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2013-03-30 02:13:47 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2037MiB
                   capacity: 2037MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2037MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: UJDA755zDVD/CDRW
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/sr0
                version: 1.20
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)

```

---

### Post by sudodus on 2013-03-31
> **OrangeCrate said:**
> Proactive advice for people who like older IBM ThinkPads...
...
**My only problem, is that I can not figure out how to get the sound working. I am suffering from the well documented "Dummy Output" issue. If anyone can supply an answer to this, it would be highly appreciated.**

The future of X/L/Ubuntu on these machines...

T42s and earlier models will not take a PAE kernel

I have used the fake-pae method for Pentium M CPUs by *7bit* according to this link

[[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2113826[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2113826")[COLOR=#ff0000]
[/COLOR]
So there seems to be a work-around to keep running the IBM ThinkPads (T41 and T42) with Ubuntu flavour pae kernels.
--
I guess the dummy output audio problem is different in T43 than I have experienced with T41 and T42 because sound is working here. Have you tried with ***pavucontrol***?

---

### Post by OrangeCrate on 2013-03-31
That's interesting about the "fake-pae" info. The next time I get a 41 or 42, I'll definitely try that...

The pavucontrol package (which is the Pulse Audio Control package) is already installed on Xubuntu 12.04.2. It's those controls that are showing the "Dummy Output" info.

Anyway, thanks for the suggestion.

---

### Post by mgwhammy on 2013-04-05
I posted this thread in the beginners section about my problem and was directed to this thread....

[COLOR=#000000]I've got an old Toshiba that ran XP poorly even after a fresh install, so I put Ubuntu 10.04 on it awhile back because it seemed to be the only distribution that properly used my sound card. After a lot of digging I've found that when the kernel went to 3.x a lot of old hardware support was dropped. One of the self-help guides posted here led me to the kernel documentation website where I found my sound card controller (ALC861-D) was no longer an option to put in the ALSA configs. ([/COLOR][https://www.kernel.org/doc/Documenta...dio-Models.txt]("https://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt")[COLOR=#000000]) [/COLOR]

[COLOR=#000000]I recently stumbled upon Lubuntu, which on the 10.04 version did not bog down my hardware at all. As much as I'd like to stick with it I want to be on something newer since there is no more desktop support forthcoming after April. I put Lubuntu 12.10 on and my hardware still rocks on it, but I knowingly have no audio now. I downloaded the 2.6.32-46 kernel and got it in GRUB as a boot option, but when I boot using it the desktop environment doesn't load and I'm left at a command prompt. I saw where I might need to re-install the desktop from the command line but it would not install since this desktop was already there. I then issued the startx command but the connection to the X server was refused and crashed.[/COLOR]

[COLOR=#000000]So far I like 12.10 and want to keep it, but I'd like to run the old kernel so I can have audio too. Is there any way to accomplish this? [/COLOR]

---

### Post by mörgæs on 2013-04-05
You seem to be getting good help in the other thread, so I'll follow another path in order not to create a duplicate.

> **mgwhammy said:**
> [COLOR=#000000]After a lot of digging I've found that when the kernel went to 3.x a lot of old hardware support was dropped. [/COLOR]

Do you have some links explaining why it was decided to drop the card?

---

### Post by sudodus on 2013-04-14
I want to share my results from testing Lubuntu Raring daily (13.04) in VirtualBox with different amount of RAM available and 512 MB swap.

[[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2135547[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2135547")

---

### Post by mörgæs on 2013-04-15
Thanks. It should help giving people realistic expectations.

---

### Post by arifalisyed on 2013-05-01
at my home I have a PC with following configuration.

a) a Interl Pentium-4 processor model no 530J, with hyper threading and   [physical address extension]("http://en.wikipedia.org/wiki/Physical_address_extension")
b) intel D915GVWB motherboard
c) 1 GB DDR1 RAM with 400 Mhz

I used Xubuntu 12.04 for almost 6-8 months... i was workifn absolutely fine.
before trying out i had also tried lubuntu/kubuntu but there were some problem with installation... so i dropped it.

X12.04 was rocking on my this old machine where Win7 never use to work properly.
when X12.10 was released I upgraded to it ... still it was ok...but little bit bigger foot print i beleive ( dont remember exactly).

In my office i have 2-3 desktops with me so i keep trying differnet OS on that , i had one of them running linux mint and otherone runnign xubuntu 12.10.
l  liked linux mint's UI green color thunar etc... and its friendlyness with windows network... it would detect other windows machine in my office network....

I decided to intall linux mint on my ancient P4 machine @ home computer.
it wasn't good at all , since my office desktops had 4GB rams and dual core/quad core it was running fine but it dint run on my P4 with 1 GB RAM.

so decided to go back to X12.10.
I moved back but then audio was not working by default ( and i dint remember if it had worked by default in X12.04 or X12.10 soon after previous installation, may even ealier i would have installed xubuntu extras) 

Now autoupdateer notidfied me that there is a X13.04 avaailable, I donwloaded X13.04 iso in office and burnt it on DVD ( from CD it became DVD, xubntu12.10 use to fit in CD) 
tried upgrading my P4 machien with 1 GB RAM , upgrade went fine until the stage called "restoring preisouly installed packages" , [I waited 4 hours in front my pc ]("https://bugs.launchpad.net/ubuntu/+source/apt-clone/+bug/1174538"), chatting on IRC ,... but it dint complete.
i then left it and next morning i saw it was completely done ...  people on IRC pointed out it ws 1GB RAM because of which it took so long in upgrade ( in that restoring stage ).

After upgrading to X13.04 with 1GB RAM my experinace wasn;t all that great , it was a bit slow, when i went to software center and I tried installing all my softwares like Childpay,Gcompri,Pre-school,primary education packs....
[sofware center hung]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1175072") , I then restarted machine and installed all softwares one by one ... ie. once one software is completly installed then browse/search and install new software...this approached worked fine... so here also the problem was 
1 GB RAM only ... with one GB RAM my sofware center  could not work , it had to use swap area, very extensively. 

After all this i went out an purchased 2  sticks of 1 GB DRR1-400 Mhz Transcend RAM.  my mother board had 4 slots for RAM, two werre already occupied by my my previous RAM 
2x512 MB Hynix DDR1-400 MB RAM, when i added two new sticks each of 1 GB from Transcend ... both hynix and Transcend dint work together.... though their frequency were same.

I then removed my 2 sticks of 512 MB RAM from Hynix, and it worked fine ... now the experinace on Xubntu 13.04 was good , it was smooth , no more swap memory usage.
but i remember having extactly  this smooth experiance with X12.04 :) with just 1 GB RAM.

So I would want to move back to Xubuntu 12.04, and would stick to it until its support is over ( i guess April 2015) , but then I need to spend aain 8-1015 hours on installations...
first install OS then installed configured software...move data ... all this takes time... but i think i will still have to take out time and do it ...cause xubuntu 13.04 is unstable in my opinion lot of isssues
 i am reporting them one by one so that it can improve. now also i see some issue when click the xubuntu menu in top-left and go to systems... there some paininting issues menus are not drawn correctly...
but all this will stablize in 2-3 months i belive with updates...

so my take for all   [COLOR=#008000][SIZE=5]PCs with Pentium-4 and 1 GB RAM go for Xubuntu 12.04.
[/SIZE][/COLOR]its still best when compare to Xubuntu 12.10 and Xubuntu 13.04 and Linux Mint 14. 

Linux Mint 14, Xubuntu 12.10 both had almost equal foot print of 140 MB after boot, and around 40 user processes running.
I dont remember how much was the foot print of Xubuntu 12.04 after boot, if somebody remember please tell me.
I will update the memory footprint of Xubuntu 13.04  after posting this message and rebooting..
 

below is my hardware details...


[http://goo.gl/3UH4w](http://goo.gl/3UH4w)

[ATTACH]242044[/ATTACH]

---

### Post by arifalisyed on 2013-05-01
Here is performance statistic of Xubuntu 13.04

From Grub it loads in 28 seconds ( while Xubutu 12.10 use to load in 32 seconds, dont remember how was Xubuntu 12.04) 
From Grub when you hit enter ,for 19 seconds is a blank screen, after that Xubuntu screen is shown and it loads in 8-9 seconds after that.

Soon after booting  memory usage are around 160MB ( while  linux mint nad Xubuntu were around 140 MB, dont remember foot print of X12.04, if anyone know please put here) 
around 38 user processes are running and around 140+ total process.

---

### Post by sudodus on 2013-05-01
Thanks for sharing your experience,[COLOR=#000000] arifalisyed[/COLOR] :-)
                        
I agree that is is often a good idea to run an LTS version, in this case Xubuntu 12.04 LTS. The only exceptions are

- if you have new hardware, that the aging LTS version "doesn't know about"
- if you want the bleeding edge features of the software packages

but these exceptions are rather common ;-)

---

### Post by sudodus on 2013-05-08
[SIZE=6]Lubuntu-fake-PAE[/SIZE]

Hello all Pentium M users,

Please visit the wiki page  [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)  and tell me what you think.

*Edit*: The detailed instructions also reside at the Ubuntu wiki and are easily available from the page above. There is a new GUI method to install directly from Windows.

---

### Post by sudodus on 2013-05-09
We have issued this poll in order to know how  much effort to focus on the Pentium M problems with PAE kernels.

[http://ubuntuforums.org/showthread.php?t=2143502](http://ubuntuforums.org/showthread.php?t=2143502)

---

### Post by sudodus on 2013-06-06
I have improved the security of Lubuntu-fake-PAE referring to an Ubuntu Forum tutorial, that should be hard to edit by others than myself and trusted forum administrators. See this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE#Checksums_and_signature](https://help.ubuntu.com/community/Lubuntu-fake-PAE#Checksums_and_signature)

and its link to the tutorial

[http://ubuntuforums.org/showthread.php?t=2151890](http://ubuntuforums.org/showthread.php?t=2151890)

---

### Post by sudodus on 2013-08-26
[SIZE=4]Comparing versions of Lubuntu and Ubuntu and LXLE[/SIZE] 

I made a comparing test in my IBM Thinkpad T42 that is close to ten years old. The ***time to boot and RAM used*** (idling right after boot) were compared between several versions of Ubuntu.

The result of the test is shown in the attached pdf file.

*Lubuntu 10.04* is fastest. But it is not much faster than *Lubuntu 12.04*. The difference is so small, that I did not notice it before I started measuring:

39 seconds for 10.04
43 seconds for 12.04

I booted at least twice after installation, for things to settle (which makes it faster, and makes it use less RAM).

But there is a bigger difference in RAM usage.

 71 MB for 10.04
109 MB for 12.04

This makes a clear advantage for Lubuntu 10.04 in computers with low RAM.

*Lubuntu 13.04 (Raring) and 13.10 (Saucy)* are slower, and as you can see, *Precise Gnome Classic Tweaks* compares rather well speed-wise, but not as well RAM-wise. So if there is enough RAM, Precise Gnome Classic Tweaks is a good alternative.

*LXLE and Lubuntu 13.10 (Saucy)* are slow starters but need not too much RAM. I think they are also good alternatives for low RAM computers. I expect better results with drivers for old hardware with LXLE, on par with Lubuntu 12.04 (LXLE is a tweaked and remastered flavour of 12.04).

-o-

I have not tested the performance with different software packages. That would take the comparison too far.

-o-

[SIZE=4]Concluding tips for Lubuntu users with old hardware[/SIZE]

***Lubuntu 12.04:***

If you have problems with hardware drivers in the newer versions, you can consider switching from Lubuntu 12.04 to *Precise Gnome Classic Tweaks* or *LXLE* at the end of life in October 2013 (or as soon as possible after that date). These two alternatives have LTS (long time support) until April 2017.

 *Xubuntu 12.04 LTS* with end of life in April 2015 is also a good alternative.

***Lubuntu 10.04 & 12.04:***

Maybe you can consider to switch from Lubuntu 10.04 to 12.04 in order to get two years newer software (and less risk for security holes). But beware, the Lubuntu specific program packages have no security updates in 12.04.

***Openbox***

When you want something very lean, you can use the Openbox window manager, that you can select from the login screen (of Lubuntu 12.04). You get a grey screen without any panel. Right-click to get a small menu. Select browser or terminal window. You can run 'everything' from the terminal window, and it uses less horsepower and RAM for eye-candy.

Most programs under the hood have LTS. I don't know but I think also Openbox has it, because it is part of 'Kubuntu light' with LTS. But many of the other Lubuntu-specific desktop packages have not LTS.

---

### Post by sudodus on 2013-09-07
There is a new alternative to install Ubuntu based operating systems  into computers of various age and kind, the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), the 'OBI'.

The OBI is designed to be easy to use and have a very small foot-print  and uses only standard programs and shell-scripts in text mode.  Installed 32-bit operating systems with non-PAE kernels or fake-PAE are portable between  many computers, and they are stored in compressed tar archive files, ***tarballs***.

```

bodhi-230-nonpae.tar.xz
GnomeClassic1204-oem.tar.xz
GnomeClassic1204.tar.xz
Kubuntu_13.10oem-nov23.tar.xz
KubuntuPrecise.tar.xz
lubuntu-10.04.tar.gz
Lubuntu_13.04sep1.tar.xz
Lubuntu_13.10oct18-tweaked.tar.xz
Lubuntu_13.10oct30.tar.xz
Lubuntu_13.10oem-oct28-tweaked.tar.xz
Lubuntu_13.10oem-oct30.tar.xz
LubuntuCoreSaucy.tar.xz
lxle-2013-08-19.tar.xz
OBI_noswap_07.tar.gz
OBI_noswap_10.tar.xz
OBI_noswap_11.tar.xz
OBI_noswap_12.tar.xz
[COLOR=#800080]OBI_noswap_21-rc.tar.xz[/COLOR]
ubuntu-10.04.tar.gz
Ubuntu_13.10oem-nov22.tar.xz
Ubuntu_Gnome_13.10oem-nov25.tar.xz
Xubuntu_13.10oem-nov22.tar.xz
xubuntu-precise.tar.xz

```

The OBI helps you make such a tarball of your own system and use it as a backup or to port the system to another computer.

---

### Post by sudodus on 2013-11-12
If you are interested in this thread, you might also be interested in a thread about [Light Linux Distributions - Hardware Testing (RAM)]("http://ubuntuforums.org/showthread.php?t=1582027")

---

### Post by sudodus on 2014-02-03
[SIZE=4]Brief general tips for old hardware[/SIZE]

An old computer often runs really well with Lubuntu, while standard Ubuntu with the desktop  environment Unity will make it slow. If you want some more (or other)  bells and whistles compared to Lubuntu, you can try Xubuntu or some  other flavour, re-spin or distro based on the Ubuntu engine but a  different desktop environment (different look, different set of  programs).

Different versions, ***12.04 LTS***, ***13.10*** and Trusty Tahr to become ***14.04 LTS***, have different drivers for hardware. You need trial and error to find out which one works best with the hardware of your particular computer. Often, but not always, an ageing long time support version (LTS) is better for old hardware.

***Lubuntu*** has the ultra-light desktop environment LXDE. The only current versions are 13.10 (until July 2014) and 14.04 LTS until April 2017.
***Xubuntu*** has the light desktop environment XFCE, and there is a long time  support version until April 2015, Xubuntu 12.04 LTS, not only 13.10 (until July 2014) and 14.04 LTS until April 2017.
***LXLE*** has the ultra-light desktop environment LXDE. The current version is 12.04 LTS with support until April 2017.
***Bento*** and ***Bodhi*** are other re-spins slightly farther away but still based on Ubuntu 12.04 LTS with support until April 2017.
***Precise Gnome Classic Tweaks*** is 'Ubuntu tweaked', so that it is using a basic and light-weight gnome desktop instead of Unity. supported until April 2017.

I can recommend all these for old computers. Among those that work with your computer it is a matter of taste, which one of them you prefer.

---

### Post by eric152 on 2014-02-26
I've tried Lubuntu 13.04 and later upgraded to 13.10 on my monther computer built on a Athlon XP with a Geforce2 MX and 2 GB of RAM. The installation was very easy, fast and run up much faster than Windows XP. 
Unfortunately, the "nouveau" driver is too buggy so the whole is not usable. So I should use the proprietary driver. The nvidia-96xx supports only up to Xorg 1.12, the Lubuntu 13.04 and later are based on Xorg 1.13 or later so will not fit. I probably have to go back to a 12.04 LTS distribution.

Since support is important, I only consider the LTS, so I was thinking about Ubuntu 12.04 LTS with LXDE instead of Unity, but know I learn from LXLE exactly, which seems to be THE one I should use!
What I don't really get is: LXDE is baded on Lubuntu; Lubtunu is not supported, but LXDE still get the full LTS of Ubuntu ?!

---

### Post by sudodus on 2014-02-26
> **eric152 said:**
> ...
What I don't really get is: LXDE is baded on Lubuntu; Lubtunu is not supported, but LXDE still get the full LTS of Ubuntu ?!

Well except for the Lubuntu specific packages version 12.04 has long time support. It is the responsibility of the people who develop and maintain LXLE to support the other program packages. I think this includes checking for upstream updates (security fixes and bug-fixes) and replacing packages that are abandoned if that would be necessary.

---

### Post by mörgæs on 2014-02-27
If you want something 12.04-based I would say that Bodhi is a better choice. Lubuntu 12.04 wasn't a good vintage and we should let it rest, not try to extend the use.

If you can get a better graphics card it will make a big difference.

---

### Post by Terry Maker on 2014-03-11
Hi All! 

I don't know if this is the right thread to be posting this on, but here goes. 

I an running, as an experiment, a very old Clevo 5100s, (550 Mhz, MMX, 30Gb HDD 512K memory), on Ubuntu Karmic Koala. The strange part, is that ONLY Karmic will run on this machine, everything else crashes, and fails to operate past the password sign in. 

On Karmic, I've managed to source, and load, some very basic use programs, (Scite, and Tweak), but Google chrome fails every time, with an error message, (Which I think is due to all the Karmic repositories being closed), BUT! In general the system works well! I have used gnome panel, to create a "autohide 'dock' menu", and Tweak just to change the login screen.

But I'm left with two questions that bug me 1, Why only Karmic? and 2. Why doesn't Google Chrome install correctly?

Any Ideas anyone!

PS: the software loads fail on all the "normal" methods of installation,  "sudo dpkg -i" Synaptic, and Gdeb installer. 

Terry

---

### Post by mörgæs on 2014-03-11
Please read post 2 before posting.

---

### Post by sudodus on 2014-03-12
> **Terry Maker said:**
> Hi All! 

I don't know if this is the right thread to be posting this on, but here goes. 

I an running, as an experiment, a very old Clevo 5100s, (550 Mhz, MMX, 30Gb HDD 512K memory), on Ubuntu Karmic Koala. The strange part, is that ONLY Karmic will run on this machine, everything else crashes, and fails to operate past the password sign in. 

- Do you get good graphics at the log in screen also with other flavours of Ubuntu or other linux distros? Which ones have you tried?

- If if crashes at/directly after login, some driver starting at that time could be causing the problem, for example the network driver.
> 
On Karmic, I've managed to source, and load, some very basic use programs, (Scite, and Tweak), but Google chrome fails every time, with an error message, (Which I think is due to all the Karmic repositories being closed), BUT! In general the system works well! I have used gnome panel, to create a "autohide 'dock' menu", and Tweak just to change the login screen.

But I'm left with two questions that bug me 1, Why only Karmic? and 2. Why doesn't Google Chrome install correctly?

Any Ideas anyone!

PS: the software loads fail on all the "normal" methods of installation,  "sudo dpkg -i" Synaptic, and Gdeb installer. 

Terry

It is OK for an experiment to run a version past end of life, but be aware, that Karmic has not received any security updates for years, so it is vulnerable to attacks via the internet.

I think that such an old computer might work better with some light or ultra-light linux distro. My personal experience is that ***Knoppix*** is often good at recognizing old hardware. There are some tips in the first post of this thread and a list of light distros in the following link (it is a bit dated, but there are new versions of many of the listed distros).

[URL="http://ubuntuforums.org/showthread.php?t=1582027"]http://ubuntuforums.org/showthread.php?t=1582027


[/URL]

---

### Post by Terry Maker on 2014-03-18
The graphics at the login screen look quite normal, and all of the graphics during the install, are what I would expect. 

I have tried Lucid Lynx, and Maverick Meerkat, and Lubuntu, all with the same results. 

The problem is, as you rightly say, these distro's are all old, and 'at risk'. 

I've never tried Knoppix, maybe I'll give that a try! 

Thanks for the 'heads up'. I agree that it wouldn't be wise to run this set up as a going computer, and it will be always an experiment, but it's nice to know that it Works! The technology is 1996 Vintage and I didn't think it would work at all, let alone having gripes about single programs not loading!

Regards

Terry

---

### Post by sudodus on 2014-03-18
You can try to install minimal versions of the latest and greatest  Ubuntu Trusty with the experimental Debian based installer 9w. You get instructions  and tips at this link, post #88 and forward

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

and you can download it at this link

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

---

### Post by eric13 on 2014-03-21
> **mörgæs said:**
> If you want something 12.04-based I would say that Bodhi is a better choice. Lubuntu 12.04 wasn't a good vintage and we should let it rest, not try to extend the use.

Why do you say Lubuntu 12.04 was not a good vintage? What's wrong there?

I just tried Bodhi and LXLE on VirtualBox, and LXLE seems to be much easier for a Windows XP user, and ready to be used with so many packages pre installed (LibreOffice, etc)!

---

### Post by mörgæs on 2014-03-21
A lot of applications in 12.04 (pcmanfm, guvcview, file-roller, gpicview, lxkeymap, gnome-mplayer and more) were buggy and the bugs were not solved until a later release. 

Lubuntu 13.10 is a significant step in the right direction. I suggest that you try this one for comparison, or test 14.04, which is coming along really good. Everything 12.04-based will lose its mojo anyway in a month or two, when 14.04 is getting traction. At that time 12.04 will mainly be used for special hardware which is unsupported in 14.04.

---

### Post by eric13 on 2014-03-22
On my laptop, I just installed both Bodhi and LXLE in their current 32 bits versions, both based on Ubuntu 12.04 LTS because I will need Xorg <= 1.12 when I need to install it on the target PC from 2002 (of my parents)! The laptop is just for testing!

Some feedback:
- linux kernel: Bodhi 3.8.x with PAE support vs LXLE on 3.2.x without PAE (my 4GB of my laptop are only recognized in Bodhi)
- RAM use on start: Bodhi desktop profile 335 MB vs LXLE 100 MB (Enlightenment vs LXLE)
- HDD use on basic install: Bodhi: 1,5 GB vs LXLE 4,2 GB. Bodhi comes almost naked: every thing has to be installed.

Lubutu / LXLE is much user friendly and much easier for a move from Windows XP (with the default XP paradigm profile). I got lost in the menu structure of Bodhi. But I have to admit that Bodhi is "nicer", fancier.

Indeed, even with latest updates, the core components of LXLE are still the one from the Lubuntu 12.04: too bad that newer package are not "back ported". And with the 14.04 coming next, it is quite unlikely to happen...
I might however stay with this one, if I don't find a better graphic card (by the way, "screen card" is quite unusual term, isn't it?)

I read again your first post, I suppose you will have to do some update, but might be worth to wait for Lubuntu 14.04 LTS which would become the main recommendation for most of cases ;)

---

### Post by ronniew on 2014-03-22
You better check again, the lxde core components in lxle have been updated. They are not the stock components that come with the standard lubuntu 12.04  the 3.2 kernel is stuck with for a reason. Perhaps read the release notes... [http://lxle.net/articles/?post=lxle-12044-officially-released](http://lxle.net/articles/?post=lxle-12044-officially-released)

---

### Post by eric13 on 2014-03-23
thanks for the link I missed before and some info I could grab there.
I just got a little confused with the versions of PCManFM: 1.01 on LXLE  12.04.4 (distribution update published 1 month ago!) : I though it was the  initial one from Lubuntu 12.04, but reading again [http://blog.lxde.org/?cat=28](http://blog.lxde.org/?cat=28), version 1.0  was out in August 2012, so obviously AFTER the release of Lubuntu  12.04!
Lubuntu 13.04 spotted v1.1.0 and I suppose version 1.2.0 would be included in Lubuntu 14.04.

I wonder how many bugs mörgæs was mentioning got fixed in LXLE 12.04.4.
The inital post with "Sometimes Lubuntu 12.04 is recommended, which is very unfortunate." is indeed quite a bad advertisement for LXLE. 

It might be interesting to check that that again. And maybe the sentence would soon be updated by something like "get Lubuntu 14.04 LTS, or if your  hardware needs an older version (e.g. NV10 or NV20 graphic cards family),  check LXLE 12.04.4! Bodhi 2.4. might be a good alternative but with a different paradigm (naked distribution: you choose the app you want to have!)"

If it is like that, it comforts me that LXLE might well be my best choice for my old parent's computer (Windows XP on Athlon XP)! I will then just have to install the old nvidia proprietary drivers (limited to xorg 1.12) and do the trick with the flash plugin not supporting SSE2!

---

### Post by sudodus on 2014-03-24
> **eric13 said:**
> ...
I wonder how many bugs mörgæs was mentioning got fixed in LXLE 12.04.4.
The inital post with "Sometimes Lubuntu 12.04 is recommended, which is very unfortunate." is indeed quite a bad advertisement for LXLE. 

I think Ubuntu 12.04.4 is quite debugged and polished, which makes the flavours and re-spins based on this point release quite good :-)
> 
If it is like that, it comforts me that LXLE might well be my best choice for my old parent's computer (Windows XP on Athlon XP)! I will then just have to install the old nvidia proprietary drivers (limited to xorg 1.12) and do the trick with the flash plugin not supporting SSE2!

If you backup the original system (for example make an image with Clonezilla), you have peace of mind while trying, at first live, then installing and tweaking. I think you have a good chance to get a nice LXLE system for your parents. *Kansasnoob*'s [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks") is another good alternative with support until April 2017.

---

### Post by mörgæs on 2014-03-24
Corrections and suggestions are welcome. A guide must be evolving like the software it describes.

"Screen card" is a direct translation of what we use in Icelandic. I didn't know it sounded strange in English, but it's changed now. 

The warning was mostly about Lubuntu 12.04 itself. Have added a link to LXLE so people have an option more to choose from. 

I'm not going to recommend 14.04 broadly before it's mature. Stability first. When 14.04 has been out for some weeks and everything has settled it will of course take 13.10's place (I am using it now on my test rig with good results). Only the PAE case is so special that it warrants sending users to a beta release.

Ubuntu 12.04.4 is in a good shape and a fine choice for newer (but not brand-new) computers, if one likes the interface. There are simply more work hours being put into Unity than LXDE. 

If more suggestions pop up feel free to post them.

---

### Post by Nopposan on 2014-03-25
I agree that XFCE is more middle-weight these days; one of the issues is that, although it's modular, the available extras are very tempting and available to install (or uninstall) as one task. There are many computers that will not run any faster with XFCE+extras than they do with Gnome3. So, although I love XFCE, it's not suitable for the old hardware we're targeting at the not-for-profit refurbisher where I volunteer.

Unfortunately, at this time, neither is LXLE. It would probably run well, once installed, but it doesn't come with an alternaive installer from Ubuntu's Ubiquity installer; therefore, it will not install on machines with 256MB or less RAM. Now, I agree that 256MB is an absolute minimum, but we don't have the option of putting more RAM in these old laptops; we're just trying to keep them out of the landfill for another couple of years. It's true that we'll probably be getting more computers sporting greater specs, but that doesn't mean we won't still have takers for the older notebooks if we're able to revive them. As we're dealing with notebook computers, we may have our share of Pentium M's too.

We were looking to install Lubuntu with 12.04 as I thought that would be equivalent to LXLE, but now I read in your post that it isn't. That's quite a disappointment as I was already finished configuring it for testing by our volunteer staff and getting ready to start cloning. I will try Bodhi Linux. However there are other options.

For example, what do you all think about installing Debian Stable with backports and LXDE+lightdm? I'm concerned that Debian Testing will involve too many updates and will have annoying bugs that will leave our end-users with a bad taste in their mouths, spoiling their opinion of Linux. I also don't think they're going to want to upgrade or reinstall every nine months. I tried multiple times to install Debian via the network though, and for some reason my network connection kept dropping and the install kept halting without error messages; I may be able to work around the problem, but only if I really feel it's worth it.

I've already rejected Knoppix as its default configuration will feel very odd to our end users, and as it looks difficult to completely rearrange, but it installs very easily. I'm sure I could tweak it, but, again, only if it really is worthwhile.

Please give us your best advice. This is an exciting project for me as the refurbisher whom I'm volunteering for always rejected my proposals of installing Linux in the past; the death knell of Windows XP seems to be their motivator. I want to give them impressive results. Fast installs, fast clones, easy-to-use system, happy end-users who don't come back with too many questions . . .

Thanks.

---

### Post by ibjsb4 on 2014-03-25
It is rumored that Lubuntu 14.04 will be an LTS release.

Could you use the mini.iso and install 13.10?

Another possibility would be to install Lubuntu-core and add necessary packages.

[http://packages.ubuntu.com/saucy/lubuntu-desktop](http://packages.ubuntu.com/saucy/lubuntu-desktop)

[http://packages.ubuntu.com/saucy/lubuntu-core](http://packages.ubuntu.com/saucy/lubuntu-core)

Other options would be DSL or Puppy Linux.

---

### Post by fantab on 2014-03-25
Give [Knoppix]("http://www.knopper.net/knoppix/index-en.html") a try, and don't miss out its '[cheat sheet]("http://knoppix.net/wiki/Cheat_Codes")'.

---

### Post by mörgæs on 2014-03-25
What about giving them Lubuntu 13.10 now with a free install of 14.04 (in May/June) included?

---

### Post by Nopposan on 2014-03-25
Thanks for your suggestions.

Actually, what I think I'll do is test Lubuntu 14.04 beta, tweak and write scripts for automating tweaks, play around with cloning via fsarchiver, then upgrade my test machine to the official release when it happens mid-April, then reiterate with corrections from what I've learned.

Does that sound like a good plan? Would I be better off experimenting with 13.10 and then upgrading to 14.04 LTS in April? I really don't see anything preferable to Lubuntu LTS at this time. I could play around with Debian Stable with backports running LXDE and lightdm, but it will take more time to configure it for newbies, and the Ubuntu community is thought to be a more friendly place for newbies anyway. (I hazard to guess that most people on the Debian forums will agree that Ubuntu is better for newbs.) Besides I encountered unusual difficulties with my Debian install getting permanently stuck after network detection.

---

### Post by sudodus on 2014-03-26
@*Nopposan*,

You can try the 9w debian installer and install Lubuntu Core Trusty with a non-pae kernel. It is made for very old computers. See this link (posts #88 and #89 and following)

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

and this link to the download site

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

Try any of the iso files, but maybe this one will be best for your particular task to revive old computers

[http://phillw.net/isos/linux-tools/9w/TrustyB1npae-LubuCore.iso](http://phillw.net/isos/linux-tools/9w/TrustyB1npae-LubuCore.iso)

---

### Post by eric13 on 2014-04-11
> **Nopposan said:**
> Unfortunately, at this time, neither is LXLE. It would probably run well, once installed, but it doesn't come with an alternaive installer from Ubuntu's Ubiquity installer; therefore, it will not install on machines with 256MB or less RAM. 
Indeed, the installer does not work on a test VM if I set only 256MB of RAM. Too bad they did not include the alternative installer!

I just read about Zion OS 6.2 Lite, another distrib based on Lubutu 12.04 with LTS (and thus supported until 2017, though I could not find any clear statement on the website) [http://zorin-os.com](http://zorin-os.com)
I haven't tried yet, but it looks actually very good! The Lite version is supposed to run fine with only 128 MB or RAM and 266 MHz x86 processor!!
EDIT: tested on a VM, livecd then install ok with 256MB RAM. With 128 MB RAM, it did not advance so shut it down.

---

### Post by bjje on 2014-04-14
I'm not sure that I understand the difference between installing ubuntu and loading LXDE as a package later, choosing it on login. Just packages they come with or more under the hood?
I've got 14.04b on an old machine this week and with LXDE it's working great. Unity not so much.

---

### Post by sudodus on 2014-04-14
You can install a minimal system from the Ubuntu mini.iso and add LXDE. It will give you a very light system, where you can add whatever mixture of programs, that you prefer, and avoid programs, that you won't use anyway. The developer of Lubuntu has done that job for you and offers a standard environment with LXDE and a mixture of programs plus some tweaking.

If you start with standard Ubuntu  and add LXDE the Ubuntu desktop environment, Unity, and the standard Ubuntu mixture of programs will stay there. You will be able to select either of the desktops at the log in screen. This is possible, and some people have such a system, and accept or even prefer to have double sets of software for some tasks.

Lubuntu has LXDE - ultra-light desktop environment
Xubuntu has XFCE - medium light desktop environment
Ubuntu has Unity - fancy but heavy desktop environment
Kubuntu has KDE - fancy but heavy desktop environment

The engine under the hood is the same in all these flavours, and there are some differences in the choice of application programs.

---

### Post by sudodus on 2014-05-07
The following link has a lot of good tips about what to consider and ask for when converting a Windows computer to linux.

[http://ubuntuforums.org/showthread.php?t=2221161&page=2&p=13016261#post13016261](http://ubuntuforums.org/showthread.php?t=2221161&page=2&p=13016261#post13016261)

---

### Post by eric13 on 2014-05-24
For a early Athlon64 3200+ with 2 GB or RAM, I still plan to install Lubuntu14.4 LTS
Do you recommend the 64 bits or 32 bits variant?
As I have enough RAM, I tend to the 64bits one: nowadays, I think that most people do use the 64bits, and thus, these program are better tested and supported. What do you think?

For those hesitating between different distributions, I just tried the multicd script ( [http://multicd.tuxfamily.org/index.html](http://multicd.tuxfamily.org/index.html) ) so that I can put 5 live cd on the same iso (which I will put on a usb HDD). Pretty handy! Don't forget to rename the Ubuntu derivatives (e.g. LXLE or Bodhi) to xxx.ubuntu.iso so that the script can handle them!

---

### Post by sudodus on 2014-05-24
Both 32 bits and 64 bits should work well. The 64-bit system will use more RAM for the same tasks, but should be faster. I don't know for such an old 64-bit system if there will be regressions. In other words, I can't really tell, please try both and compare :-)

---

### Post by ibjsb4 on 2014-05-24
You should be good with 64bit.  If you do run out of ram, your system will use your swap partition.  If this happens, you will see an overall system slowdown as swap is way slower than ram.  But with 2G, I'm thinking your good.

I have 4G ram and run 32bit, but this is because I run some software that eats up my ram and I try to stretch it out (32bit will use less). And still on rare occasion I have ran this into swap.  About 64bit being faster, that also depends on the software you run and find it not to be a concern for me.

---

### Post by mörgæs on 2014-05-24
If performance and swap usage is a problem then you could take a look at post #2.

---

### Post by eric13 on 2014-06-03
> **sudodus said:**
> The 64-bit system will use more RAM for the same tasks, but should be faster.

Indeed, the 64bits takes 35% more RAM just on start! I am surprised that is that much!

I started the live CD of different distribution to give an idea of the RAM usage. CD Started on a Virtual Machine with 1 GB of RAM (tried both under Virtualbox in Debian and HyperV in Windows 8.1, they give similar results).
The RAM used on start is the one seen in "Task Manager" or with "free -m", considering the 2nd line '-/+ buffers/cache' under 'used'
[TABLE="width: 500"]
[TR]
[TD]Distrib[/TD]
[TD]archi[/TD]
[TD]kernel[/TD]
[TD]RAM on start in MB[/TD]
[/TR]
[TR]
[TD]Debian Live LXDE
[/TD]
[TD]i686[/TD]
[TD]3.2[/TD]
[TD]100[/TD]
[/TR]
[TR]
[TD]Bodhi[/TD]
[TD]i686[/TD]
[TD]3.8[/TD]
[TD]110[/TD]
[/TR]
[TR]
[TD]LXLE  12.04.4[/TD]
[TD]i686[/TD]
[TD]3.2[/TD]
[TD]125[/TD]
[/TR]
[TR]
[TD]Lubuntu 14.04[/TD]
[TD]i686[/TD]
[TD]3.13[/TD]
[TD]155[/TD]
[/TR]
[TR]
[TD]Lubuntu 14.04[/TD]
[TD]x86_64[/TD]
[TD]3.13[/TD]
[TD]210[/TD]
[/TR]
[TR]
[TD]Mint 17 MATE[/TD]
[TD]x86_64[/TD]
[TD]3.13[/TD]
[TD]400[/TD]
[/TR]
[TR]
[TD]Ubuntu 14.04[/TD]
[TD]x86_64[/TD]
[TD]3.13[/TD]
[TD]630[/TD]
[/TR]
[/TABLE]

Ubuntu as live CD under HyperV is so slow and almost unusable. All other reacts quite fast, especially the LXLE variants. Bodhi and LXLE are based on Ubuntu 12.04 LTS ; Mint 17 is based on Ubuntu 14.04

---

### Post by sudodus on 2014-06-04
Thanks for sharing your test results :-)

You wrote Debian Live LX**L**E. Do you mean Debian Live LX**D**E?

---

### Post by JLUbunt on 2014-06-09
Hello I have an Acorn Aspire 1 netbook, with 1 Gig of RAM,  and have just put Lubuntu 14.04 LS on to it. It works well. Just wondered if Lubuntu can do the same trick as Windows 7 where a fast SD card, Scan Disc Ultra, can be used as memory. Thought this might to make it a bit faster. Is it possible? Any ideas would be appreciated. 
I've noticed that Lubuntu does not have Calibre in its list of software but is in Ubuntu. I expect I'd need to learn how to install it if I want to try it.
Thanks for  all the advice.

---

### Post by mörgæs on 2014-06-09
You're welcome, please distribute.

Like most other packages the install is simply
```
sudo apt-get install calibre
```

I don't know how to enable the SD card.

---

### Post by famewolf on 2014-06-10
> **eric13 said:**
> Indeed, the installer does not work on a test VM if I set only 256MB of RAM. Too bad they did not include the alternative installer!

I just read about Zion OS 6.2 Lite, another distrib based on Lubutu 12.04 with LTS (and thus supported until 2017, though I could not find any clear statement on the website) [http://zorin-os.com](http://zorin-os.com)
I haven't tried yet, but it looks actually very good! The Lite version is supposed to run fine with only 128 MB or RAM and 266 MHz x86 processor!!
EDIT: tested on a VM, livecd then install ok with 256MB RAM. With 128 MB RAM, it did not advance so shut it down.


If you can manage to swap the hard drive and do the install on another device lxle will indeed run ok in 256mb....I had to do so for some inspiron 4000 laptops because the installer crashes.

---

### Post by famewolf on 2014-06-10
> **JLUbunt said:**
> Hello I have an Acorn Aspire 1 netbook, with 1 Gig of RAM,  and have just put Lubuntu 14.04 LS on to it. It works well. Just wondered if Lubuntu can do the same trick as Windows 7 where a fast SD card, Scan Disc Ultra, can be used as memory. Thought this might to make it a bit faster. Is it possible? Any ideas would be appreciated. 
I've noticed that Lubuntu does not have Calibre in its list of software but is in Ubuntu. I expect I'd need to learn how to install it if I want to try it.
Thanks for  all the advice.


If all else fails you can use the generic linux install [cut/paste to command line or save as "calupdate" and chmod 755 it to make it executable as it can also be used for future upgrades]:

```

sudo python -c "import sys; py3 = sys.version_info[0] > 2; u = __import__('urllib.request' if py3 else 'urllib', fromlist=1); 
exec(u.urlopen('http://status.calibre-ebook.com/linux_installer').read()); main(install_dir='/opt')"

```

---

### Post by eric13 on 2014-06-16
I came a few times on that topic to prepare the install of the 12y old PC of my Dad.
I initially though to install a LXDE variant on 12.04 LTS because of issue with VGA driver (GF4 inside), but found purely by chance a GeforceFX 5200 AGP for 4&#8364; on the bric a brac market when I was there to find a bike for a friend 2 weeks ago.
So I could successfully install Lubuntu 14.04 LTS 32 bits on that old Athlon XP PC. 
I repeat the install on a 8y old Athlon64 PC of another senior few days later, this time Lubuntu 14.04 64bits since I gave him my unused 2GB of DDR2 RAM.
So both PC got migrated from Windows XP to Lubuntu, and so far, I got good feedback that their computer is faster. Wonder how good they will use it on a daily basis, but it is a good start!

---

### Post by sudodus on 2014-06-17
> **eric13 said:**
> I came a few times on that topic to prepare the install of the 12y old PC of my Dad.
I initially though to install a LXDE variant on 12.04 LTS because of issue with VGA driver (GF4 inside), but found purely by chance a GeforceFX 5200 AGP for 4€ on the bric a brac market when I was there to find a bike for a friend 2 weeks ago.
So I could successfully install Lubuntu 14.04 LTS 32 bits on that old Athlon XP PC. 
I repeat the install on a 8y old Athlon64 PC of another senior few days later, this time Lubuntu 14.04 64bits since I gave him my unused 2GB of DDR2 RAM.
So both PC got migrated from Windows XP to Lubuntu, and so far, I got good feedback that their computer is faster. Wonder how good they will use it on a daily basis, but it is a good start!

Thanks for sharing this success story :-)

---

### Post by JLUbunt on 2014-06-28
Thanks
I'll have a go this week.

---

### Post by wandalalakers on 2014-07-27
The only thing that frustrates me about bringing old hardware back to life is family members who don't understand linux and complain.  I put linux on two old desktops for family members and ended up putting XP back on their desktops.

---

### Post by mörgæs on 2014-07-28
Often teaching people and helping them to overcome their fear is the biggest task. Could take several weeks after the install.

---

### Post by charitosha on 2014-09-03
Hello, 
There is an old acer laptop, travelmate 251lc_dt.
It has pentium 4 at 2,5 GHz, Intel 82852/855GM, and 512 Mb of RAM. It runs Lubuntu 14.04.1 LTS. It runs fast I can have multiple windows on both "desktops" even with miltiple tabs on firefox on both "desktops". Only one thing  spoils it, It cannot play youtube videos at all! I mean it has good cpu with good amount of ram.
I get this pop-up every time i try to play a video on youtube:
```

A script on this page may be busy, or it may have stopped responding. You can stop the script now, or you can continue to see if the script will complete.

Script: http://s.ytimg.com/yts/jsbin/www-en_US-vfl8O7vjo/base.js:23
```
To be honest i think i made it worse when i did:
```
sudo apt-get install zram-config
```
I'm saying this because prior to that i could play youtube videos but not in fullscreen.
Any suggestions???

---

### Post by sudodus on 2014-09-03
It may be hard to play video with only 512 MB RAM. So I think you cannot expect more performance than you had without zram. I suggest that you remove zram, as it obviouly caused problems for you.

```
sudo apt-get remove zram-config
``` and try again.

The best solution would be to add RAM, at least another 512 MB, but the computer would work even better with another 1 MB. I have an old IBM Thinkpad T42 with Pentium M and 1.25 GB (1280 MB) RAM, and it works reasonably well, but it is not playing any high resolution video (the CPU is too slow and there is no advanced graphics chip).

---

### Post by charitosha on 2014-09-03
after removing zram i was able to watch youtube videos again (without sound letancy) at the small window of course.
Being unable to watch it fullscreen i think it's the graphics chip fault, since task manager shows that only half of the ram available is being used...

P.S. what the difference of zram compared to a swap partition?

---

### Post by sudodus on 2014-09-03
See this link

[https://en.wikipedia.org/wiki/Zram](https://en.wikipedia.org/wiki/Zram)

---

### Post by mörgæs on 2014-09-03
Changing swap settings is only relevant if one sees a lot of hard disk activity. If something else than the hard disk is the bottleneck the settings can be left as they are.

---

### Post by charitosha on 2014-09-04
Simply want to add that youtube videos played much better (they even played on fullscreen) after install intel graphics drivers for linux.
it took big amount of time to update, but after reboot the difference was very noticable.

---

### Post by sudodus on 2014-09-04
> **charitosha said:**
> Simply want to add that youtube videos played much better (they even played on fullscreen) after install intel graphics drivers for linux.
it took big amount of time to update, but after reboot the difference was very noticable.

Please describe which driver you installed, and where you found it :-)

---

### Post by charitosha on 2014-09-05
Basically there is this thing called Intel Graphics Drivers for Linux*, here's the link:[https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=13815](https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=13815)

However, although videos were able to be played in fullscreen, i don't think it's possible to play them beyong 480p, at least on my old acer.

update, 07/09. i just streamed and watch a movie in hd with no sound lag

---

### Post by sudodus on 2014-09-05
Thanks for sharing *charitosha* :KS

---

### Post by mörgæs on 2014-10-29
The original post (or posts, four of them) have been edited many times now. 

I think it's time for asking for a review, please. Anything missing / should be deleted / unclear / ... ?

---

### Post by sudodus on 2014-10-30
Thank you *mörgæs* for a very good update of the first few posts in this thread :-)

I have only a few minor suggestions. (You can remove this post afterwards)


Post #1

1. wirefree --> wireless

2. at least in previous versions (e.g. 12.04), pavucontrol needed a separate installation of pulseaudio (it was not added automatically), so

```
sudo apt-get install pulseaudio pavucontrol
```

You may want to check if it is necessary in 14.04, but it should work even if not necessary.

Maybe you should also add that 'it can take hours to find and test all the options in order to get the microphone, earplugs and loudspeakers to work properly. But it is definitely worthwhile taking that time, because it usually works in the end'.


Post #2

install and old flash package
-->
install an old flash package

---

### Post by nacor2 on 2014-11-18
Thank God, changing Swap from 60 to 10 made my Lubuntu 10.04 running a lil' faster on my amd k6-2 with 512 mb ram and 20 gb hdd.

---

### Post by Darth Riker on 2014-12-05
A couple of questions:

1. In regards to PAE. According to the PAE help page - [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) - my understanding is the CPU in my Dell Inspiron 8600 should be a Dothan based CPU and therefore not require the forcepae flag.

However - when running Ubuntu/Lubuntu/Xubuntu 14.04.1 from USB (Live not installing) - I receive the PAE message so have to use the forcepae flag.

Is this ok?

```


computer
    description: Portable Computer
    product: Inspiron 8600
    vendor: Dell Computer Corporation
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0D5689
       vendor: Dell Computer Corporation
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A14
          date: 06/30/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.6
          slot: Microprocessor
          size: 1800MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM_B
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e0000000-e7ffffff
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:fc000000-fdffffff memory:d0000000-dfffffff
           *-display
                description: VGA compatible controller
                product: RV350/M10 [Mobility Radeon 9600 PRO Turbo]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master vga_palette cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:11 memory:d0000000-dfffffff ioport:c000(size=256) memory:fcff0000-fcffffff memory:fc000000-fc01ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf80(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf40(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf20(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:11 memory:f4fffc00-f4ffffff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=8192) memory:f6000000-fbffffff memory:40000000-43ffffff
           *-network:0
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:11 memory:faffe000-faffffff
           *-pcmcia
                description: CardBus bridge
                product: PCI4510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:f8000000-f8000fff ioport:d000(size=256) ioport:d400(size=256) memory:40000000-43ffffff memory:48000000-4bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI4510 IEEE-1394 Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:11 memory:faffd800-faffdfff memory:faff8000-faffbfff
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2915ABG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth1
                version: 05
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=[REMOVED] latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
                resources: irq:7 memory:faffc000-faffcfff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:44000000-440003ff
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:7 ioport:b800(size=256) ioport:bc40(size=64) memory:f4fff800-f4fff9ff memory:f4fff400-f4fff4ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:b400(size=256) ioport:b080(size=128)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HTS726060M9AT00
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: MH4O
             serial: [REMOVED]
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=9e909e90
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 55GiB
                capacity: 55GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-08-02 00:31:40 filesystem=ntfs state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD+-RW ND-6500A
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 203E
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 7646MiB (8017MB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=4cfda4e2
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /cdrom
                version: FAT32
                serial: [REMOVED]
                size: 7643MiB
                capacity: 7644MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
  *-battery
       product: DELL 0004P22
       vendor: Sony
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 71590mWh
       configuration: voltage=11.1V


```

2. Based on my system specifications above - would it make more sense for me to be running Xubuntu or Lubuntu (rather than Ubuntu)?

---

### Post by sudodus on 2014-12-06
> **Darth Riker said:**
> A couple of questions:

1. In regards to PAE. According to the PAE help page - [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) - my understanding is the CPU in my Dell Inspiron 8600 should be a Dothan based CPU and therefore not require the forcepae flag.

However - when running Ubuntu/Lubuntu/Xubuntu 14.04.1 from USB (Live not installing) - I receive the PAE message so have to use the forcepae flag.

Is this ok?

If you receive the PAE message you have to use the forcepae flag, and I'm rather sure that it works to run that CPU with forcepae.
> 

2. Based on my system specifications above - would it make more sense for me to be running Xubuntu or Lubuntu (rather than Ubuntu)?

Yes, depending on your preferences (for example eye candy versus speed).

Lubuntu - ultra light foot-print
Xubuntu - medium light foot-print

Try both ***live*** and install the flavour you like the best. In my opinion, standard Ubuntu needs more horsepower (and more than 1 GB RAM) to work well.

-o-

It is possible to install any tools to Lubuntu, that come with Xubuntu and Ubuntu, for example pulseaudio and pavucontrol, which make it easier to get the audio system working.

---

### Post by Darth Riker on 2014-12-07
Thank you for the reply and reassurance regarding forcepae flag.

I've tried about Lubuntu and Xubuntu live (from USB) and like the look and feel of Xubuntu. Didn't feel too slow either so will install that and see how I go.

---

### Post by sudodus on 2014-12-07
Good luck :-)

---

### Post by NM5TF on 2014-12-17
don't know if this is right place for this...mods can move to appropriate place, please...

would like to thank the Ubuntu MATE team for bringing my Wife's Dell Inspiron 6000 laptop
back to life...

she had Ubuntu 12.04 LTS which worked fine....until the upgrade to Ubuntu 14.04 LTS....

she only has 500 MB of memory to work with....not enough for 14.04....untill MATE came along...

14.04 MATE is working great on this old unit & will for some time to come.....thanks team !!!

---

### Post by mörgæs on 2014-12-17
I doubt that they are following the thread but you are free to post.

---

### Post by siggi2 on 2015-02-01
Thank you mörgæs, for this blog! It inspired me to _get my 12 year old machine with Nvidia 2 to get to work with Xubuntu 14.04.1_. This is how I did it:

_The machine:_

Processor: AMD Athlon XP 1700+ 
CPU: 1466.807 MHz i386 32bit
Memory: 1001.5 MiB
Display: NV11(GeForce 2 MX/Mx 400)
Harddisk:  80 GB

I opened [http://wiki.ubuntuusers.de/Grafikkarten/Nvidia/nouveau]("http://wiki.ubuntuusers.de/Grafikkarten/Nvidia/nouveau")

went down to "ShadowFrame Buffer aktivieren" (activate ShadowFrame Buffer)

and followed the instructions. Here they are:

Using *sudo*

*** 1 ***
Create /etc/X11/xorg.conf.d/

*** 2 ***
create new file /etc/X11/xorg.conf.d/20-nouveau.conf
with the following text:

Section "Device"
   Identifier  "NvidiaGraphics"
   Driver      "nouveau"
   Option      "NoAccel"  "1"
EndSection

Save this file, logoff, logon, and was happily astonished 

Cheers, siggi2

P.S. Installing Xubuntu 14.04.1 was tricky on my system, because many installation-menu items disappeared, appeared and played other havoc. After the installation it still looked weird, appearing disappearing map icons, color-changing text and other havoc. However, after the ShadowFrame business, it is just beatuful! 
P.P.S. And we love the reappearance of the user pictures for login - sorry Marc Shutleworth ;-)

---

### Post by mörgæs on 2015-02-01
- and thank you for your contribution.

---

### Post by mattharris4 on 2015-02-28
> **sudodus said:**
> If you receive the PAE message you have to use the forcepae flag, and I'm rather sure that it works to run that CPU with forcepae.


Yes, depending on your preferences (for example eye candy versus speed).

Lubuntu - ultra light foot-print
Xubuntu - medium light foot-print

Try both ***live*** and install the flavour you like the best. In my opinion, standard Ubuntu needs more horsepower (and more than 1 GB RAM) to work well.

-o-

It is possible to install any tools to Lubuntu, that come with Xubuntu and Ubuntu, for example pulseaudio and pavucontrol, which make it easier to get the audio system working.

Sudodus, first thank you to you and the other moderators for the work you do here.  I was a moderator of a small cell phone forum for a while, fortunately we didn't have too many problems but we did have to install an anti-spam program to catch the 100 or so spammers that used automation to attempt to post advertisements on our forum every day without a lot of work on our parts.

I have played around with the different Canonical OS versions including Kubuntu via live USB session and Lubuntu, Ubuntu and Edubuntu as installed (I use Edubuntu on a daily basis).  I kept an eye on the system monitor installed in these programs, I found that worst-case (in my use that is the site sfgate.com with 6-8 tabs running in Firefox) Lubuntu uses 800-1100 MB of RAM, Kubuntu uses 1000-1300 MB of RAM and Ubuntu/Edubuntu use 2200-2500MB of RAM.  Just booted up without anything running except the system monitor Lubuntu uses about 250-300MB, Kubuntu about 700-800MB and Ubuntu/Edubuntu about 1000-1200MB.  When I only had 2GB of RAM on my desktop running Edubuntu (Pentium 4 running at 3.0GHz) SFGate would just about crash the computer and cause it to slow down to a crawl when it went into swap in an attempt to handle the RAM load.  I upped the RAM to 3.5GB (3.2GB recognized as the computer is only 32 bit) and this issue stopped.  With my live USB use I found that on my low-powered laptop running a E1-2100 CPU from AMD running at 1.0GHz with 4GB RAM Lubuntu maxed out the CPU much less often than the other Canonical releases I have tried on it (Kubuntu, Ubuntu and Edubuntu) making for a much smoother experience.  I have actually recently installed Lubuntu on that machine, it seems smoother than even the Windows 8.1 it came with (my installation is a dual-boot with Windows and Lubuntu so if I need to I have still access to Windows on that machine as well).

From my experience I suggest one thing -- do not depend on a swap area using a Canonical OS.  In my experience swap will slow your computer to a crawl and you will need to reboot to get it working properly again.  If you don't have the amount of RAM I specify in the worst-case scenario add RAM to the computer, use a lighter version of Linux (Lubuntu instead of Ubuntu for example) or find another OS to use (Puppy Linux claims it works on 128MB of RAM but others suggest 256MB for a smooth experience -- be warned that Puppy IS NOT a Canonical OS and doesn't have the large support base Canonical has as a result, from my research it sounds like 2-3 people do the bulk of the work with Puppy unlike Canonical which has hundreds of people supporting their OSes between their staff and user base which can make a big difference if you have a problem while installing or using an OS).  Please thoroughly research any OS candidate you want to use before installing it to a computer you depend on!  Using an OS with a small following and/or small tech support team could bite you in the rear end should you have any issues with it.  Regarding Puppy, it might be a good OS, I really don't know but my advice still stands.  I would actually like to play with Puppy on an old computer someday if I get hold of one (I did play around with a USB image and was not impressed with its features) but at this stage certainly would not depend on it for daily use from what I have seen but it might work better than other OSes on a computer with only 256-384MB of RAM.

---

### Post by sudodus on 2015-03-02
@ *mattharris4*

Welcome to the discussion in this thread, and thanks for you contribution :-)

---

### Post by mattharris4 on 2015-03-02
^ You are welcome, sudodus.

---

### Post by matey3 on 2015-03-25
Thanks to mörgæs and everyone else for this thread.
I dont know if this is the right thread but here's my problem/question:

I wanted to ask about setting up a Partitionless Ubuntu using Wubi on Windows machines?
(I never really had problems before except this last time when):

My new Asus laptop crashed and would not boot into anything because of an Upgrade from windows7 to 8/8.1 
It took a few months* but I finally got it up and running (win8.1 runs fine) BUT Ubuntu does not run and locks up?

1- Is there a way I could get into the Ubuntu command prompt? (The Ctrl, Alt F1 or F2 etc does not work) it acts like it is booting to X (desktop) but locks up with black screen and no msgs.

2- Is there any way that I can get Ubuntu's own boot menu back on? (I only get the 1st (main) menu with choice of MS or Ubuntu. In my PC if I choose Ubuntu I get the 2nd boot menu which I can choose diff. versions/releases etc.).
 Thanks in advance!



*This info maybe too old and not useful but just in case someone is interested in problems that a win7 to 8.1 upgrade will cause:
 I received windows 8 almost for free so I installed it to test and find out about it (didnt need it since my laptop doesnt have touch screen and 8/8.1 is like a tablet OS really) then when I was running win8, I got the msg that I have to upgrade to 8.1 so I did not knowing that MS deletes the backup files and if you dont have the win7 or 8 boot DVD then you are out of luck. 
I had Mfg's backup partition for 7 but 8.1 deleted it. My Asus laptop did not come with win7 dvd so I ordered the win8 dvd from MS but was not useful and was no a bootable dvd!? 
Anyway I could only boot into windows command prompt (safe mode didnt work either). Ubuntu would not come up at all (or I dont know if there is a trick that you can do to get into the command prompt?) so I kept running chkdsk /f (or whatever that repairs the hdd automatically within win8) to no avail until one day it took longer to run chkdsk so I left it alone and when I came back the windows 8.1 was up and running? I have not had any problems since!?
I learned from MS forums that MS deliberately deletes the backup files so in an upgrade or update if things went wrong, you could not go back and that really made me mad. 
so even though this maybe an old info. but if you or your work place decided to upgrade your windows machine from 7 to 8.1 or whatever, be sure do a real backup on a separate usb drive or something.

---

### Post by sudodus on 2015-03-25
> **matey3 said:**
> 
I wanted to ask about setting up a Partitionless Ubuntu using Wubi on Windows machines?
(I never really had problems before except this last time when):

My new Asus laptop crashed and would not boot into anything because of an Upgrade from windows7 to 8/8.1 
It took a few months* but I finally got it up and running (win8.1 runs fine) BUT Ubuntu does not run and locks up?

Wubi does not work with Windows 8, and it is no longer supported. See this link [Forums Staff recommendations on WUBI]("http://ubuntuforums.org/showthread.php?t=2229766")

I suggest that you run Ubuntu live from a DVD or USB drive and use it to extract your personal files (documents, pictures, video clips, music, mailboxes and bookmark files).
> 
1- Is there a way I could get into the Ubuntu command prompt? (The Ctrl, Alt F1 or F2 etc does not work) it acts like it is booting to X (desktop) but locks up with black screen and no msgs.

***ctrl + alt + F1***
> 
2- Is there any way that I can get Ubuntu's own boot menu back on? (I only get the 1st (main) menu with choice of MS or Ubuntu. In my PC if I choose Ubuntu I get the 2nd boot menu which I can choose diff. versions/releases etc.).
 Thanks in advance!

It may be hard without a running Windows system. Maybe you can loop mount the file containing Ubuntu and read/extract personal files (if any) from there. But I have never done that.
> 
... but if you or your work place decided to upgrade your windows machine from 7 to 8.1 or whatever, be sure ***do a real backup*** on a separate usb drive or something.

+1

I agree about backing up your data.

---

### Post by matey3 on 2015-04-04
Thanks a lot sudodus
you are right, wubi won't work in windows 8 or any other windows any more!
in fact it wipes off your last install then gives an error that the setup files are missing from ubuntu's ftp site etc...

well maybe they had a good reason? but to me it sucks because wubi was easy to use and risk-free. I definitely do not want to lose my windows partitions/OS for lot of reasons, plus most of these machines we buy are designed/built to Windows specifications only, (for instance) I could never use my touch screen functions in Linux since there are No drivers available.
(I know if you ask dell or msi etc, for linux drivers they'll call the cops on you lol ;) )
anyway I am not impressed ..we seem to be walking backward toward more closed source n less freedom! :mad:


> **sudodus said:**
> Wubi does not work with Windows 8, and it is no longer supported. See this link [Forums Staff recommendations on WUBI]("http://ubuntuforums.org/showthread.php?t=2229766")

I suggest that you run Ubuntu live from a DVD or USB drive and use it to extract your personal files (documents, pictures, video clips, music, mailboxes and bookmark files).

***ctrl + alt + F1***

It may be hard without a running Windows system. Maybe you can loop mount the file containing Ubuntu and read/extract personal files (if any) from there. But I have never done that.


+1

I agree about backing up your data.

---

### Post by d-cosner on 2015-04-04
I just got a P4 small form factor computer running beautifully thanks to Xubuntu 14.04 x64! It's a P4 2.8 GHz with hyper threading, Intel on-board graphics, sound and NIC, 3.5 GB DDR 2 RAM, 250 Seagate SATA hard drive and an IDE CD-ROM.

Since there was no DVD drive I had to put the hard drive in my newer computer to do the install, then put it back in the HP. After that was done I installed all the updates, rebooted and cleaned out the old kernels. I wanted to stay with the 3.13 kernel because I knew it would work well with this hardware. Next I found the ppa repos to upgrade Xfce to 4.12 and did a dist upgrade. 

I turned off all of the start up services that were not needed and set the swappiness value to 10, after rebooting the system was only using 220 MB of RAM. I removed a few apps that I did not think were necessary and added and changed a few. I swapped out the default music player for Audacious, it's plenty light and blends in better with the rest of the applications. I added the gnome-disk-utility to be able to check out the condition of the hard drive too.

The computer was really running nice at this point! Application launch time is nearly instant on most applications, even Firefox loads in just a couple seconds! I installed all the restricted extras and all multimedia playback worked great, even full screen flash! I did turn off hardware acceleration in Firefox and the Flash player itself to achieve that, it's not supported in Linux anyway.

All that was left to do was give the system a nice modern look. I found a ppa with the numix theme and numix circle icons and installed them. I found a nice wallpaper to go with the new theme and things were looking really nice! I put a deskbar on the bottom of the screen, added some useful shortcuts, made it transparent and set it to intelligent hiding. I ended up with a kind of Mac style desktop that makes Xfce look pretty modern.

It took some trial and error to achieve really good results but in the end it was well worth the time! I ended up with a 10 year old computer that runs as nice as a modern system and the OS looks fresh and new. Sure, it will not play any high end video games but it is still really nice for daily use.:D

Edit: Almost forgot, I installed uBlock in Firefox so web pages load quicker. It's light and I have never seen any problems with it under Linux like some Windows users reported.

---

### Post by Mike_Walsh on 2015-04-17
Evening, all.

I've been trying on and off, over the last year, to get an ancient Dell Inspiron 1100 laptop (from 2002) to run one of the 'buntus. I soon realized that with an elderly 'Netburst' Celeron and 1 GB RAM, I was asking too much for Unity to work properly. So I tried Xubuntu & Lubuntu (Kubuntu? Not even GOING there, thank you very much!)

Oh, they would all install. But in every single case, the desktop ended up jammed into the top left-hand corner of the 1024x768 display, at just 640x480; annoying, to say the least. So, since October she's been running Puppy Linux 'Tahrpup' 6.0. Everything worked OOTB, especially the display.

It has an Intel 'Extreme Graphics', 'Brookedale'-cored, 82845 G/GL/GE/PE/PV video adapter; a somewhat awkward device. They threw the rule book out of the window when they designed THAT thing, believe me! 

I've tried several of morgaes' workarounds over this time frame, none of which have actually worked.....with the exception of the 'nomodeset' option, which DID at least move the miniature display into the centre of the screen...

Anyway; for no particular reason that I can think of, I decided to have another go at putting Lubuntu 14.04 LTS on her last night, alongside 'Tahrpup' (having tried it before, and liked it). I thought I'd give the most recent point release a try, 14.04.2.....couldn't hurt. I'd done some digging around in the depths of the forum 'back-pages', and found this fix, which promised to sort the problematic card out:-

[http://ubuntuforums.org/showthread.php?t=2222014&page=2&highlight=dell%2C+inspiron%2C+1100%2C+laptop](http://ubuntuforums.org/showthread.php?t=2222014&page=2&highlight=dell%2C+inspiron%2C+1100%2C+laptop)

So I was fully prepared to give the above workaround a try. I installed, and re-booted, not expecting the new install to behave any different to the previous attempts. Well...! WHAT a surprise. There, staring back at me, was a full screen display, with the log-in screen on it. I was GOBSMACKED. Had a job believing my eyes.....

The inclusion of the 3.16 kernel into this point release seems to have tamed the 'awkward' adapter.....it's behaving itself like a charm, for now. Finally, I have a fully-working 'buntu install on the old Dell; many thanks indeed to Julien Lavergne & the Lubuntu team! Wonderful work. I suspect the kernel probably made the biggest difference; even 'Tahrpup' uses the 3.14 kernel.....both of the afore-mentioned being newer than 'Trusty's' original 3.13.

I'm SO pleased, I'm seriously considering making a contribution to the Lubuntu team. They deserve it. Yet the strangest thing is, I've always understood that Intel hardware has worked successfully with the Linux kernel for several years now.....

Odd, indeed. But who CARES...?? The Dell is going from strength to strength..!



Regards,

A VERY pleased Mike. :D

---

### Post by mörgæs on 2015-04-18
Congratulations.

Would be great if you would help promoting the latest kernels, also for old hardware. Some users are under the impression that old hardware should be fed old software.

---

### Post by sudodus on 2015-04-18
Congratulations *Mike_Walsh* :KS

Sometimes an old kernel is better for old hardware, because it comes with drivers, that are needed. Sometimes a new kernel is better also for old hardware, because it comes with drivers, that are needed. 

Mike shows us that it is worthwhile to [try several versions and distros live]("http://ubuntuforums.org/showthread.php?t=2230389"), and after that install and use what works best in *your* particular computer :-)

---

### Post by Mike_Walsh on 2015-04-18
@morgaes, sudodus:-

Guys, I may not be sticking with Lubuntu... I'm about to try Xubuntu 14.04.2, because out of all the 'buntu flavours, it's always been my absolute favourite for ease of configuration, and what you can do with it. I've just created a LiveUSB, and am about to 'take the plunge'..!

It, too, has the 3.16 kernel. Watch this space; I'll keep you posted. Here goes.....


Regards,

Mike.

BTW: @morgaes; I'll be more than happy to help promote the newer kernels if they have such positive results for old hardware like mine. I am REALLY impressed, after the long. slow slog of the last year or so!

---

### Post by mörgæs on 2015-04-19
As Sudodus points out there are some exceptions like really old Nvidia graphics processors but in general I recommend that people try the newest first and then go for the old one only if some problem appears. 

Feel free to post your experience with Xubuntu as well. Lubuntu mentioned in original post is only an example.

---

### Post by Mike_Walsh on 2015-04-20
> **mörgæs said:**
> As Sudodus points out there are some exceptions like really old Nvidia graphics processors but in general I recommend that people try the newest first and then go for the old one only if some problem appears. 

Feel free to post your experience with Xubuntu as well. Lubuntu mentioned in original post is only an example.

Sorry to be a little while getting back to you; hectic couple of days.

I'm pleased to be able to say that Xubuntu 14.04.2. LTS has installed very smoothly. This time, I've had to employ the workaround given by LukeM in post #16 of this article:-

[http://ubuntuforums.org/showthread.php?t=2222014&page=2&highlight=dell%2C+inspiron%2C+1100%2C+laptop](http://ubuntuforums.org/showthread.php?t=2222014&page=2&highlight=dell%2C+inspiron%2C+1100%2C+laptop)

Upon restart, I was greeted by the small screen jammed into the top left corner of the screen! (Been there, done that, etc....)

I used Mousepad to edit /etc/default/grub, and changed this line

```
 GRUB_CMDLINE_LINUX="persistent" 
```

to

```
 GRUB_CMDLINE_LINUX="vga=792" 
```

.....and it really does work! I don't know WHERE LukeM dug this up from, or how he came across it (trial & error, maybe? Who knows...), but I'll give the guy credit where credit's due.....IMHO he deserves a medal for this one..!

At this very moment I'm in the middle of updating, setting 'swappiness', etc., and all the thousand & one other little bits & bobs that are needed to make a new installation perform really smoothly. As soon as I have a screenshot worth showing, I'll post it, and let y'all know how she's performing.

I'm dead chuffed!! To quote morgaes:-

>  [COLOR=#000000]Would be great if you would help promoting the latest kernels, also for old hardware. Some users are under the impression that old hardware should be fed old software.[/COLOR][COLOR=#000000]

[/COLOR]In case anybody hasn't figured out where I'm coming from with this, we have a 13-yr old machine running nicely with the most up-to-date kernels. But I can't help wondering if this 'vga=792' trick would have worked on one of my earlier attempts, had I but known about it.....

Never mind. She's running as smooth as so much oiled silk now.....and that WAS the whole point of the excercise.


Regards,

Mike. :D

---

### Post by Mike_Walsh on 2015-04-20
**UPDATE**

I now have everything set up.....and here's a couple of screenshots to show the 'finished product':-

Clean...

[ATTACH=CONFIG]261436[/ATTACH]


...and 'dirty', with modified highlight colour, and the Numix theme.

[ATTACH=CONFIG]261437[/ATTACH]

Performance is not.....'exciting'. You wouldn't expect that from a 13-yr old P4-gen 2.2 GHz single-core Celeron, with a very small L2 cache (128k). It's best described as 'stately'! But I'm quite happy with everything; I don't need her for work, or anything like that.....so it's quite OK for what I use her for.

Astonishingly, Psensor is giving me a fairly accurate CPU temp, despite claiming during setup that it couldn't find a sensor! The Celeron is averaging 45-48C, with occasional forays up to the mid-50's; the 20 GB Hitachi HDD is running roundabout 40-42C. The Dell motherboard uses a 'thermal hardware' sensor somewhere **close** to the CPU, though not internal to it. Not sure **where**, exactly.....I believe with the Socket 478 CPUs, this was actually in the socket itself, rather than on the CPU die.

That's on a par with what I remember her running at according to HWMonitor, when she was still on Win XP a couple of years ago; if anything, she's running somewhat cooler. Mind you, that WAS before I stripped her down, gave her a good cleanout and re-applied the thermal paste last autumn..! The fan used to cut-in on high regularly prior to that; since then, I don't think I've heard it come on more than a couple of times (and that was when she was running streaming radio somewhat choppily..!)

I shall be uprating the Celeron for a 2.6 GHz P4 (with a 512k L2 cache) in the next fortnight or so.....which should improve matters somewhat. TDP's about 5W higher, but I think the stock heatsink should handle that; with the larger L2, I don't expect it to work quite so hard. The lack of SSE3's means they DO work harder than a more modern processor, though. I'll keep y'all posted as to the outcome.


Regards,

Mike. :)

---

### Post by sudodus on 2015-04-21
So after all these tests with different linux distros, flavours and versions, what would you run in this computer, if you would need it for doing 'work', not only taking part in a veteran computer's rally :-D

Still Tahrpup, or are the light-weight Ubuntu flavours efficient enough?

---

### Post by Mike_Walsh on 2015-04-21
> **sudodus said:**
> So after all these tests with different linux distros, flavours and versions, what would you run in this computer, if you would need it for doing 'work', not only taking part in a veteran computer's rally :-D

Still Tahrpup, or are the light-weight Ubuntu flavours efficient enough?

I think, in all honesty, that I'm torn between Lubuntu and TahrPup. Lubuntu, simply because like ALL the 'buntu flavours, it's very professionally finished, it runs well, there's awesome backup, and huge, well-maintained repositories. Tahrpup, because it runs at lightning speed, is super lightweight on resources, and it, too, has good community backup. I'd dual-boot. My 20 GB HDD  would have:-

One 12 GB partition (for Lubuntu or Xubuntu)
One 6 GB partition (that's HEAPS for Tahrpup), &
A 2 GB swap partition ( but with 'swappiness' dialed down to about 10).
And I have a 64 GB SanDisk flash drive that I use for external storage anyway.....which gives me a total of over 80 GB; that's enough.

The 'buntu's run SAMBA, the Puppies Samba-TNG. It appears the two ARE compatible; I have both Xubuntu & Tahrpup on my 'big' desktop, so it doesn't matter which way I transfer files, it still works. I've also recently discovered NitroShare, after reading about it SOMEWHERE on the Forums; works brilliantly.....rather similar to how Bluetooth file transfer works, except it will handle entire directories, unlike Bluetooth, which works rather better with single files. Plus, it's completely automatic; no 'setting up' required. It's a good choice for total newcomers, actually. And network printing works well, too.....though of course, that's taken care of by CUPS, so it **would** work regardless.

I'm going to wait until I get the P4 installed, at some point during the next couple of weeks, before delivering a final verdict on this. I really like Xubuntu; if the P4 does what I hope it will, then I could make that dual-boot with Xubuntu & Tahrpup.

Time will tell. Will report back with the results, as & when.


Regards,

Mike. :)

---

### Post by Mike_Walsh on 2015-04-27
I have to be honest here. After using Xubuntu on the Dell for a week or so, the Celeron is **not **'bogging things down' as much as I feared it would. In some respects, she actually seems to run **faster** under Xubuntu than she does under Tahrpup. Chromium certainly does; I'm really quite surprised at that. I shall still go ahead with the P4 upgrade.....it will be interesting to see how much better she may perform.

It appears that the P4 should go straight in, without the need to upgrade the BIOS:-

[http://en.community.dell.com/what-do-i-buy/for_home/f/4510/t/2259155](http://en.community.dell.com/what-do-i-buy/for_home/f/4510/t/2259155)

Apparently (can't remember where I saw it now) the existing A22 Dell BIOS supports up to a **2.8 GHz P4**. Makes sense; it's still single-core, the same FSB, still the same instruction set, even the exact same architecture on the same socket; just a speed & L2 increase.

I'm not expecting a **huge** boost in performance. The higher frequency ought to give me a small increase (2.2 GHz to 2.6 GHz), and the L2 increase (from 128k to 512k) should increase things a bit further. We'll see what happens. I may well end up leaving things as they are, with Xubuntu on the HDD by itself, and Tahrpup running from a flash-drive. I don't think I'm going to bother with a dual-boot. 

There's also the added complication that with Puppy running as root all the time, it kinda screws up file permissions when I want to access them from Xubuntu, so.....I'm not quite sure whether I'll continue with Puppy on the Dell. It'll definitely remain on the Compaq desktop for the foreseeable future.


Regards,

Mike.

---

### Post by Mike_Walsh on 2015-05-03
Well, the P4 is in. Everything's working A-OK; the BIOS didn't even need updating, as the existing A22 Dell BIOS supports up to a 2.8 GHz P4, so all that was needed was a stripdown, CPU replacement, and re-assembling; totally straight forward, and about an hour's work all told.

As far as OS's are concerned,  well.....the P4's running about 25% faster than the Celeron was, so; I honestly think that Xubuntu is now a viable alternative as a 'work' tool. I'd quite happily use it for work, if I had to. The P4 has made quite a difference in that respect; the machine is **that** much faster, and more responsive.

I'm very pleased with the outcome. Nice one. Job's a "good'un"!


Regards,

Mike. :)

---

### Post by sudodus on 2015-05-03
Congratulations Mike :-)

---

### Post by sammiev on 2015-05-03
Worked on a laptop and desktop this weekend with low specs. They both settled for Xubuntu 1504 after seeing the different flavors and how the ran on their computers.

Even though only nine months support, they got what they wanted.

---

### Post by Mike_Walsh on 2015-05-03
@sudodus:- I'm pleasantly surprised at just how big a difference the P4 has made. Best hour's work I've done for a LONG time; I've been on her all afternoon, and most of the evening..!

I AM going to do a dual-boot with 'Tahrpup', though; I've become ridiculously fond of it, these last few months. As I said, it only needs 3-5 GB of disk space, at most; still leaves me nearly 15 GB for Xubuntu.....which is plenty. The .sfs-based 'frugal' installation set-up that Puppy uses is just so versatile.....it can even be installed in the same partition as Xubuntu, and the two would quite happily co-exist. From what I understand, the whole 'frugal' system was originally developed by the same people who developed Knoppix? Still... I'm 'old-fashioned', I'm afraid; I'm happier with each OS in it's own partition (I've got at least** some **vague idea of what I'm doing, that way...!) 

I don't tend to keep very much stuff on board locally, anyhow; now that I've got file-sharing sorted out (thanks to [COLOR=#ff0000]Morbius[/COLOR], with a little help from [COLOR=#ff0000]steeldriver[/COLOR]; it all boiled down to the difference between upper- and lower-case on a single letter.....I am **so** embarrassed), I tend to pull everything across from the 'big' Compaq, as and when I need it. Yes, I **could** fit a larger HDD (with Puppy, you can copy a 'frugal' install on a flashdrive across to a HDD partition, and it just fires straight up..!), but in all honesty, I can't be bothered. Everything just 'works' nicely now. 

"If it ain't broke..."

-----------------------------------------------------------------------------------------------------------------------

@sammiev:- The silly thing is, at the time when Mum bought this old girl, nearly 13 years ago, I knew very little about 'tech' stuff, despite using them since the late 70's.....I've only really got into that side of things quite recently. I've pretty much grown up with these things ever since the start of the 'home computer revolution'.....seen a LOT of changes, too, over the last 35 years. With my 'change of direction' this last couple of years, and looking after Mum full-time, it gives me a lot of spare time to play with. 

If I'd known more at the time, I'd have advised her to go for the P4 in the first place. I'd have also advised her to go for more RAM, too, while she was at it.....this thing only had 128 MB when it came. XP used to run like a slug.....actually, I think a slug would've been faster, now I think back on it..!

Oh, and BTW: Congrats on your membership...well done, and well deserved! Couldn't have happened to a nicer person.


Regards,

Mike. :)

---

### Post by sudodus on 2015-06-28
[SIZE=4]General tips, that may help if you come here and your computer is around ten years old (or older)[/SIZE]

It will probably work best if you try the flavour  of Ubuntu with the lightest foot-print, ***Lubuntu***. There will still be  difficulties if there is less than ***512 MB RAM***. With more RAM, 768 MB or 1GB, you will probably succeed with ***Ubuntu Mate*** and ***Xubuntu*** too. So please tell us more  about your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card

and it will be possible to give you better advice, maybe even to try some ultra-light linux distro (lighter than Lubuntu) depending on the hardware components in your computer.

Until then, please read the following links.
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Read again the first post of this thread (Old hardware brought back to life)[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]
[URL="https://wiki.ubuntu.com/Lubuntu"]
https://wiki.ubuntu.com/Lubuntu[/URL]

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

If you can burn a CD-rom and boot from it, you can [download Lubuntu 14.04.2 LTS]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS").

If you can boot from USB, see this link, [Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

The alternate ISO is better if you have less than 512 MB RAM or if you have problems with the graphics, [download Lubuntu 14.04.1 LTS alternate ISO file]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO/14.04.1")

---

### Post by Mike_Walsh on 2015-09-30
**UPDATE**

Further to my escapades with the Dell a few months back, I'm now planning an HDD upgrade.....for a 32GB or 64GB Transcend SSD. I didn't think this would be possible, originally; a PATA HDD/SSD should have a dual row of pins at the end.....but the Hitachi HDD has what appears to be an 'edge-connector', with 'fingers' either side (like a graphics card, or PCI/PCI-e card).

However, further research indicates that this 'edge-connector' is merely an adapter that was employed by not only Dell, but several other manufacturers in the early 2000s.....to gull novices into thinking that they needed to purchase a 'hard-disk pack'; HDD, proprietary tray/caddy, and this adapter....all 'pre-assembled', of course! The adapter just pulls off, after easing a couple of 'clips' loose with a small screwdriver.....so this can go onto the new SSD, which will then be a 'drop-in' replacement.

Watch this space. I'll be interested to see just how much difference this'll make to a P4 setup.


Mike. ;)

---

### Post by Mike_Walsh on 2015-10-24
Afternoon, all.

Well; I've done it. The old Dell is now sporting a 32 GB SSD with PATA/IDE interface. Very easy swap, too; undo 2 screws, remove the caddy; undo 4 more screws, and remove the drive itself.

The 'edge-connector' adapter was slid off the pins of the Hitachi HDD, and then pushed onto the pins of the Transcend SSD. Back in the caddy, replace the screws. Caddy back in the Dell, replace the screws.

Repartition from the FAT32 it came with to ext3 (for Puppy) and ext4 (for Xubuntu), and re-install. Quickest re-install I've ever done! Xubuntu used to take about 25-30 mins for an install; it's now down to just over 10. I'm impressed. Puppy's re-install was about the same (but then all that consists of is copying the entire partition over, running the Grub4DOS config tool that Puppy comes with, and she's up & running).

So; to recap:-

**Original** (2002):-

2.2 GHz Intel Celeron (128k L2)
128 MB RAM
20 GB Hitachi Travelstar HDD
Windows XP Home.

**Today**:-

2.6 GHz Pentium 4 (512k L2)
1 GB RAM
32 GB Transcend PATA/IDE SSD
Puppy 'Tahrpup' 6.03, Xubuntu 14.04.3 LTS.

I'd estimate the performance, vis-a-vis read/writes, boot-up, saving, etc., has probably increased by about 75%. (Or, to put it another way, things take a little over half the time they used to).

And I didn't even need to employ the 'workaround' on the graphics this time! The 3.19 kernel detected & displayed my screen correctly, first time round. Excellent stuff.

She isn't a 'powerhouse', and never will be; the P4 architecture is the biggest bottleneck now. But as a day-to-day laptop, I think this old lady is eminently usable...and I think I could happily use her for work as she currently stands.

I wouldn't mind getting a little bit more speed out of her, by using the 3.0 GHz non-HT Pentium 4 (the fastest one Intel produced for the 400MHz FSB), but I think that's 'pie-in-the-sky' wishful thinking; they're rarer than hen's teeth, and even extensive searching on eBay & Amazon, as well as a few other sites, hasn't thrown up any positives. Intel only made a very limited run of them; they were starting to concentrate on the 533 & 800 MHz versions, with HT, and the Prescott-based 'Extreme Editions'.

It's not a bad package, though; and just goes to show that patient, gradual upgrading can keep any old machine viable.....with some help from the right software, of course!


Regards,

Mike. ;)

[ATTACH=CONFIG]265144[/ATTACH][ATTACH=CONFIG]265145[/ATTACH]

---

### Post by sammiev on 2015-10-24
+1 @ Mike

---

### Post by Mike_Walsh on 2015-10-24
Hey, sammiev.

I know it's daft ( and considered plain pointless by some people), but I've grown very attached to this old lady. She and I have been some places together!

Just goes to show, if you're patient, even a 'dowager duchess' like this one can eventually benefit from modern technology. Fitting this, together with the P4 ( and now the most recent point release of 14.04), has transformed the old girl.....and given her a new lease on life.

It's all good stuff! :D


Regards,

Mike. ;)

---

### Post by Sweet_Baby_Jamie on 2015-10-24
My computer is actually older than me!  I got it as a hand-me-down when my parents finally bought a new one.  It was awful, super slow, and then when support ended for Windows XP I thought I would have to throw it away!  I Googled for help and wow, it's amazing.  The full fun story is in the link in my signature.  The short version is that I discovered an ultra-light Lubuntu-based OS and this old fossil runs better now - according to my parents anyway - than when it was new!  But the best part of the story is what happened *after* that!  Click on my signature to see how much *more* awesome it got!

---

### Post by JKyleOKC on 2015-10-24
Great story, Jamie! The linked thread has been closed for a while so I had to come back here to congratulate you!

And I agree with others that you're likely to go far. I have grandkids more than twice as old as you and I'm glad to see that the coming generations are doing great!!!

---

### Post by Mike_Walsh on 2015-10-25
One thing I have noticed with this new SSD is that they seem to run quite a bit hotter than a traditional HDD. The old Hitachi Travelstar would run between 42-44C; this Transcend SSD averages between 55-60C.

Googling this subject, it appears this is normal for these devices. Unlike a mechanical HDD, which has spinning platters that cause air movement inside the case, an SSD is, of course, banks of chips in a completely sealed case. It's basically an oversized flash drive.....and I know, from running Puppy off a flash drive, just how warm they **can** get.

According to the manufacturers, operating temperatures between 0C-70C are acceptable. Another learning curve...!

[http://uk.transcend-info.com/products/images/modelpic/512/Product%20Sheet_PSD330_520_1228.pdf](http://uk.transcend-info.com/products/images/modelpic/512/Product%20Sheet_PSD330_520_1228.pdf)

Amongst other things, I've learnt that to help prolong the life of the device, you need to leave about 10% un-formatted. This gives the controller room to play with as it shuffles used blocks around, prior to deleting them & marking them as ready for re-use.

It's like learning basics all over again..... :lol:

Unfortunately, the only thing the PATA interface doesn't support is the most important one; TRIM. Bugger..! Now, how do I get round that one? Hmmm... Anybody got any ideas?


Regards,

Mike. ;)

---

### Post by sudodus on 2015-10-25
> **Mike_Walsh said:**
> 
Unfortunately, the only thing the PATA interface doesn't support is the most important one; TRIM. Bugger..! Now, how do I get round that one? Hmmm... Anybody got any ideas?


1. Use the mount option **noatime** (in fstab)

2. Avoid swapping as much as possible

3. Run the ext4 file system without a journal (can be tweaked with tune2fs). This makes the files system more sensitive to errors, so there is a tradeoff.

4. Maybe use a trick I use to keep USB pendrives alive and responsive:

a. Backup the content if necessary
b. Wipe the whole device (overwrite with zeros)
c. Restore from backup

See [this link](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297).

---

### Post by Mike_Walsh on 2015-10-25
Hi, sudodus.

Thanks for the link, and the ideas. I wasn't aware you could run an ext4 partition without the journal; surely that kinda defeats the purpose of having it, doesn't it? Still, I don't mind admitting, I've got a whole lot yet to learn. I'm a 'hardware' guy; I'm happy pulling things to bits, seeing how they work, then putting them back together, and improving upon the original assembly wherever possible. I'm not so 'hot' on the software side of things....but at that, I guess my 'learning curve' is about the same gradient as most other folks...

As far as I can tell, with what I've gleaned off the 'net in the last couple of days, you can only use 'noatime' with the SATA derivatives; I don't think it's supported by the PATA types. But hey; what do I know? :lol:

I'll investigate the link in a bit. Thanks again, Olle.


Regards,

Mike. ;)

EDIT: Just had a quick skim through.....I think I've read that before. I know I've read Duckhook's explanation about 'gridlocking'; quite informative.

---

### Post by SuperTrainStationH on 2016-02-02
Thanks everyone. So here's what happened.

For whatever reason the audio settings started working in Xubuntu.

I was able to turn off the internal bell speakers and get either external speakers or headphones to work with the headphone jack in the front, but not the one in the back. After a deal of fiddling around it seems like the jack in the back may be legitimately defective, but honestly the external speakers I have are so bad that I'd be more likely to use headphones anyway, and even so I'm not using this for multimedia, so I was pretty happy.

Still couldn't get the network connection to work.

So friend gave me a DVD with Fedora on it.

I ran it "live" off the disk. I instantly had internet access without touching a thing, but I couldn't get the headphone jack to work, or turn off the bell speaker, even using the same means that worked with Xubuntu. 

I guess I'll just try different flavors of Ubuntu till I find one that just wants to work alright.

What you fellows have walked me through has pretty much got me to a point where I feel comfortable trying to peck my way through this and see what does and doesn't work, and if I have trouble I'll ask in the specific boards or threads dedicated to specific problems. 


Thanks everyone!

---

### Post by Mike_Walsh on 2016-02-03
Hi, SuperTrainStationH.

This is only a suggestion (feel free to ignore it, by all means!).....but why don't you give Puppy Linux a try? It's very lightweight, and designed specifically to breathe new life into elderly, yet still useable hardware. Specifically, this one:-

[http://smokey01.com/rg66/X-slacko/iso/](http://smokey01.com/rg66/X-slacko/iso/)

X-Slacko 2.3.2 is more stable than X-Slacko 3.0, or 3.1; both of which are still in beta, and hence still rather 'buggy'. It's based on the 'classic' Slacko Puppy 5.7.0, with the addition of the XFCE desktop environment (so if you like Xubuntu, you'll feel right at home with it).

I've been using this for at least 6 months now, on a 2005 Compaq Presario desktop (post the HP takeover, but definitely manufactured before.....hence much higher quality components).....and it's as stable as a rock.

Same procedure; download, burn to disc (CD, in this case, 'cos of the small size), and run from the LiveCD. You'll soon find out what works, and what doesn't; but I'll be very surprised if you don't have external speakers and an internet connection working right from the word 'go'. You **will **find Puppy running from the LiveCD is a lot faster than Xubuntu running from the LiveDVD, as Puppy runs entirely in RAM. And this particular Pup has everything but the kitchen sink installed as standard..!

Just a suggestion, as I said. Make of it what you will.

EDIT: BTW, it **is** worth spending a bit on a halfway decent set of external speakers; at least a separate amp, and powered sub-woofer. Makes a **world **of difference!

And to answer one of your questions from the other thread, Puppy Linux Forum member rcrsn51 has created a major thread on installing printers in Puppy, including loads of links to specific brands & models, what **does** work, what **doesn't**, etc. He's our printer 'guru'! See here:-

[http://www.murga-linux.com/puppy/viewtopic.php?t=59015](http://www.murga-linux.com/puppy/viewtopic.php?t=59015)

Hope some of that helps, anyway.


Mike. ;)

---

### Post by SuperTrainStationH on 2016-02-10
My machine's basically running flawlessly except for one thing.

The screen will occasionally spontaneously become corrupted.

When this happens its usually when I'm doing things like using the Software Center, or very occasionally when I have my Settings panels open.  

The Software Center is pretty much the most heavy duty thing I do on this computer aside from maybe browsing the web, as I'm basically using this thing for early 90's DOS games, looking at photos of trains, and word processing, and its rarely had this problem while doing any of those other things.

Moving windows around helps un-distort some of the corruption, and my upper left main menu is fine, to the point where I'm able to log out, and then log back in, which always fixes the corruption.

Below are screenshots depicting before and after images of the corruption.

Thanks in advance everyone.

If a solution is found for this my new (old) machine will be everything I wanted of it. 

Oh, and 'm using xubuntu 15.10.


[[IMG]http://s13.postimg.org/3ne1ndd3n/Screenshot_2016_02_08_23_59_18.jpg[/IMG]]("http://postimg.org/image/3ne1ndd3n/")

[URL="http://postimg.org/image/6g6dmat0t/"][IMG]http://s30.postimg.org/6g6dmat0t/Screenshot_2016_02_08_23_58_19.jpg[/IMG]
[COLOR=#000000]
[/COLOR]
[/URL]

---

### Post by mörgæs on 2016-02-11
Please begin with reading the initial posts, especially #4.

---

### Post by bcschmerker on 2016-02-13
**Thanks for keeping a Thread available for rebuilders.**  As of February 2016 I am weighing my options for the old Hot Rod gPC&#8482; (Advanced Micro Devices® Athlon64® X2 5600+, AMD® RS780G/SB710 chipset), which will soon need new drives and a second-upgrade video card (which the previously-fit Antec® TruePower® New&#8482; 750 Blue&#8482; should have no trouble supplying).  The case can take four 3.5" hard drives; both the Fujitsu® PATA drives are coming due for replacement, and the Gigabyte® GA-MA78GM-S2HP 'board can take five internal (SATA0 through SATA 3 in AHCI, SATA 4 in IDE/ATAPI) and one external (in IDE/ATAPI) SATA devices in addition to two devices on the one PATA header (which I plan to reassign to an optical drive).  Only issue I don't know is whether this rig can handle the Gigabyte® GV-R726X-2GD, which has one of AMD's late-model RV1260XP 128-bit chips from the Volcanic Islands series; I was unable to use an Asus® EAH6850DC in this rig, probably due to the lack of 256-bit support in the stock Phoenix® Award® BIOS, but it runs a Diamond® HD 5450 with its 1 GiB 128-bit memory just fine.

This rig runs like a champ on its old hardware under Ubuntu® 12.04.6-LTS (upgraded to Kernel 3.13.0).  I anticipate needing NAS-grade hard drives for the rebuild for Ubuntu® 16.04.0-LTS, as my system has to endure Central Valley (CA, USA) summers where the ambient temperature can approach 40°C; my target max safe operating temperature for the new HDD's is 60°C.  The Western Digital® WD7500BFCX Scorpio Red model is larger than I planned on for each of four (i plan to put /, /var, /home, and potentially /usr on separate drives for ultimate performance in normal operation), but it's WDC's smallest capacity for the temperature range I need.  The GA-MA78GM-S2HP probably having been built for SATA 1.*n*, any recommendations on alternative models of hard drives for highish temperatures for SATA 1 through 2?

---

### Post by Mike_Walsh on 2016-02-16
** UPDATE **

I've now swapped the 32 GB Transcend SSD for a 64 GB version. Just wanted more space to play with ( and install another Pup or two!) Still running very, **very** well.....and transforming a 14-yr old Inspiron.


Mike. ;)

---

### Post by poorguy on 2016-02-24
*deleted.*

---

### Post by Tashley235 on 2016-03-17
First, thank you so much. Great thread.

Now, my issue. I've revived a fairly old laptop with Lubuntu 14.04. Unfortunately, this is a 32-bit processor and I did so a few days after Google stopped supporting a 32-bit Chrome browser. My main reason for wanting to get Chrome working is so that I can watch Netflix on this laptop (which is the last thing that *isn't* working that I really want). I have verified that my processor is SSE2-capable. I wasn't sure how to proceed to get Netflix to work. Attached is my hardware report.[ATTACH]267857[/ATTACH]

Thank you for any help/advice you can give! :)

---

### Post by mörgæs on 2016-03-18
Thanks, but there are many good posters gathered in this thread. I don't use Netflix myself and have not played with it, but there is a good chance that someone else posting here could give advice.

---

### Post by mail-2o on 2016-04-22
Thanks for a very useful thread. 

Just in case anyone is fighting with a VIA Nano X2 L4050 @ 1.4 GHz mini ITX Board, I have had some success as I posted at Thread: [Lubuntu installation]("http://ubuntuforums.org/showthread.php?t=2320221"). I tried just about every flavour of ubuntu and DVDs, CDs, USB keys and minimal install distros. I have had considerable success with a Mythbuntu 14.04 DVD ISO and now have a functioning MythTV computer. I still have to start by editing the boot to add VGA=791, but have read how to edit GRUB2, so that can wait a while. ```
<CODE>computer
    description: Computer
    width: 64 bits
    capabilities: smbios-2.6 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3703MiB
     *-cpu
          product: VIA Nano X2 L4050 @ 1.4 GHz
          vendor: CentaurHauls
          physical id: 1
          bus info: cpu@0
          size: 900MHz
          capacity: 1400MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc rep_good nopl pni monitor vmx est tm2 ssse3 cx16 xtpr sse4_1 popcnt rng rng_en ace ace_en ace2 phe phe_en pmm pmm_en lahf_lm ida cpufreq
     *-pci:0
          description: Host bridge
          product: VX900 Host Bridge: Host Control
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 80
          width: 32 bits
          clock: 33MHz
        *-display UNCLAIMED
             description: VGA compatible controller
             product: VX900 Graphics [Chrome9 HD]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list
             configuration: latency=64
             resources: memory:fc000000-fcffffff memory:fd000000-fdffffff memory:d0000000-dfffffff memory:febf0000-febfffff
        *-multimedia:0
             description: Audio device
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:35 memory:febec000-febeffff
        *-pci:0
             description: PCI bridge
             product: VX900 PCI Express Root Port 0
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:1
             description: PCI bridge
             product: VX900 PCI Express Root Port 1
             vendor: VIA Technologies, Inc.
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27
        *-pci:2
             description: PCI bridge
             product: VX900 PCI Express Root Port 2
             vendor: VIA Technologies, Inc.
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:d000(size=4096) memory:fe000000-fe7fffff ioport:f4000000(size=33554432)
        *-pci:3
             description: PCI bridge
             product: VX900 PCI Express Root Port 3
             vendor: VIA Technologies, Inc.
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:e000(size=4096) ioport:f7e00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 06
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-1.fw ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:33 ioport:e800(size=256) memory:f7efb000-f7efbfff memory:f7efc000-f7efffff
        *-ide
             description: IDE interface
             product: VX900 Serial ATA Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=64
             resources: irq:21 ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=16)
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:20 ioport:c080(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:22 ioport:c000(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:bc00(size=32)
        *-usb:3
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:23 ioport:b880(size=32)
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:23 memory:febebc00-febebcff
        *-isa
             description: ISA bridge
             product: VX900 Bus Control and Power Management
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: VX855/VX875/VX900 PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:f8000000-fbffffff
           *-multimedia
                description: Multimedia video controller
                product: CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
                vendor: Conexant Systems, Inc.
                physical id: 3
                bus info: pci@0000:06:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm bus_master cap_list
                configuration: driver=cx18 latency=64 maxlatency=200 mingnt=2
                resources: irq:16 memory:f8000000-fbffffff
        *-multimedia:1
             description: Audio device
             product: VT8237A/VT8251 HDA Controller
             vendor: VIA Technologies, Inc.
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:36 memory:febe4000-febe7fff
     *-pci:1
          description: Host bridge
          product: VX900 Error Reporting
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: VX900 CPU Bus Controller
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: VX900 DRAM Bus Control
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: VX900 Power Management and Chip Testing Control
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: VX900 APIC and Central Traffic Control
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: VX900 Scratch Registers
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VX900 North-South Module Interface Control
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: VX900 PCI Express Physical Layer Electrical Sub-block
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:03.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: VX8xx South-North Module Interface Control
          vendor: VIA Technologies, Inc.
          physical id: 109
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=8
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DRW-24B1ST   i
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: ST9500325AS
             vendor: Seagate
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sda
             version: BSM1
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=48f54475
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 25GiB
                capacity: 25GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-04-11 20:02:50 filesystem=ext4 label=antiX15root lastmountpoint=/ modified=2016-04-18 20:05:45 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2016-04-18 20:05:45 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.1.0,2
                logical name: /dev/sda2
                size: 49GiB
                capacity: 49GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 24GiB
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 24GiB
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.1.0,3
                logical name: /dev/sda3
                version: 1
                serial: [REMOVED]
                size: 8424MiB
                capacity: 8424MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@0:0.1.0,4
                logical name: /dev/sda4
                logical name: /home
                version: 1.0
                serial: [REMOVED]
                size: 334GiB
                capacity: 334GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-04-11 20:03:12 filesystem=ext4 label=antiX15home lastmountpoint=/home modified=2016-04-18 20:05:47 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2016-04-18 20:05:47 state=mounted
     *-scsi:1
          physical id: 3
          bus info: usb@1:1
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: SCSI Disk
             product: Officejet Pro 85
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
     *-scsi:2
          physical id: 4
          bus info: usb@1:7
          logical name: scsi5
          capabilities: emulated
        *-disk
             description: SCSI Disk
             product: Cruzer Blade
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
             version: 1.27
             serial: [REMOVED]
             size: 58GiB (62GB)
             capabilities: removable
             configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdc
                size: 58GiB (62GB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: guid=2093827d-7223-42a0-8725-7e9c89c5b54b
              *-volume
                   description: Windows FAT volume
                   vendor: mkfs.fat
                   physical id: 1
                   logical name: /dev/sdc1
                   logical name: /media/sdc1
                   version: FAT32
                   serial: [REMOVED]
                   size: 58GiB
                   capacity: 58GiB
                   capabilities: fat initialized
                   configuration: FATs=2 filesystem=fat label=64GB-USB mount.fstype=vfat mount.options=rw,nosuid,nodev,noexec,relatime,uid=1000,gid=1000,fmask=0177,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,quiet,utf8,errors=remount-ro state=mounted</CODE>
```

---

### Post by mörgæs on 2016-05-05
Thanks for posting. VIA processors are a recurring problem and sometimes VESA drivers are the only option. 

Still they are an interesting piece of hardware due to their low power consumption.

If you find other ways of getting the graphics to work please post again.

---

### Post by poorguy on 2016-05-05
Got several of these from work that they were going to destroy a 10 year old desktop running perfectly.  
Ubuntu Mate 16.04 32 bit install. 
Probably will run 64 bit but didn't have it handy.

Dell Precision 380 
Year Born 2006
Processor intel Pentium D 820 Smithfield 2.8GHz 2.0MB L2 cache.
Amd / ATI Sapphire Radeon X1300 Pro 128MB PCIE graphics card.
Memory 3.0GB DDR2 800MHz FSB.
Hard Drive Sata 40 GB 
Sound Card Creative Labs SB X-Fi.

Dell-Precision-380:~$ inxi -Fxz
System:    Host: Dell-Precision-380 Kernel: 4.4.0-21-generic i686 (32 bit gcc: 5.3.1)
           Desktop: MATE 1.12.1 (Gtk 3.18.9-1ubuntu3) Distro: Ubuntu 16.04 xenial
Machine:   System: Dell product: Precision WorkStation 380
           Mobo: Dell model: 0CJ774 Bios: Dell v: A07 date: 04/18/2006

---

### Post by mörgæs on 2016-05-05
All Pentium D's are 64 bit, so when you for some reason want to reinstall you could take the 64 bit ISO.

For all used gear it's a good habit to open the case and clean fans and radiators from dust. After this you should be good to go.

---

### Post by poorguy on 2016-05-05
I work for the State Dept and we are upgrading / updating desktops so all of these leave without HDD in them. 
So when I get them they get air hosed and then a 40 GB HDD as I have a lot of 40GB HDD just laying around from my Windows XP days. 

I figured they would run 64 bit just didn't have my 64 bit DVD handy. 
 
These Desktops are tanks I bet each one weighs in at 40 pounds. 
These were built when Dell Computers were really good and not just mediocre as they are now IMO.

I will probably get several more as nobody seems to want them due to their size.
So I will take as many as I can and either sell them or give them away after installing Linux on them.

Just thought I would add to the Old hardware brought back to life list.

---

### Post by sudodus on 2016-05-09
I made a new tarball with a 32-bit Lubuntu system using UXA acceleration. It makes it easier to install Lubuntu in computers with some old graphics chips from Intel, where Lubuntu 16.04 LTS has problems.

**Lubuntu_16.04_oem-uxa.tar.xz**

It is described at [the following link (in my tutorial thread about the One Button Installer)](http://ubuntuforums.org/showthread.php?t=2172971&page=2&p=13486102#post13486102).

There is a corresponding compressed image file to be installed with [mkusb](https://help.ubuntu.com/community/mkusb),

**dd_Lubuntu_16.04_oem-uxa_2016-may_7.8GB.img.xz** at [http://phillw.net/isos/linux-tools/compressed-images](http://phillw.net/isos/linux-tools/compressed-images)

***Edit:*** There is a new method, that is often better than this UXA method. See posts #1 and #150 describing how to use the method with 'xserver-xorg-video-intel'.

---

### Post by poorguy on 2016-05-10
*deleted*

---

### Post by sudodus on 2016-05-12
Now there is another new Lubuntu tarball and a compressed image file with 'xserver-xorg-video-intel' for old Intel graphics. According to tests (not only by me) this method is better than the UXA method with many Intel graphics chips.

Installing this way can make it easier to install Lubuntu in computers with some old graphics chips from Intel, where Lubuntu 16.04 LTS has problems.

**Lubuntu_16.04_oem-intel.tar.xz**

It is described at [the following link (in my tutorial thread about the One Button Installer)](http://ubuntuforums.org/showthread.php?t=2172971&page=2&p=13487384#post13487384).

There is a corresponding compressed image file to be installed with [mkusb](https://help.ubuntu.com/community/mkusb),

**dd_Lubuntu_16.04_oem-intel_2016-may_7.8GB.img.xz** at [http://phillw.net/isos/linux-tools/compressed-images](http://phillw.net/isos/linux-tools/compressed-images)

If you want to start from an official iso file, you can do it from the Ubuntu mini.iso according to the instructions in the first post of this thread.

In that case, please remember to install **xserver-xorg-video-intel** in the mini system before rebooting to start Lubuntu or Lubuntu Core.

---

### Post by matey3 on 2016-05-14
Hi;
great thread! I was wondering about the same thing, I have an old MSi laptop which I think still has MS Vista on it. I want to wipe it out and start fresh because HDD's too full to have both OSes. I don't have much RAM either maybe 1 Gig. Anyway I was wondering if I still could download the older versions. I had a very good luck with 7.04 but that was a while ago on the other hand the newest version requires so much more machine than I have (More RAM more HDD etc.).

If anyone can post a link to older versions of Ubuntu it will be greatly appreciated.
Thanks a lot.

Oh I have an Asus laptop which has 12.04 on it but I cant boot with it, I cannot get an Ubuntu startup menu at the boot-up so I just boot into Windows 10...Long story... I have to explain what happened...
I guess I post under another thread. 
Thanks very much!

---

### Post by sudodus on 2016-05-15
We recommend to ***avoid*** old versions of Ubuntu or any operating system after its end of life. Then there are no updates, not even security updates, and your computer can easily be attacked via the internet.

Use a current version with a light desktop environment instead, for example Lubuntu. Your computer, that works with Windows Vista will work quite well with current versions of Lubuntu :-)

---

### Post by kurt18947 on 2016-05-15
> **matey3 said:**
> Hi;
great thread! I was wondering about the same thing, I have an old MSi laptop which I think still has MS Vista on it. I want to wipe it out and start fresh because HDD's too full to have both OSes. I don't have much RAM either maybe 1 Gig. Anyway I was wondering if I still could download the older versions. I had a very good luck with 7.04 but that was a while ago on the other hand the newest version requires so much more machine than I have (More RAM more HDD etc.).

If anyone can post a link to older versions of Ubuntu it will be greatly appreciated.
Thanks a lot.

Oh I have an Asus laptop which has 12.04 on it but I cant boot with it, I cannot get an Ubuntu startup menu at the boot-up so I just boot into Windows 10...Long story... I have to explain what happened...
I guess I post under another thread. 
Thanks very much!

Try a 'lighter flavor' like Lubuntu or Xubuntu? You could use a 32 bit version which should require less memory. Could you upgrade your machine's RAM? I've purchased sodimms off of Ebay and so far so good, they've performed as expected.

---

### Post by mörgæs on 2016-07-09
Unfortunately there are plans to drop 32 bit Ubuntu support and I think you people should be informed about that . A questionnaire has been launched to gauge the interest in keeping the 32 bit ISO:

[https://bryanquigley.com/crazy-ideas/when-should-i386-support-for-ubuntu-end](https://bryanquigley.com/crazy-ideas/when-should-i386-support-for-ubuntu-end)

Please fill in for all your 32 bit computers.

---

### Post by SantaFe on 2016-07-09
Clicked on the link, went to the link there to enter my 32 bit systems and got the following:
```

The form "End x86_32 bit support, impact" is no longer accepting responses.

```

Hmmm...

---

### Post by mörgæs on 2016-07-10
That was short lived. It was launched only a week ago: [http://ubuntuforums.org/showthread.php?t=2329753](http://ubuntuforums.org/showthread.php?t=2329753)

If the questionnaire is failing somehow I hope people will inform Bryan Quigley directly that 32 bit computers are still relevant.

---

### Post by mörgæs on 2016-08-05
The Lubuntu developers have built a new and much improved web site: [www.lubuntu.me]("http://www.lubuntu.me") . While the old site often lagged behind the new one seems to be better maintained.

For Lubuntu related news it's a good place to start.

---

### Post by poorguy on 2016-08-27
> **mörgæs said:**
> Unfortunately there are plans to drop 32 bit Ubuntu support and I think you people should be informed about that .
I'm finding that most of my 10 year old computers are able to run 64 bit Ubuntu and doing it very well. =d>

$ inxi -Fx
System:    Host: ASUSTek-Lithium Kernel: 4.4.0-36-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: MATE 1.12.1 (Gtk 3.18.9-1ubuntu3.1) Distro: Ubuntu 16.04 xenial
Machine:   System: HP Pavilion 061 product: ED843AA-ABA M7267C
           Mobo: ASUSTek model: LITHIUM v: 1.05 Bios: Phoenix v: 3.17 date: 04/20/2006
CPU:       Dual core Intel Pentium D (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 vmx) bmips: 13604 
           clock speeds: max: 3400 MHz 1: 2400 MHz 2: 2400 MHz
Graphics:  Card: NVIDIA G96 [GeForce 9400 GT] bus-ID: 01:00.0
           Display Server: X.Org 1.18.3 drivers: nouveau (unloaded: fbdev,vesa) Resolution: 1280x720@60.00hz
           GLX Renderer: Gallium 0.4 on NV96 GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes

---

### Post by lah-ca on 2017-02-03
[SIZE=5][B][SIZE=3]Date 3-Feb-17

SIS 771/671 Video Chipset Driver Installation Guide

[/SIZE][/B][/SIZE]This post presents a solution for installing Linux SIS drivers on an Olidata U40SL1 notebook. This notebook is apparently identical to ECS, Uniwill, and Olivetti units with the same model number, and the solution **_*should*_** work for them, as well. The solution **_*should*_** also work for any device with a SIS 771/671 video chipset.

The solution is for ***LUbuntu 16.04 32 bit***, but it _***should***_ also work for various contemporary Ubuntu distros and forks - and maybe Debian, as well.

[B]Acknowledgements 

[/B]Thanks to **Temüjin** and **mörgæs** here at UF: [https://ubuntuforums.org/showthread.php?t=2350126](https://ubuntuforums.org/showthread.php?t=2350126)

Thanks also to **rasdark** at Github for the largely anonymous and often thankless task of driver development: [https://github.com/rasdark](https://github.com/rasdark)

**Expectations**

The results will _***not***_ be perfect. The SIS drivers provide only some level of 2D acceleration and no 3D. There will be occasional display anomalies/corruption - restarting applications usually fixes this - in rare cases, rebooting or logging out/in is required. There will also be sporadic Ubuntu-has-experienced-an-internal-error messages, these associated with XOrg, probably as a result of the SIS drivers - the problem beneath the error message seems to be non-disruptive, however. In the end, 1280x800 resolution is achieved. The vesa drivers, the next best alternative, provide only 1024x768 resolution, with some minor distortion of aspect ratio and with no acceleration, and full screen video playback, Youtube, DVDs, etc, is either not possible or is of unacceptable quality. The SIS drivers provide higher resolution, better clarity, better colour, and better aspect ratio. They also allow full screen video playback, including DVDs, at a moderately acceptable level. I would also say that the notebook does not get as hot with SIS drivers as it does with the vesa ones, suggesting that the vesa drivers put more work on the proc. Overall the performance of the notebook is better. Web pages load faster, etc.

**Don't Work in 600 x 480 unless You Are a Masochist!**

The default fbdev drivers, those loaded, after installation, provide only 600x480 resolution. It is difficult to work with this. Create an xorg.conf file in /etc/X11/ in order to load the Linux-native vesa drivers which will provide 1024x768 resolution. You will need this file later, anyway, to load the SIS drivers.

If you are new/newish to Linux, you can open a terminal and use sudo to launch a text editor so that you will have rights to save the file in the X11 folder. For LUbuntu:

```
sudo leafpad
```

Copy/paste the following:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection


Section "Monitor"
        Identifier      "Configured Monitor"
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Save the file as ***xorg.conf*** in the X11 folder - /etc/X11

**Reboot**

If you are new/newish to Linux and still have a terminal open:

```
shutdown -r now

```

This seems to work faster than GUI menu-driven reboot button.

You should have 1024x768 resolution, which will make the rest of the work easier.

**Install a Log Reader**

This is not a necessity, but if something goes wrong, you will have easy access to the XORG logs for diagnostics. For LUbuntu:

```
sudo apt-get install ksystemlog
```

**Prerequisites**

Here I present the creation of the environment in which the compilation and installation of the drivers worked. Not all steps may be necessary but this was the state in which things did work.

Run the following in a terminal. Copy/paste is your friend.

```
sudo apt-get install build-essential xorg-dev
sudo apt-get install autoconf automake git
sudo apt-get install libtool-bin
# typo found here by Temüjin: sudo apt-get install _***xutils.dev***_
# should read:
sudo apt-get install xutils-dev
```

**Downloading, Compiling and Installing Driver**

Run the following in a terminal. Copy/paste is your friend.

```
cd ~/   #or whatever dir you want to use - note: the process works well in the root of the home folder.
git clone https://github.com/rasdark/xf86-video-sis671.git
cd xf86-video-sis671/
git checkout for-xorg-1.18
autoreconf
automake
./configure --prefix=/usr --disable-static
make
sudo make install
```

**Check for Driver Files**

Look in /usr/lib/xorg/modules/drivers - there should now be two SIS driver files: ***sis671_drv.la*** and ***sis671_drv.so***

**Loading Driver: Edit xorg.conf**

Open the xorg.conf file created above. Remember to use sudo to open the text editor.

Change:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"

```

To:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "sis671"

```

Save and close the file.

**Reboot**

Again you can use the command line, if you still have a terminal open:

```
shutdown -r now

```

**Enjoy!**

---

### Post by Youngblood52 on 2017-02-17
After successfully loading Kubuntu (32bit) on an old desktop system  (**3.06Ghz P4** + **2GB** dual-boot with **Win7x86**) and checking it out, I decided to replace the  Xubuntu Installs on my old **1GB RAM**, **2.4GHz Pentium4-M** CPU, **WinXPx86  Dell Latitude C640**s.

The first laptop sports an upgraded 1400x1050 panel.  The Install,  apparently, completed smoothly.  After creating the .bin file and  altering the boot.ini for dual-boot with the WinXP, I  rebooted and selected Kubuntu in the menu and all looked fine ... until  the screen switched to white with a moveable mouse cursor (before  reaching the login screen).

That was all.  When I eventually pressed the power button to bailout, a  KUBUNTU screen displayed for a few seconds prior to shutdown.

Thinking the upgraded panel *may* be (part of) the issue, I then installed Kubuntu  on another C640 with a standard 1024x768 panel.  Same result.

The graphics on these old laptops is provided by **ATI Mobile Radeon 7500**s  with only 32MB.  I am left wondering if the tiny bit of graphics RAM may be  the Issue.

Anyway ...

Prior to giving up on running Kubuntu on these laptops and reinstalling  another flavor, I decided to take a few days to see if someone here had  experience with this specific Issue ... and, possibly, a corrective cfg file workaround.  :)

Thanks for taking the time to read my post.

---

### Post by sudodus on 2017-02-17
I am not sure but I suspect that Kubuntu (as well as standard Ubuntu) wants 3D capability of the graphics hardware. I know that standard Ubuntu can emulate it (I think it is called 'llvmpipe') and it works but very slowly with old hardware.

I don't know the details about Kubuntu, but I am rather sure that you have better luck with a medium light desktop environment, Xubuntu that you have used, or Ubuntu MATE, or the ultra light desktop environment of Lubuntu.

---

### Post by Youngblood52 on 2017-02-17
> **sudodus said:**
> I am not sure but I suspect that Kubuntu (as well as standard Ubuntu) wants 3D capability of the graphics hardware. ...Thank you for the *fast *response, **sudodus**! 

Yeah ... I am suspicious of the capability (or lack thereof) of the old RV200 DirectX7 vidcard in these laptops.

If it turns out that Kubuntu is a no-go for these laptops, at least I already know that they can easily handle Xubuntu.

That brief time I spent working with Kubuntu on the old desktop system convinced me that I would prefer it ... if only it and my old laptops played well together.  ;)

---

### Post by Youngblood52 on 2017-02-17
After giving the system plenty of time to get to the Login, I typed the password ... and the screen went black with a white-outlined black X cursor.

Within a minute (I could see by the HDD activity LED that files were being loaded) a fault notification window appeared, titled Plasma.

"We are sorry, Plasma closed unexpectedly." ... 

Above the 4 buttons at the bottom:

**Details:**
Executable: plasmashell PID: 2650 Signal: Aborted(6) Time: 2/17/17 20:26:29

The buttons are marked:
Report a Bug     Debug     Restart Application     Close

Two tabs at the top:

General     Developer Information


As time goes by the title changes from Plasma to Plasma<1> to Plasma<2> to Plasma<3> and so on as restarts apparently fail.

When I have it generate debug info, after it does so it tells me, 

"The generated crash information is probably not useful."  :)

Ayup ... it appears to me that Plasma and my first-generation *ATI Mobility Radeon *VidCard are just not playing well together.

---

### Post by mörgæs on 2017-02-18
In original post, top part, there is a link showing memory consumption in various Buntus. With this 'in memory' I am not surprised that Kubuntu and Plasma are too much of a workload for the old C640. 

Distrohopping is a good thing but I recommend that you try a selection of the light ones.

---

### Post by Youngblood52 on 2017-02-18
G'morning, **mörgæs**!

Yes, I saw that memory comparison (just prior to happily whiling away a chunk of afternoon reading the info contained in this Thread :)) .  

It left me with a tiny hope that I might be able to install & boot Kubuntu so that I could then checkout how proggies actually functioned.

Going into it, I figured that the 2 possible tripping points were the 1GB of RAM limitation and the antique graphics capabilities.

Schade ... I will have to be satisfied with Xubuntu on my C640s and Kubuntu on my old, rarely-used desktop.

Actually, I am considering replacing the Ubuntu on my primary laptop with Kubuntu.

Thanks for sharing your insight & advice!

---

### Post by mörgæs on 2017-02-19
You're welcome. If you while experimenting find some advice that is useful to others please post and I shall add it to the original post.

---

### Post by hennmann on 2017-02-26
Perhaps this is not the place to request advice on what version I should or should not use or perhaps it is. After being turned off from having to use the command line and being away from Linux for a number of years I decided to give it another try with "older hardware" that isn't being brought to life, but is always in use with Windows XP32/64.7 32/64, and Limping along on Windows 10/32 Professional making me reconsider the command line saga:confused:
This is what I'm currently using:
MSI K8T Neo2-F Motherboard(originally designed for the socket 939 AMD 64 bit processor now being picked on by Windows 8.1 and 10, 64 bit versions:-({|=) with the only issues of  Dinosaur VGA and temperamental with RAM](*,):-x
AMD Athlon 64 x2 4800+ 2.4GHz Toledo dual core
MSI FX5700LE TD128 VGA ( Nvidia G-Farce FX) Dual monitor
DDR PC3200/400 RAM @4GB
Silicon Image 3114 SATA PCI card (4 SATA ports)
Aiwa TD-AS10  10GB IDE TR3 Tape Drive (Identical to the Sony SuperStation):lol:
And essential goodies such as a floppy drive which is still used.

Would the latest and greatest Ubuntu work fine with this or am I possibly going to run into driver issues? The last version of Ubuntu I stumbled around with was 5.10/64 bit and it is obviously no longer supported even though its from 2006:redface:

---

### Post by JKyleOKC on 2017-02-26
With only 4 GB of RAM you may have problems with the current mainstream Ubuntu and all its included eye candy, but the Xubuntu variation (which differs only in having less eye candy and a less-bloated window manager) should work for you (I have run older version of this in as little as 256 MB of RAM. but it crawled rather than ran). None of the current releases require use of the command line, although many of the replies here in the forum tend to imply otherwise. The reason for the prevalence of command-line responses is that they are MUCH easier to describe visually, and are not subject to wild variations depending on exactly which video chip or text editor one uses.

I doubt that you'll run into driver issues although not all the older Nvidia hardware is still supported properly. And I have no experience with tape drives, having stopped using them when the Q80 format became obsolete some 10 to 20 years ago. You WILL need a DVD player to install any current version, since they have all grown too bloated to fit onto a CD, and USB 2.0 support will also be extremely helpful.

I would recommend, though, that you try the LTS versions, the latest of which is 16.04.2, rather than the "latest and greatest." The LTS versions are for "long term support" while the three that come between each of them are essentially beta tests for new ideas, so have quite a few more bugs plus shorter support lives!

---

### Post by sudodus on 2017-02-27
@hennmann,

'+1' I would also suggest that you try the LTS versions, and would add Lubuntu and Ubuntu MATE to Xubuntu as good candidates. I have a computer with AMD Athlon 64 x2 4400+ and old nvidia graphics (not the same chip as yours), and all these flavours with light desktop environments work well without any tweaking at all.

See this link for details, [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by mörgæs on 2017-02-27
> **JKyleOKC said:**
> The LTS versions are for "long term support" while the three that come between each of them are essentially beta tests for new ideas, so have quite a few more bugs

Au contraire. A non-security bug found in release X will normally be fixed in release X + 1. This means that if a bug found in 16.04 is fixed the fix will appear in 16.10 and/or 17.04. An LTS release is a museum for old bugs which are fixed in later releases; the older the age of the LTS the more it's lagging behind. 

Security related bugs will be fixed in all supported releases. This is the definition of support. The same goes for a small number of select non-security bugs. 

I also tend to recommend LTS for old hardware. I do this as a compromise believing that a longer support period for most people is more important than some unfixed bugs.

---

### Post by hennmann on 2017-02-27
And many thanks to all of your help and advice&#128077;
My initial response or post was on my Win10/32 attempt with this hardware which is as sad as a baby crying due to driver issues and that includes the motherboard and video card causing video to have audio studder where the audio sounds like a frog croaking and at times performance issues. This hardware sings and soars like an eagle on XP64 professional and could even handle that pathetic resource hog Vista which I ripped out by the roots!  Windows 7 was like putting lipstick on a pig and the pig is Vista but it handled 7 very well(another hog) prob because of good drivers. This was all before I found the 4800+x2 on ePay a few months ago. Prior to that all I had was a 3500+ single core. I had Zorin ultimate 11 on it a few months ago but the mouse cursor didn't appear and I later found out while struggling with ram and bios flashes, that removing the battery and resetting bios caused the cursor to magically appear. I went away from Zorin because just trying to install software such as a different Internet browser was beyond my means because a simple procedure such as that required a command on the dreaded command line or in my case sitting infront of the screen looking at it wondering what to do. Before I pulled the plug I found this hardware performed very well with Zorin running multiple monitors. The board is old but USB installation works very well to the point of myself using Rufus and flash or thumb drives. Just for the heck of it I will download the latest bloated Ubuntu and give it a try. As for the command line it is still required as I found and it disappoints me by the fact that perhaps this operating system should be more GUI orientated and because of myself and many others being "GUI salves" is the reason it isn't as popular as it should be. Years ago with the much earlier versions of Mandrake (early 2000's) that I tried I even had to properly set up partitions, etc. but I found having to remember or should I say try to remember let alone find commands caused me to run away.

---

### Post by hennmann on 2017-02-28
After being told on this forum that my 5,10 was too old too upgrade my only?? option was a clean install of 16.10 and now the Deja vu comes back to haunt me!! No mouse or rodent is indicated what so ever during install and this is the problem I had with Zorin 11.0 Ult. in the past as well. Trying earlier versions of Ubuntu and Zorin PRIOR to the versions where the man and keyboard showing up at the bottom of the screen during installation DO NOT have the missing cursor problem and at times moving the mouse around drop down menus occur indicating the cursor is there but not visible. Otherwise the graphics are very clear and sharp with my older VGA NVidia  FX5700LE. The entire installation had to be done toggling with the keyboard. When installation was completed and reboot occurred, when I reached the boot loader I was greeted with:

GRUB Loading stage1.5.
GRUB loading, please wait...
Error 2

FYI the hard drive with my Windoze 10 is SATA fed by the onboard SATA port and the Hard drive I installed the Ubuntu on is IDE so none of these are on the SATA controller card (Silicon Image 3114)
Right now I'm posting this on my Win 10 on the same hardware. From going through this in the past was why I was hoping an upgrade from an older working version to the 16.10 would be an option and perhaps the older versions have the proper drivers etc. Different mice were tried including much older models with the ball underneath instead of optical rodents, including a much older one with a serial port connector. 
Suggestions other than looking at the Red, Blue, Yellow, and Green logo????

---

### Post by sudodus on 2017-03-01
I suggest that you try the first point release 16.04.**1** LTS. Try it ***live*** according to this link,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

If still not luck, please try some other Ubuntu flavours and versions according to the following link,

[How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

If still no luck, you can try some other linux distro, that is likely to work with old hardware, for example Bodhi, Knoppix, LXLE, Puppy (Wary Puppy, TahrPup), Tiny Core ...

---

### Post by hennmann on 2017-03-01
All of my previous experiences of "live" were quite lousy to say the least!! Every time I tried it, drivers were not properly installed, poor performance graphics etc. and when I did a permanent install the system worked like it was supposed to. No I don't want some crummy skimpy trimmed down version because performance is obviously not the issue here. I'm not running a 286 here and it's most likely a driver is missing or not configured properly. Please remind me of how Linux is supposed to be better?? As for not being able to upgrade and the versions that do work cannot be upgraded most certainly puzzles me. Why is upgrading from an earlier working version not possible? If we as new users are supposed to learn how to use this operating system, this would be a good place to start. Otherwise I have a boot loader issue and other than the graphics being crisp, clear, sharp  (in other words excellent) everything appears to be stable and I would think there should be a "work around" solution to why the mouse cursor doesn't appear.  A working system without the cursor showing being replaced by a different, smaller, older version sounds like solving a problem with a shotgun. As it is I'm trying to stay positive here using and learning an OS where a terminal and command line are required instead of using a full GUI OS. 
What is the difference?? Where the problem starts is with the versions (probably the supported non EOL) that have the circle with a man beside what looks like a keyboard at the bottom of the screen during installation and this includes ZORIN looking identical except the color is blue.  I haven't used Linux Mint yet but if it uses the same Kernel it will probably a repeat of Zorin and Ubuntu.

---

### Post by JKyleOKC on 2017-03-02
The less-bloated versions we have recommended in this thread are NOT "skimpy" or "trimmed down" other than omitting multiple megabytes of eye candy, and replacing many third-party applications that offer "something for everyone whether you need it or not" with more compact but equally capable equivalents. The mainstream Ubuntu distribution itself was originally designed to attract die-hard Windows users, and as Windows itself has added sparkly bells and whistles, Ubuntu has apparently felt forced to follow. That, in turn, gave rise to the less-bloated versions -- but they are fully capable. For instance, my Xubuntu 14.04 and 16.04 systems run fully capable Windows virtual machines, on which I produce a 40-page quarterly professional-grade magazine. The virtualized Windows systems run FASTER than they did in native form on my machines before I converted to Linux.

If you're looking for a totally full-featured distribution, Debian may be more to your liking. Mainstream Ubuntu is derived from Debian, but with the addition of more user-friendly (and consequently less configurable) driver packages. What has driven its popularity over the last decade is that, for many people, it "just works" out of the box with no need for tricky tweaks.

The inability to upgrade more than one minor version at a time was a conscious design decision, intended to reduce the load on the mostly volunteer support staff. It greatly reduces the number of possible combinations of software in any single machine -- but it also puts a high premium on staying current and never skipping an upgrade. The LTS (Long Term Support) releases were an answer to this, but even there skipping a release is not allowed.

But to address your initial concern about poor performance of the "live" test versions, these were never intended to become permanent production installations. To run from the read-only CD (now DVD) medium, they must create a ramdisk in memory on the fly when powering up, and since few systems have enough RAM to handle today's programs in addition to the operating system itself, they depend heavily on the swap file, paging blocks of memory in and out as required. This is a slow process at best, and older hardware makes it even worse.

The live versions, however, contain exactly the same drivers and driver detection algorithms as do the final installed versions. Their primary purpose is to determine in advance whether a specific package is compatible with your hardware, and if it is (and you like its look but not necessarily its performance) to install it to your hard drive. You can get some increase in performance by converting the DVD to boot from a USB drive, but much of the older hardware cannot handle this solution.

---

### Post by hennmann on 2017-03-03
Well out of frustration of having something totally useless due to a missing cursor I started trying other versions as well as Debian and Mint. The installer for the latest Mint version worked right away but the final install resulted in taking over 10 minutes for the desktop to crawl onto the screen and very dim I might add. After pushing the reset button I tried Robolinux the latest version because I'm still waiting for the earlier versions to download via BitTorrent. The live version booted up with no cursor (why am I not surprised??) so after wasting much time getting nowhere with Zorin which resulted in what I know now about Zorin and Ubuntu is the older versions work but when I tried the newer supported versions (with the man in a circle beside the keyboard or however you describe it) we get to the mouse saga (with no help). A Google search revealed there are lots of us with this "small" problem. Next attempt was Robolinux and the "live" version installed without a mouse, again not surprised. Right now I have grown used to my exercises of futility and decided to ignore this and try a full installation and during the installation process my cursor appeared throughout the whole procedure functioning like it should. Next when it rebooted the system booted up nice and fast (like it should with a reasonably substantial dual core processor) presenting a crisp clear dual monitor desktop but of course without the cursor. Obviously if it installed with the cursor working throughout the entire installation procedure, why should this rodent die when all of the final drivers and other assorted paraphernalia are installed? Right now I'm looking at a fighter jet with RoboLinuz Cinnamon on the side with no cursor as I type this out with my thumbs on my smart phone. 

My my brother who is an Electrical Engineer with his Computer Science degree ( and is full of himself I might add) has a saying about Linux "Linux chooses it's own friends". I guess this answers the question why I personally know very few people that use it if it is this "user unfriendly". The older versions of Mandrake that later became Mandriva usually installed quite well and easily and that was back in the day when I had to set up my partitions etc. and even the boot loader worked great with dual booting Windows and Linux but as usual if something more advanced had to be done it resulted in sitting back and looking at the screen like I'm doing today. Nothing has changed since I went away from Linux a number of years ago too now.

---

### Post by mörgæs on 2017-03-05
You guys are posting some big chunks of text. 

It's all right and I am not complaining, just mentioning that you will give yourselves a better chance of getting response when posting a brief and precise question.

---

### Post by poorguy on 2017-04-26
> **hennmann said:**
> 
My my brother who is an Electrical Engineer with his Computer Science degree ( and is full of himself I might add) has a saying about Linux "Linux chooses it's own friends". I guess this answers the question why I personally know very few people that use it if it is this "user unfriendly".
Linux isn't hard to learn or unfriendly. 

One must first be willing to spend the time to understand how Linux works.

People are used to using Windows it's is all they have ever known and just don't or aren't willing to make any changes.

---

### Post by Youngblood52 on 2017-04-26
> "Linux chooses it's own friends"I think that is *very* apt.

I think that it is *much* easier on those of us who have spent years, and especially those who started, on a command line.

Most with a GUI-only experience are probably (initially, at least) put-off by the arcane-seeming nature of the command line action.

Then, there are those who just like the challenge, despite their prior experiences.  :)

---

### Post by poorguy on 2017-04-27
> **hennmann said:**
> My my brother who is an Electrical Engineer with his Computer Science degree ( and is full of himself I might add) has a saying about Linux "[COLOR=#0000ff]Linux chooses it's own friends[/COLOR]". I guess this answers the question why I personally know very few people that use it if it is this "user unfriendly". 
And I quote  "[COLOR=#0000ff]Linux chooses it's own friends[/COLOR]"[COLOR=#000000] Please explain. :confused:
 


[/COLOR]

---

### Post by missmoondog on 2017-11-16
wow! quite long posts for something as ridiculous as cursor not working!

not offering any help here but just want to say that linux IS NOT hard to learn and DOES NOT pick it's own friends! the command line is not really ever necessary to run linux anymore as i can attest to as i can't stand the command line either.

if your computer can run that crapware windows 10, it's almost impossible to believe it can't run linux even better. 

i'm setting here on an ancient everex computer with a POS via c-7 D, 1.5mhz cpu and 2 lousy gigs's memory and everything runs as sweet as can be. windows 7 didn't run to bad on this machine as far as just surfing the net, but the difference between that OS and Lubuntu is like night and day.

anyway, i hope you get your cursor issue fixed and can learn to love linux as much as i do now!! i love it so much i've wiped 6 of 8 computers and installed it on them. would've wiped all 8 but need windows on 1 for updating my tomtom and other computer is spouse's.

---

### Post by melisang on 2017-12-13
LucidPup and PrecisePup are both Ubuntu based, and run anything, nearly, PII, PIII, Duron800. Believe me, I dunnit.

---

### Post by hrsetrdr on 2018-03-31
> **missmoondog said:**
> wow! quite long posts for something as ridiculous as cursor not working!

not offering any help here but just want to say that linux IS NOT hard to learn and DOES NOT pick it's own friends! the command line is not really ever necessary to run linux anymore as i can attest to as i can't stand the command line either.

if your computer can run that crapware windows 10, it's almost impossible to believe it can't run linux even better. 

i'm setting here on an ancient [SIZE=4]everex computer with a POS via c-7 D, 1.5mhz cpu and 2 lousy gigs's memory[/SIZE] and everything runs as sweet as can be. windows 7 didn't run to bad on this machine as far as just surfing the net, but the difference between that OS and Lubuntu is like night and day.

anyway, i hope you get your cursor issue fixed and can learn to love linux as much as i do now!! i love it so much i've wiped 6 of 8 computers and installed it on them. would've wiped all 8 but need windows on 1 for updating my tomtom and other computer is spouse's.

''everex computer with a POS via c-7 D, 1.5mhz cpu and 2 lousy gigs's memory, ''  sounds like you somehow got my old laptop.

---

### Post by Sami Lehtinen on 2018-04-02
About older hardware, I've been using the legendary [Samsung NC10]("https://en.wikipedia.org/wiki/Samsung_NC10") netbook / mini laptop for lots of stuff with Xubuntu. But lately it seems that the display drives have gotten broken? About 80% of the screen gets corrupted from left side, and only 20% of screen remains working on right hand side. I think something is broken on driver level. It would be so awesome if this would get fixed. I'm not 100% sure that's the case, but at least it seems very plausible. Here's [one post]("https://plus.google.com/+SamiLehtinen/posts/QULk9hnR7xJ"), I made about this earlier, but maybe the target group wasn't right, the true nerds dealing with old hardware, I mean. 

I'm sure someone is using exactly the same hardware, I'm just curious if this setup is working for you with latest updates?

---

### Post by sudodus on 2018-04-02
@Sami Lehtinen,

If you suspect that the software is bad (the graphics driver), you can 'Try Xubuntu', booted from some live USB drives with different versions. At least the version that you installed from originally should work that way.

See this link and links from it,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Sami Lehtinen on 2018-04-02
@sudodus,

I've done that... (it was mentioned later on that Google+ comment chain) Even booting from HD and just selecting older kernel works out, I just choose it from boot menu. Also if I run / install from live USB / CD the Xubuntu until I run update / upgrade and boot the system.

---

### Post by bcschmerker on 2018-04-02
> **missmoondog said:**
> ...i'm setting here on an ancient everex computer with a POS via c-7 D, 1.5mhz cpu and 2 lousy gigs's memory and everything runs as sweet as can be. windows 7 didn't run to bad on this machine as far as just surfing the net, but the difference between that OS and Lubuntu is like night and day.

anyway, i hope you get your cursor issue fixed and can learn to love linux as much as i do now!! i love it so much i've wiped 6 of 8 computers and installed it on them. would've wiped all 8 but need windows on 1 for updating my tomtom and other computer is spouse's.
:-D  Actually, as a VIA® pc2500&#8482; licensee, the Everex® TC2502 shipped stock with a 1.5 *GHz* VIA® C7-D and CN700 chipset with integrated UniChrome&#8482; GPU - that's how mine was, prior to a complete rat rodding with an Antec® TruePower® New&#8482; 750 Blue&#8482; and Gigabyte® GA-MA78GM-S2HP running 4 GiB DDR2-800.  As of 2 April 2018 the Hot Rod gPC&#8482; needs an Advanced Micro Devices® Athlon II® X2 240 or up, or a Phenom II® X4 915e to restore its performance - the Athlon 64® X2 5600+ blew out its memory manager and I'm running a 3500+ in the interim.

---

### Post by mörgæs on 2018-04-02
@Sami Lehtinen, it's a problem often seen with Atom processors. Here is a possible solution:

[https://ubuntuforums.org/showthread.php?t=2376580](https://ubuntuforums.org/showthread.php?t=2376580)

---

### Post by Sami Lehtinen on 2018-04-02
@mörgæs
Awesomeness! Thanx, fixed. I tried Googling it several months ago, and I just couldn't find anything relevant. Nor anyone in Google+ knew anything about it. But now it's working perfectly. I knew someone would know it in this thread. - Gotta post a link there too.

---

### Post by mörgæs on 2018-04-02
You're welcome. 
Do you have the option for testing if the problem is solved in 18.04, please?

---

### Post by Sami Lehtinen on 2018-04-16
[COLOR=#000000][FONT=Calibri][SIZE=4]Yes, it's fixed.

Tested using:
[bionic-desktop-i386.iso]("http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/lubuntu/daily-live/current/bionic-desktop-i386.iso")                   2018-04-15 19:18  1.0G  Desktop image for 32-bit PC (i386) computers (standard download)
BE9CAB13EAE73A979ECA6D1C0F63FF8163973C330D1D227688A16A681A00BE34    1085194240  bionic-desktop-i386.iso
[/SIZE]
[/FONT][/COLOR]

---

### Post by mörgæs on 2018-04-20
Thanks for testing.

---

### Post by kurtkoch on 2018-05-14
mörgæs,

I am excited about your post. It's so well written and put together. Thank you very much!
I was wondering if you would consider to add a table of contents at the beginning, which would help with navigation?
Also, I am curious why you chose the term "operative system" instead of "operating system"?

Thanks again,
Kurt

---

### Post by mörgæs on 2018-05-15
Thanks for reading it :-)

> **kurtkoch said:**
> 
I was wondering if you would consider to add a table of contents at the beginning, which would help with navigation?

Good idea. I shall take a look to see how to create it.


> **kurtkoch said:**
> 
Also, I am curious why you chose the term "operative system" instead of "operating system"?


As English is not my mother tongue I am happy to receive corrections. What is the difference between these two?

---

### Post by poorguy on 2018-05-29
Hey morgaes,

Short interesting read you posted.

[http://www.alandmoore.com/blog/2011/08/21/reviving-your-old-pc-with-linux-part-i-defining-expectations/](http://www.alandmoore.com/blog/2011/08/21/reviving-your-old-pc-with-linux-part-i-defining-expectations/)



Thanks

---

### Post by mörgæs on 2018-06-16
> **kurtkoch said:**
> 
Also, I am curious why you chose the term "operative system" instead of "operating system"?


It's changed now. If anyone finds more examples of strange expressions please post them here.

---

### Post by maurer on 2018-08-21
Hello community,

first of all thank you for the work you put supporting old hardware.
I want to contribute to this by compiling a SSE-only firefox-60-esr.
I have an old sempron but available in about 1 month.
Is there someone with a SSE-only CPU willing to test my build [FONT=arial]**[https://gofile.io/?c=YKJGpG](https://gofile.io/?c=YKJGpG) **?thanks[/FONT]

---

### Post by sudodus on 2018-08-21
@maurer,

Is this what you mean: 32 bit without SSE2 (as quoted from the opening post in this thread)?

> 
**2) Hardware**
The main rule is that software in the Buntu world works more or less everywhere. Some exceptions apply, though.

[TABLE="class: grid, width: 1000, align: left"]
[TR]
[TD]**Hardware**[/TD]
[TD]**Age (approx.)**[/TD]
[TD]**Occurrence**[/TD]
[TD]**Examples of applications which don't work**[/TD]
[TD]**Remarks**[/TD]
[/TR]
[TR]
[TD]32 bit without SSE2[/TD]
[TD]2001-2[/TD]
[TD]Rare[/TD]
[TD]Firefox, Chromium, Chrome, Skype[/TD]
[TD][/TD]
[/TR]
[/TABLE]


---

### Post by mörgæs on 2018-08-21
I guess it must be. The standard Firefox works fine on 32 bit with SSE2.

So, does anyone have a Pentium 3 or an AMD K7?

Thanks Maurer!

---

### Post by maurer on 2018-08-22
yes, exactly  - [COLOR=#000000][I]32 bit without SSE2
Thanks[/I][/COLOR]

---

### Post by sudodus on 2018-08-23
@maurer,

I tested your **firefox-esr** like this:

- Installed it into a persistent live Lubuntu 16.04.1 LTS system (in a Sandisk Extreme pendrive). I had to download and install two more packages from deb files in order to make it work (in a more modern computer).

```

ls -l Downloads/*.deb
-rw-rw-r-- 1 999 999 45340462 aug 22 16:07 Downloads/ff60sse.deb
-rw-rw-r-- 1 999 999  1209420 aug 22 16:24 Downloads/libnss3_3.35-2ubuntu2_i386.deb
-rw-rw-r-- 1 999 999   675934 aug 22 16:07 Downloads/libvpx3_1.5.0-2ubuntu1_i386.deb

```

- Tested in an old computer with a Soltek motherboard dated 2003 with nVidia-nforce2 and an AMD Athlon with sse but without sse2. See the attached screenshot.

I am sorry, but I could not make **firefox-esr** work in this computer. I did re-install, but it did not help.

- Tested in a slightly newer Dell Dimension 4600 with a Pentium 4 CPU. **firefox-esr** works in this computer.

[hr][/hr]
Please advice what can be done in a different way:

- Which operating system (distro, version) should your **firefox-esr** be installed into (which system did you use)?

- Which extra deb packages should be installed alongside?

- Other advice?

---

### Post by maurer on 2018-08-23
thanks for the test.
I'll do more compiling next week i hope when i'll get access to my old sempron (no sse2)

---

### Post by missmoondog on 2018-08-26
> **maurer said:**
> Hello community,

first of all thank you for the work you put supporting old hardware.
I want to contribute to this by compiling a SSE-only firefox-60-esr.
I have an old sempron but available in about 1 month.
Is there someone with a SSE-only CPU willing to test my build [FONT=arial]**[https://gofile.io/?c=YKJGpG](https://gofile.io/?c=YKJGpG) **?thanks[/FONT]

i just tested this on an old amd athlon xp without sse2 support, running lubuntu 18.04.1 and get the following error:

error:
dependency is not satisfiable: 
libevent-2.0.5 (>=2.0.10 stable)

---

### Post by maurer on 2018-09-03
unfortunately i wasn't; able to get back my old sempron so my development is stalled.
you can test my latest build [(]("https://transfer.sh/2DzOh/firefox-60.1.0.en-US.linux-i686.tar.bz2")targeting noSSE2) here [https://gofile.io/?c=vY45ti](https://gofile.io/?c=vY45ti)

---

### Post by missmoondog on 2018-09-04
that build does absolutely nothing :(

no pop up error messages or anything.

---

### Post by lah-ca on 2018-09-26
Hi.  If you are desperately trying to get an OS for older hardware, I suggest that you have a look at the Ubuntu fork, Bhodi Linux.  

The current version is based on 18.04.  It is _***quite minimal***_, but it works, and being Ubuntu-based it seems to be quite stable.  It has extremely modest minimum system requirements.

It is quite quirky and requires a readjustment of assumptions of how a desktop environment should behave, but once you understand its features/limitations, it is easy to live with.  

The support community for the distro is small, very small, but, in my limited experience in dealing with this community, I have found them to be quite friendly and responsive, much like the larger community here.  

I came to this distro because I have an old HP Mini-110 netbook that I use for travel.  It has been upgraded to the maximum of 2 Gb of RAM, and it now has an SSD hard drive.  It has a wimpy little dual core Intel Atom proc.  It started out its out-of-box life by having Win 7 starter nuked and being loaded with a full LTS version of Ubuntu which ran spectacularly well.  Over the years, it has been migrated various leaner distros, XUbuntu and LUbuntu and variants thereof.  The updates around the time of Meltdown and Spectre patches crushed the life out of the poor little netbook which was then running LUbuntu 16.04. 18.04 was tried, but it was was worse.  The little computer was rendered largely non-functional.  It now works quite well with the current version of Bhodi - quite peppy.

I prefer the full version of Ubuntu 18.04 LTS which I am using on my desktop as I type now, but this will not run, well not acceptably, on the netbook.

---

### Post by lah-ca on 2018-09-26
A suggestion for trying to get older hardware to stream video at an acceptable level is the use of a blocking hosts file, such as the MVPS, there's no place like 127.0.0.1, hosts file - there are others, as well.

The purpose of the blocking hosts file is not to improve streaming performance.  It is a privacy/security measure.  It blocks unwanted connections from advertising and tracking servers through DNS by referring their URLs to the reflexive IP address 0.0.0.0 - telling your browser that your local machine hosts the remote content.  Since your machine does not host it, no connections are made.  Apologies to the technically adept for the pedanticism here.

The use of a hosts file on an older system, however, frees up system resources and can allow, for example, a Youtube video to stream at an *acceptable* level of performance, no frame skipping, no video corruption, no video stalling while sound continues.

Are there negative aspects to using a blocking hosts file?  Yes.  1. General browsing will be ***slightly*** slower in that pages will take longer to load.  The blocking hosts files are very large with thousands of entries.  2. There is an ethical downside.  Many wonderful, entertaining, useful, important, etc, etc, websites survive only through advertising.  You might be able to support some through donation or subscription but nobody can support all.  Using a blocking hosts file cheats sites of revenue, and unlike an ad blocker browser plug-in, which can be used with surgical precision, the blocking hosts file has more of a thermonuclear Armageddon approach.  3. There is a maintenance burden.  The Internet is more dynamic than it is static.  Things change, and a blocking host file must be updated, usually every few months.

I don't advise just replacing your hosts file with a downloaded blocking hosts file.  Rather preserve the head of your hosts file and append the blocking entries from the downloaded file.  You will need to run a text editor with root privileges to modify your hosts file, btw.

---

### Post by missmoondog on 2018-10-02
> **lah-ca said:**
> A suggestion for trying to get older hardware to stream video at an acceptable level is the use of a blocking hosts file, such as the MVPS, there's no place like 127.0.0.1, hosts file - there are others, as well.

The purpose of the blocking hosts file is not to improve streaming performance.  It is a privacy/security measure.  It blocks unwanted connections from advertising and tracking servers through DNS by referring their URLs to the reflexive IP address 0.0.0.0 - telling your browser that your local machine hosts the remote content.  Since your machine does not host it, no connections are made.  Apologies to the technically adept for the pedanticism here.

The use of a hosts file on an older system, however, frees up system resources and can allow, for example, a Youtube video to stream at an *acceptable* level of performance, no frame skipping, no video corruption, no video stalling while sound continues.

Are there negative aspects to using a blocking hosts file?  Yes.  1. General browsing will be ***slightly*** slower in that pages will take longer to load.  The blocking hosts files are very large with thousands of entries.  2. There is an ethical downside.  Many wonderful, entertaining, useful, important, etc, etc, websites survive only through advertising.  You might be able to support some through donation or subscription but nobody can support all.  Using a blocking hosts file cheats sites of revenue, and unlike an ad blocker browser plug-in, which can be used with surgical precision, the blocking hosts file has more of a thermonuclear Armageddon approach.  3. There is a maintenance burden.  The Internet is more dynamic than it is static.  Things change, and a blocking host file must be updated, usually every few months.

I don't advise just replacing your hosts file with a downloaded blocking hosts file.  Rather preserve the head of your hosts file and append the blocking entries from the downloaded file.  You will need to run a text editor with root privileges to modify your hosts file, btw.

thanks for the 2 posts you made. what browser does that linux distro you mentioned in other post use and does it require sse2 as 2 of my old machines do not support it.

as far as your post here about the host file, that is EXACTLY what i use and how i update it. have used it for years now.

edit:
i just did a quick search of their forums about sse2 and only found 1 result that didn't say anything about it and it's not mentioned in the system requirements. both my older machines easily have more than the minimal requirements though. just need to know about sse2.

---

### Post by lah-ca on 2018-10-02
@missmoondog

The distro has the Midori browser bundled because it is lean and small.  But you can install pretty much anything, Chrome, Chromium, Opera, Vivalidi, Firefox ....  

I don't know about SSE2 requirements.  You could ask them, or you could just try it by booting to a USB key or DVD and see what happens.

One of the big limitations for me is that the Distro is pretty much a single user thing (no user management interface) unless you are real cool with terminal work.

Also the desktop is not a desktop.  There is a desktop folder in your profile, but its contents are not visible on "the desktop" and you can't put program links there.  It is always really clean.  LOL.

But it is fast.

---

### Post by missmoondog on 2018-10-03
thank you, lah-ca

---

### Post by lah-ca on 2018-10-03
> **missmoondog said:**
> thank you, lah-ca

You are most welcome.

---

### Post by Ralph L on 2018-10-11
I have an old Toshiba Satellite A215-S4697. I just clean installed Xubuntu 18.04. Now Xubuntu 18.04 hangs on shutdown.  Even the live memory stick hangs on shutdown.  Shutdown worked fine on Xubuntu 16.04.  Also, I get a Machine Check on boot and it says "APIC ERROR" also during boot.  I did not get this on 16.04.

The computer also will not resume from a suspend (started by closing the lid), when the lid is opened. Resume worked fine under 14.04 and under 16.04 until some update in the past 6 months or so. I am very suspicious that my problem is caused by an update to make uefi work, since I have an old bios. I tried a lot of suggestions by other people who have had shutdown hangs, but none of them worked for me.

 My log is very similar to the one in [https://www.queryxchange.com/q/3_1080529/ubuntu-18-04-hangs-on-shutdown-or-restart/](https://www.queryxchange.com/q/3_1080529/ubuntu-18-04-hangs-on-shutdown-or-restart/) the last two items being:  [https://www.queryxchange.com/q/3_1080529/ubuntu-18-04-hangs-on-shutdown-or-restart/](https://www.queryxchange.com/q/3_1080529/ubuntu-18-04-hangs-on-shutdown-or-restart/)
    Code:

    Reached target Final Step.
    Starting Power-Off...

Anybody else getting shutdown hangs with an old computer, and an old BIOS.  Like I said, I think this is caused by the new uefi support code. 
Any help is appreciated. I really don't want to go back to Xubuntu 14.04.

Note:  This problem (and the "unable to resume with lid opening problem) were solved by installing Kernel 4.4.97 into Xubuntu 18.04 using Uukk from ppa:teejee2008/ppa.  Surprisingly, everything seems to run. I tried Kernel 4.4.98 and it fails, so the bug was introduced in Kernel 4.4.98.  I'll keep trying new Kernels to see if the problem gets fixed, but for now it looks like I am doomed to running an old kernel forever.

---

### Post by hk42 on 2019-09-25
Thanks for this nice topic.
One point that I would like to emphasize in the choice of what to keep alive or revive
is the choice of a mother board with as many extension slots and ports as possible.
So it will allow testing and reviving of various devices like parallel printers, IEE1394
or SCSI devices.
Dual booting with an old version of Windows or even OS2 is a good idea too.

---

### Post by mörgæs on 2019-11-01
Since all Buntus are abandoning 32 bit hardware we have to focus somewhere else. An obvious choice is Debian from which Buntu is derived.

This [Thinkpad]("https://ubuntuforums.org/showthread.php?t=1543006&page=177&p=13880989&viewfull=1#post13880989") now runs Debian 10 which can be seen by the command ```
lsb_release -a
```

```
Distributor ID: Debian
Description:    Debian GNU/Linux 11 (bullseye)
Release:        11
Codename:       bullseye

```

When connected to the internet by wire the installation goes like this: 

Download the mini.iso, for example from [here]("https://ftp.debian.org/debian/dists/bullseye/main/installer-i386/current/images/netboot/"). It's a small file, less than 50 MiB.

'Burn' it to a USB stick or CD and boot from the medium.

During install: The root account will not be enabled if one selects an empty password for root. This gives a setup like in Buntu where the first user created has the option to gain temporary root rights using sudo.

Partitioning is easiest if Debian gets permission to do it all by default but it's also possible to install into partitions created in advance. In any case it's best to stay away from LVM for a beginner and just choose normal logical partitions.

At the end a list offering a number of desktop environments is shown. I chose Mate but other options are worth trying, too. 

Reboot and you should be ready to go. 

The only tweaking I had to do after install was setting swappiness to 10 as described [here]("https://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289").

During boot the display goes through a number of garbled spasms but from the login screen onwards everything is fine.

---

### Post by Artim on 2019-11-02
I have [COLOR=#0000cd]**antiX**[/COLOR] running on a reeeeeally old 32-bit Dell with 512 RAM.  Based on Debian and systemd-free, it's plenty nimble and quick, even with Xfce added.

---

### Post by jago25_98 on 2019-11-27
Question: If I boost RAM up to 4GB will it really be any faster? 

My laptop: 
2GB RAM, 64bit 2x2.16ghz, XFCE. 160gb IDE HDD. 




To be honest...
I don't have the motivation to do much work on this. 
I'd prefer to just be able to access a cloud instance to browse. Is there a cloud instance available without needing to setup remote GUI access rather than just ssh? 

After losing half my weekend I couldn't get any of these to work with the Azure trial and Xbuntu image: VNC, x11rdp, Teamviewer, ChromeRemoteDesktop

---

### Post by uRock on 2019-11-28
> **jago25_98 said:**
> Question: If I boost RAM up to 4GB will it really be any faster? 

My laptop: 
2GB RAM, 64bit 2x2.16ghz, XFCE. 160gb IDE HDD. 




To be honest...
I don't have the motivation to do much work on this. 
I'd prefer to just be able to access a cloud instance to browse. Is there a cloud instance available without needing to setup remote GUI access rather than just ssh? 

After losing half my weekend I couldn't get any of these to work with the Azure trial and Xbuntu image: VNC, x11rdp, Teamviewer, ChromeRemoteDesktop

You may want to start a support thread.

---

### Post by mörgæs on 2019-11-29
For the questions regarding memory you are welcome to ask here. Please begin with posting the results from the memory related commands in initial post.

Questions regarding cloud are better off in another thread.

---

### Post by j2ee on 2019-12-27
Ubuntu related distros will not support 32 bits, Debian is the only choice for major distros.

---

### Post by mörgæs on 2019-12-28
They won't in the future but they do today.
Lubuntu 18.04 is available for 32 bit with support until april 2021 as described in original post. 

I'm afraid that Lubuntu will fade out of people's attention after it goes medium-heavy-64-bit-only like all the other ones.

---

### Post by sudodus on 2019-12-28
> **mörgæs said:**
> They won't in the future but they do today.
Lubuntu 18.04 is available for 32 bit with support until april 2021 as described in original post. 

I'm afraid that Lubuntu will fade out of people's attention after it goes medium-heavy-64-bit-only like all the other ones.

Long ago Lubuntu's target was computers that are 12 years or newer. It is still the target, but now it means computers from 2008 and newer. Most of these computers can run 64-bit operating systems, but there are exceptions, for example netbooks with Intel Atom processors.

It is a major problem, that Ubuntu will not maintain the basic 32-bit architecture, and that several application programs have also abandoned 32-bit.

So I think it was a good decision by Lubuntu to adapt to the current situation within the Ubuntu community.

-o-

There are several other linux distros, that still make 32-bit operating systems with light-weight application programs, that can work with computers that are more than 12 years old. I think we can still use this 'old-hardware'-megathread to help people keep old computers alive, including those that are less than 12 years old and those that are more than 12 years old.

But at the same time I want to refer to the opening post, and remind of the *limit when an old or weak computer is no longer useful* for browsing the current bloated web sites.

---

### Post by GhX6GZMB on 2020-01-04
[SIZE=4]**Steps to get a HP/Compaq 6910p running with Lubuntu 19.x**[/SIZE]
 
 
 The 6910p is hardware-wise a great machine, though not up to the latest &#8222;gaming&#8220; specifications with respect to GPU performance.
 It has all necessary interfaces from birth, plus even more when you have the Port Replacement Unit, aka &#8222;docking station&#8220;. The only limiting factor is the display, which is 1280 x 800.

 It was born with Windows Vista, and often downgraded to Win XP, neither of which are viable today.

 Fortunately, it is fully supported by Ubuntu Linux and installation is much easier than with any Win flavour.

 For Ubuntu, I recommend an upgrade to 4 GB RAM, for Lubuntu 2 GB is sufficient.
 
 
 [SIZE=4]**Preparation**[/SIZE]
 
Boot into the BIOS using F10 and go to the &#8222;System Configuration&#8220; menu. Select &#8222;Boot Options&#8220;:
 
[LIST]
[*]CD-ROM Boot &#8211;     Enable
[*]MultiBoot &#8211;     Enable
[LIST]
[*]USB CD-ROM -         First
[/LIST]
  
[/LIST]
 Save, exit and boot.
 Open the DVD drive and leave it open.
 Power down.
 
 
 [SIZE=4]**Installing**[/SIZE]

 Insert your DVD containing a Ubuntu 19.xx .iso image into the DVD drive and power up the 6910p. This should start the installation process automatically.
  ***[SIZE=1]Tip: in my experience you might have to repeat this a couple of times. Apparently remnants of an older Win bootloader plays up.[/SIZE]***

 During installation, select keyboard layout (a no-brainer) and language. I recommend selecting US-English to begin with, you can change it later.
 Concerning disk partitioning, put on your thinking hat. I strongly recommend creating a swap-partition that is equal to or slghtly larger than the size of your RAM. Other partitioning is up to you.

 Installation can easily take an hour or more. Don&#8216;t be impatient.
 
 
 [SIZE=4]**Errors during Installation**[/SIZE]
 
You will experience repeated errors during installation and reboot that refer to &#8222;tpm_module&#8220;, &#8222;flip_done timed out&#8220; etc. Ignore it, this will be dealt with afterwards.

 
  [SIZE=4]**Getting Rid of the Errors**[/SIZE]
 
As soon as you have a stable boot after the installation (this takes a couple of attempts, where the annoying error mentioned above keeps reappearing), edit (as root) **/****etc/default/grub** and  
 change:
  **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash&#8220;**
 to:
  **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=SVIDEO-1:d&#8220;**
 Save.

 From a terminal then run:
  **sudo update grub**

 Reboot.

 The 6910p will now boot (original HDD: ~100 s, SSD: ~25 s) with no errors. Further installations and customizations are up to you. Enjoy your reborn 6910p.

---

### Post by mörgæs on 2020-01-05
Thanks for the advice. 

A small comment: Swap partition is only necessary if one decides to use hibernation. If not then it's fine just to let Lubuntu take care of all partitioning.

---

### Post by GhX6GZMB on 2020-01-05
> **mörgæs said:**
> Thanks for the advice. 

A small comment: Swap partition is only necessary if one decides to use hibernation. If not then it's fine just to let Lubuntu take care of all partitioning.

Agreed. But with storage so cheap nowadays, why not plan for the future? And having hibernate is really wonderful on a laptop :)

---

### Post by mörgæs on 2020-04-30
The original post has been updated with info for Lubuntu 20.04. Summing up:

All my 20.04 installs have worked without errors. This was expected as 20.04 is only a minor step away from 19.10 which is also a great release. 

The only modifications I had to do after a vanilla install was setting the privacy level in Firefox and running **sudo apt remove snapd**. Besides this it was plug and play. 

Muon seems like a good replacement for Synaptic. A nice detail is that one can take a look at the packages available without the sudo password; this is only necessary when installing.

If anybody has advice for other users they are as always welcome to post.

---

### Post by sudodus on 2020-04-30
I can confirm that the 20.04 LTS versions of Lubuntu and Xubuntu work well for me.

Please notice that there is a [Xubuntu Core iso file](https://unit193.net/xubuntu/core/), that is maintained privately by a member of the Xubuntu team. This is the smallest Ubuntu family iso file with a graphical desktop environment.

[hr][/hr]
- There is no longer a 'lubuntu-core' meta package (for 20.04), but not installing the Recommends of 'lubuntu-desktop' has a similar effect.

- There is still a 'xubuntu-core' meta package (for those who do not want to download an unofficial iso file).

So in a simple text based system (installed from the Ubuntu mini.iso  or an Ubuntu Server iso file) we can run

```

sudo apt update

sudo apt install xubuntu-core                             #  to get Xubuntu Core
# or
sudo apt install xubuntu-desktop                          #  to get Xubuntu
# or
sudo apt install lubuntu-desktop                          #  to get Lubuntu
# or
sudo apt install --no-install-recommends lubuntu-desktop  #  to get 'Lubuntu Core'

```

and get the desktop flavours with a light footprint based on Ubuntu 20.04 LTS.

---

### Post by mörgæs on 2020-04-30
Thanks for the input. 
Do you know if the mini.iso is being deprecated?

---

### Post by sudodus on 2020-04-30
I tested the Ubuntu 20.04 LTS **mini.iso** and it worked for me (but as usual only in BIOS mode, in UEFI mode you need an Ubuntu Server iso file for the same purpose).

Edit: The released version is '614' found at

[archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/20101020ubuntu614/legacy-images](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/20101020ubuntu614/legacy-images/netboot/)

We may prefer the current version at

[archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images](http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/)

But yes, it is deprecated in the context that Canonical is steering away from it (and hiding it).

The md5sum is in the parent directory.

---

### Post by danimal1968 on 2020-07-12
Hope this question is correct to post here - about the commands given in the first post of this thread to verify the installed and maximum possible RAM.  Are the results of these commands ever incorrect?  I have a 2010 Acer Aspire 5740G-6395 with 8 gigs of RAM, which I'd always understood to be the max it was capable of handling but these commands suggest the max is 16 gigs:  [COLOR=#000000][FONT=&quot]sudo dmidecode -t memory | grep -i max and [/FONT][/COLOR][COLOR=#000000][FONT=&quot]sudo lshw -short -C memory | grep -i empty


[/FONT][/COLOR]

---

### Post by cparke on 2021-04-12
I've got a Pentium III (32-bit SSE-only processor) with 512MB that I'm trying to use mostly as a X Server and VNC/RDP client, the idea being that a remote machine running is doing all the heavy lifting, and the old PC is mostly just a GUI console with some limited functionality.

To that end, I installed Trisquel Mini 9.0, which is a Lubuntu 18.04 derivative distro with the packages even further narrowed down.  I must say, just doing that was not easy, and many basic things are not working:
[LIST]
[*]The 'Ubiquity' installer for Ubuntu crashes on non-SSE2 equipment because it uses WebKitGtk to display an entertaining graphical slideshow during the installation.  Alas, WebKitGtk is in fact the back-end for some web browsers, and it is now using SSE2.  Worse, the hidden option to hide the installer slideshow during the installation is broken, and setting that causes the installer to crash (on all hardware type).  Recompiled WebKitGtk without SSE2 and was able to get the installation to finally complete! 
[*]VNC clients are behaving funny.  The remote screen displays, but mouse clicks are not recognized on the remote system.  I'm assuming that illegal instructions are happening internally in the graphical library but being handled quietly (i.e. silent errors).  The situation does seem to mess up the x11vnc server on the remote machine too! 
[*]Remote X windows are simply not displaying on the laptop.  The remote process thinks that its window is up and showing, but locally nothing has actually appeared!  Again, I'm assuming illegal instructions are happening internally in the graphical library and being handled insufficiently (i.e. silent errors) 
[/LIST]

At this point, a Raspberry Pi 3 using ARM seems to perform better than this laptop does.  It's really frustrating!  And it really isn't that the hardware isn't just as capable, but rather too many packages have introduced the newer instruction set now.  I am thinking that a full emulator like QEMU might be what these machines now need, however that sort of process needs space, memory, and speed to run an effective virtualization environment, and that is not the type of thing these machines are going to be able to handle very well; Rather, it will just make them perform even more awfully (even if that approach might actually promise even support for a virtual 64-bit environment on these machines).

What i think we really need now is a full blown 32-bit SSE-only certified Linux distro, but to do that right is going to require examining the compile flags of thousands of packages, and modifying and recompiling a good number of them to stay off the newer instruction sets.

---

### Post by exploder on 2022-11-14
Ubuntu 22.04 runs great on an old FX 6100 processor! Had to overclock it to 4.1 GHz but it's no longer slow!

---

### Post by MIJ-VI on 2022-12-15
An immensely useful resource for those who revitalize older PCs of nearly every make, model and type imaginable:

[I]"This is a project to anonymously collect hardware details of Linux-powered computers over the world and help people to collaboratively debug hardware related issues, check for Linux-compatibility and find drivers.

Probe your computer in order to participate in the project and discover your hardware in details. Share your probes with Linux developers to debug and fix problems with your computer. Please read more in our blog."[/I]

Ubuntu Hardware Database
[https://linux-hardware.org/?d=Ubuntu](https://linux-hardware.org/?d=Ubuntu)

A sample taken from the notebook in my signature:

HW probe of Dell Latitude E4310 #dd3e716d03
[https://linux-hardware.org/?probe=dd3e716d03](https://linux-hardware.org/?probe=dd3e716d03)

The Intel AX200 / Bluetooth 5.2-based mPCIe card my June 2010-era Dell Latitude E4310 was successfully further upgraded with:

MPE-AX3000H - Fenvi Technology
[https://fenvi.com/product_detail_1.html](https://fenvi.com/product_detail_1.html)

--

---

### Post by MIJ-VI on 2022-12-16
x86-64-v2

To a degree, this may be a future consideration for those choosing a GNU/Linux OS for an older PC.

[I]"Tumbleweed currently targets base x86_64 (v1) but now will be moving to x86-64-v2. By going with x86-64-v2, CPU instructions set extensions now required include CMPXCHG16B, LAHF-SAHF, POPCNT, SSE3, SSE4.1, SSE4.2, and SSSE3. This basically shifts the baseline CPU requirements to roughly Intel Nehalem era processors or AMD Bulldozer and newer. Now being able to always assume SSE4.2 / SSSE3 / etc make for better compiler targeting to newer systems.

The x86-64-v2 requirement limits the Tumbleweed CPU support to roughly Intel CPUs of the past 15 years or on the AMD side hardware within roughly the past decade.

This is a sane move for openSUSE/SUSE to make as we roll into 2023. Besides openSUSE ALP requiring x86-64-v2, RHEL9 also mandates x86-64-v2 and being eyed by other distributions too. It's at the x86-64-v3 level where AVX becomes a requirement and other newer instructions that more sharply limit the supported processors, particularly in the low-end and embedded space. But x86-64-v2 for 2023+ Linux distributions makes sense."[/I]

28 November 2022
openSUSE Tumbleweed Begins Transitioning To x86-64-v2 CPU Requirements - Phoronix
[https://www.phoronix.com/news/openSUSE-Tumbleweed-x86-64-v2](https://www.phoronix.com/news/openSUSE-Tumbleweed-x86-64-v2)
[URL="https://archive.ph/zjwuA"]https://archive.ph/zjwuA

[/URL]Things aren't so cut & dried when it comes to what a Nehalem core can support.

```
john@john-Latitude-E4310-SSD:~$ cpu-info
Packages:
    0: Intel Core i5 560M
Microarchitectures:
    2x Nehalem
Cores:
    0: 2 processors (0-1), Intel Nehalem
    1: 2 processors (2-3), Intel Nehalem
Logical processors (System ID):
    0 (0): APIC ID 0x00000000
    1 (2): APIC ID 0x00000001
    2 (1): APIC ID 0x00000004
    3 (3): APIC ID 0x00000005
john@john-Latitude-E4310-SSD:~$ 
john@john-Latitude-E4310-SSD:~$ 
john@john-Latitude-E4310-SSD:~$ lscpu
Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         36 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  4
  On-line CPU(s) list:   0-3
Vendor ID:               GenuineIntel
  Model name:            Intel(R) Core(TM) i5 CPU       M 560  @ 2.67GHz
    CPU family:          6
    Model:               37
    Thread(s) per core:  2
    Core(s) per socket:  2
    Socket(s):           1
    Stepping:            5
    Frequency boost:     enabled
    CPU max MHz:         2667.0000
    CPU min MHz:         1199.0000
    BogoMIPS:            5320.02
    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mc
                         a cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ht 
                         tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon p
                         ebs bts rep_good nopl xtopology nonstop_tsc cpuid aperf
                         mperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est t
                         m2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes l
                         ahf_lm pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpri
                         ority ept vpid dtherm ida arat flush_l1d
Virtualization features: 
  Virtualization:        VT-x
Caches (sum of all):     
  L1d:                   64 KiB (2 instances)
  L1i:                   64 KiB (2 instances)
  L2:                    512 KiB (2 instances)
  L3:                    3 MiB (1 instance)
NUMA:                    
  NUMA node(s):          1
  NUMA node0 CPU(s):     0-3
Vulnerabilities:         
  Itlb multihit:         KVM: Mitigation: VMX disabled
  L1tf:                  Mitigation; PTE Inversion; VMX conditional cache flushe
                         s, SMT vulnerable
  Mds:                   Vulnerable: Clear CPU buffers attempted, no microcode; 
                         SMT vulnerable
  Meltdown:              Mitigation; PTI
  Mmio stale data:       Unknown: No mitigations
  Retbleed:              Not affected
  Spec store bypass:     Mitigation; Speculative Store Bypass disabled via prctl
  Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer
                          sanitization
  Spectre v2:            Mitigation; Retpolines, IBPB conditional, IBRS_FW, STIB
                         P conditional, RSB filling, PBRSB-eIBRS Not affected
  Srbds:                 Not affected
  Tsx async abort:       Not affected
john@john-Latitude-E4310-SSD:~$ 
```

---

### Post by MIJ-VI on 2022-12-17
Yet another consideration in determining whether a particular older PC is worth restoring or salvaging for parts.

[I]... Requiring SSE4.1 is far less controversial than trying to mandate AVX for Blender while allows for a slightly newer baseline than the current SSE2 requirement. This could help with better performance of Blender and also shorter build times since right now the Blender Cycles renderer compiles separate kernels for SSE2, SSE3, SSE41, AVX, and AVX2. 

SSE4.1 has been around since Intel's 45nm "Penryn" processors in 2007. For AMD processors it's with Bulldozer and newer having full SSE4.1 support. ...
[/I]
9 December 2022
Blender Eyes Raising Its CPU Requirements - Phoronix
[https://www.phoronix.com/news/Blender-Eyes-Raising-CPUs](https://www.phoronix.com/news/Blender-Eyes-Raising-CPUs)

--

---

### Post by him610 on 2024-02-11
> Yet another consideration in determining whether a particular older PC is worth restoring or salvaging for parts.

Our local township has a recycle facility that accepts usable and unusable computers and other electronics. They, in turn, turn them over to a firm that recovers the salvageable parts for reuse. I have [s]two or[/s] three computers that I am dropping off this week.

---

### Post by mörgæs on 2024-11-28
Hi all, a voice from the past...

The switch to Discourse is soon coming up. I don't know if there is room for a thread like this on the new platform but if so: Would anyone be interested in adopting, moving and maintaining Old Hardware?

Myself, I stopped using Buntu as Snap entered the scene. My only activity in the forum has been editing this thread once in a while.

Debian is now my distro of choice for both old and new. None of the Buntus qualify as lightweight today so naturally Debian is also the focus of Old Hardware.

I'm aware that this sounds like a Nigeria letter. Anyway, if interested then feel free to send me a message.

---

