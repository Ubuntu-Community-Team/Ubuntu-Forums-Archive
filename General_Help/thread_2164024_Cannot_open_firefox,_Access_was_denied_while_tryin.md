---
title: "Cannot open firefox, Access was denied while trying to open files in your profile dir"
date: 2013-07-20
forum: General Help
---

### Post by Kr0nZ on 2013-07-20
I just reinstalled ubuntu yesterday, 
shortly after the reinstall I was using a seperate program as root then after opening the help menu in this program it tried to open a web page and browser also as root, this caused firefox to be opened for the first time as root, and now I am unable to open firefox at all.

The .mozilla folder in my home directory was claimed as root, so I changed the permissions to my normal user and group (demon), but was still unsuccessful in opening firefox, then tried removing the profile directory in .mozilla/firefox, still no luck, then I tried removing firefox completely with "apt-get purge firefox" then reinstalling it, but still every time I open firefox I get the message "Access was denied while trying to open files in your profile directory."

So now I'm at a loss on what to do, I do use Chromium normally, but I also like to use Firefox to access certain sites.

**ETA** i did also try opening the firefox profile manager, with firefox -ProfileManager, but I still get the same message

```

demon@Access-Denied:~$ firefox
Error: Access was denied while trying to open files in your profile directory.
demon@Access-Denied:~$ 

```


```
demon@Access-Denied:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
```

```
demon@Access-Denied:~$ ll ~
drwx------  3 demon demon  4096 Jul 20 13:20 .mozilla/

```

```
demon@Access-Denied:~$ ll .mozilla/
total 12
drwx------  3 demon demon 4096 Jul 20 13:20 ./
drwxr-xr-x 35 demon demon 4096 Jul 20 13:29 ../
drwx------  3 demon demon 4096 Jul 20 13:20 firefox/


```

```

demon@Access-Denied:~$ ll .mozilla/firefox/
total 12
drwx------ 3 demon demon 4096 Jul 20 13:20 ./
drwx------ 3 demon demon 4096 Jul 20 13:20 ../
drwx------ 2 demon demon 4096 Jul 20 13:20 Crash Reports/

```

---

### Post by Kr0nZ on 2013-07-30
YES!! we are back.. Gratz UbuntuForums Team
however Im still having this firefox issue.. So, I hope someone can help :)

---

### Post by matteosistisette on 2013-10-12
Did you solve this? I have the same issue.
Looks like [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1180227](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1180227) but that's supposed to be fixed and there are not enough instruction about how to apply the workaround described there (where are those apparmor rules supposed to be added?)

---

