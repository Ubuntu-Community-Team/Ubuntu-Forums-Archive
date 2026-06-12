---
title: "Questions of a newbie"
date: 2007-08-09
forum: General Help
---

### Post by Thunderhit on 2007-08-09
Ok, hope you can give me some answers :)
When I installed feisty 7.04, I got updates for gaim, although pidgin, its successor has been available for quite some time now. But its not only gaim, there were so much old versions of software in the official reps, why? There wasnt even Thunderbird 2! Only the old 1.5. No idea if its still the case, well I found a repo for 64bit with newer versions for that software, but still, I also tried media players and they all were at least 1 version behind the latest one, be it audacious or others. Oh, ntfs-3g is also kinda old version there.
A friend of mine that convinced me to switch to ubuntu said that its great that updating software is so easy compared to windows, but I dont get the sense if there are only old versions :D

I don't want firefox, using Opera. No problem to get it running, but when I wanted to remove firefox, there were some other packages that also needed to be removed, like ubuntu-desktop and ubuntu-help. I dont want to remove them, its firefox and not those. Think its the same for another ubuntu standard program, though I cant remember its name. Wont there be problems if those packages are removed? Dont want to get into problems because firefox is too linked with the installation (somehow reminds me of IE and Windows...)

Nautilus is the..uh..how to call it.. file browser in ubuntu, right? Even though I have the resolution at 1280x1024, those icons are still amazingly big at 75% of the zoom. But I can only go to 50% and then they are too small.. no way to get an inbetween number? 

My mouse, like any other since the last 5 years has some buttons to move forward and backward in folders... why doesnt that work? How do I get it to work?

Please enlighten me :)

---

### Post by apetresc on 2007-08-09
> **Thunderhit said:**
> Ok, hope you can give me some answers :)
When I installed feisty 7.04, I got updates for gaim, although pidgin, its successor has been available for quite some time now. But its not only gaim, there were so much old versions of software in the official reps, why? There wasnt even Thunderbird 2! Only the old 1.5. No idea if its still the case, well I found a repo for 64bit with newer versions for that software, but still, I also tried media players and they all were at least 1 version behind the latest one, be it audacious or others. Oh, ntfs-3g is also kinda old version there.
A friend of mine that convinced me to switch to ubuntu said that its great that updating software is so easy compared to windows, but I dont get the sense if there are only old versions :D
Ubuntu follows a 6-month release schedule. Every few months, Ubuntu gets a new version, and with it, all the applications in the repositories are updated as well. This is good -- over the 6 months that a release is developed, all those packages are rigorously tested, so that when it is ready for release, you know you have a stable program.

If you absolutely must be bleeding edge, you can simply add the repository for the upcoming Ubuntu release (Gutsy Gibbon), which will have all the latest versions of everything. But it is still in the testing phase. They will be stable somewhere in October. You can get them if you want, but 100% stability is not guaranteed.

There are also backport repositories that only take certain packages from Gutsy and make them available without needing to upgrade your whole system. This is a good compromise, and there's a whole forum dedicated to these things. Check here: [http://ubuntuforums.org/forumdisplay.php?f=41](http://ubuntuforums.org/forumdisplay.php?f=41)

> I don't want firefox, using Opera. No problem to get it running, but when I wanted to remove firefox, there were some other packages that also needed to be removed, like ubuntu-desktop and ubuntu-help. I dont want to remove them, its firefox and not those. Think its the same for another ubuntu standard program, though I cant remember its name. Wont there be problems if those packages are removed? Dont want to get into problems because firefox is too linked with the installation (somehow reminds me of IE and Windows...)
Nope, there willl be no problems :) A lot of beginners misunderstand what "ubuntu-desktop" and similarly named packages are. They are NOT packages that contain any part of Ubuntu! In fact they are empty packages (meta-packages is the technical term). The only reason they exist is because they are listed as having dependencies for every component of a base Ubuntu install. This means that if you installed the KDE version of Ubuntu, and you want to also have Gnome, you can just do "sudo apt-get install ubuntu-desktop" and (even though the package itself is empty), all of its dependencies will give you what you want. It is 100% safe to remove this package. The package is empty.

Anyway, welcome to Ubuntu, and enjoy! :)

---

