---
title: "can not install update?"
date: 2007-10-15
forum: General Help
---

### Post by chunchengch on 2007-10-15
Synaptic can not install the new updates, the message is about that "package audacious-plugins_1.3.5-3ubuntu3_i386.deb is trying to overwrite /usr/lib/audacious/General/libcurl.so which is part of package audacious-plugins-extra", what can I do to finish the update? thanks!

[ATTACH]46409[/ATTACH]

[ATTACH]46410[/ATTACH]

---

### Post by Pumalite on 2007-10-15
Total Removal of: audacious-plugins-extra via Synaptic. Proceed with update. Reinstall if need be.

---

### Post by raydar on 2007-10-15
I'm getting this too, specifically:

E: /var/cache/apt/archives/audacious-plugins_1.3.5-3ubuntu3_i386.deb: trying to overwrite `/usr/lib/audacious/General/libcurl.so', which is also in package audacious-plugins-extra

I found one thread where this "which is also in package" problem was mentioned, and it was suggested one just needs to remove the old package and the update will go fine.  I looked into doing that, but Synaptic wanted to remove not just "audacious-plugins" and "audacious-plugins-extra" but also "audacious" itself and "ubuntustudio-audio" (I'm running UbuntuStudio Gutsy release candidate).  That sounded like rather a lot to remove, so I'm hoping a future update will fix this problem.

I've seen the "trying to overwrite . . . which is also in package" error several times recently; a couple times the problem "went away" on its own, and one time I found a thread that suggested using a terminal command with, I think, an -f switch to force the overwrite.

Is there a consistent way to deal with this issue, or does the resolution depend on the particular package or circumstances?

---

### Post by Pumalite on 2007-10-15
I just did what I said in my own computer and it worked.

---

### Post by raydar on 2007-10-15
Was "audacious-plugins-extra" the only thing Synaptic removed when you did it?  

I suppose the difference may just be that I'm running UbuntuStudio--you aren't also running that, by chance, are you?

In any case, thanks for affirming that the fix does work.  :)  (This latest upgrade to Gutsy is the first time Ubuntu audio & MIDI have worked for me without major problems, so I'm just reluctant to let Synaptic remove those other packages along with the plugin(s) at issue in this thread.)

---

### Post by saint-x on 2007-10-15
Uninstall "audacious-plugins-extra" only. Not "audacious-plugins"(uninstalling "audacious-plugins" is what makes audacious uninstall). Or just reinstall audacious altogether.Either way you're golden.

Have a good one =)


**Edit

Btw, Pumalite... Great signature :D

---

### Post by Pumalite on 2007-10-15
Glad you liked it. Cheers.

---

### Post by raydar on 2007-10-15
Argh . . . I've tried Synaptic and apt-get (incl. with -f switch) and neither will let me remove, upgrade, or reinstall just audacious-plugins-extra or audacious-plugins. :P  

I'm interpreting the brief description in Synaptic ("Ubuntu Studio is a multimedia creation flavor of Ubuntu for the Linux audio, video, and graphic enthusiast or professional. A collection of applications aimed at audio creation and editing.") and the longer one at [https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList) to mean that when Synaptic or apt-get wants to remove the package ubuntustudio-audio along with both plugin packages, it's going to remove all the UbuntuStudio applications.  If that isn't a picture tube blowing to protect a 50-cent fuse, I don't know what is. :)  

It doesn't list those apps separately--only the audacious-plugins and ubuntustudio-audio, so maybe I'm wrong.  Some other ubuntustudio upgrades just became available, but ubuntustudio-audio isn't among them, and I'm skeptical whether applying those upgrades would do anything about the fact I can't uninstall audacious-plugins-extra all by itself (though apt-get is also among the upgrades).  I'm almost ready to resign myself to the over-reinstallation . . . but does anyone know a safe way to sneak under Synaptic's or apt-get's radar for this circumstance?

---

### Post by Pumalite on 2007-10-15
I did mine in Gutsy. I don't know about Studio. Someone will chime in.

---

### Post by por100pre1 on 2007-10-15
> **raydar said:**
> It doesn't list those apps separately--only the audacious-plugins and ubuntustudio-audio, so maybe I'm wrong.

If only audacious-plugins and ubuntustudio-audio are to be removed don't worry about removing audacious-plugins-extra. The ubuntustudio-audio package is just a listing of the default audio programs for an Ubuntu Studio installation. Use synaptic to remove them.

---

### Post by raydar on 2007-10-15
Aha, thank you--I went ahead with it (removing audacious-plugins-extra), and ubuntustudio-audio was removed with it, not 20 apps, just it.  I was all worried for nothin'. :]

Afterward, when I checked in Synaptic, audacious-plugins was still installed, and I had to mark audacious-plugins-extra & ubuntustudio-audio and install them.  (Got a realtime kernel with it, that won't start X. :) )

What's everyone think, should this thread be marked solved?

---

### Post by Pumalite on 2007-10-15
Maybe start a new thread with your x problem if you need to.

---

### Post by raydar on 2007-10-18
I did wind up starting a thread for that (see [http://ubuntuforums.org/showthread.php?p=3558300#post3558300](http://ubuntuforums.org/showthread.php?p=3558300#post3558300) )--I wasn't intending to follow that tangent here in this one, but it turns out they're related, at least for those running UbuntuStudio.

In short, having to uninstall audacious-plugins-extra required uninstalling ubuntustudio-audio, and reinstalling ubuntustudio-audio resulted in the realtime kernel's being installed too, but without the linux-rt package.  The lack of that latter package was the cause of X failing to start when I booted the realtime kernel.

So for UbuntuStudio users, if you happen to run into the problem this thread was started for, be aware that the fix for that may cause Synaptic to do what's cautioned against at [http://packages.ubuntu.com/gutsy/base/linux-ubuntu-modules-2.6.22-14-rt](http://packages.ubuntu.com/gutsy/base/linux-ubuntu-modules-2.6.22-14-rt) , namely "You likely do not want to install this package directly. Instead, install the linux-rt meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed."

Thanks for your help, Pumalite & por100pre1!

---

