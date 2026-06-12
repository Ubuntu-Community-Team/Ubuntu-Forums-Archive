---
title: "Installing compiz xgl - looks like beerorkid and blutkind.org have messed up scripts?"
date: 2006-11-21
forum: General Help
---

### Post by Litropy on 2006-11-21
This is my sources.list:
```
deb http://www.beerorkid.com/compiz edgy main-edgy
deb http://media.blutkind.org/xgl/ edgy main-edgy
deb http://www.beerorkid.com/compiz edgy main-edgy
deb http://media.blutkind.org/xgl/ edgy main-edgy
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

```


this is what I get when I try sudo apt-get update:
```
litropy@Litropy:~$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Get:3 http://www.beerorkid.com edgy Release.gpg [189B]
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Get:4 http://us.archive.ubuntu.com edgy-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Get:5 http://media.blutkind.org edgy Release.gpg [189B]
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release
Hit http://security.ubuntu.com edgy-security/main Packages
Ign http://media.blutkind.org edgy/main-edgy Translation-en_US
Ign http://media.blutkind.org edgy/main-edgy Translation-en_US
Hit http://us.archive.ubuntu.com edgy-updates Release
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://media.blutkind.org edgy Release
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Ign http://www.beerorkid.com edgy/main-edgy Translation-en_US
Ign http://www.beerorkid.com edgy/main-edgy Translation-en_US
Hit http://www.beerorkid.com edgy Release
Fetched 193B in 1s (101B/s)
Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/Release  Unable to find expected entry  main-edgy/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://media.blutkind.org/xgl/dists/edgy/Release  Unable to find expected entry  main-edgy/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
litropy@Litropy:~$     
```


I tried adding  "main-ppc" to the end of the deb lines like this:
```

deb http://www.beerorkid.com/compiz edgy main-edgy main-ppc
deb http://media.blutkind.org/xgl/ edgy main-edgy main-ppc
deb http://www.beerorkid.com/compiz edgy main-edgy main-ppc
deb http://media.blutkind.org/xgl/ edgy main-edgy main-ppc
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

```


and I still get this:
```
litropy@Litropy:~$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Get:3 http://www.beerorkid.com edgy Release.gpg [189B]
Ign http://www.beerorkid.com edgy/main-edgy Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Get:4 http://us.archive.ubuntu.com edgy-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Get:5 http://media.blutkind.org edgy Release.gpg [189B]
Ign http://media.blutkind.org edgy/main-edgy Translation-en_US
Ign http://media.blutkind.org edgy/main-ppc Translation-en_US
Ign http://media.blutkind.org edgy/main-edgy Translation-en_US
Ign http://media.blutkind.org edgy/main-ppc Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://media.blutkind.org edgy Release
Hit http://us.archive.ubuntu.com edgy-updates Release
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Ign http://www.beerorkid.com edgy/main-ppc Translation-en_US
Ign http://www.beerorkid.com edgy/main-edgy Translation-en_US
Ign http://www.beerorkid.com edgy/main-ppc Translation-en_US
Hit http://www.beerorkid.com edgy Release
Fetched 193B in 4s (42B/s)
Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/Release  Unable to find expected entry  main-edgy/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://media.blutkind.org/xgl/dists/edgy/Release  Unable to find expected entry  main-edgy/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
litropy@Litropy:~$  
```

any ideas?

---

