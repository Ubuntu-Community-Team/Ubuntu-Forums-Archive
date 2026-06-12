---
title: "Installing Mendeley Dektop in Ubuntu 20.04"
date: 2020-08-02
forum: General Help
---

### Post by drpjkurian on 2020-08-02
Hi
Please follow the steps to install Mendeley Desktop in Ubuntu. The usual Debian files provided by the Mendeley desktop website failed to install in My Dell Latitude. I realized the following dependencies were missing and installed it by the following command in the terminal. ```
sudo apt-get install gconf2
```
I extracted the tarball to my home folder. The tarball was downloaded from the Mendeley website.
I used the Menu editor to create the launcher. Menu editor can be installed from the software center. In the command box, I entered the following  ```
/home/dr/mendeleydesktop-1.19.4-linux-x86_64/bin/mendeleydesktop
``` Please change the path according to the destination of the folder in your machine.

However, you can also try running the software from the command line. Go the extracted folder of Mendeley Desktop, In my case, it is in the home folder. Right-click anywhere in the opened window and select 'open in terminal' from the pop-up. In the terminal type the following command to run the software. 
```
./bin/mendeleydesktop
```

---

