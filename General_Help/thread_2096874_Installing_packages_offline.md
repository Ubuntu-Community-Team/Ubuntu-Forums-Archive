---
title: "Installing packages offline"
date: 2012-12-21
forum: General Help
---

### Post by Holmes.Sherlock on 2012-12-21
I have installed vlc on my Ubuntu system using
```

sudo apt-get install vlc

``` 
Downloaded .deb files got stored under /var/cache/apt. If I collect all those files, can VLC be installed onto a machine having no Internet connection?

---

### Post by fdrake on 2012-12-21
> **Holmes.Sherlock said:**
> I have installed vlc on my Ubuntu system using
```

sudo apt-get install vlc

``` 
Downloaded .deb files got stored under /var/cache/apt. If I collect all those files, can VLC be installed onto a machine having no Internet connection?

```
sudo dpkg -i ./myDir/package.deb
```

---

### Post by cortman on 2012-12-21
If that machine is running the same version of Ubuntu, you should be able to. Collect them all in a folder and run

```
sudo dpkg -i /path/to/folder/*.deb
```

to install. Part of that process is detailed in my tutorial [here]("http://cortman.wordpress.com/2012/07/08/download-packages-with-windows/").

---

### Post by Holmes.Sherlock on 2012-12-25
> **cortman said:**
> If that machine is running the same version of Ubuntu, you should be able to. Collect them all in a folder and run

```
sudo dpkg -i /path/to/folder/*.deb
```to install. Part of that process is detailed in my tutorial [here]("http://cortman.wordpress.com/2012/07/08/download-packages-with-windows/").
What is the advantage/disadvantage of installing packages like this compared to creating a image by APTonCD and using that as repository?

---

### Post by cortman on 2012-12-28
This way is easy and I know it works, I've never used AptOnCD, perhaps that is the solution for you. You need to decide that yourself.

---

### Post by Holmes.Sherlock on 2012-12-28
> **cortman said:**
> 
... I've never used AptOnCD, ...
APTonCD indexes that available packages and creates one local repository image which can be added to the repo list.

---

