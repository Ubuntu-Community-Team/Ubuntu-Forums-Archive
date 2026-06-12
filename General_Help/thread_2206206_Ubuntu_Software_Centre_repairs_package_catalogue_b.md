---
title: "Ubuntu Software Centre repairs package catalogue but deletes Skype"
date: 2014-02-17
forum: General Help
---

### Post by desconocido on 2014-02-17
I have a new computer which has the amd64 version of Ubuntu 12.04.3 installed. (Also has unity and unity2d removed and gnome-shell installed - I use Gnome Classic.)

Attempts to install FreeWRL led to dependencies getting tangled (details in another thread).
Finally apt-get says
"E: Unable to correct problems, you have held broken packages."

Running Ubuntu Software Centre leads to a message something like
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=250114&d=1391607257[/IMG]

So I said yes.

However the Update Manager decided to remove more than I wanted (see attachment).
It removed Skype as well and I cannot reinstall it:

```
$ sudo  gdebi skype-ubuntu-precise_4.2.0.13-1_i386.deb 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 
This package is uninstallable
Cannot install 'libqtgui4:i386'

```

I can't install Wine either for similar reasons.

Is there any way of restoring my missing :i386 packages without reinstalling Ubuntu yet again?

---

### Post by ibjsb4 on 2014-02-17
You seem to be plagued with problems.  You just fixed skype a week ago.

From what I make of your post you have installed the gnome-shell ppa and run gnome-classic.

Maybe you need to try a different install method.

You could do a standard install and add gnome-classic to it.

```
sudo apt-get install gnome-panel
```

That command would add the classic desktop without using the ppa.  I would also suggest using metacity (no-effects), compiz can be problematic.

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by deadflowr on 2014-02-18
Do you think maybe following the advice that was posted in your other thread on installing skype from the partner repos instead jumping through the same hoops with a package that keeps causing problems might be a better solution at this point?

---

### Post by al3arbe1 on 2014-02-18
Your use 64bit ?
Try
```
sudo dpkg --add-architecture i386 && sudo apt-get update
```

---

### Post by desconocido on 2014-02-18
> **ibjsb4 said:**
> You seem to be plagued with problems.  You just fixed skype a week ago.
Yes, but I fixed it by re-installing Ubuntu!

> 
You could do a standard install and add gnome-classic to it.

sudo apt-get install gnome-panel

That command would add the classic desktop without using the ppa.  I would also suggest using metacity (no-effects), compiz can be problematic.

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

Yes, although I have now got on top of the desktop problems. Do you think the ppa might be causing my dependency problems? The link is excellent, I wish I had found it a month ago.

---

### Post by desconocido on 2014-02-18
> **deadflowr said:**
> Do you think maybe following the advice that was posted in your other thread on installing skype from the partner repos instead jumping through the same hoops with a package that keeps causing problems might be a better solution at this point?
Thanks, could you point me to exactly where that advice was (I have more than one thread about 12.04 problems).

---

### Post by desconocido on 2014-02-20
> **deadflowr said:**
> Do you think maybe following the advice that was posted in your other thread on installing skype from the partner repos instead jumping through the same hoops with a package that keeps causing problems might be a better solution at this point?
Ah, maybe that was the bit in the [thread]("http://ubuntuforums.org/showthread.php?t=2203319") where you say
> Skype is in the Partners repo. Instead of trying to reinstall those i386 libs I would just try to install Skype with synaptic. In Precise you should install ia32 for 32 bit program in 64 bit platform.
I found the bit in Update Manager settings where you can turn "Canonical Partners" on (see attachment).
Now:
```
 sudo  apt-get update
...
$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.
```

I found some useful info on askubuntu.com:

[http://askubuntu.com/questions/7498/how-do-i-install-skype]("http://askubuntu.com/questions/7498/how-do-i-install-skype")
[http://askubuntu.com/questions/284725/install-skype-on-ubuntu-12-04-lts-64-bit]("http://askubuntu.com/questions/284725/install-skype-on-ubuntu-12-04-lts-64-bit")

However, it looks like I'm going to have to re-install Ubuntu again, but probably not until the weekend.

---

### Post by deadflowr on 2014-02-20
> **desconocido said:**
> Ah, maybe that was the bit in the [thread]("http://ubuntuforums.org/showthread.php?t=2203319") where you say
> Skype is in the Partners repo. Instead of trying to reinstall those i386  libs I would just try to install Skype with synaptic. In Precise you  should install ia32 for 32 bit program in 64 bit platform.                      


That wasn't me, but yes.

This might give a good reason to use the one in the repos,
from here
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)
> It is highly recommended to use the package provided in the Canonical  partner repository, not the one distributed from the skype website, as  the skype website currently points users to the wrong package for 64-bit  systems of Ubuntu 11.10 and above

---

### Post by desconocido on 2014-02-24
> **ibjsb4 said:**
> 
From what I make of your post you have installed the gnome-shell ppa and run gnome-classic.

Maybe you need to try a different install method.

You could do a standard install and add gnome-classic to it.

```
sudo apt-get install gnome-panel
```

That command would add the classic desktop without using the ppa.  I would also suggest using metacity (no-effects), compiz can be problematic.

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

Yes, but when I try that on a freshly installed 12.04.3, I get:

```
$ sudo apt-get install gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-panel is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-panel' has no installation candidate

```

Am I missing something here?

---

### Post by ibjsb4 on 2014-02-24
Should of worked.

Try

```
sudo apt-get install gnome-session-fallback
```

---

### Post by desconocido on 2014-02-24
> **ibjsb4 said:**
> Should of worked.

Try

```
sudo apt-get install gnome-session-fallback
```
That didn't either. In the end I went with ```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-session-fallback

```

That seems to work fine.

---

### Post by desconocido on 2014-03-04
> **deadflowr said:**
> This might give a good reason to use the one in the repos,
from here
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

I have finally got Skype working again. See my post at [http://ubuntuforums.org/showthread.php?t=2208261&page=2&p=12946625#post12946625]("http://ubuntuforums.org/showthread.php?t=2208261&page=2&p=12946625#post12946625")

In fact, I found it impossible to find Skype through USC, even with the Partners source ticked. 

In the end I went back to my previous approach.

I went to [http://www.skype.com/en/download-skype/skype-for-linux/]("http://www.skype.com/en/download-skype/skype-for-linux/")
 I chose the option "Ubuntu 12.04 (multiarch)".
That gave me a file called "skype-ubuntu-precise_4.2.0.13-1_i386.deb"
I installed that by right-clicking on the downloaded file and chosing the option "Open with Ubuntu Software Centre".

In spite of the link you quote, Skype is running perfectly on my machine (so far). But then, it is running under 12.04, not 11.10.

---

