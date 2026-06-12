---
title: "Fresh Installation"
date: 2007-05-17
forum: General Help
---

### Post by jefe486 on 2007-05-17
Hello all, I apologize for the silly question but I have not used Linux/Ubuntu in quite awhile. Long enough to have forgotten virtually everything I learned. Anyways, I downloaded the stable version of Ubuntu tonight, burnt it to a DVD and went through the installation process.

I botched the installation part quite badly and deleted my Windows partition... oh well, I can live without it. So obviously I'm trying to make a fresh start start back over on Linux.

The problem I'm running into is the software updates application doesn't seem to be connecting to the server. The error I'm seeing is:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10), connection timed out

ad nausem of course.


I apologize for the silly question but I don't know where to begin. 

Clarification: I am behind a router firewall but I added my IP to the DMZ to clear up any issues(or so I thought).

---

### Post by heimo on 2007-05-17
Does your browser work without problems? Did you have to enter proxy for that?

You could try changing your package source to another mirror / country - open System->Administration->Synaptic Package Manager, and there from menu, Settings->Repositories->Download From. Choose something else.  Mark all upgrades, Apply.

Any problems? In that case, try running this in terminal:
```
sudo aptitude update
sudo aptitude upgrade

```


BTW: Welcome to Ubuntuforums!

---

### Post by jefe486 on 2007-05-17
Thank you kindly for the help. I followed your first suggestion and selected all the sources. I seem to hang indefinately at 8 of 17 updates. I tried your suggestion in the console as well and it seems to hang at the same spot as well.

---

### Post by jefe486 on 2007-05-17
```
jeff@jeff-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Ign http://security.ubuntu.com dapper-security Release
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
20% [Connecting to ca.archive.ubuntu.com (206.167.141.10)]

```

That is what is being displayed in the console.

---

### Post by heimo on 2007-05-17
Can you open, for instance, this file in a browser:
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)

Try opening sources.list in a text editor and changing 
[LIST]
[*] ca. -> us.[/LIST]OR
[LIST]
[*] ca. -> se.[/LIST] ```
gksudo gedit /etc/apt/sources.list
```Rerun:
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by jefe486 on 2007-05-17
I tried both changes to the sources.list file. I was also able to open that file you linked me to without any issues.

I'm still receiving this error though:

```

Err http://us.archive.ubuntu.com dapper-backports/multiverse Sources
  Connection failed [IP: 91.189.89.8 80]

```

It cycles through approx. 10 IP's in that range before giving up..

---

### Post by heimo on 2007-05-17
Can you access it with browser?
[http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/)

---

### Post by jefe486 on 2007-05-17
I can, it displays without any issues.

---

### Post by heimo on 2007-05-17
Is the dapper-backports error only one you're now receiving, or is there bunch of these errors?

---

### Post by jefe486 on 2007-05-17
This is what $sudo aptitude update spits at me:

```

jeff@jeff-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err http://us.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 91.189.89.8 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 91.189.88.31 80]
Ign http://security.ubuntu.com dapper-security Release
Err http://us.archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://us.archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://us.archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://us.archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://us.archive.ubuntu.com dapper/main Packages
Ign http://us.archive.ubuntu.com dapper/restricted Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://us.archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://us.archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Ign http://us.archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Ign http://us.archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Ign http://us.archive.ubuntu.com dapper-updates/main Sources
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Ign http://us.archive.ubuntu.com dapper-updates/restricted Sources
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Ign http://us.archive.ubuntu.com dapper-backports/main Packages
Ign http://us.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://us.archive.ubuntu.com dapper-backports/universe Packages
Ign http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://us.archive.ubuntu.com dapper-backports/main Sources
Ign http://us.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/universe Sources
Ign http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://us.archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err http://us.archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com dapper/universe Sources
  Connection failed [IP: 91.189.89.6 80]
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com dapper-backports/main Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err http://us.archive.ubuntu.com dapper-backports/universe Packages
  Connection failed [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com dapper-backports/multiverse Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com dapper-backports/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err http://us.archive.ubuntu.com dapper-backports/restricted Sources
  Connection failed [IP: 91.189.89.8 80]
Err http://us.archive.ubuntu.com dapper-backports/universe Sources
  Connection failed [IP: 91.189.88.31 80]
Err http://us.archive.ubuntu.com dapper-backports/multiverse Sources
  Connection failed [IP: 91.189.89.6 80]
Reading package lists... Done

```

So I guess that's a no:P

Thanks again for taking the time to help.

---

### Post by heimo on 2007-05-17
I found several similar threads, but no obvious solution(*.

What I'd try is removing sources, updating, adding sources back and updating again. First close all instances of Synaptic Package manager, then I'd try something like this:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list_bak
sudo aptitude update

```These shouldn't give you any output or errors. Then open your Synaptic Package Manager (System->Administration->Synaptic Package Manager), go to menu Settings->Repositories, check boxes for repositories you want included, also include Security sources, click close. Click Reload button. Any errors?


*) The solution I'm suggesting here is something that I remember reading from these forums, so it's not my invention originally - so if it works, credit goes to someone else, if it fails you can blame me. :)

---

### Post by jefe486 on 2007-05-17
I think I missed a step. I typed exactly what you told me to into the console(no errors, yay). Opened up Synaptic, followed your steps and clicked on menu Settings -> Repositories. It comes up with a window saying "Repositories Changed -The repository information has changed. You have to click on the "Reload" button for your changes to take effect" I do as it says, I reload and try again and well, I loop around a bit but no repositories menu.

---

### Post by heimo on 2007-05-17
> **jefe486 said:**
> I think I missed a step. I typed exactly what you told me to into the console(no errors, yay). Opened up Synaptic, followed your steps and clicked on menu Settings -> Repositories. It comes up with a window saying "Repositories Changed -The repository information has changed. You have to click on the "Reload" button for your changes to take effect" I do as it says, I reload and try again and well, I loop around a bit but no repositories menu.

Oh. Synaptic Package Manager must have changed from Dapper to Feisty. I assume you did move the sources.list file to sources.list_bak. Then open your sources.list in text editor 
```
gksudo gedit /etc/apt/sources.list
```and put this content in:

```
deb http://security.ubuntu.com/ubuntu/ dapper-security universe main
deb http://archive.ubuntu.com/ubuntu/ dapper-updates universe main
deb http://archive.ubuntu.com/ubuntu/ dapper main universe
```Then run:
```
sudo aptitude update
```Any errors?

EDIT: This message contained wrong, harmful information for about 10-20 seconds (repositories to Feisty even though jefe486 has Dapper installed). Phew. Hopefully I got it fixed in time. :)

---

### Post by jefe486 on 2007-05-17
I found what I did wrong and am caught up to your last step but when adding those sources it spits out the same error code I posted earlier. I may have to throw in the towel for the time being as this is a production system that I need functional within a few hours(clients calling in, etc.) I appreciate your time and effort.

---

### Post by heimo on 2007-05-17
Oh. Ok. Shame that this problem hasn't been solved properly on these forums yet (if anyone knows solution, please let me know and post in this thread).

---

