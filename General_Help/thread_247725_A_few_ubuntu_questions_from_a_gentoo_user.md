---
title: "A few ubuntu questions from a gentoo user"
date: 2006-08-31
forum: General Help
---

### Post by degreseven on 2006-08-31
Hello, 
I have been using gentoo for a couple years now & thought I'd give ubuntu a try on my laptop. Since pretty much everything in gentoo requires manual configuration, I have always known exactly what's going on, where to find everything, etc. Since everything was automatically installed & configured for me in ubuntu, I can't find anything & don't know how anything works =P

Some of my questions may not make sense unless you're familiar with gentoo.

1. What does automatix do that synaptic doesnt? many apps that appear in automatix are also in synaptic.

2. What's the deal with the constant password prompts? I tried editing /etc/sudoers with NOPASSWD: ALL, but this seemed to break things. Is there something else I can do?

3. When I use places > connect to server to mount a samba share, where does it get mounted, or how is it connected? It reconnects at logon, but doesnt show up in mount. How can I access this share from the cl?

4. Where is the config for the command run when I press the volume buttons on my laptop? The headphone channel is not being affected by it, so I need to make it adjust both Master & Headphone.

5. What's the difference between Breezy/Hoary/Dapper, etc., and will tips or howto's for one usually work in another? I'm using dapper, and I've had at least one howto that didn't work at all for me (it was for breezy). I assume these are just major releases with strange names.

6. WHY won't this networking icon stay off my gnome panel? I have to remove it every time i log in.

7. Are ubuntu users somehow against terminal colors?

8. How do I add/remove/display things that are run on boot? (like init scripts), there is no rc-update, and also i cant find something like local.start/local.stop.

9. Where are all the config files? Where can I find all the stuff that is in /etc/conf.d/ in gentoo?


I'm sure there are many more things that I can't think of right now, but these are the things that have been bugging me the most. 

Asside from my initial confusion, I have been extremely impressed by this distro. The devs have obviously put a lot of work into making it simple & easy to use, and I think they've done a great job. I have already recommended it to several people. Keep up the good work!

Thanks in advance.

---

### Post by The Keeper on 2006-08-31
I can answer a few of those questions.

1. Automatix is a tool to install the most common customizations automatically, intended for new users or for those who want to get these installed quickly. Personally I don't think it's all that useful.

2. I don't know how it works in Gentoo, but it's logical to ask for a password when a task requires root privileges.

3. You should see the mounted volume on your Gnome desktop, Nautilus and also in the Places menu.

5. These are abbreviations of the nicknames of major release. Such as Hoary Hedgehog, Breezy Badger and Dapper Drake. The latest is Dapper. Instructions may or may not work in newer releases depending on what the instructions are about.

6. I don't have that problem, have you updated your packages? Might be a bug in Gnome.


Rest of the questions I have to leave for others to answer. :)

---

### Post by Jussi Kukkonen on 2006-08-31
> 
2. What's the deal with the constant password prompts? I tried editing /etc/sudoers with NOPASSWD: ALL, but this seemed to break things. Is there something else I can do?

Don't do that -- it would mean you'd be practically using a root account all the time. If you don't like sudo, enable the root account (see [https://help.ubuntu.com/community/RootSudo)](https://help.ubuntu.com/community/RootSudo)), or use *sudo -i* to get a root shell.

> 
5. What's the difference between Breezy/Hoary/Dapper, etc., and will tips or howto's for one usually work in another? I'm using dapper, and I've had at least one howto that didn't work at all for me (it was for breezy). I assume these are just major releases with strange names.

You are correct. See [http://www.ubuntu.com/ubuntu/releases](http://www.ubuntu.com/ubuntu/releases)

> 
7. Are ubuntu users somehow against terminal colors?

?

> 
8. How do I add/remove/display things that are run on boot? (like init scripts), there is no rc-update, and also i cant find something like local.start/local.stop.

Well, installing/removing with apt or synaptic mostly takes care of that, that's the easiest way. The init scripts live in */etc/init.d*, and they are symlinked for different runlevels in */etc/rc?.d/*. You can use *update-rc.d*.

local boot scripts live in */etc/rc.local*

> 
9. Where are all the config files? Where can I find all the stuff that is in /etc/conf.d/ in gentoo?

Not familiar with gentoo. but all config files are under /etc/, e.g. network settings in /etc/network/.

---

### Post by Irony on 2006-08-31
You can open a root terminal by going to System Tools > Root Terminal. I think this is actually sudo but it looks like root?

To mount a samba share just right click on the folder and click Share Folder - it should end up in the /etc/samba/smb.conf file. You can go to Places > Network Servers (or in Nautilus network:///) to see it mounted.

---

### Post by Royel on 2007-02-18
"7. Are ubuntu users somehow against terminal colors?"

One of the features I miss most with Gentoo, I have yet to figure out how to enable the colors in Ubuntu terminals.

"6. WHY won't this networking icon stay off my gnome panel? I have to remove it every time i log in."

I think this is coming from what you've done here (3. When I use places > connect to server to mount a samba share, where does it get mounted, or how is it connected? It reconnects at logon, but doesnt show up in mount. How can I access this share from the cl?).
You could try mount via a command line, IE:
 # mount -t smbfs -o username=name,password=password //hostname(or-i.p)/sharename /mnt/path

, or add it to /etc/fstab.
One of my samba mounts in /etc/fstab is as follows: 
 //192.168.0.103/Public /home/chris/public smbfs credentials=/etc/public.smbpass,**noauto**,dmask=777,fmask=777 0 0


the contents of /etc/public.smbpass (well, not truly) is:
username=name
password=pass

There is a known bug with mounting samba shares, to work-around this you can do the following, put "noauto" as my example shows, an then add in your /etc/rc.local as follows:

#!/bin/sh -e
#
...
mount /home/chris/public    # <- change this to reflect your actual mount point
exit 0

When you figure out how to enable color to your terminal windows, please either post the directions back here, or kindly PM me :)

Enjoy!

---

### Post by yabbadabbadont on 2007-02-18
> **degreseven said:**
> 2. What's the deal with the constant password prompts? I tried editing /etc/sudoers with NOPASSWD: ALL, but this seemed to break things. Is there something else I can do?  In Gentoo you would just su to root when needed, here you can use, "sudo -s -H", to acheive the same thing.  Just like in Gentoo, you should exit back to your normal user as soon as you are done with your administrative tasks.  Personally, I did an expert install and went ahead and created a normal root user just like Gentoo has.

> **degreseven said:**
> 6. WHY won't this networking icon stay off my gnome panel? I have to remove it every time i log in.  Check your Settings->System->Sessions (I think that is the correct place, I don't use Gnome).  It is probably in your autostart list.

> **degreseven said:**
> 7. Are ubuntu users somehow against terminal colors? Just add an alias to your ~/.bashrc that looks like, "alias ls='ls --color=auto'".  Don't include the double quotes.

> **degreseven said:**
> 8. How do I add/remove/display things that are run on boot? (like init scripts), there is no rc-update, and also i cant find something like local.start/local.stop.This is one place where Gentoo's rc scripts kick the crap out of anybody elses.  All services are controlled by symbolic links in the /etc/rc?.d/ directories.  (which is sort of how Gentoo does it, only there it is simplified and rc-update is easy to use)  Links that start with 'S' are started when init hits that runlevel (i.e. /etc/rc2.d is runlevel 2)  They are started in numerical order, hence the S01, S10, S20, ...  Likewise, the 'K' entries control the shutdown of services.  There are tools to manipulate these links (at least some of them).  Search the forums for BUM -> Boot Up Manager.  There is a large thread about it.  However, some of the services can be disabled through their configuration files.  See next answer.  There isn't an equivalent to local.stop, but /etc/rc.local is the equivalent to local.start.

> **degreseven said:**
> 9. Where are all the config files? Where can I find all the stuff that is in /etc/conf.d/ in gentoo?  The debian (and Unix by the way) equivalent is /etc/default.

Hope this helps.  (In case you were wondering yes, I am the same yabbadabbadont from the Gentoo forums.  :D)

---

### Post by nereid on 2007-02-18
This should get you a colored prompt like Gentoo

```

PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u \[\033[00m\]\[\033[01;34m\]\W \$\[\033[00m\] '

```

Simply put it in your ~/.bashrc file. The \u is the current user and the \W is the current working directory in the short form (not the whole path, this would be \w as far as I can remember).

> This is one place where Gentoo's rc scripts kick the crap out of anybody elses.

This is the only thing that I really do miss from Gentoo. In Gentoo managing the boot scripts was very easy, you could do it even by hand without a problem, but here...

---

### Post by llamakc on 2007-02-18
Controlling init scripts from the cli:

```

ken@llamakc 09:00:33:~$ apt-cache show rcconf
Package: rcconf
Priority: optional
Section: universe/admin
Installed-Size: 112
Maintainer: Atsushi KAMOSHIDA <kamop@debian.org>
Architecture: all
Version: 1.19
Depends: whiptail | whiptail-provider | dialog, sysv-rc, perl, perl-modules
Conflicts: file-rc
Filename: pool/universe/r/rcconf/rcconf_1.19_all.deb
Size: 18158
MD5sum: 63c0710100f2f90f86a770eb685ab14e
SHA1: db77cd701704f8e7bb5164878d2f6dc87da21472
SHA256: d4df6b971fe9ff6478175b0f6be01971f47c8640ffa1103f1c13cf047a532a58
Description: Debian Runlevel configuration tool
 This tool configures system services in connection with system
 runlevels.  It turns on/off services using the scripts in
 /etc/init.d/.  Rcconf works with System-V style runlevel configuration.
 It is a TUI(Text User Interface) frontend to the update-rc.d command.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```


Or in Gnome:

```

ken@llamakc 09:01:23:~$ apt-cache show bum
Package: bum
Priority: optional
Section: universe/admin
Installed-Size: 524
Maintainer: Fabio Marzocca <thesaltydog@gmail.com>
Architecture: all
Version: 2.1.7-1
Depends: gksu, sysv-rc, perl, libgtk2-perl (>= 1:1.100-1), libglib-perl (>= 1:1.
100-1), liblocale-gettext-perl, libgtk2-gladexml-perl
Conflicts: file-rc
Filename: pool/universe/b/bum/bum_2.1.7-1_all.deb
Size: 82902
MD5sum: 9274493c42f2b3093b856c001167a8e4
SHA1: 08942aef1ec14bcfa5ff30143634a268bd8c5aaf
SHA256: e632e0965bf9d09a83fcf5714d8bfde4654531996cdb2a5f58850b65db93cf28
Description: graphical runlevel editor
 Boot-Up Manager is a graphical tool to allow easy configuration
 of init services in user and system runlevels, as far as changing
 Start/Stop services priority.
 Homepage: http://www.marzocca.net/linux/bum.html
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

