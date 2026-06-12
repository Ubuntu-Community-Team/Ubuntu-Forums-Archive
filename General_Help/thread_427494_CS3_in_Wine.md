---
title: "CS3 in Wine"
date: 2007-04-29
forum: General Help
---

### Post by Bender00 on 2007-04-29
I followed the instructions at [http://portableapps.com/node/4310]("http://portableapps.com/node/4310") to make a portable version of Photoshop CS3 and moved it onto a flash drive.

I then had to copy msvcr80.dll, msvcp80.dll and gdiplus.dll to the folder.

When I try to execute the Photoshop.exe in wine I get the following error:

[B]Runtime Error!

Program: I:\CS3 Portable\Photoshop.exe

R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application's support team for more information.[/B]


Is this something that I can workaround or correct?

---

### Post by BRAXS69 on 2007-04-29
have you tried opening a terminal window, entering "cd  location of the cs3 folder" (the linux location not the fake windows location, can be done simply by just drag and drop the folder in terminal) then.
"wine Photoshop.exe" if it doesn't work paste the information in the terminal so i can see

---

### Post by Bender00 on 2007-04-29
I still get the message box with the previous error 

Here are the contents of the terminal:

bender00@ubuntu:~$ cd '/media/UDISK 2.0/CS3 Portable' 
bender00@ubuntu:/media/UDISK 2.0/CS3 Portable$ wine Photoshop.exe
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x337b6c
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
err:module:LdrInitializeThunk "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"I:\\CS3 Portable\\Photoshop.exe" failed, status c0000142

---

### Post by BRAXS69 on 2007-04-30
3 things it could be 1. it cant find the dlls 2. you don.t have permissions to t
he fake c 3. fake c is not setup properly. i never paid much attention to error language they use. but the only real thing it should be is the first one, the other2 would be very very odd to have only capable if you changed it yourself.  

looking by what you have said and the the link have you copied "msvcr80.dll, msvcp80.dll and gdiplus.dll", did you it to the fake c:\windows\system32 dir? if not you should. 

type 
"nautilus ~/.wine/drive_c/windows/system32"  copy "msvcr80.dll, msvcp80.dll and gdiplus.dll" into there
close the window
then try and run photoshop

i also did a little hunting on you error and found this [page link]("http://ubuntuforums.org/archive/index.php/t-180831.html")
the guy has almost the same kind of error message as you do by what they say it was the second and third thing.


if things still don't work after all that, the only thing i could suggest it pop in the photoshop cd and install it and see if it will at least run under wine, it should i installed photoshop and it worked for me. 


sorry if i cant be of much help...

---

### Post by Bender00 on 2007-04-30
Thanks for your help.

I copied the dll files to system32 and my CS3 folder

I then tried removing the .wine directory and running winecfg again and then re-copied the dll to system32.

Unfortunately, none of this changed the error message box that would come up in wine.

I did, however, find this which may have something to do with it.

> See [http://bugs.winehq.org/show_bug.cgi?id=6591](http://bugs.winehq.org/show_bug.cgi?id=6591)
It's possible that a single touch cl.exe.manifest in the right place
will help...
otherwise you might have to wait for activation context / sxs support
to be implemented in wine.   (Which might happen before long, you
never know.) 

I tried using a manifest, but it only changed the message box error to module not found.

I guess I'll try installing from disk and if that doesn't work I will just have to use CS2 until wine is capable of running CS3.

Thanks again

---

### Post by BRAXS69 on 2007-04-30
well i guess its just a matter of time, i found that there is a hell of a lot of work  put in  [ the wine project]("http://www.winehq.org") and if it doesn't work now it will always seem to ether work better the next release or work completely, well that's my experience with it anyways.

of cause you could always learn to use "Gimp Image editor", sure the names are a little differtent and so is the layout but that's only something you get used to over time. plus its possible to run photoshop plugins in Gimp, never tried though so i don't know how...

anyways cya and good luck XD

---

### Post by xjas05 on 2007-05-03
gimp sucks =( try the program called Pixel, one and only true replacement for photoshop on linux =)

---

### Post by ZombieBear on 2007-09-27
In any case, Photoshop CS2 works fine on Ubuntu 7.04. If you have a license, you could use that until CS3 works.

---

### Post by anaconda on 2007-09-27
same thing here. CS2 works. Couldn't get CS3 to work. that was about 5 months ago..

---

