---
title: "Accidentally Removed Gnome"
date: 2019-06-29
forum: General Help
---

### Post by cliffflip on 2019-06-29
Hi, I made a fatal mistake when trying to install some fan monitoring app in Ubuntu 19.04, and now gnome is wiped out leaving me only with shell interface. I've tried to use *sudo apt install ubuntu-gnome-desktop *but returned with "unmet dependencies" for other things e.g. "ubuntu-desktop". 

I just want to know is there's a way to restore the OS or at least recover the data after I freshly reinstalled Ubuntu. As I use this PC for Plex and scanning those files will take >10 hours at least. 

Thanks in advance

---

### Post by coffeecat on 2019-06-29
You need the metapackage ubuntu-desktop, not ubuntu-gnome-desktop. Since gnome became the default desktop for Ubuntu, replacing Unity, the metapackage ubuntu-desktop has brought in the necessary gnome packages as dependencies, rather than Unity. The package ubuntu-gnome-desktop is in the Universe repository, and was used - I believe - for when there was a separate Ubuntu Gnome flavour. I don't know why it's in the repositories for 18.04 and later. 

So, try:

```
sudo apt install ubuntu-desktop
```

See if that works without errors.

---

### Post by cruzer001 on 2019-06-29
Hello
Have you tried
```
sudo dpkg --configure -a && sudo apt -f install
```
Please post any errors.

---

### Post by cliffflip on 2019-06-29
Thanks for the replies!

> **coffeecat said:**
> You need the metapackage ubuntu-desktop, not ubuntu-gnome-desktop. Since gnome became the default desktop for Ubuntu, replacing Unity, the metapackage ubuntu-desktop has brought in the necessary gnome packages as dependencies, rather than Unity. The package ubuntu-gnome-desktop is in the Universe repository, and was used - I believe - for when there was a separate Ubuntu Gnome flavour. I don't know why it's in the repositories for 18.04 and later. 

So, try:

```
sudo apt install ubuntu-desktop
```

See if that works without errors.

This returns with a lot more "unmet dependencies", with this message at the end of it "unable to correct problems, you have held broken packages".

> **cruzer001 said:**
> Hello
Have you tried
```
sudo dpkg --configure -a && sudo apt -f install
```
Please post any errors.

This brings a list of removed packages. Is there any way to restore them?

---

### Post by cruzer001 on 2019-06-29
Please post the output of those commands and what happens if you try to update?
```
sudo apt update
```

---

### Post by coffeecat on 2019-06-29
> **cliffflip said:**
> 
This returns with a lot more "unmet dependencies", with this message at the end of it "unable to correct problems, you have held broken packages".


If when trying to re-install the metapackage ubuntu-desktop, you get such a message, then I think you have a serious problem. That's assuming your Ubuntu 19.04 is/was vanilla Ubuntu 19.04. The packagae ubuntu-desktop is at the heart of the installed gnome desktop in recent releases of Ubuntu. Perhaps you should confirm - you do have standard Ubuntu 19.04, not some sort of respin, or other flavour, or Ubuntu with a load of other desktops added?

It would be useful for those trying to help you, if you could give more details of the fan monitoring app, how you were installing it, and what the fatal mistake was. Also, the output of this command will give helpful information:

```
sudo apt update
```

Please post the output - all of it - between BBCode [noparse]```
 and 
```[/noparse] tags. There's a link in my sig if you need to know how.

And finally, cruzer001 asked you to post the output of the command they suggested, not a digest. That is all invaluable information for diagnosing your problem. Code tags as well, please.

---

### Post by cliffflip on 2019-06-29
I'm sorry I'm switching between my Windows PC (where I write this) and Ubuntu (which only has shell interface, no GUI whatsoever) with the same monitor. I'm kinda panic so once again I'm sorry.
Yes this is standard Ubuntu, default flavor with no additional desktops.

It started when I want to install lm-sensors, basically I'm stupidly followed [this post]("https://askubuntu.com/questions/1144976/libsensors5-or-libsensors-config-upgrade-problem") except it's "lm-sensors", not "sysstat" at the beginning. After that :

```
sudo apt install libsensors5
```

and it returns with :

```
The following packages have unmet dependencies.
 libsensors5 : Depends: libsensors-config but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

So I install it with :

```
sudo apt install libsensors-config
```

it returns with a list of packages and I chose to continue. After that completed I notice some apps like Files and Steam are gone but I can still use GUI apps like Firefox. After reboot, even login screen is in shell interface.


This is the shot from
```
sudo dpkg --configure -a && sudo apt -f install
```
[https://imgur.com/CMsOQ9z](https://imgur.com/CMsOQ9z)

And this is from
```
sudo apt update
```
[https://imgur.com/g9IaMyU](https://imgur.com/g9IaMyU)

---

### Post by HermanAB on 2019-06-29
Hmm, it may be easier to install something simpler, such as XFCE or LXDE, then figure out what to do with Gnome at your leisure.

---

### Post by TheFu on 2019-06-29
> **cruzer001 said:**
>  
```
sudo dpkg --configure -a && sudo apt -f install
```
Please post any errors.

Please post any errors.  Not the description of errors, but he actual errors.  These people are trying to help and need the facts. Text and code tags are preferred over images.


Please.

---

### Post by cliffflip on 2019-06-29
> **TheFu said:**
> Please post any errors.  Not the description of errors, but he actual errors.  These people are trying to help and need the facts. Text and code tags are preferred over images.


Please.

This is the shot from
```
sudo dpkg --configure -a && sudo apt -f install
```
[https://imgur.com/CMsOQ9z](https://imgur.com/CMsOQ9z)

I'm sorry a shot from my phone's camera is the best I can do right now

---

### Post by cliffflip on 2019-06-29
> **HermanAB said:**
> Hmm, it may be easier to install something simpler, such as XFCE or LXDE, then figure out what to do with Gnome at your leisure.

I've tried installing them (and others too), all of it returns with endless "E: Unable to correct problems, you have held broken packages."
The closest to success is with xfce, but after reboot it failed to run gpu-manager.service & lightdm.service


I give up, I'll do fresh install, thanks for all your help :)

---

### Post by TheFu on 2019-06-29
> **cliffflip said:**
> This is the shot from
```
sudo dpkg --configure -a && sudo apt -f install
```
[https://imgur.com/CMsOQ9z](https://imgur.com/CMsOQ9z)

I'm sorry a shot from my phone's camera is the best I can do right now
If it was me, I'd 
* backup /var/lib/plex* 
* backup /etc/
* backup /home/
* create a list of **MANUALLY** installed packages using **apt-mark**, save that list to a file
* backup that list of packages
* disconnect any non-OS drives from the system to prevent accidents
before doing a fresh install.

There could be other places that I'd want to backup too. What to backup would depend on where data is stored.

After the install, I'd put the data back where it is expected to be, with the expected permissions, owner, group, any ACLs. Then I'd install the programs from the list made using apt-mark. Since the settings and data are already restored from the restore, the installed packages should see that and use the prior settings. 

BTW, I wouldn't install 19.04 for a plex server.  I'd use 18.04, which is an LTS release.  Many reasons for that choice.  New is the enemy of stable.  19.04 is VERY new and not an LTS release.

IMHO.

When new to Unix, people often don't know some techniques for moving data or connecting from other systems.
We can redirect the output from CLI programs into files and sneaker*net them over to Windows with a flash drive or send the files to other systems using any of the network tools like ssh, sftp, scp, rsync.
An example:
```
sudo dpkg --configure -a && sudo apt -f install | tee /tmp/log-of-stuff
```

There are two types of output, stdout (1) and stderr (2). The numbers are file descriptors.  This applies to Windows and every Unix, including Linux, iOS, Android.  Redirecting output can redirect one or the other or both. Often, just getting stdout is sufficient. That's what happens in the example above.  To get both, use 
```
sudo dpkg --configure -a && sudo apt -f install  **2>&1 |** tee /tmp/log-of-stuff
```
That's the important part.

Something like this will be needed to capture the **apt-mark showmanual > pkgs_manual.lst** output for that backup above. Then during the restore, that file would be fed back into apt-mark.
```
sudo apt-mark manual $(cat pkgs_manual.lst)
sudo apt-get -u dselect-upgrade
```
Easy-peasy.

One of the first tools I install on every Unix system is openssh-server.  Then it can be access by pretty much any client system with a network over ssh.  Window people tend to use Putty, then copy/paste the text. ssh is one of those tools used by Unix people daily, constantly, that we forget non-Unix people don't know about how amazing it is.  Of course, ssh only works when it is already installed.  On a system with broken package management, I don't know how to install an ssh server. ;(

There are lots of other normally used CLI techniques that the point-n-click crowd doesn't learn. Having a few already learned can be extremely helpful.

Anyway, I know there's a bunch of stuff above. Hopefully, it is helpful, not confusing.

---

### Post by cruzer001 on 2019-06-29
To add to TheFu's post.

When working in console (tty) you must first save the command output to a file (as TheFu has pointed out).  The commands I use will do the same thing as tee, just a matter of user preference for me.

[https://askubuntu.com/questions/420981/how-do-i-save-terminal-output-to-a-file/731237](https://askubuntu.com/questions/420981/how-do-i-save-terminal-output-to-a-file/731237)

Then you can upload the file to Pastebin.  This requires pastebinit to be installed, another thing that cannot be done on your broken system.  I would add it when your up and running again, better than using your camera if ever needed.

[https://wiki.ubuntu.com/Pastebin](https://wiki.ubuntu.com/Pastebin)

I assume you decided to reinstall, so I bid you good luck.  If that is what worked for you, then don't forget to mark this thread solved (in the Thread-Tools).

---

### Post by cliffflip on 2019-06-29
Thanks a lot TheFu and cruzer001!

I've copied your posts to my notepad, those are super helpful to know! But I'm sorry it's 11PM in Jakarta when I write my last post (GMT+7) so I was looking faster solution and leave Plex scanning while I sleep. But hey, at least I get everything working again ;)

---

### Post by TheFu on 2019-06-30
> **cruzer001 said:**
> To add to TheFu's post.

When working in console (tty) you must first save the command output to a file (as TheFu has pointed out).  The commands I use will do the same thing as tee, just a matter of user preference for me.

[https://askubuntu.com/questions/420981/how-do-i-save-terminal-output-to-a-file/731237](https://askubuntu.com/questions/420981/how-do-i-save-terminal-output-to-a-file/731237)


Yep.  Good examples in that link.  The Art of the Command Line is full of stuff like that: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)

Redirection can be used in surprising ways.  Unix systems use programs as *filters* all the time. MS-Dos and Windows have that capability too, but it is seldom used.  I'll use it at least 30x today alone on my systems.

The reason I showed 'tee' is not seeing any output can freak out noobs.  Plus, if you need to write something redirected to a file .... like a config file, piping it through ( **| sudo tee ** ) gets passed that pesky PERMISSION DENIED issue.  In general, I don't use 'tee' for things like this thread would need, but a teaching moment was presented.

Anyways, this is solved, so that's that.

---

