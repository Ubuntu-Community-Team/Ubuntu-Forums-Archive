---
title: "Wine - can't open applications"
date: 2006-12-18
forum: General Help
---

### Post by Klarsin on 2006-12-18
I have installed wine and installed two windows programs. I opened them right after install and they both worked fine. But when I tried to open again, they won't open. I guess I had the wong commands because I get a "can't find file" response. What is the correct command process to open these. These two are located under two different files - c: and drive_c. Its confusing.

---

### Post by tbroderick on 2006-12-18
wine /path/to/program.exe

---

### Post by Klarsin on 2006-12-21
Here is what I did:

-------
# wine /drive_c/program_files/autosketch/sketch.exe
wine: cannot find '/drive_c/program_files/autosketch/sketch.exe'

---

### Post by Get_Ya_Wicked_On on 2006-12-21
```

wine ~/.wine/drive_c/program_files/autosketch/sketch.exe

```

---

### Post by Klarsin on 2006-12-21
It still can't find the file. Iv'e checked the path carefully and it is correct. There is another path though. It is under c: rather than drive_c. Why are there two c drive folders?

-------
$ wine ~/.wine/drive_c/program_files/autosketch/sketch.exe
wine: cannot find '/home/kim/.wine/drive_c/program_files/autosketch/sketch.exe
-------

Also, when I do a system wide search for "sketch.exe" Ubuntu cant find it. This is like Windows ME!

---

### Post by hikaricore on 2006-12-21
> **Klarsin said:**
> It still can't find the file. Iv'e checked the path carefully and it is correct. There is another path though. It is under c: rather than drive_c. Why are there two c drive folders?

-------
$ wine ~/.wine/drive_c/program_files/autosketch/sketch.exe
wine: cannot find '/home/kim/.wine/drive_c/program_files/autosketch/sketch.exe
-------

Also, when I do a system wide search for "sketch.exe" Ubuntu cant find it. This is like Windows ME!

Are you sure it's:
```
wine ~/.wine/drive_c/*program_files*/autosketch/sketch.exe
```

and not:
```
wine ~/.wine/drive_c/**Program\ Files**/autosketch/sketch.exe
```

The folder is named "Program Files" by default, and the \ is needed to continue from a terminal in the case of a space character.  :)

Also linux is mostly case sensitive:

autosketch and Autosketch are different entirely.

Make sure it's the exact case.


Good Luck,

--Aaron

---

### Post by hikaricore on 2006-12-21
Also as far a searching goes for best results after making changes to the contents of your system, run:

```
sudo locate -u /
```

To update the locate database with all the new files on the system.

Then gnome/kde search as well as:

```
locate sketch.exe
```

Should work correctly.

Just thought it might help ya out, I run this every few days or so, even tho I believe the system does it automaticly, just not as often.

Note:  This will take awhile to run, no it didn't crash.

---

### Post by jhenager on 2006-12-21
> **Klarsin said:**
>  It is under c: rather than drive_c. Why are there two c drive folders?


Wine creates a 'dummy' windows drive so it doesn't corrupt your 'real' Windows directory. That's why you see two similarly named drives.

---

### Post by Klarsin on 2006-12-21
> **hikaricore said:**
> Are you sure it's:
```
wine ~/.wine/drive_c/*program_files*/autosketch/sketch.exe
```

and not:
```
wine ~/.wine/drive_c/**Program\ Files**/autosketch/sketch.exe
```

The folder is named "Program Files" by default, and the \ is needed to continue from a terminal in the case of a space character.  :)

Also linux is mostly case sensitive:

autosketch and Autosketch are different entirely.

Make sure it's the exact case.--Aaron


-----
$ wine ~/.wine/drive_c/Program\ Files/AutoSketch/Sketch.exe
err:module:import_dll Library acge15.dll (which is needed by L"C:\\Program Files \\AutoSketch\\sxMath2.dll") not found
err:module:import_dll Library sxMath2.dll (which is needed by L"C:\\Program File s\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACDB15.dll (which is needed by L"C:\\Program Files \\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library acge15.dll (which is needed by L"C:\\Program Files \\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACRX15.dll (which is needed by L"C:\\Program Files \\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACUTIL15.dll (which is needed by L"C:\\Program Fil es\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACDBXREF.dll (which is needed by L"C:\\Program Fil es\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library fct42.dll (which is needed by L"C:\\Program Files\ \AutoSketch\\Sx2.dll") not foundGood Luck,
err:module:import_dll Library kern42.dll (which is needed by L"C:\\Program Files \\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library Sx2.dll (which is needed by L"C:\\Program Files\\A utoSketch\\Sketch.exe") not found
err:module:import_dll Library acge15.dll (which is needed by L"C:\\Program Files \\AutoSketch\\sxMath2.dll") not found
err:module:import_dll Library sxMath2.dll (which is needed by L"C:\\Program File s\\AutoSketch\\Sketch.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\A utoSketch\\Sketch.exe" failed, status c0000135
$

-----
The caps were put in, but it looks like something is missing?

I have downloaded a new application "winexs" that is a GUI for all this. Don't know how well it works, but might using it resolve all these newbie errors?

---

### Post by hikaricore on 2006-12-21
> **Klarsin said:**
> -----
$ wine ~/.wine/drive_c/Program\ Files/AutoSketch/Sketch.exe
err:module:import_dll Library acge15.dll (which is needed by L"C:\\Program Files \\AutoSketch\\sxMath2.dll") not found
err:module:import_dll Library sxMath2.dll (which is needed by L"C:\\Program File s\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACDB15.dll (which is needed by L"C:\\Program Files \\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library acge15.dll (which is needed by L"C:\\Program Files \\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACRX15.dll (which is needed by L"C:\\Program Files \\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACUTIL15.dll (which is needed by L"C:\\Program Fil es\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library ACDBXREF.dll (which is needed by L"C:\\Program Fil es\\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library fct42.dll (which is needed by L"C:\\Program Files\ \AutoSketch\\Sx2.dll") not foundGood Luck,
err:module:import_dll Library kern42.dll (which is needed by L"C:\\Program Files \\AutoSketch\\Sx2.dll") not found
err:module:import_dll Library Sx2.dll (which is needed by L"C:\\Program Files\\A utoSketch\\Sketch.exe") not found
err:module:import_dll Library acge15.dll (which is needed by L"C:\\Program Files \\AutoSketch\\sxMath2.dll") not found
err:module:import_dll Library sxMath2.dll (which is needed by L"C:\\Program File s\\AutoSketch\\Sketch.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\A utoSketch\\Sketch.exe" failed, status c0000135
$

-----
The caps were put in, but it looks like something is missing?

I have downloaded a new application "winexs" that is a GUI for all this. Don't know how well it works, but might using it resolve all these newbie errors?

Doubtful winexs will help you here.

You are however on the right track though it may not seem like it due to the fact that you were able to locate and attempt to launch the application.

Possibly you should do some research at [Wine Application Database's section for Autosketch]("http://appdb.winehq.org/appview.php?iAppId=1826").

It would appear some of the newer versions are working properly after some minor adjustments, version 8 & 9 have a silver rating which mean someone(or multiple users) is/are able to get them running with some modifications.  Don't fool yourself into thinking this will be super easy if you don't know exactly how everything works, but it may help you to better understand wine and it's functions a little better in the end.

Failing this for any reason you can't waste time, or don't feel confident that you can make this work, you may want to see if [Crossover Office]("http://www.codeweavers.com/products/cxoffice/") has any support for your application.  Crossover is not free software, but if this is needed for a office/working environment and they do have support, it may be the more sensible route.

I'm not saying that I personally don't think you can get this running, just offering you solutions you may not know about.  From what I can tell with a little bit of tweaking your software will run in wine, I just don't know how deadset you are on getting it to do so.

Good luck,

--Aaron

---

### Post by Klarsin on 2006-12-23
> **hikaricore said:**
> Doubtful winexs will help you here.

Possibly you should do some research at [Wine Application Database's section for Autosketch]("http://appdb.winehq.org/appview.php?iAppId=1826").

I'm not saying that I personally don't think you can get this running, just offering you solutions you may not know about.  From what I can tell with a little bit of tweaking your software will run in wine, I just don't know how deadset you are on getting it to do so.

Good luck,

--Aaron

I'll work with it some more and check out that URL for wine autosketch, and like you said I may have to try crossover office, but would rather get as many apps working with wine as possible. 

Thanks

Paul

---

### Post by Klarsin on 2006-12-23
> **hikaricore said:**
> Doubtful winexs will help you here.

You are however on the right track though it may not seem like it due to the fact that you were able to locate and attempt to launch the application.

Possibly you should do some research at [Wine Application Database's section for Autosketch]("http://appdb.winehq.org/appview.php?iAppId=1826").

It would appear some of the newer versions are working properly after some minor adjustments, version 8 & 9 have a silver rating which mean someone(or multiple users) is/are able to get them running with some modifications.  Don't fool yourself into thinking this will be super easy if you don't know exactly how everything works, but it may help you to better understand wine and it's functions a little better in the end.

Failing this for any reason you can't waste time, or don't feel confident that you can make this work, you may want to see if [Crossover Office]("http://www.codeweavers.com/products/cxoffice/") has any support for your application.  Crossover is not free software, but if this is needed for a office/working environment and they do have support, it may be the more sensible route.

I'm not saying that I personally don't think you can get this running, just offering you solutions you may not know about.  From what I can tell with a little bit of tweaking your software will run in wine, I just don't know how deadset you are on getting it to do so.

Good luck,

--Aaron

I went to that wine URL and found the solution. The dll files are located in common shared folder where wine can't find them (this is for Autosketch 7). I just copied them over to the Autosketch folder and all works well now.

I'll remember to check the WineHQ next time for such probelems. 

Thanks, 

Paul

---

### Post by Irony on 2007-01-24
Heck this worked! I posted this problem in November 2005! Thanks Klarsin.

---

