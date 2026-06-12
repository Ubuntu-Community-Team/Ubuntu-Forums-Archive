---
title: "Nerolinux doesn't install correctly on edgy"
date: 2006-12-18
forum: General Help
---

### Post by juraj on 2006-12-18
I've noticed that edgy won't install properly on my edgy. Everything worked in dapper, and this is an updated version.

```
Selecting previously deselected package nerolinux.
(Reading database ... 133719 files and directories currently installed.)
Unpacking nerolinux (from nerolinux-2.1.0.3-x86.deb) ...
Setting up nerolinux (2.1.0.3-1) ...
/var/lib/dpkg/info/nerolinux.postinst: 70: function: not found
/var/lib/dpkg/info/nerolinux.postinst: 85: cannot create configure/NeroLINUX.desktop: Directory nonexistent
/var/lib/dpkg/info/nerolinux.postinst: 85: cannot create configure/NeroLINUX.desktop: Directory nonexistent
/var/lib/dpkg/info/nerolinux.postinst: 85: cannot create configure/NeroLINUX.desktop: Directory nonexistent
/var/lib/dpkg/info/nerolinux.postinst: 93: function: not found
/var/lib/dpkg/info/nerolinux.postinst: 103: CreateDesktopFile: not found
Unsupported Linux distribution. Please copy the '.desktop' file manually.
This file is /usr/share/nero/desktop/NeroLINUX.desktop.
/var/lib/dpkg/info/nerolinux.postinst: 109: CreateDesktopFile: not found
Operating System: Debian GNU/Linux version testing/unstable
grep: Unmatched [ or [^
/var/lib/dpkg/info/nerolinux.postinst: 544: 3.1]: not found
/var/lib/dpkg/info/nerolinux.postinst: 544: ShowDefaultLocation: not found
```

Anyway, I don't get my nero icon now. No, don't answer me to add it myself - already done - why that doesn't happen at first place?! Everything worked in dapper! I've tried purging nerolinux and everything, but it won't install it properly.

---

### Post by bodhi.zazen on 2006-12-18
Why Nerolinux ? I find K3b works for all my needs.

---

### Post by talbain on 2006-12-18
Does install, just doesnt seem to be able to create the desktop shortcuts, make one yourself the command is

```
nero
```

try opening the terminal and typing that there, ull see nerolinux start

[http://www.ubuntuforums.org/showthread.php?t=311354&highlight=nerolinux]("http://www.ubuntuforums.org/showthread.php?t=311354&highlight=nerolinux")

---

### Post by juraj on 2006-12-19
@ bodhi.zazen: I know that k3b is a good program, but I like nerolinux. I have a license for it. 

Thanks to all of you for replying, but... the problem is that on Dapper Drake, while installing the .deb package shortcuts are successfully created. On Edgy Eft they are not. I've tried this even with versions that are known to install correctly on Dapper. That is the problem, and the answer isn't adding them manually to my Applications menu.

---

### Post by MJN on 2006-12-19
Juraj,
 
Sort your attitude out - there is little to be gained from getting angry at something not working quite the way you think it ought to, particularly when others are telling you how to fix it - that *is* the answer whether you like it or not! ;)
 
Where did you get your NeroLinux package from? From Nero directly? i.e. [http://www.nero.com/eng/nerolinux-prog.html](http://www.nero.com/eng/nerolinux-prog.html) ?
 
If so, that is a Debian package and whilst Ubuntu is Debian-based and hence will install the majority of Debian packages there are some circumstances where the architectures will differ slightly. This case is one of them.
 
If you want a packages to install perfectly every time then stick to the official (main/restricted) repositories - sources from elsewhere (even if supposedly packaged for Ubuntu which in this example is not the case) may not always work completely - this is something you're going to have to get used to.
 
However, in this case it is not a problem - as the installer correctly states it has been installed on a 'unsupported' distribution and whilst the installation was largely successfull the only failure was the non-inclusion of a suitable menu entry.
 
The solution, as suggested, is simple - just create your own menu entry and/or desktop icon - you can find the location of the Nero pictorial icon in /usr/share/nero/desktop/NeroLINUX.desktop (I think that's the correct location as advised - I'm not at my machine to confirm right now).
 
You mentioned it 'fully installs' on Dapper - I can confirm it doesn't having done this only recently on a fresh installation. Adding the meny entry as advised solves the issue.
 
Mathew

---

### Post by juraj on 2006-12-19
I am really sorry if I sounded angry; that was not my intention at all. I just wanted to see if other people are experiencing this, so I could file a bug report on it (probably something wrong with dpkg), and maybe if someone has a fix for this.

I'm saying this because if it worked in a previous version of the distro, and doesn't work in the current, then it's a regression of some sort... obviously not with nero, because the same version installs fine in dapper. What if this quirk is needed in a company environment? If an admin wants to deploy nero on many pcs, he'll have to go around each one and manually create the shortcut (though, if he is savvy he'll create a script that will do it for him). And same for uninstallation. My intention was just to make ubuntu better by reporting the problem, and certainly not to insult anyone.

Cheers.

---

### Post by hikaricore on 2006-12-19
The problem is you're installing an unsupported debian package, there is nothing wrong with edgy because of this.  I'm able to run the version directly from nero without a problem (and my shortcuts are installed), so this is obviously just an issue with the debian package.

---

### Post by MJN on 2006-12-19
Indeed. It's almost like filing a bug report against the Nero RPM as it won't install on Ubuntu - it's not intended to do so! Just because Ubuntu can usually (nearly always) install Debian packages doesn't mean that the Nero one will necessarilly work! Ubuntu (any version) is not Debian - end of story (yes, yes, Ubuntu is Debian-*based* but there will inevitably be differences... you've just found the symptom of one of those differences).

As mentioned, if you install Nero on Dapper using the Debian package then you get the **very same problem**. I say 'problem' but as the installer tells you waht to do manually then I wouldn't even call it that.

I'm back at my machine now so can confirm that if you want the 'official' icon to go with your menu entry then you'll find it at /usr/share/nero/pixmaps/nero.png

Mathew

(P.S. I can empathise with your anger when things don't work as you'd hoped however this case really shouldn't be one of them for the reasons outlined above)

---

