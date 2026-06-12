---
title: "Wine very slow"
date: 2005-03-21
forum: General Help
---

### Post by cory-79 on 2005-03-21
Hi i've installed wine, made the setup, but now when i start an application i get this error and then after 3 minuts it start

```
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels to set the screen resolution and remove the "Resolution" entry in the config file 
``` 

Any suggestion ?

---

### Post by az on 2005-03-21
Did you use winetools?

winesetup is depreciated.


You can get the latest wine packages from winehq.  They have current ubuntu and debian packages.

---

### Post by cory-79 on 2005-03-22
I get wine from the repository 
```
http://wine.sourceforge.net/apt/
``` 

I used winesetup, now i try winetools.

Tnx

---

### Post by cory-79 on 2005-03-22
can't get arial font

```
downloading http://umn.dl.sourceforge.net/sourceforge/corefonts/arial32.exe to arial32.exe with 554208 bytes... 
``` 

any idea ?

---

### Post by cory-79 on 2005-03-22
I got this error when try to right click to paste in any win application started with wine

```

X Error of failed request:  BadMatch (invalid parameter attributes)  
 Major opcode of failed request:  1 (X_CreateWindow)   
Serial number of failed request:  793   Current serial number in output stream:  794
 
```

---

### Post by az on 2005-03-22
[QUOTE=cory-79]can't get arial font

```
downloading http://umn.dl.sourceforge.net/sourceforge/corefonts/arial32.exe to arial32.exe with 554208 bytes... 
``` 

any idea ?[/QUOTE]


sudo apt-get install msttcorefonts.

(I removed it, since it uglified my desktop fonts)

---

### Post by cory-79 on 2005-03-26
[QUOTE=cory-79]I got this error when try to right click to paste in any win application started with wine

```

X Error of failed request:  BadMatch (invalid parameter attributes)  
 Major opcode of failed request:  1 (X_CreateWindow)   
Serial number of failed request:  793   Current serial number in output stream:  794
 
```[/QUOTE]

Noone can help me ?

---

### Post by jdong on 2005-03-26
What version of WINE are you using? Official Ubuntu? Backports-Staging? WineHQ?

---

### Post by cory-79 on 2005-03-28
I get wine from the repository 
```
http://wine.sourceforge.net/apt/
```

---

### Post by cory-79 on 2005-04-09
New wine version, new error :-|

when using winetools, in "create fake windows" i get this error

```

wine: cannot find 'wineboot' 
Wine failed with return code 1 
no suitable Wine directory found... 

``` 

I installed "wine" "winetools" "libwine", i miss something ?

---

### Post by Giturar on 2005-04-15
[QUOTE=cory-79]New wine version, new error :-|

when using winetools, in "create fake windows" i get this error

```

wine: cannot find 'wineboot' 
Wine failed with return code 1 
no suitable Wine directory found... 

``` 

I installed "wine" "winetools" "libwine", i miss something ?[/QUOTE]

im getting this exact error as well, ive tried running winetools as sudo and normally

---

### Post by berthold on 2005-04-22
I had the same problem with winetools, you can solve it by installing wine-utils.

-berthold

---

