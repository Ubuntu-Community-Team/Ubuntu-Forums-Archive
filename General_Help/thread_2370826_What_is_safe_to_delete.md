---
title: "What is safe to delete ?"
date: 2017-09-07
forum: General Help
---

### Post by raleigh3 on 2017-09-07
Other than the backgrounds I want to keep, can  I delete everything else in the following dirs ?

I understand that my screensaver rotates backgrounds.
I can not find out what screensaver I have ?

```
drwxr-xr-x 2 andy 4096 08-26-2017 ubuntu-mate-xenial
drwxr-xr-x 2 root 4096 05-30-2017 ubuntu-mate-common
drwxr-xr-x 2 root 4096 04-20-2016 cosmos
drwxr-xr-x 5 root 4096 04-20-2016 mate

```

---

### Post by speartip on 2017-09-08
I'm not even sure what those directories are. I have nothing like them.
Personally though, I wouldn't delete anything from the root directory, it may cause problems elsewhere.
I'm intrigued though, what are you trying to achieve here? Is it just a space thing?

---

### Post by Perfect Storm on 2017-09-08
If it's root, leave it. You'll only causing unnecessary trouble by deleting stuff from there.

---

### Post by vasa1 on 2017-09-08
> **raleigh3 said:**
> ...
I can not find out what screensaver I have ?
...
If you haven't tinkered too much, it probably is *mate-screensaver*. And running```
apt list --installed | grep -i screensaver
```may provide some information.

---

### Post by him610 on 2017-09-08
It would be helpful if you showed the complete directory specifications.
```
/usr/share/doc/xubuntu-docs/
```

---

### Post by raleigh3 on 2017-09-08
> **vasa1 said:**
> If you haven't tinkered too much, it probably is *mate-screensaver*. And running```
apt list --installed | grep -i screensaver
```may provide some information.

mate-screensaver/xenial,now 1.12.0-1 amd64 [installed]
mate-screensaver-common/xenial,xenial,now 1.12.0-1 all [installed]

Thanks.

Can it be configured ?

---

### Post by raleigh3 on 2017-09-08
> **him610 said:**
> It would be helpful if you showed the complete directory specifications.
```
/usr/share/doc/xubuntu-docs/
```

Those were under /usr/share/backgrounds/

---

### Post by vasa1 on 2017-09-08
> **raleigh3 said:**
> Those were under /usr/share/backgrounds/

This information should be in the first post itself so that people know what you're talking about. Other useful information is here: [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by raleigh3 on 2017-09-08
> **vasa1 said:**
> This information should be in the first post itself so that people know what you're talking about. Other useful information is here: [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475")

It was an honest mistake.

No one is perfect.

---

