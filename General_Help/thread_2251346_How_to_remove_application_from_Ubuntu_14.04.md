---
title: "How to remove application from Ubuntu 14.04"
date: 2014-11-03
forum: General Help
---

### Post by Nathan_McAuley on 2014-11-03
Hi, 

new Ubuntu user. I installed some software for my wife that she needed for work. It's called activeInspire which is a teaching resource, but it didn't work in wine. 

Anyway, not to worry I don't really want her using my new computer anyway haha! 

In terminal I ran the command **sudo apt-get remove activinspire** which seemed to remove the software. 

However, in my list of applications in Ubuntu it's still there! 

Also, when I update in terminal with **sudo apt-get update** the computer searches for activeinspire and brings up the following:
[COLOR=#696969]
[/COLOR][COLOR=#696969]Ign [http://activsoftware.co.uk](http://activsoftware.co.uk) oss Release.gpg                           
Ign [http://activsoftware.co.uk](http://activsoftware.co.uk) oss Release                                     
Ign [http://activsoftware.co.uk](http://activsoftware.co.uk) precise/non-oss Translation-en_GB               
Ign [http://activsoftware.co.uk](http://activsoftware.co.uk) precise/non-oss Translation-en
Ign [http://activsoftware.co.uk](http://activsoftware.co.uk) precise/oss Translation-en_GB
Ign [http://activsoftware.co.uk](http://activsoftware.co.uk) precise/oss Translation-en
Err [http://activsoftware.co.uk](http://activsoftware.co.uk) oss/non-oss amd64 Packages
  404  Not Found
Err [http://activsoftware.co.uk](http://activsoftware.co.uk) oss/non-oss i386 Packages 
  404  Not Found
Ign [http://activsoftware.co.uk](http://activsoftware.co.uk) oss/non-oss Translation-en_GB
Ign [http://activsoftware.co.uk](http://activsoftware.co.uk) oss/non-oss Translation-en
Fetched 1,449 kB in 17s (83.2 kB/s)
W: Failed to fetch [http://activsoftware.co.uk/linux/repos/ubuntu/dists/oss/non-oss/binary-amd64/Packages](http://activsoftware.co.uk/linux/repos/ubuntu/dists/oss/non-oss/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://activsoftware.co.uk/linux/repos/ubuntu/dists/oss/non-oss/binary-i386/Packages](http://activsoftware.co.uk/linux/repos/ubuntu/dists/oss/non-oss/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]


then when I try to remove again I get this message:

[COLOR=#808080]sudo apt-get remove activinspire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'activinspire' is not installed, so not removed[/COLOR]

I'm not losing sleep at night because of this, but I would like this uninstalled properly.

Can anyone help? 

Nathan

---

### Post by xubu2 on 2014-11-03
You could try checking:
var/log/apt/history.log
or
var/log/apt/term.log

cheers.

---

### Post by phidia on 2014-11-03
I think aptitude would remove all the files you are not losing sleep over :) 
See [this]("http://www.psychocats.net/ubuntu/aptitude") for more info-hope that helps.

---

### Post by ibjsb4 on 2014-11-03
Remove it from your software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by Nathan_McAuley on 2014-11-03
xubu2 - not sure what I'm looking for here but the text from the history log file is:

[COLOR=#696969]Start-Date: 2014-11-03  20:11:30
Commandline: apt-get dist-upgrade
Install: linux-image-extra-3.13.0-39-generic:amd64 (3.13.0-39.66, automatic), linux-image-3.13.0-39-generic:amd64 (3.13.0-39.66, automatic), linux-headers-3.13.0-39:amd64 (3.13.0-39.66, automatic), linux-h$
Upgrade: linux-headers-generic:amd64 (3.13.0.37.44, 3.13.0.39.46), libgnome-bluetooth11:amd64 (3.8.2.1-0ubuntu4, 3.8.2.1-0ubuntu4.1), wine-compholio-i386:i386 (1.7.29~ubuntu14.04.1, 1.7.30~ubuntu14.04.1), $
End-Date: 2014-11-03  20:13:28[/COLOR]

---

### Post by Nathan_McAuley on 2014-11-03
Sorry - I'm a total newbie, I tried **sudo aptitude remove activeinspire **

I'm assuming that's not right as nothing happened.

---

### Post by Nathan_McAuley on 2014-11-03
Hi ibjsb4, 

I tried that and it worked - thanks! 

Basically solved then, but just one last thing my OCD won't let go, and that's the fact that the activeinspire programme still appears in my list of apps when I click on "search your computer and online sources". 

Any ideas how I can get rid of that? 

N

---

### Post by ibjsb4 on 2014-11-03
```
sudo apt-get autoclean && sudo apt-get autoremove
```
This will clean out unused packages.  It is a good idea to review what autoremove is removing before entering 'yes'.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by xubu2 on 2014-11-04
> **Nathan_McAuley said:**
> xubu2 - not sure what I'm looking for here but the text from the history log file is:

[COLOR=#696969]Start-Date: 2014-11-03  20:11:30
Commandline: apt-get dist-upgrade
Install: linux-image-extra-3.13.0-39-generic:amd64 (3.13.0-39.66, automatic), linux-image-3.13.0-39-generic:amd64 (3.13.0-39.66, automatic), linux-headers-3.13.0-39:amd64 (3.13.0-39.66, automatic), linux-h$
Upgrade: linux-headers-generic:amd64 (3.13.0.37.44, 3.13.0.39.46), libgnome-bluetooth11:amd64 (3.8.2.1-0ubuntu4, 3.8.2.1-0ubuntu4.1), wine-compholio-i386:i386 (1.7.29~ubuntu14.04.1, 1.7.30~ubuntu14.04.1), $
End-Date: 2014-11-03  20:13:28[/COLOR]

This list only shows a little part of the log, and it is not the part you need if you want to know what's installed together with activinspire.

You've already removed activinspire with **sudo apt-get remove** **activinspire**.
**sudo apt-get autoremove ****activinspire** removes it with dependecies.
Best to use autoremove next time.[B][URL="http://ubuntuforums.org/member.php?u=1729120"][COLOR=#000000]

ibjsb4[/COLOR][/URL][/B] has already explained this.

Little note: you have to scroll back in the history.log to the time when you installed activinspire.
Most of the things you showed on the forum here are the kernel and driver packages, so it's best to leave those alone ;)
Never remove packages if you don't know what they are for.

cheers.

---

### Post by ian-weisser on 2014-11-04
> **Nathan_McAuley said:**
> It's called activeInspire which is a teaching resource, but it didn't work in wine. 

I'm confused...

If activeInspire was packaged for Ubuntu, then it wouldn't need Wine to run.
If activeInspire is Windows software (which uses Wine to run), then apt-get cannot install/uninstall it. Only Debian/Ubuntu software uses apt-get.

Where, exactly, did you get this software from?
What instructions did you follow to install it? A link would be helpful.

---

### Post by xubu2 on 2014-11-05
> **ian-weisser said:**
> I'm confused...

If activeInspire was packaged for Ubuntu, then it wouldn't need Wine to run.
If activeInspire is Windows software (which uses Wine to run), then apt-get cannot install/uninstall it. Only Debian/Ubuntu software uses apt-get.

Where, exactly, did you get this software from?
What instructions did you follow to install it? A link would be helpful.

Maybe this helps.
[http://support.prometheanplanet.com/server.php?show=nav.19255](http://support.prometheanplanet.com/server.php?show=nav.19255)

---

### Post by ian-weisser on 2014-11-05
Ah, non-Ubuntu software.
What complicated-looking install instructions.
Seems like it shouldn't need Wine

ibjsb4 is right, of course:
1) Uninstall the application (you did that part).
2) Autoremove all the non-Ubuntu dependencies from that non-Ubuntu source.
3) Disable or delete the non-Ubuntu source.

---

### Post by Gordonbp531 on 2014-11-06
If it's this Activeinspire here, [http://www.prometheanworld.com/us/english/education/products/classroom-software/activinspire/](http://www.prometheanworld.com/us/english/education/products/classroom-software/activinspire/) then the System Requirements definitely state Ubuntu 12.04.
So I agree, why would the OP be trying to run it in Wine at all?

---

### Post by xubu2 on 2014-11-06
> **Gordonbp531 said:**
> If it's this Activeinspire here, [http://www.prometheanworld.com/us/english/education/products/classroom-software/activinspire/](http://www.prometheanworld.com/us/english/education/products/classroom-software/activinspire/) then the System Requirements definitely state Ubuntu 12.04.
So I agree, why would the OP be trying to run it in Wine at all?

Guess he downloaded a windows exe cause he couldn't find a deb package for linux.

---

