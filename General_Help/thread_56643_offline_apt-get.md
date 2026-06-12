---
title: "offline apt-get"
date: 2005-08-13
forum: General Help
---

### Post by agro1986 on 2005-08-13
I've configured "sources.list" and did "sudo apt-get update" as mentioned in ubuntuguide.org. I've also succesfully installed flash plugin for firefox using apt-get. My question is...

I'll probably install ubuntu on at least 3 other machines. It'll be really pain if each machine must download the same bits (still need to install other stuffs such as mp3 support). I believe "apt-get install" saves the downloaded files somewhere. How do I use it on other machines?

Thanks

---

### Post by SGC on 2005-08-13
The files are saved to:
/var/cache/apt/archives

You can copy them, put them in a folder in the other computers, and then run this command to install them:
dpkg -i *.deb

---

### Post by agro1986 on 2005-08-13
Cool! Thanks a lot

---

### Post by agro1986 on 2005-08-15
I've installed around 50 megabytes worth of programs... However, when I wanted to backup the .deb files, only 1 .deb file remains on /var/cache/apt/archives  ](*,) !

Is there an autodelete mechanism in apt-get? If so, how do I disable it?

Thanks

---

### Post by RaymondQE on 2005-08-16
If you want to prevent apt-get from deleting the cache you need to create an '/etc/apt/apt.conf' file.

Here's my apt.conf
```

APT {
   Archives {
      MaxAge "360";
      MaxSize "10000000";
   };
};
```

So far none of my cached files have been automatically deleted.

---

### Post by jiyuu0 on 2005-08-17
you might want to check this too:
[http://ubuntuforums.org/showpost.php?p=150088&postcount=1](http://ubuntuforums.org/showpost.php?p=150088&postcount=1)

---

