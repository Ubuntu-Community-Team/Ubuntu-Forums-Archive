---
title: "VIrtualbox half installed and messing things up..."
date: 2007-05-02
forum: General Help
---

### Post by juxtaposed on 2007-05-02
I tried to install VirtualBox on my Ubuntu 7.04, it started but gave me some license to agree to. I couldn't figure out how to agree to it, and I couldn't close the window. So I logged out, which closed the window. Now synaptic won't work.

> 
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


Other people seem to have a problem similar to this, and ive searched for it, but I can't seem to get it working.

> 
patrick@patrick-desktop:~$ sudo aptitude purge virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  virtualbox{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing virtualbox (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 virtualbox
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
patrick@patrick-desktop:~$ 



Any way to uninstall or remove it tells me that it is an inconsistent state and I should reinstall before removing it, but that's the whole thing, I can't install because it wouldn't let me aggree to the license.

The license window looked like the old non-gui ubuntu installer.

Any ideas on how to fix it?

---

### Post by useResa on 2007-05-02
You could try
```
dpkg --remove --force-remove-reinstreq virtualbox
```

Basically with the above command you are asking the package to be removed (the --remove option) and additionally force some extra requests.
The remove-reinstreq asks for a removal of a package even if it is broken and marked for reinstallation, which is the case in your situation.
If you like to know more about the dpkg command, there are many locations where you can find this. One example is [here]("http://www.abc.se/home/m10828/webgine1320e_linux/man__H_dpkg.html").

Hope this helps and will solve your problem.
Regards.

---

### Post by juxtaposed on 2007-05-02
> 
patrick@patrick-desktop:~$ sudo dpkg --remove --force-remove-reinstreq virtualbox
Password:
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.
116537 files and directories currently installed.)
Removing virtualbox ...



Yay, seemed to work perfectly. Thanks alot =)

"You just can't do that" is almost non existent in linux :)

---

### Post by AAM on 2007-05-04
I have had the same problem with the feisty package. Note that the screen you can't answer or leave that stuffs you up asks you to agree to installing version **1.1**!

I shall try to inform them.

---

### Post by AAM on 2007-05-04
**SOLUTION!!**
you have to scroll down the page to the bottom before the 'OK' activates! So press the down arrow until you reach the bottom and the press the 'move right' key to highlight the 'OK' and press enter!
what an idiot I feel!

---

### Post by juxtaposed on 2007-05-04
Thanks, pressing the right arrow button worked :)

Odd how the people who made it expected people to know how to do that.

---

