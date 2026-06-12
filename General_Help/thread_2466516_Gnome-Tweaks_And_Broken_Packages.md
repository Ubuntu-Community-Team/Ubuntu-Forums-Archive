---
title: "Gnome-Tweaks And Broken Packages"
date: 2021-08-29
forum: General Help
---

### Post by wyattwhiteeagle on 2021-08-29
> wyatt@wyatt-Aspire-E1-532:~$ sudo apt install gnome-tweaks
[sudo] password for wyatt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-tweaks : Depends: gnome-shell-extension-prefs but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
wyatt@wyatt-Aspire-E1-532:~$ 



How do I go about correcting this?

---

### Post by bobunderwood99 on 2021-08-29
[https://www.fosslinux.com/44375/install-gnome-tweak-tool-ubuntu.htm](https://www.fosslinux.com/44375/install-gnome-tweak-tool-ubuntu.htm)

---

### Post by wyattwhiteeagle on 2021-08-29
> **bobunderwood99 said:**
> [https://www.fosslinux.com/44375/install-gnome-tweak-tool-ubuntu.htm](https://www.fosslinux.com/44375/install-gnome-tweak-tool-ubuntu.htm)

My first attempt was for Gnome-Tweaks.

My second attempt via the abbove link was for Gnome-Tweak-Tool

I followed the steps at that link

Here is the terminal output... (pretty much the same message)

> wyatt@wyatt-Aspire-E1-532:~$ sudo apt install gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-tweaks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
wyatt@wyatt-Aspire-E1-532:~$ 


---

### Post by deadflowr on 2021-08-29
Post the full outputs for
```
sudo apt update
sudo apt full-upgrade
```
Use Code Tags,
see this post on how to use code tags: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by wyattwhiteeagle on 2021-08-30
> **deadflowr said:**
> Post the full outputs for
```
sudo apt update
sudo apt full-upgrade
```
Use Code Tags,
see this post on how to use code tags: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

sudo apt update
```
wyatt@wyatt-Aspire-E1-532:~$ sudo apt update
[sudo] password for wyatt: 
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:3 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]      
Hit:4 https://dl.winehq.org/wine-builds/ubuntu focal InRelease                 
Fetched 114 kB in 1s (96.8 kB/s)                                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

sudo apt full-upgrade
```
wyatt@wyatt-Aspire-E1-532:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wyatt@wyatt-Aspire-E1-532:~$ 

```

Would including this terminal output lead in the correct direction...

```
wyatt@wyatt-Aspire-E1-532:~$ sudo apt install gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-tweaks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


```
wyatt@wyatt-Aspire-E1-532:~$ sudo apt install gnome-tweaks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-tweaks : Depends: gnome-shell-extension-prefs but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

```
wyatt@wyatt-Aspire-E1-532:~$ sudo apt install gnome-shell-extension-prefs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-shell-extension-prefs : Depends: gnome-shell (= 3.36.4-1ubuntu1~20.04.2) but 3.36.9-0ubuntu0.20.04.2 is to be installed
                               Depends: gnome-shell-common (= 3.36.4-1ubuntu1~20.04.2) but 3.36.9-0ubuntu0.20.04.2 is to be installed
E: Unable to correct problems, you have held broken packages.
wyatt@wyatt-Aspire-E1-532:~$
```

---

### Post by deadflowr on 2021-08-30
Your output doesn't show focal-updates.
Is it enabled?

Open the Software and Updates app and go to the section Updates.
See if the Recommended Updates is checked or not.
If not checked, check it.

After that, I'd recommend running another update as posted before in post #4.
Then after all that try installing gnome-tweaks.

---

### Post by wyattwhiteeagle on 2021-08-30
> **deadflowr said:**
> Your output doesn't show focal-updates.
Is it enabled?

Open the Software and Updates app and go to the section Updates.
See if the Recommended Updates is checked or not.
If not checked, check it.

After that, I'd recommend running another update as posted before in post #4.
Then after all that try installing gnome-tweaks.

Doing that has allowed Tweaks to install.

 Does that mean I no longer hold these particular broken packages?

---

