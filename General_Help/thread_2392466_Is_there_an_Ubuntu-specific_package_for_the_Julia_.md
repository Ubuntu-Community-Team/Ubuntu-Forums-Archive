---
title: "Is there an Ubuntu-specific package for the Julia language?"
date: 2018-05-21
forum: General Help
---

### Post by klundermann on 2018-05-21
As suggested [here]("https://gino244o.wordpress.com/2015/04/26/julia-language-installation-on-ubuntu/") and elsewhere, I have attempted to install [Julia]("https://julialang.org/") under Ubuntu 18.04 using```

sudo add-apt-repository ppa:staticfloat/juliarelease
sudo add-apt-repository ppa:staticfloat/julia-dep
sudo apt-get update
sudo apt-get install julia
```

The result of executing the first of these commands is```
> sudo add-apt-repository ppa:staticfloat/juliareleases
 Stable releases of the Julia language (http://julialang.org)

For nightly, bleeding-edge builds see (https://code.launchpad.net/~staticfloat/+recipe/julianightlies)
 More info: https://launchpad.net/~staticfloat/+archive/ubuntu/juliareleases
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease                                                                                     
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease                                                                                   
Ign:4 http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu bionic InRelease
Hit:5 http://security.ubuntu.com/ubuntu bionic-security InRelease        
Ign:6 http://ppa.launchpad.net/staticfloat/juliareleases/ubuntu bionic InRelease
Err:7 http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Err:8 http://ppa.launchpad.net/staticfloat/juliareleases/ubuntu bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/staticfloat/juliareleases/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Executing the second command produces a similar result.

Does this mean that the repositories [FONT=system]staticfloat/juliareleases[/FONT] and [FONT=system]staticfloat/julia-dep[/FONT] do not exist?  Is there some other way I should try to install Julia?

---

### Post by deadflowr on 2018-05-21
> Does this mean that the repositories staticfloat/juliareleases and staticfloat/julia-dep do not exist? Is there some other way I should try to install Julia?
It means no archive for 18.04, yet.
the only substantial way to install julia on bionic I see thus far is from git:
[https://github.com/JuliaLang/julia]("https://github.com/JuliaLang/julia")
at least in the interim until someone builds a ppa or snap package or a flatpak package or an appimage for it.

You'll need to remove the ppa, for now. so it won't keep messing up the systems updater.

---

### Post by monkeybrain20122 on 2018-05-21
It has a release [binary]("https://julialang.org/downloads/") for download, just un-tar it and you are ready to go, no installation needed . The ppa is outdated anyway.

Edited: I am curious actually why does Ubuntu or any Linux distro even bother "packaging" software like julia or blender which provides a binary which you just click and run. The repo versions are 100 years old and have all kinds of dependencies.

---

### Post by klundermann on 2018-05-21
Thanks for the clear and concise answers, deadflowr and monkeybrain20122!  I have removed the ppa.

---

