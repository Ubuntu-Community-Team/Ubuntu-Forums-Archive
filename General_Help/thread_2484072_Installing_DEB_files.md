---
title: "Installing DEB files"
date: 2023-02-16
forum: General Help
---

### Post by lwalper on 2023-02-16
I've been playing with Ubuntu off and on for a number of years and would really like to move away from WinOS, but the Linux OS has always been intimidating, working from the prompt. If I'm ever going to "convert" I'm going to *have* to run some WinX software. I've never been happy with WINE and have settled on running WinXP in a VM. I have downloaded the *.deb file for VirtualBox, but have no idea how to install it. Certainly there must be a basic instructable somewhere for installing software in Ubuntu. [COLOR=#ff0000]***HELP!***[/COLOR] The [installation instructions]("https://www.virtualbox.org/wiki/Linux_Downloads") on the VirtualBox site don't seem to work as described. I'm sure it's my own idiocy showing, but "copy/paste" ain't cuttin' it.

---

### Post by ian-weisser on 2023-02-16
One easy way:

Step 1: Undo EVERYTHING you already did that's "not working." Undo EVERY step of installing virtualbox so far. Don't ignore it. Don't leave it behind. Figure out how (you're smart) and undo it so like never happened.

Step 2: Enable the Universe repository
             Then run 'sudo apt update' because you just changes your apt sources

Step 3: sudo apt install virtualbox

Advice: Get out of the Windows habit of looking on random websites for your software. That habit will destroy your Ubuntu system.

---

### Post by lwalper on 2023-02-16
Well then, I just may be in a mess. I installed Gdebi and then installed the downloaded *.deb file I got from VirtualBox. Uninstalling may be a problem, since the app doesn't show in the list of installed applications to uninstall. Hmmm??? What's next?

---

### Post by lwalper on 2023-02-16
I have
1. enabled the Universe repository
2. ran "[FONT=inherit]sudo apt-get update"
[/FONT]3. ran "[COLOR=#000000]sudo apt install virtualbox" hopoing it would overwrite what I had already installed and correct any possible errors
4. Started VirtualBox and everything seemed to work OK
5. tried to install the guest VM and get errors

[/COLOR]```
[FONT=Verdana]Kernel driver not installed (rc=-1908)[/FONT]

[FONT=Verdana]The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please reinstall virtualbox-dkms package and load the kernel module by executing[/FONT]

[FONT=Verdana]'modprobe vboxdrv'[/FONT]

[FONT=Verdana]as root.[/FONT]

[FONT=Verdana]If your system has EFI Secure Boot enabled you may also need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them. Please see your Linux system's documentation for more information.[/FONT]

[FONT=Verdana]where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.[/FONT]
```

--------------
Need to sign kernel modules??? That'll be a new one for me.

---

### Post by ian-weisser on 2023-02-17
> **lwalper said:**
> 
3. ran "[COLOR=#000000]sudo apt install virtualbox" hopoing it would overwrite what I had already installed and correct any possible errors
[/COLOR]

I warned you specifically against doing that. Now you know why.

You need to go back into those source files that you changed (following the Oracle instructions) and change them back. And you need to identify and uninstall the Oracle packages from that non-Ubuntu source. Both need to happen, or you are stuck. The easiest way to do both is to bite the bullet and learn to use the Terminal. Sorry, but that's the best advice. Gdebi and Ubuntu Software simply won't get you there.

Installing non-Ubuntu software (like virtualbox directly for Oracle) is not a beginner activity. It's an advanced activity that requires terminal familiarity and an understanding of how deb sources and packages work. Goodness, you have the kernel and Secure Boot involved, too. Hence your problem. Unfortunately, cleaning up a botched non-Ubuntu install is also advanced.

Try again:

1. Rid your system of the Oracle apt sources

2. Use apt to locate and remove the Oracle-provided packages

---

### Post by MAFoElffen on 2023-02-17
*Please go back to Post #4, Edit > Advanced Reply > Select the text of the raw output in that post > Select the "#" icon > Save post. All posted raw output and commands should be wrapped with Code tags...

The Oracle version and the repo version cannot coexist. Bad JuJu. They have conflicting binaries with similar names... When both are there, they get "confused."

Run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") to display what is in the current sources list, extended sources.d list and what was manually installed packages. Please post the URL of where it uploads the report to a pastebin. That will give Ian the information on recommending if you need to repair your sources list...

Additionally, open your filemanager, and rightclick on the Downloads folder (or wherever you downloaded that .deb file to). Select "Open In Terminal". Post the output of 
```

ls ./*.deb

```
In your post, wrapped with code tags... To do that go to advanced reply, and press the "#" icon, then copy / paste the output within those code tags.

That will give Ian the "name" of the deb file with you installed, so it can be removed via
```

dpkg -r <deb_file_name.deb>

```
Then post the contents of /var/log/apt/term.log and  /var/log/apt/history.log ... (Again, within code tags) So we can review  what you did and what exactly got installed... so we can make a plan to  get you back to a clean start.

Then you will have to remove/purge virtualbox package... 
```

sudo apt remove --purge virtualbox

```
Getting that report URL, so we can review it, then repairing your sources.list, if needed...

Then we can lead you back to installing virtualbox fresh. Or maybe even talk you into installing KVM instead. It already has virtualization support directly from the Linux Kernel without having to install outside vbox kernel module and dkms support. But that is your choice.

Please do that, so we can get you back to a good starting point.

---

### Post by lwalper on 2023-02-17
OK, thanks. I'll give it a try.

---

### Post by TheFu on 2023-02-17
> **lwalper said:**
> Well then, I just may be in a mess. I installed Gdebi and then installed the downloaded *.deb file I got from VirtualBox. Uninstalling may be a problem, since the app doesn't show in the list of installed applications to uninstall. Hmmm??? What's next?

Actually, installing .deb files directly is a good way to make your system get into "dependency hell" where nothing can be updated after a few months.  Some programming+packaging teams are careful and keep migrating their code for new core libraries and those will avoid this "dependence hell", but most do not.

There are 2 versions of Virtualbox.  
a) The version in the Ubuntu Repos contains the F/LOSS version.
b) The version gotten from virtualbox.org containers the Oracle version which has non-free software inside it. Carefully read the license agreements.

The Oracle version tends to work best according to people still using it. Take ian-weisser's warning about the complexities seriously. It is possible to integrate the Oracle version into APT using their PPA, which will get updates from that add-on repo automatically, as released.  [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) has instructions for adding the PPA ... it is the Debian version with a gpg line.  As a beginner, probably best to avoid this version.

But to answer the subject question, there are a few different ways to install programs.  Linux isn't like MS-Windows.  Anyone can create an installation program, so we have lots of choices.  I've heard of Gdebi, but have never used it.  
If we have a package-6.01.deb file to be installed in our CWD - current working directory, there are a few ways.
```
sudo apt -i ./package-6.01.deb
```
without the ./ in the path or the correct relative or absolute path to the downloaded .deb file, 'apt' will assume you want to get the package from a repo.
or
```
sudo dpkg -i ./package-6.01.deb
```
There are other methods.
dpkg doesn't handle dependencies. 'apt' does.

The ./ says "in this directory".   Linux uses directory paths just like Windows does, so there's nothing new to learn there, assuming you learned the difference between a relative path and an absolute path on Windows.  In fact, MS-Windows actually supports using the '/' character instead of the '\' character everywhere a path can/would be entered, so the are really exactly the same.  Directory hierarchies work the same, so how we point at files works the same.

Every .deb file that you manually install needs to be kept in a list, because when you get into "dependency hell", you'll need to remove them until that problem is solved.  The alternative is to to plan on a fresh re-install of the OS when the problem happens.  Reinstalling the OS is about 15 minutes, putting your data and settings back is probably another 15 minutes, then installing the previously installed packaged software another 15 minutes, so that's about 45 minutes every 3-9 months.  Or just use software in the repos + trusted PPAs.  Then you'll probably not need to reinstall or track any manually installed .deb files before you need/want to move to a new LTS release - between 2 and 4 yrs from now.  Life is much easier.

BTW, manually pulling software directly off the interent to be installed, including drivers, is asking for problems.  99% of users shouldn't grab video drivers from the GPU maker's websites.  Let the "Additional Drivers" tool find what you need and install it.  There are exceptions for a few people, but it you stay away from bleeding edge hardware, hopefully, it won't be you.  Life is much easier if we avoid hardware that doesn't have built-in Linux kernel support.

**Most beginners should get all their software through the "Software Center" tool included with most Linux distros.**

---

### Post by SeijiSensei on 2023-02-17
Mandatory suggestion that you dump VirtualBox in favor the built-in KVM facility.

[https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)

It's part of the kernel so it will always be available and up-to-date on Linux machines.

---

### Post by vendax on 2023-02-17
KVM is just the kernel module he would need something like Virtual Machine Manager to have a GUI somewhat like VirtualBox.

Even then, many novices would prefer the GUI of Virtualbox. It is also known to 'just work' on many systems, whereis a KVM+Virtmanager would require a lot of setup to get working right. For example, the nice shared folder functionality of virtualbox is easy to setup. But when going the KVM/QEMU/Virtmanager route this requires additional configuration.

Also, installing virtualbox using apt means you get an older version. In Windows it is so simple, go to virtualbox.org, click download, double click .exe and afterwards you launch program and it works. On Linux it often means you have to spend many hours/days/weeks to get things working the way you want to.

Some tip: ubuntu supports ZFS during installation. If you use ZFS, you can easily rollback to an earlier state back in time. Like timemachine on Apple-systems i guess though i haven't tried that. It means newbies can try things and when the system screws up, they can rollback and undo all their changes.

---

### Post by monkeybrain20122 on 2023-02-17
You shouldn't just download the .deb. Instead you should set up the VB repository and install it with apt like other software. That way you will get updates when a new version is available. 

The instruction is here [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by monkeybrain20122 on 2023-02-17
> **vendax said:**
> 


Also, installing virtualbox using apt means you get an older version. In Windows it is so simple, go to virtualbox.org, click download, double click .exe and afterwards you launch program and it works. On Linux it often means you have to spend many hours/days/weeks to get things working the way you want to.


Not if you add Oracle's repository, in that case you get the latest version with apt. VB is simple to set up on Linux if one follows the instructions on Oracle's download page. If you spent hours/days/weeks to set it up you are doing something very wrong.

Virtmanager is a very simple gui. I don't see why that is more complicated than VB's gui. However I do agree that setting up shared folders is a bit of a pain. I think those who recommend it for new users should give some simple instructions (there are tutorials on the internet but many are outdated and make it unnecessary complicated, it is a bit of work to wade through them)

I use kvm for Linux guests (in Ubuntu) but TBH I don't find much difference between VB and KVM for Windows guest in terms of performance. However kvm is optimized for Linux guests. My problem with VB was it tried to make python2 the default python so that was a show stopper for me and I had no need for it anyway. That was in 16.04 or 20.04, not sure if it is still the case since I haven't used it (I have no more need for the  Windows VM)

---

### Post by MAFoElffen on 2023-02-17
Lets separate the question of support here... One, the OP has a mixed installation of Repo and Oracle version of VirtualBox. That is when I saw this thread and said to myself--- Ah oh, that is not good. He needs help to get back to square one.

After that he can decide if he wants to go with the Oracle Version of VirtualBox, the Ubuntu Repo version of VirtualBox, or KVM. He just wants to run Windows XP. It is not a big ask. He needs to be lead through and helped with sound instructions, and advice. His recent posts demonstrate that he needs instructions on going from A to B, without skipping to C... Clear and concise, "Do this first".

Sidenote: Even though I am a promoter of ZFS... At this time, I would not recommend ZFS to a user that does not have a certain level of skills to use it and maintain it. The future of ZFS in Ubuntu is now a bit "questionable" for the next LTS cycle. Me and a few others are fighting for it's continued use and growth with Ubuntu. (Time will tell how ZFS goes with Ubuntu and it's future.) We will see where that goes, but that is afterthoughts to what is going on here. 

I don't care what the OP wants, I will help him get there, in a sound manner. My personal opinions and use would lean towards KVM, but that is based on a lot different experience and skillset. I have experience with many virtual host systems, but the decision for which one is best for the OP is his own personal decision.

Lets focus on getting him back to a point where his system is healthy and sound... and go from there.

---

### Post by lwalper on 2023-02-17
Output of ...

```
leslie@leslie-OptiPlex-9020:~/Downloads$ ls ./*.deb./virtualbox-7.0_7.0.6-155176_Ubuntu_jammy_amd64.deb

```

```
leslie@leslie-OptiPlex-9020:~/Downloads$ dpkg -r virtualbox-7.0_7.0.6-155176_Ubuntu_jammy_amd64.debdpkg: error: requested operation requires superuser privilege

```

It looks like I'm one step to completion. Ooops, an error -- need superuser privilege ... whatever that is??

---

### Post by MAFoElffen on 2023-02-17
Do:
```

sudo dpkg -r ./virtualbox-7.0_7.0.6-155176_Ubuntu_jammy_amd64.deb

```
Then do
```

sudo apt remove --purge virtualbox

```

---

### Post by ajgreeny on 2023-02-17
My suggestion may at first appear to be adding an application simply to remove another one but I think if you install **synaptic package manager** with command ```
sudo apt install synaptic
``` you will find it much easier to deal with the sort of situation you seem to have got yourself into.

Synaptic was the default package manager for Ubuntu and the only GUI one available in the first few years of Ubuntu. It allows you to search for packages in the repos by type or by name alone and shows those installed making it much easier sometimes to find a package and particularly to remove unwanted packages as you are being told to do.
Incidentally, packages installed using gdebi will show in synaptic though I have no idea about the other GUI package managers as I have never used any of them.

As an example, if you use synaptic to search for virtualbox by name alone it will show many packages that are available in the Ubuntu repos. If you add the Oracle Virtualbox repos as detailed in the ***Debian-based Linux distributions*** section of [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) you will see the Oracle versions of Virtualbox-6.1 as well as some older Ubuntu repos versions in synaptic.

You will also see virtualbox-7 is available direct from Oracle but not yet from the Oracle Virtualbox repos so there is as yet no way to keep Virtualbox-7 automatically updated as you can Virtualbox-6.1.
This is all a bit confusing I agree but I would advise you to try the 6.1 version for a start either most simply from the standard Ubuntu repos or if you want easier upgrading, after adding the Oracle virtualbox repos as mentioned above.

---

### Post by lwalper on 2023-02-17
Synaptic? Now THAT's the ticket!! Worked like a charm -- I guess?

Since there's really not much on this OS as of yet (except a messed up installation of VirtualBox) I think I'll just format the partition and start again with a clean install. I'll be back.

---

### Post by ian-weisser on 2023-02-18
> **lwalper said:**
> Synaptic? Now THAT's the ticket!! Worked like a charm -- I guess?

Since there's really not much on this OS as of yet (except a messed up installation of VirtualBox) I think I'll just format the partition and start again with a clean install. I'll be back.

That's a smart decision for you: It's a path you have trod and understand. It involves no mysterious incantations.

A new install (or, once you get it working, a VM) is a fabulous learning and tinkering opportunity.

On a new install, it's generally as easy as `sudo apt install virtualbox` to install the application from the Ubuntu repositories.

As you have seen, there are lots of options. My advice is to make for first try *successful* rather than *perfect*. You can always experiment with different applications and different ways of doing things, and it's always nice to know that you have one easy way that is reliably successful.

After a couple successes, it gets easier!

---

### Post by MAFoElffen on 2023-02-18
+1 with ian-weiser

Over 17-18 years ago, I started learning about using virtual machines with programs like MS Virtual PC, QEMU, VirtualBox and VMware Virtual Player. Using them taught me a lot about virtual machines.. Gaining experience with those lead me to use XEN, KVM, ESXi, vSphere, Hyper-V and KVM. It's been a fun an worthwhile learning experience.

I, for one, welcome you to that journey and experience. If you have and questions or need any help, do not hesitate to ask. On questions about Virtualization, this forum has a Virtualization Section, where there are people there with a lot of varied experience and knowledge to share.

---

### Post by lwalper on 2023-02-18
I'm back -- with a clean install of 22.04.1 -- and actually on the correct partition. Hooray!

Since I still want to do virtualization with WinXP, from consensus it appears that VirtualBox is "old news" with people favoring KVM with some sort of GUI. When I look for KVM all I see are a "frontend" -- that's the GUI I suppose. Installing a backend may be a trick? Guess I need to go to the virtualization forum. Thanks for all your help on this issue!

---

### Post by monkeybrain20122 on 2023-02-18
> **lwalper said:**
> I'm back -- with a clean install of 22.04.1 -- and actually on the correct partition. Hooray!

Since I still want to do virtualization with WinXP, from consensus it appears that VirtualBox is "old news" with people favoring KVM with some sort of GUI. When I look for KVM all I see are a "frontend" -- that's the GUI I suppose. Installing a backend may be a trick? Guess I need to go to the virtualization forum. Thanks for all your help on this issue!

If you just want to get things up and running fast VB is the way to go. If you want to learn virtualization go kvm.

Just follow the instructions here [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

The version "6.1" may be old, so adjust the apt install command accordingly or  get synaptic, reload and see which version is available (it seems that 7.0.6 is the current version from the website's front page). Look at the description in synaptic to make sure you choose the oracle version instead of the "community version" from Ubuntu.

Then don't forget to install the extension pack after you get VB [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads), just click download and VB should open and install it for you.

kvm is cool but I don't think it is suitable for beginner who just wants to get things up and running fast. To set up shared folders in kvm is quite complicated for new users. It is super simple for VB. In any case you are running Windows xp and kvm is more optimized for Linux guests. Some most interesting features won't work for Windows guests anyway.

---

### Post by lwalper on 2023-02-18
> **MAFoElffen said:**
> Lets separate the question of support here... One, the OP has a mixed installation of Repo and Oracle version of VirtualBox. That is when I saw this thread and said to myself--- Ah oh, that is not good. He needs help to get back to square one.

After that he can decide if he wants to go with the Oracle Version of VirtualBox, the Ubuntu Repo version of VirtualBox, or KVM. He just wants to run Windows XP. It is not a big ask. He needs to be lead through and helped with sound instructions, and advice. His recent posts demonstrate that he needs instructions on going from A to B, without skipping to C... Clear and concise, "Do this first".

Sidenote: Even though I am a promoter of ZFS... At this time, I would not recommend ZFS to a user that does not have a certain level of skills to use it and maintain it. The future of ZFS in Ubuntu is now a bit "questionable" for the next LTS cycle. Me and a few others are fighting for it's continued use and growth with Ubuntu. (Time will tell how ZFS goes with Ubuntu and it's future.) We will see where that goes, but that is afterthoughts to what is going on here. 

I don't care what the OP wants, I will help him get there, in a sound manner. My personal opinions and use would lean towards KVM, but that is based on a lot different experience and skillset. I have experience with many virtual host systems, but the decision for which one is best for the OP is his own personal decision.

Lets focus on getting him back to a point where his system is healthy and sound... and go from there.

So, ZFS? What's not to like about being able to easily backward to a previous state? I've got that set up in WinXX and have needed to use it on occasion -- glad it was there.

BTW -- I have installed VB using synaptic -- so far so good. Have not tried installing WinXP yet. That's next.

---

### Post by lwalper on 2023-02-18
Up and running! GREAT! My 20+ years old software runs perfectly. Had some glitches in Win10. Thanks all.

---

### Post by Paulgirardin on 2023-02-20
I'm going to stick my nose in here to add:

If you use Gdebi to install a .deb file you can right click on the .deb file again and open with Gdebi (again) and you will see the option to uninstall . I have used that but do not know if it reverts all changes.

If you want an easy VM using KVM ,use Gnome Boxes.
 I have used VB and Gnome Boxes and the latter is way easier to set up.
[https://apps.gnome.org/app/org.gnome.Boxes/](https://apps.gnome.org/app/org.gnome.Boxes/)

Instead of using ZFS for snapshots ,why not use Timeshift - the Linux equivalent of Apple's time machine.
[https://github.com/linuxmint/timeshift](https://github.com/linuxmint/timeshift)

---

