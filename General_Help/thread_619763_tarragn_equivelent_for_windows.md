---
title: "tarragn equivelent for windows"
date: 2007-11-21
forum: General Help
---

### Post by markp1989 on 2007-11-21
[http://www.planetside.co.uk/terragen/win/downloadwin.shtml](http://www.planetside.co.uk/terragen/win/downloadwin.shtml)

my friend showed me some scenery  he had generated using this, i was wondering if there are any programs that do this for Ubuntu. preferable in the repository's, but if there arnt  and in the repository i they will do??

---

### Post by MrFSL on 2007-11-21
I was successful getting this program running using wine.

I downloaded the Windows port and ran:
```
 wine msiexec /i ./tginstall0943.msi
```

Cheers!

EDIT: If you don't have wine installed you can find instructions:
here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by markp1989 on 2007-11-21
> **MrFSL said:**
> I was successful getting this program running using wine.

I downloaded the Windows port and ran:
```
 wine msiexec /i ./tginstall0943.msi
```

Cheers!

EDIT: If you don't have wine installed you can find instructions:
here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

thanks the install when fine, but i cannot run the program, i get an error saying 

"run time error 53
file not found terragen"

---

### Post by MrFSL on 2007-11-21
Odd..

try running if from the terminal and perhaps you will get better error message:

```
wine "C:\\Program Files\\Terragen\\Terragen.exe" 

```

---

### Post by markp1989 on 2007-11-21
> **MrFSL said:**
> Odd..

try running if from the terminal and perhaps you will get better error message:

```
wine "C:\\Program Files\\Terragen\\Terragen.exe" 

```

```
mark@mark-desktop:~$ wine "C:\\Program Files\\Terragen\\Terragen.exe"
fixme:ole:OleLoadPictureEx (0xb528d4,4718,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33faf0), partially implemented.
err:toolbar:ToolbarWindowProc unknown msg 2210 wp=00000001 lp=00010032
err:statusbar:StatusWindowProc unknown msg 2210 wp=0001 lp=00010036
fixme:ole:OLEPictureImpl_SaveAsFile (0x129f78)->(0x13b0f0, 0, (nil)), hacked stub.
err:module:import_dll Library msvcirt.dll (which is needed by L"C:\\Program Files\\Terragen\\Terragen.dll") not found

```

i have never used wine before so im sure what these mean

---

### Post by MrFSL on 2007-11-21
```
err:module:import_dll Library msvcirt.dll (which is needed by L"C:\\Program Files\\Terragen\\Terragen.dll") not found
```

This last line is the one we probably need to look at. This file (msvcirt.dll) should be located in:

~/.wine/drive_c/windows/system32/

I don't know why I have it and you don't... how did you install wine?

---

### Post by markp1989 on 2007-11-22
i installed from apt (sudo apt-get install wine), would it help if i can get that dll from a working windows machine?

---

### Post by markp1989 on 2007-11-22
i reinstalled using the deb prom the site, and then got the dll from my sisters pc, and it works ok now :D thansk for the help

---

### Post by MrFSL on 2007-11-22
sure thing, you're very welcome. Thanks for turning me on to a pretty interesting app.

:)

---

