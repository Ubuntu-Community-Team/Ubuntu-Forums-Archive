---
title: "Backup current version of my installed programs"
date: 2014-11-09
forum: General Help
---

### Post by b-12-3838 on 2014-11-09
Hello everybody,

is there a way how i can backup my software currently insatalled? 

The current version of spotify finally runs smooth and i would like to make a backup of it so i can install the old version if the versions in the future do not run smooth.

I got it from here: [https://www.spotify.com/de/download/previews/](https://www.spotify.com/de/download/previews/)
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 94558F59
sudo apt-get update
sudo apt-get install spotify-client

so I want to have this version I installed as an single-installable .deb package.

How can I do that?

---

### Post by ian-weisser on 2014-11-09
Depends on your skill level.

Do you know how to install/remove deb files using dpkg instead of apt-get?
Do you know how to edit your /etc/atp/sources.list.d?
Do you know how to use apt-cache or dpkg-query to trace dependencies?
Does your favorite version of spotify have any dependencies that also need to be preserved? Are those dependencies tied to a specific version? Or will any future version work?

In theory, all you need to do to backup the application is to: *Copy* the spotify-client deb and non-Ubuntu dependency debs *from* /var/cache/apt/archives *to* someplace else (like /home/$YOU/my_favorite_spotify).

To restore, uninstall the newer version of spotify, then use dpkg --install on each dependency deb and finally upon the spotify-client deb. You can also copy the debs back to /var/cache/apt/archives and use apt-get install. Do not enable or re-enable the spotify repositories (that will simply give you the newer version that you dislike again).

This will backup/restore the application only. Your database(s) and media are not included.

---

