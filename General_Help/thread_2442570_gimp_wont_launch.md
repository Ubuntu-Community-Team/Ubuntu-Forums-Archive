---
title: "gimp wont launch"
date: 2020-05-04
forum: General Help
---

### Post by guine on 2020-05-04
Since upgrading to 20.04 a last week I have been unable to get gimp to launch. When I try to launch it through the launcher or by trying to open an image in gimp I just get the spinning icon for it trying to work for several seconds and it goes away and nothing else happens. Anyone have any ideas?
Thanks

---

### Post by Frogs Hair on 2020-05-04
Try starting from the terminal and see what if any errors are reported. This won't work if using a snap version. 

```
gimp
```

---

### Post by guine on 2020-05-04
```
gimp: symbol lookup error: gimp: undefined symbol: gegl_rectangle_subtract
```

With some more searches I've seen some things about python issues with scripts from it being updated and I do have one python script, could removing that folder from my script folder help?

---

### Post by mc4man on 2020-05-05
Remove whatever package of libgegl you have, to get the package name run
```
apt-cache policy libgegl*
``` 
It''l be named something like libgegl-0.4-0 or similar, use the name of the installed one, remove with apt.
Then re-install gimp.

Or remove gimp and run sudo apt autoremove.
Most likely you have  ppa or locally install gegl source packages in 18.04 that weren't updated to the one's used by gimp in 20.04's gimp package.

---

### Post by ActionParsnip on 2020-05-05
[https://askubuntu.com/questions/1086452/gimp-2-10-will-not-start-due-to-undefined-symbol-gegl-operation-get-source-spac](https://askubuntu.com/questions/1086452/gimp-2-10-will-not-start-due-to-undefined-symbol-gegl-operation-get-source-spac)

---

### Post by guine on 2020-05-05
Clearing out the libgegl and reinstalling worked. Thanks

---

