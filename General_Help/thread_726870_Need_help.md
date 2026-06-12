---
title: "Need help"
date: 2008-03-17
forum: General Help
---

### Post by LilLew on 2008-03-17
Hi i am new to linux i am using ubuntu 7.10 i am looking to play  a windows game using linux i have heard alot about this WINE application but i am unsure of how to install it  and config it please could some one help 

Thank you

---

### Post by NightwishFan on 2008-03-17
Open a terminal and type:
```
sudo apt-get update && sudo apt-get install wine
```

It should show up under the applications menu. The configuration is simple. Also do not be looking for perfection the Wine team already gives us miracles. Check the wine app database for information about a specific game. Just remember to visit all tabs of winecfg and autodetect drives.

---

### Post by LilLew on 2008-03-17
hi right i have done that but it will not let me config all tht has done is downloaded and installed i ahve done that if i go to run a windows program nothing is happening

---

### Post by NightwishFan on 2008-03-17
You have to install it with Wine. It will not run programs already installed in Windows, and some programs wont work at all. Find the .exe and right click run in Wine. I do not recommend Wine at all if you want Windows, use it.

Also you can use wine via terminal (thats what I did when I played around with wine)
```
cd /path/to/file && wine file.exe
```

---

### Post by zvacet on 2008-03-17
Type in terminal 

```
winecfg
```

---

