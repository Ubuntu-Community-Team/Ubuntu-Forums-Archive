---
title: "Thumbnails are only sucessfully created for root user"
date: 2020-07-11
forum: General Help
---

### Post by tiagoferreira on 2020-07-11
Hello;

I have recently (freshly) installed Ubuntu 20.04 on my laptop machine I have an issue with the thumbnails that I do not understand.

When enabling thumbnails preview from nautilus (preferences -> search & preview -> show thumbnails: "All files" "Only for files smaller than 1024MB") it is not possible for me to see any of them, after looking into the .cache/thumbnails/ folder, I took notice that all of them are in the fail folder. However, if I open nautilus with root permissions (sudo -i nautilus), the thumbnails are shown correctly for the video files. 
I have searched this and other forums about similar issues and none of the solutions seems to work for me.

OS information:
- ubuntu 20.04 - 64bit
- Gnome version - 3.36.3
- x11


Things I checked and tried (also remove all generated thumbnails from fail folder in pretty much every tried tentative to solve this):
- remove and reinstall ffmpegthumbnailer
- make sure my user is the owner of the cache folder and subfolders (sudo chown -R $USER:$USER .)
- give full permissions inside cache folder (sudo chmod 777 -R .)
- successfully generate thumbnails using ffmpegthumbnailer api (ffmpegthumbnailer -i test.mkv -o test.png)
- disable ufw firewall 
- launch nautilus in debug mode to check for any error (none found) (G_DEBUG="all" NAUTILUS_DEBUG="All" nautilus)

For now, i am also assuming that the issue is not related with gnome, since until i have installed Ubuntu i was using this same version of gnome with Manjaro in this laptop.

Besides reinstalling Ubuntu once again (something that i would like to avoid), I do not have any additional ideas... So any idea, forum post, you guys can provide me, it will be very helpful. 

Thanks in advance

---

### Post by TheFu on 2020-07-13
Did you run nautilus with sudo before?

[LIST]
[*]sudo -s leaves HOME the same.
[*]sudo -i changes HOME to the new userid's location.
[*]sudo nautilus leaves HOME the same.
[/LIST]

There's are multiple reasons we suggest not using ANY GUI programs with sudo.

Normally, I'd say NEVER run this:
```
sudo chmod 777 -R .
```
That is for lazy people who don't understand permissions or simply don't care about security at all.  It could trash any Unix system depending on the cwd/pwd.

Running 
```
sudo chown -R $USER:$USER .
```
is dependent on the CWD, so it may do nothing good and can easily break a system. Which happens depends on the pwd/cwd.

However, running 
```
sudo chown -R $USER:$USER $HOME
```
should be safe for all real userids.

**There's are multiple reasons we suggest not using ANY GUI programs with sudo.**

---

### Post by ajgreeny on 2020-07-13
It would be interesting to see who is the owner of those thumbnails in ~/.cache/thumbnails with command ```
ls -la -R .cache/thumbnails
```
Everything should be owned by you but I suspect some may be owned by root (or some other user).

---

