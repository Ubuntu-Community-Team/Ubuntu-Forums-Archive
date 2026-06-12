---
title: "List User Installed Applications in 16.04, and an older release"
date: 2016-10-04
forum: General Help
---

### Post by mikeincousa on 2016-10-04
I have been thrashing about in internet and my 2013 notes regarding the subject,
but I have NOT come upon any clear, compact technique.

All the solutions I have found are at least a few years old.

I question if they are current?

I would like to generate such a list from my current 16.04 install.

And get the same listing from a mirror copy (hopefully) of what I think is a full 13.04 version.

BTW I am not sure how to confirm that either.

I am not very sophisticated. Most of the older solutions I found are script driven, use SED, .....

I do know that mistakes in scripts can cause a lot of damage.

That is another reason why I am hoping for a simple solution.

Is there a simple way to generate such lists?

Thanks for any help.

---

### Post by ian-weisser on 2016-10-05
No, there is no simple way to generate a list of the applications you told apt to install.

Apt does not keep track of which applications you told it to install.
Well, that's not quite true. Apt does indeed keep track, and the command 'apt-mark showmanual' will list those packages.

However, the thousands of packages installed by the Ubuntu installer are also marked 'manual' (to keep you from accidentally deleting your entire desktop), so the command is less useful than you probably hope.

Generally, it's easy enough to simply install applications the first time you realize that you need it.
It's all in the Software Center, free and just one click away.

---

### Post by VictorR on 2016-10-05
dpkg --get-selections

The above lists all installed packages. More details can be found [http://www.howtogeek.com/howto/linux/show-the-list-of-installed-packages-on-ubuntu-or-debian/]("http://www.howtogeek.com/howto/linux/show-the-list-of-installed-packages-on-ubuntu-or-debian/")

---

### Post by vasa1 on 2016-10-05
> **mikeincousa said:**
> ...
I am not very sophisticated. Most of the older solutions I found are script driven, use SED, .....

I do know that mistakes in scripts can cause a lot of damage.
...
A script for this particular purpose would be unlikely to cause any damage. It could possibly miss out on some software. [Here's an answer]("http://askubuntu.com/a/425040") that would work _if_ you've used apt-get and not the software center or something like Synaptic Package Manager and _if_ you've retained all your log files. (Normally, logrotate gets rid of very old logs.)

But ian-weisser's suggestion is most practical. It's quite possible that what you installed some months ago isn't needed any more!

---

### Post by mikeincousa on 2016-10-05
In Ubuntu, the last few years, I have worked in fits and starts. 

These epochs span several general topics and are widely spaced in time.

I only vaguely recall a couple of themes. and that is what put me into this frame--trying to recall the packages and concepts of value.

The idea was generating a tickler list so to speak.

I am looking at learning Awk and Sed basics for cleaning illegal characters from file names across several drives. 

I will include looking at the script files for building a tickler list in the course of that project.

Thank you for your concise and sage comments. They are all well taken.

---

### Post by CantankRus on 2016-10-05
May be a good time to start adding those must have installed applications manually to an install script.
eg: I have added to this script over the years which I run after a fresh install
```
#!/bin/bash

sudo apt install man2html synaptic easystroke kupfer conky-all xdotool wmctrl numlockx curl glipper lm-sensors hddtemp w3m keepassx artha p7zip-full p7zip-rar shutter gdebi vlc smplayer gnote compizconfig-settings-manager sox libsox-fmt-all xsel xclip nemo gtk-redshift ack-grep normalize-audio undistract-me speedtest-cli
```

---

