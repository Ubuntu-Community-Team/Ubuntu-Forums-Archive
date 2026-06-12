---
title: "List all packages that were manually installed after installation?"
date: 2017-03-09
forum: General Help
---

### Post by &amp;KyT$0P# on 2017-03-09
This command lists all manually-installed packages -
```
aptitude search '?and(?not(?automatic), ?installed)'
```
However, some of these were manually installed by the Lubuntu installer, not me.

How to get a list of all packages that were manually installed **after** the initial system installation?

---

### Post by vasa1 on 2017-03-10
> **halogen2 said:**
> ...
How to get a list of all packages that were manually installed **after** the initial system installation?
How have you been installing software? I (i) exclusively use *sudo apt-get install <package_name(s)>*, and (ii) retain *all* the archived logs. 

In such a case, it's possible to make one text file including the latest history.log and the various archived logs using *cat* and *zcat*.

The software I *manually installed* can be found in sections like this:```
Start-Date: 2014-11-25  18:51:40
Commandline: apt-get install gtk2.0-examples
Install: gtk2.0-examples:amd64 (2.24.23-0ubuntu1.1)
End-Date: 2014-11-25  18:51:44

```

Software that's *updated* by apt-get upgrade or apt-get dist-upgrade is in sections like this:```
Start-Date: 2014-11-26  05:36:32
Commandline: apt-get dist-upgrade
Upgrade: google-chrome-stable:amd64 (39.0.2171.65-1, 39.0.2171.71-1), libnautilus-extension1a:amd64 (3.10.1-0ubuntu9.3, 3.10.1-0ubuntu9.4), nautilus-data:amd64 (3.10.1-0ubuntu9.3, 3.10.1-0ubuntu9.4)
End-Date: 2014-11-26  05:37:40
```

So I then clean up, in several steps, using a combination of sed, grep, and sort to end up with something like:
```

Start-Date: 2014-11-14  18:24:18	Commandline: apt-get purge firefox
Start-Date: 2014-11-14  18:25:01	Commandline: apt-get install conky
Start-Date: 2014-11-14  18:25:35	Commandline: apt-get install compton
Start-Date: 2014-11-14  18:25:51	Commandline: apt-get install tint2
Start-Date: 2014-11-14  18:26:10	Commandline: apt-get install xdotool
Start-Date: 2014-11-14  18:26:30	Commandline: apt-get install shimmer-themes
Start-Date: 2014-11-14  18:27:53	Commandline: apt-get install geany
Start-Date: 2014-11-14  18:31:34	Commandline: apt-get install mpv
Start-Date: 2014-11-14  18:49:14	Commandline: apt-get install wmctrl
Start-Date: 2014-11-14  19:33:21	Commandline: apt-get install firmware-b43-installer
Start-Date: 2014-11-14  19:42:04	Commandline: apt-get install aria2 clipit gcolor2 hsetroot libnotify-bin gpaint qpdf
Start-Date: 2014-11-14  20:16:54	Commandline: apt-get purge abiword*
Start-Date: 2014-11-14  20:18:38	Commandline: apt-get purge audacious*
Start-Date: 2014-11-14  20:19:42	Commandline: apt-get purge fonts-nanum*
Start-Date: 2014-11-14  20:21:18	Commandline: apt-get purge pidgin*
Start-Date: 2014-11-14  20:21:38	Commandline: apt-get purge sylpheed*
Start-Date: 2014-11-14  20:22:52	Commandline: apt-get purge xul-ext-ubufox*
Start-Date: 2014-11-14  23:16:50	Commandline: apt-get install libreoffice-calc
Start-Date: 2014-11-14  23:21:24	Commandline: apt-get install libreoffice-writer
Start-Date: 2014-11-14  23:22:39	Commandline: apt-get install libreoffice-help-en-us
Start-Date: 2014-11-14  23:23:33	Commandline: apt-get install libreoffice-gtk
Start-Date: 2014-11-15  00:42:46	Commandline: apt-get install gmrun
Start-Date: 2014-11-15  05:28:53	Commandline: apt-get purge scrot
Start-Date: 2014-11-15  05:30:51	Commandline: apt-get install xfce4-screenshooter
Start-Date: 2014-11-15  07:32:36	Commandline: apt-get install imagemagick
Start-Date: 2014-11-16  08:11:03	Commandline: apt-get install scrot
Start-Date: 2014-11-16  10:38:32	Commandline: apt-get install --no-install-recommends gnome-mahjongg
Start-Date: 2014-11-16  15:34:22	Commandline: apt-get install curl
Start-Date: 2014-11-17  17:07:52	Commandline: apt-get install mousepad
...

```I purposely retained lines with "purge" in them.

IIRC, the old Ubuntu Software Center had a sort of "history" button to see all that you've done but I've no personal knowledge of that.

---

### Post by &amp;KyT$0P# on 2017-03-10
I thought I retained all the history logs, but apparently my oldest history log is from one year ago.  I installed this Lubuntu 14.04 system in mid-2015.

I currently use both [FONT=Courier New]apt-get[/FONT] and Synaptic to install software.  When this system was first set up, I may have used Ubuntu Software Center (that is, [FONT=Courier New]software-center[/FONT], **not** the Lubuntu one) for some stuff as well.  But I've since uninstalled Ubuntu Software Center.

---

### Post by vasa1 on 2017-03-10
The problem, if I may call it that, is that with Synaptic Package Manager (SPM) and Lubuntu Software Center (LSC), the package to be installed is in the same line as the dependencies:
SPM used to install pastebinit:```
Start-Date: 2013-11-14  17:21:40  
Commandline: /usr/sbin/synaptic  
Install: pastebinit:amd64 (1.3-4ubuntu1), python-configobj:amd64 (4.7.2+ds-5, automatic)  
End-Date: 2013-11-14  17:21:47  
```
LSC used to install dclock:```
Start-Date: 2013-11-14  12:18:11  
Commandline: aptdaemon role='role-install-packages' sender=':1.36'  
Install: libsox-fmt-alsa:amd64 (14.4.1-3, automatic), libsox-fmt-base:amd64 (14.4.1-3, automatic), sox:amd64 (14.4.1-3, automatic), dclock:amd64 (2.2.2-6), libsox2:amd64 (14.4.1-3, automatic)  
End-Date: 2013-11-14  12:18:24
```With pure apt-get, the command-line makes the package being installed very clear.

BTW, this is my */etc/logrotate.d/apt*:```
/var/log/apt/term.log {
  rotate 60
  monthly
  compress
  missingok
  notifempty
}

/var/log/apt/history.log {
  rotate 60
  monthly
  compress
  missingok
  notifempty
}

```and my */etc/logrotate.d/dpkg*:```
/var/log/dpkg.log {
	monthly
	rotate 60
	compress
	delaycompress
	missingok
	notifempty
	create 644 root root
}
/var/log/alternatives.log {
	monthly
	rotate 60
	compress
	delaycompress
	missingok
	notifempty
	create 644 root root
}
```

---

### Post by &amp;KyT$0P# on 2017-03-10
> **vasa1 said:**
> The problem, if I may call it that, is that with Synaptic Package Manager (SPM) and Lubuntu Software Center (LSC), the package to be installed is in the same line as the dependencies:
Yeah.  I can write a Python script to parse those lines.  The bigger problems are A) the missing history and B) the packages I set to manually installed after the fact.

> **vasa1 said:**
> BTW, this is my */etc/logrotate.d/apt*:
...
and my */etc/logrotate.d/dpkg*:
Oh heck, I thought that was controlled by Synaptic.  Thanks for the tips, I will definitely make those changes! :KS

---

### Post by deadflowr on 2017-03-10
For what it's worth all the initial packages installed at installation should be listed in the /var/log/installer/initial-status.gz > file.
So probably compare that file against the current /var/lib/dpkg/status file.

---

### Post by &amp;KyT$0P# on 2017-03-10
That looks promising, thanks!  I'll try writing a script to remove the packages listed there from the output of the above [FONT=Courier New]aptitude[/FONT] command.

* Success!  Thanks again deadflowr! :D

---

### Post by vasa1 on 2017-03-10
Won't the "diff" list dependencies as well as the packages themselves? Is there any way to remove the dependencies?

---

### Post by &amp;KyT$0P# on 2017-03-10
> **vasa1 said:**
> Won't the "diff" list dependencies as well as the packages themselves? Is there any way to remove the dependencies?
The aptitude command already takes care of that.  It's then just a matter of weeding out the packages listed in [FONT=Courier New]/var/log/installer/initial-status.gz[/FONT].

Basically, get all the lines starting with "Package:", and use those lines to trim down the list given by aptitude.

---

### Post by vasa1 on 2017-03-10
> **halogen2 said:**
> The aptitude command already takes care of that.  It's then just a matter of weeding out the packages listed in [FONT=Courier New]/var/log/installer/initial-status.gz[/FONT].

Basically, get all the lines starting with "Package:", and use those lines to trim down the list given by aptitude.

I don't have aptitude installed, but what would a bit of the output look like? This what I see with```
apt-mark showmanual | head -20
2048 ***
abiword
accountsservice
adduser
aha ***
alsa-base
anacron
app-install-data
apparmor
apport-gtk
apt
apt-doc
apt-transport-https
apt-utils
aptdaemon
aptdaemon-data
apturl
apturl-common
aria2 ***
aspell

```I've put *** against the packages that I installed. Several "system-installed" packages are also shown as manual. Does your aptitude command show the list of only what you've installed? Sorry to keep banging on but if your method is cleaner, I'd prefer to use that (even if I have to bite the bullet and install aptitude).

---

### Post by &amp;KyT$0P# on 2017-03-11
I think your command gives the same results in a different format.  It would probably be cleaner your way, so thanks for that. :)

For what it's worth, this command gets aptitude to print it out in that format -
```
aptitude --disable-columns -F '%p' search '?and(?not(?automatic), ?installed)'
```

Either way should work, the 'weeding out' of system-installed packages is done after the fact.


* I just replaced the aptitude command in my script with
```
apt-mark showmanual
```
Results are identical, and it looks simpler, so I'll be keeping it that way.

---

### Post by vasa1 on 2017-03-11
> **halogen2 said:**
> I think your command gives the same results in a different format.  It would probably be cleaner your way, so thanks for that. :)

For what it's worth, this command gets aptitude to print it out in that format -
```
aptitude --disable-columns -F '%p' search '?and(?not(?automatic), ?installed)'
```

Either way should work, the 'weeding out' of system-installed packages is done after the fact.


* I just replaced the aptitude command in my script with vasa1's apt-mark command.  Results are identical, and it looks simpler, so I'll be keeping the change.
Re. weeding, here's what Toz (awesome guy) suggested: [https://ubuntuforums.org/showthread.php?t=2190230&p=12858855#post12858855](https://ubuntuforums.org/showthread.php?t=2190230&p=12858855#post12858855)

---

### Post by vasa1 on 2017-03-11
So how's that going for you?

I went through the routine you've outlined and it was largely successful though the list included some packages that I'm pretty sure I didn't install and a few dependencies. But, overall, I much prefer your route than the convoluted approach I was using.

Edit: There are two "one-liners" in this answer: [http://askubuntu.com/a/492343](http://askubuntu.com/a/492343)

---

### Post by &amp;KyT$0P# on 2017-03-11
I did a Python script -
```
#!/usr/bin/env python3

import subprocess, re

def run(*args, **kwargs):
  return str(subprocess.check_output(*args, **kwargs), 'utf_8')

def getManualPkgs():
  installerPkgs=run(['zcat', '/var/log/installer/initial-status.gz']).split('\n')
  manualPkgs=run(['apt-mark', 'showmanual']).split('\n')
  for raw_line in installerPkgs:
    if not(raw_line.startswith('Package:')): continue
    line=re.sub(r'^Package:\s*', '', raw_line, flags=re.I)
    if line in manualPkgs: manualPkgs.remove(line)

  return manualPkgs

if __name__ == '__main__':
  print('\n'.join(getManualPkgs()))

```

---

