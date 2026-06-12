---
title: "Cannot see installed files and folder in GUI - Ubuntu 16.04 LTS 64-bit Desktop"
date: 2018-01-15
forum: General Help
---

### Post by nomonitor on 2018-01-15
Good evening all,

I am having some trouble with my fresh install of Ubuntu running a Counter Strike Source dedicated server with metamod and sourcemod.

I did command line installs of the packages but when I try to navigate to the folders that were created using the terminal it shows an empty folder even though I can navigate to that path through terminal.


matthew@Dedicated-Server-R1:/home/steam/steamCMD/css/cstrike/addons/metamod$ 


Screenshot showing the empty folder (css)...  [https://www.dropbox.com/s/jvsph55icy5srdf/Screenshot%20from%202018-01-15%2019%3A47%3A38.png?dl=0](https://www.dropbox.com/s/jvsph55icy5srdf/Screenshot%20from%202018-01-15%2019%3A47%3A38.png?dl=0)


I have made sure that "show hidden files" is checked.

3.4GB RAM
AMD Athlon II X2 B24
32 bit
1TB HDD

---

### Post by nomonitor on 2018-01-15
I have upgraded to 16.04 LTS with the same issue.

---

### Post by again? on 2018-01-15
"Home" as shown in the path toolbar represents **/home/$USER**
When in the file browser hit ctrl+l to show the location entry.
You'll see that it is
 ```
**/home/mathew**/steam/steamCMD/css/cstrike/addons/metamod
```
Not the same as the directory you are going to in the terminal...
```
**/home/steam**/steamCMD/css/cstrike/addons/metamod
```

---

### Post by nomonitor on 2018-01-15
Thank you so much!

---

### Post by again? on 2018-01-15
> **nomonitor said:**
> Thank you so much!
No problem. You can set the file browser to always show the location entry with
```
gsettings set org.gnome.nautilus.preferences always-use-location-entry true
```

---

### Post by nomonitor on 2018-01-16
Perfect, I applied that setting.

Thanks again!

---

