---
title: "Make Ubuntu FASTER! :D"
date: 2006-10-05
forum: General Help
---

### Post by Patrick-Ruff on 2006-10-05
hey all, theres one thing that I've always wanted to accomplish with ubuntu, see for a while I worked with OSX on PC (yes, illigal, I'm not suggesting anyone do it so don't take that the wrong way mods), and it literally boots up in about 23 seconds on my laptop, but ubuntu is close to 40, and I /know/ Ubuntu has the potential to boot faster then that.


is there anything I can posisbly do to make it so I can get it to boot up as fast or faster then OSX? also, in my ventures of OSX, I also noticed that it shuts down in about 6 seconds...is that possible with ubuntu as well?


thanks.

---

### Post by skymt on 2006-10-05
The best way is to upgrade to Edgy. The new init system, Upstart isn't designed to increase boot speed, but it's a nice side-effect.

If you don't want to do that, install bum (GUI) or sysv-rc-conf (CLI) and disable things you don't need. Check out [this guide](http://ubuntuforums.org/showthread.php?t=89491&highlight=speed+boot) for help deciding which things those are.

---

### Post by Mr Frosti on 2006-10-05
Apple is fast because it uses a startup application named "Launched" that runs the startup processes in parallel as soon as dependencies are filled. Previous versions of Ubuntu used a linear startup method where the next service would only start when the previous was finished loading. For Edgy Eft, "Launched" was considered, but abandoned because of licensing complications.

Your best bet would be to look into InitNG, or wait for a distribution to offer InitNG as an option during installation. This boot method is similar to Launched.

---

### Post by skymt on 2006-10-05
> **Mr Frosti said:**
> Apple is fast because it uses a startup application named "Launched" that runs the startup processes in parallel as soon as dependencies are filled. Previous versions of Ubuntu used a linear startup method where the next service would only start when the previous was finished loading. For Edgy Eft, "Launched" was considered, but abandoned because of licensing complications.

Your best bet would be to look into InitNG, or wait for a distribution to offer InitNG as an option during installation. This boot method is similar to Launched.

Upstart, the default init in Edgy, is parallel like Launchd.

---

### Post by Patrick-Ruff on 2006-10-05
so edgy is basically the ver that is hela faster on boot time then?  when is it comming out again? ;). 

also, I heard something amongst the Mac OS X community about Linux's lack of sound capability, I forgot what exactly was said but does linux have some sort of disability as far as multiple streams of sound or something similar?   (not to get off topic here, just wondering)

---

### Post by Patrick-Ruff on 2006-10-05
also, are there any backports for Upstart that would work on Dapper  Drake?

---

### Post by K.Mandla on 2006-10-05
If you think Dapper boots slow, you should install Breezy. ;)

There are a lot of speed tweaks around. I've got some of them collected [here]("http://ubuntuforums.org/showthread.php?t=206022"), but if you dig around the forums you'll find lots more.

---

### Post by hw-tph on 2006-10-06
You can replace the standard init in Dapper with [InitNG](https://help.ubuntu.com/community/InitNG). This can shave off quite some time off of the startup time.

Another alternative that can decrease the bootup time is re-profiling the startup files. Add **profile** to the kernel parameters at the Grub prompt and boot. It will take a *long* time to boot. When you see the login screen, reboot the computer and let it boot as usual. It should be a tad quicker.

Also, hard drives in laptops are usually dogs. I have a 4200rpm drive it's just horrible comparing to a modern desktop hard drive. I'm looking to upgrade to a 7200rpm drive as soon as possible.


Håkan

---

### Post by doobit on 2006-10-06
The **profile** command actually helped by Xubuntu system boot up a lot faster. You have to run it after every kernel upgrade though.

---

### Post by Patrick-Ruff on 2006-10-06
thanks guys, I'll test the suggestions soon.

and yes, I do think Dapper boots slower...I ran bloody OSX and it booted in 23 seconds, I mean common lol.  but anywyas thanks for the suggestions I will test them out.

peace

---

### Post by 3rdalbum on 2006-10-07
You may come across a suggestion to install Preload. Note that Preload decreases the startup time for applications, but increases the system's startup time. It depends on what you prefer. Until Edgy Eft comes out (version 6.10, due in the 10th 2006... get it?), your best bet will be to install InitNG or disable unessential startup services. The latter has the side-effect of making your computer more secure. If you're a real power user, you could decrease the "sleep" times in your startup scripts.

---

### Post by Patrick-Ruff on 2006-10-07
hmm, thanks for the suggestions. I'll probably do some tweaking here and there and wait till edgy comes out :)


thanks all

---

### Post by UltraSonicSite on 2006-10-07
Maybe, get a lightweight window manger.

---

### Post by Patrick-Ruff on 2006-10-11
haha...UltraSonicSite, been there, done that, hated it, etc.

Gnome is for me.

thanks for such suggestions, I'll wait till edgy comes out before I get into /real/ tweaking.

---

