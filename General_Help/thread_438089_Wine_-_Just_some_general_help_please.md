---
title: "Wine - Just some general help please"
date: 2007-05-09
forum: General Help
---

### Post by RudolfMDLT on 2007-05-09
Hi there,

I'm really need to get an application working on Ubuntu - unfortunately I can only use it in windows. It's neuro programmer 2. The application installs fine, but when open it, the splash screen appears and then after a minute disappears. How do I go about trouble shooting this? How do  you configure wine or get games to work in Linux? I may be asking a lot but the help will really be appreciated! Thanks a lot!

Rudolf

PS: the link to the application if any body's interested. [http://www.transparentcorp.com/products/np/download_home.php](http://www.transparentcorp.com/products/np/download_home.php)

---

### Post by zvacet on 2007-05-09
To configure wine type in terminal

```
winecfg
```

You can install app in several ways.

1.download exe in any folder(programs if you want organized things) and right click on it and you will see open with and you choose wine

2..download exe in any folder and type in terminal

wine /home/your_user name/folder where exe is/app exe

3.put exe in .wine folder(it is in home directory>view>show hidden folders)>program files and after that type in terminal 
```
winefile
```
you will find your exe in program files and just double click on it

---

### Post by defishguy on 2007-05-09
Another way to troubleshoot wine is to launch the Windows application from the terminal.

Typed out it might look something like this:

user@computer$wine ~/.wine/drive_c/Program Files/Folder/binary.exe

When the application closes the terminal window will still be open with any application messages still in it.

---

