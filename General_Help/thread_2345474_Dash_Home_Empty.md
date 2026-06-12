---
title: "Dash Home Empty"
date: 2016-12-04
forum: General Help
---

### Post by stepheny on 2016-12-04
I am using Ubuntu 16.04 and recently noticed that Dash home is empty with a message that no applications could be found. This has happened over the last few days and is not because of the upgrade to 16.04 which I did months ago. If I start a search in Dash the apps are found. 

After opening the Dash, syslog reports the following:

```
04.12.16 14:50  steve64bit-EasyNote com.canonical.Unity.Scope.Home[1579]    (unity-scope-home:2454): unity-scope-home-WARNING **: scope.vala:669: Unable to search scope: Zeitüberschreitung wurde erreicht

04.12.16 14:50  steve64bit-EasyNote-TSX66HR com.canonical.Unity.Scope.Home[1579]    (unity-scope-home:2454): libunity-WARNING **: unity-master-scope.vala:114: Unable to search scope: 'Zeitüberschreitung wurde erreicht'
```

I have reinstalled unity-scope-home but the probem remains.

---

### Post by stepheny on 2016-12-05
I have found the solution. I purged all zeitgeist installs (zeitgeist-core, zeitgeist-datahub etc)  except for libzeitgeist-2,0-0 (too many dependencies inluding nautilus!) and then re-installed them all and  then re-installed libzeitgeist-2,0-0 too.

---

### Post by n-righeriu on 2016-12-05
I also have this problem on ubuntu 16.04, some support would be great. 
EDIT: after reinstalling unity-scope-home it worked for me

---

