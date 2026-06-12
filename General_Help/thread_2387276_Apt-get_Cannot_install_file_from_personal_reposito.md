---
title: "Apt-get Cannot install file from personal repository"
date: 2018-03-17
forum: General Help
---

### Post by zimasystem on 2018-03-17
Hello 
A few days i am looking for some ways to install software on my Ubuntu 17.10 with out an internet connection.
I found some thread that show many solution for that the best way i think i found it :

Run Local Repository 
1 ) with local Apache web service (need internet connection for install Apache and Some Dependency)
2 ) file location that (I used it)

I know some software developed for this same as Keryx but that not work for me ! it make my computer very slow and no response

Finally i run my personal repository from this tutorial : 
[Personal Repository Tutorial]("https://help.ubuntu.com/community/Repositories/Personal")

I got a lot of errors that I could fix some of them but now i have error on installation that some others have same problem as my issue
same as : [URL="https://ubuntuforums.org/showthread.php?t=2321662&amp;"]This Link
[/URL]
this is my error
```

Get:2 file:/usr/local/mydebs ./ InRelease
Ign:2 file:/usr/local/mydebs ./ InRelease
Get:3 file:/usr/local/mydebs ./ Release
Err:3 file:/usr/local/mydebs ./ Release
  File not found - /usr/local/mydebs/./Release (2: No such file or directory)


N: Updating from such a repository can't be done securely, and is therefore disabled by default. 
N: See apt-secure(8) manpage for repository creation and user configuration details. 


```
I download my package with 2 ways .... get same error
1 ) copy from /var/cache/apt/archives on other pc have internet connection
2 ) use this command
```
$ apt-get download $(apt-cache depends --recurse --no-recommends --no-suggests --no-conflicts --no-breaks --no-replaces --no-enhances --no-pre-depends <your-package-here> | grep "^\w" | sort -u)
```
Have any tested solution for my issue ?

Thank in advance

---

### Post by zimasystem on 2018-03-18
I found my problem
Apt-get update show some error but it is not make any issue on local repository
i try to install package with Apt-get install pkg-name and have error
we should use this Apt install pkg-name

---

