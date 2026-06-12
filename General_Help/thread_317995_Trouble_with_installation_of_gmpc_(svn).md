---
title: "Trouble with installation of gmpc (svn)"
date: 2006-12-13
forum: General Help
---

### Post by elektronaut on 2006-12-13
Hi,

as I'd like to check out gmpc with some plugins, the only way to go seems to install using subversion. I found [this spanish thread](http://ubuntuforums.org/showthread.php?t=312428&highlight=svn+gmpc) and followed the installation procedure described there. It mainly describes these commands for gmpc and the plugins:
```

svn co https://svn.musicpd.org/*gmpc_or_plugin*/trunk *directory*
./autogen.sh
make
sudo make install
```
I chose to call 'sudo checkinstall' instead of 'sudo make install' so I could remove the software later on in case a new version with plugins might appear in the Ubuntu repositories. I didn't install mpd with svn, as the repository version seems up to date. While everything worked fine with gmpc itself, the installation of the plugins yields strange results. coverart-amazon was still o.k., but calling 'make' for gmpc-lyrics results in ```
No package 'gmpc' found
```... and indeed, gmpc is **GONE!**
Here the situation before trying to install the lyrics plugin:
```
$ which gmpc
/usr/local/bin/gmpc

```
and after:
```
$ gmpc
bash: gmpc: command not found
```
I tend to suspect the fact that mpd is not the svn version might be responsible for this trouble, but when I had the svn version installed, the update notifier instantly informed me about the same version number for the official package, so I chose to remove the svn version and use the official one.

---

### Post by qball on 2007-01-27
A small guide I wrote about installing gmpc from svn: [http://sarine.nl/gmpc-compile-svn](http://sarine.nl/gmpc-compile-svn)

p.s. I don't read the forum allot so I might reply very late, or not...

---

### Post by Badjaccur on 2007-11-10
The page is no longer available. Good thing [Google cached]("http://72.14.209.104/search?q=cache:uiokT5eHu_AJ:sarine.nl/") it. I found it rather helpful. [-o<

---

