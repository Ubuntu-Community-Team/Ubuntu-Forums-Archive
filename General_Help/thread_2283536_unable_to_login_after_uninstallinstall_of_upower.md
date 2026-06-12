---
title: "unable to login after uninstall/install of upower"
date: 2015-06-22
forum: General Help
---

### Post by rawlins02 on 2015-06-22
Running 14.04 LTS. I'm getting an 'unable to start session' error when attempting to login. This issue arose just after I executed the following commands and loged out

```

sudo apt-get remove upower
sudo apt-get install upower
sudo apt-get install indicator-power

```

I noted no errors in execution. Able to login to my account after dropping to command line with Ctrl-Alt-F1, so perhaps window manager has been corrupted?

To diagnose problem, I've run commands which returned no errors

```

sudo apt-get update
sudo apt-get upgrade

```

and

```

sudo dpkg-reconfigure lightdm
sudo update-desktop-database

```

---

### Post by kostkon on 2015-06-22
You could check your logs in /var/log for any errors, e.g.:
```
nano /var/log/syslog
```
also, your .xsession-errors file:
```
nano .xsession-errors
```

You could try reinstalling ubuntu-desktop and then reboot and see if that changes anything, i.e.
```
sudo apt-get clean
sudo apt-get install ubuntu-desktop --reinstall
```

Hope that helps.

---

### Post by rawlins02 on 2015-06-22
I've checked syslog and .xsession-errors but was unable to identify anything obvious. The reinstall of ubuntu-desktop failed due to unmet dependencies for: ubuntu-session, unity-control-center, unity-settings-daemon, xul-ext-webaccounts. Not clear to me why those aren't fetched automatically?

---

### Post by ka55o5 on 2015-06-22
Might as well... Try and take this opportunity to dump Precise (because, lol)? I used it for the longest time, as well (quite possibly due to the name, hehe); but, well, let's not even get into the whole 32-bit deal (omg). Anywho, that's my observation / question; hope you don't mind the bump, tnx. xD

[color=gray]No idea if it's me, or things are getting weird.[/color]

---

### Post by kostkon on 2015-06-22
> **rawlins02 said:**
> I've checked syslog and .xsession-errors but was unable to identify anything obvious. The reinstall of ubuntu-desktop failed due to unmet dependencies for: ubuntu-session, unity-control-center, unity-settings-daemon, xul-ext-webaccounts. Not clear to me why those aren't fetched automatically?
Have you added any PPAs to your system? You could check by listing the contents of the sources.list.d folder for example:
```
ls /etc/apt/sources.list.d
```

Also, what's the output of
```
apt-cache policy ubuntu-session
```
and maybe
```
apt-cache policy ubuntu-desktop
```

You could even paste the output of your apt-get or other commands directly from the command line, if the pc is still able to connect to the internet, by using [pastebinit]("https://help.ubuntu.com/community/Pastebinit").

---

### Post by rawlins02 on 2015-06-22
Here are the results to standard output of those commands. I'm afraid I'm unable to see where this is going. But thanks.

The sources.list.d directory
[http://paste.ubuntu.com/11759860](http://paste.ubuntu.com/11759860)

apt-cache policy ubuntu-session
[http://paste.ubuntu.com/11759852](http://paste.ubuntu.com/11759852)

apt-cache policy ubuntu-desktop
[http://paste.ubuntu.com/11759856](http://paste.ubuntu.com/11759856)

---

### Post by rawlins02 on 2015-06-22
> **ka55o5 said:**
> Might as well... Try and take this opportunity to dump Precise (because, lol)? I used it for the longest time, as well (quite possibly due to the name, hehe); but, well, let's not even get into the whole 32-bit deal (omg). Anywho, that's my observation / question; hope you don't mind the bump, tnx. xD

[color=gray]No idea if it's me, or things are getting weird.[/color]

running 14.04 LTS.  Updating profile now.

---

### Post by kostkon on 2015-06-22
The Gnome3 PPA has definitely messed up your system. Are you running Unity or Gnome Shell?

I don't know why you added it but you could purge it with ppa-purge. You need to install it first, then
```
man ppa-purge
```
for usage instructions.

---

### Post by rawlins02 on 2015-06-23
Running Unity. I've installed ppa-purge. I've determined that the ppa-purge command accepts an argument of url of ppa that one wishes to purge. How do I determine what that URL is?  I tried

```

sudo ppa-purge http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/

```
which returned an error. I'll recheck the URL.

In the source.list.d directory I've deleted a file with gnome3 in the name, then run apt-get update. That did not appear to fix problem.

---

### Post by rawlins02 on 2015-06-23
Attempting to determine if Gnome3 PPA has corrupted my system. Believe I'm purging it from system. 

```

sudo ppa-purge ppa:gnome3-team/gnome3-staging
Updating packages list
PPA to be removed: gnome3-team gnome3-staging
Warning: Could not find package list for PPA gnome3-team gnome3-staging

```

Could this failure of ppa-purge be due to the fact that I've removed the gnome3 files from /etc/apt/sources.lists.d/ ?

---

### Post by kostkon on 2015-06-23
> **rawlins02 said:**
> Attempting to determine if Gnome3 PPA has corrupted my system. Believe I'm purging it from system. 

```

sudo ppa-purge ppa:gnome3-team/gnome3-staging
Updating packages list
PPA to be removed: gnome3-team gnome3-staging
Warning: Could not find package list for PPA gnome3-team gnome3-staging

```

Could this failure of ppa-purge be due to the fact that I've removed the gnome3 files from /etc/apt/sources.lists.d/ ?
Yes, re-add the ppa:
```
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
```
then run ppa-purge again.

---

### Post by rawlins02 on 2015-06-23
> **kostkon said:**
> Yes, re-add the ppa:
```
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
```
then run ppa-purge again.

purge successful.  Would the next step be any or all of these commands?

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall ubuntu-desktop

in the hope that the dependencies can now be handled?

---

### Post by kostkon on 2015-06-23
> **rawlins02 said:**
> purge successful.  Would the next step be any or all of these commands?

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall ubuntu-desktop

in the hope that the dependencies can now be handled?
```
sudo apt-get update
sudo apt-get clean
sudo apt-get install --reinstall ubuntu-desktop
```

If the reinstall is successful, you could then try rebooting, i.e.:
```
sudo reboot
```

---

### Post by rawlins02 on 2015-06-23
> **kostkon said:**
> ```
sudo apt-get update
sudo apt-get clean
sudo apt-get install --reinstall ubuntu-desktop
```

If the reinstall is successful, you could then try rebooting, i.e.:
```
sudo reboot
```

I've reinstalled ubuntu-desktop and after rebooting now have access to login of desktop session. Thank you kostkon for the help. Marking as solved.

---

