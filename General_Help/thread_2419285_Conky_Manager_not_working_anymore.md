---
title: "Conky Manager not working anymore"
date: 2019-05-19
forum: General Help
---

### Post by jitterssnowpaw on 2019-05-19
The site for Conky Manager doesn't work anymore so what can I do for a replacement or is there?

[https://dl.dropbox.com/u/67740416/linux/conky-manager-latest-amd64.deb?dl=1](https://dl.dropbox.com/u/67740416/linux/conky-manager-latest-amd64.deb?dl=1)

---

### Post by Frogs Hair on 2019-05-19
The link has a 404 error . 18.10 was the last version of conky manager I've seen installation instructions for. You can always learn to install and modify existing conky themes which was the only way to do it prior to conky manager. The conky syntax changed for a new conky version a couple of years ago and conky manager was based on an older version, so some of the themes wouldn't work and I guess the developer didn't want to update all the .conkyrc files.   

[https://www.gnome-look.org/browse/cat/124/page/1/ord/latest/](https://www.gnome-look.org/browse/cat/124/page/1/ord/latest/)

---

### Post by again? on 2019-05-26
Frogs Hair is right in saying you are better off to learn a little about conky configs as 
conky manager is just a gui way of previewing/starting/stopping a collection of conky configs.

That being said you can install it from the mx repo.

**_Add the repo signing key_**
```
cd ~/Downloads
wget http://teharris.net/mx17repo.asc
sudo apt-key add mx17repo.asc
```

**_Add the mx repo_**
```
sudo add-apt-repository "deb http://mxrepo.com/mx/repo/ stretch main non-free"
```

**_Install conky-manager_**
If you install conky-manager from the mx repository it depends on a package called realpath.
Realpath was moved into the coreutils package a number of years ago in Ubuntu.
To satisfy the dependency you can install the xenial package which is an empty transitional package.
```
cd ~/Downloads
wget http://us.archive.ubuntu.com/ubuntu/pool/main/c/coreutils/realpath_8.25-2ubuntu3~16.04_all.deb
sudo apt install ~/Downloads/realpath_8.25-2ubuntu3~16.04_all.deb
sudo apt install conky-manager
```

If you don't have a collection of conky-manager themes/configs in ~/.conky 
you will need to download a theme pack.
[http://www.mediafire.com/file/icvmpzhlk7vgejt/default-themes-extra-1.cmtp.7z](http://www.mediafire.com/file/icvmpzhlk7vgejt/default-themes-extra-1.cmtp.7z)
Open conky-manager and use the import theme pack button to navigate to the theme pack download location.


**_*** Remove the mx repo to avoid package conflicts ***_**
```
sudo add-apt-repository -r "deb [http://mxrepo.com/mx/repo/](http://mxrepo.com/mx/repo/) stretch main non-free"
```

---

