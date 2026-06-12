---
title: "Cedega from CVS. error: invalid lvalue in increment"
date: 2005-10-14
forum: General Help
---

### Post by meastp on 2005-10-14
So, I just got Breezy up and running fresh from CD.

I want Cedega from cvs for RA2 and WC3, so I am following this guide:
[http://frankscorner.org/index.php?p=cedegacvs](http://frankscorner.org/index.php?p=cedegacvs)

However, the ./tools/wineinstall gives me the following error:

newstruc.c: In function &#8216;handle_ani_list&#8217;:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function &#8216;new_ani_curico&#8217;:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/meastp/nedlastet/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/meastp/nedlastet/winex/tools'
make: *** [tools] Error 2
meastp@ubuntu:~/nedlastet/winex$

How can I solve this?
How to clean up the mess (./configure and make, I think) so I can start over?

EDIT: I know there are quite a lot of threads regarding this issue, but they were never really solved, were they?

---

### Post by meastp on 2005-10-14
I found the code on lines 740 and 851. They are identical: ((char *)rtp)++;
			


------------------------------------------------------------------------


/* FIXME: This relies in sizeof(DWORD) == sizeof(pointer_type) */
			if((DWORD)rtp & 1)
				((char *)rtp)++;
		}

		/* We must end correctly here */

-------------------------------------------------------------------------

However, I'm no programmer, so I guess I'll have to wait if this is a developer issue?

---

### Post by Wavey on 2005-10-14
I'm having the same problem. This is happens if you try the version cedega_head_userinstall (option 0 ) and also when you try version winex330 (option 8 ).

I was expecting it to be a problem with the latest build, but when I built v. 330 it gave me the same error so I am a little puzzled :)

Anybody any ideas?

---

### Post by aminalshmu on 2005-10-14
some searching today told me that it's a gcc4 problem. apt-get install gcc-3.3 or gcc-3.4, then a quick "export CC=gcc-3.3" (or 3.4) will let you run the cvs cedega script without a problem, after it cleans up the working directory. there is an option somewhere in the script to uninstall/clean/whatever, it's just a little tricky to navigate at first. cvscedega compiles cleanly after that though.

my problem is cvscedega refuses to run my diablo II installer and gives me a segfault... need to tweak settings maybe, or compile with gcc3.3 instead of 3.4 maybe... who knows. good luck to both of you.

EDIT: gcc-3.3 is no go. use 3.4 only.

---

### Post by Wavey on 2005-10-15
Cool - thanks. I got gcc 3.4 and it *seems* to be running okay now :) Its got onto make install and no problems yet... fingers crossed :)


Thanks!

---

### Post by meastp on 2005-10-15
Hi!

I had tried export, but had not checked whether the gcc-3.4 package was installed. When I installed it, it worked, sort of, anyway. This is at the very end of the script:
```

Configuring Wine without Windows.
Some fake Windows directories must be created, to hold any .ini files, DLLs,
start menu entries, and other things your applications may need to install.
Where would you like your fake C drive to be placed?
(default is /c) yes
Configuring Wine for a no-windows install in yes...

Created /home/meastp/.wine/config using default Wine configuration.
You probably want to review the file, though.

Compiling regapi...
rm -f regapi && ln -s ../../tools/winelibwrap regapi

Preparing to install default Wine registry entries...
Installing default Wine registry entries...

./tools/wineinstall: line 562: programs/regapi/regapi: Ikke tilgang
Registry install failed.

meastp@ubuntu:~/cedega/winex$

```

How can I solve this?

"Ikke tilgang" = "Permission denien", btw.

EDIT: Google told me the solution: chmod +x winelibwrap

---

### Post by meastp on 2005-10-15
D'oh... Now I get another error message instead:

```
Created /home/meastp/.wine/config using default Wine configuration.
You probably want to review the file, though.

Compiling regapi...
rm -f regapi && ln -s ../../tools/winelibwrap regapi

Preparing to install default Wine registry entries...
Installing default Wine registry entries...

/home/meastp/cedega/winex/wine: binary overlaps reserved area (08048000-0804c95c )
wine: chdir to /home/meastp/.wine/wineserver-ubuntu : No such file or directory
Registry install failed.

meastp@ubuntu:~/cedega/winex$

```

Ok, so I skipped the error and moved on. Have gotten this far:

```

meastp@ubuntu:~$ wine dcom98.exe
wine: exists lstat socket : No such file or directory
meastp@ubuntu:~$ wineserver
meastp@ubuntu:~$ wine dcom98.exe
fixme:win32:PE_CreateModule Security directory ignored
Warning: Language 'nb_NO' was not found, retrying without country name...
Warning: Language 'nb' was not recognized, defaulting to English
XIO:  fatal IO error 0 (Success) on X server ":0.0"
      after 19 requests (18 known processed) with 0 events remaining.
meastp@ubuntu:~$

```

Now, what?

---

### Post by meastp on 2005-10-16
Noone? I've tried googling it, and it seems that a lot of people has this problem. However, I found no solution.

UPDATE: I tried again today and for a minute or so, it worked. The "Would you like to install dcom98" showed up. Then again, after a minute or so, without touching anything, it terminated with:

```

XIO:  fatal IO error 0 (Success) on X server ":0.0"
      after 226 requests (198 known processed) with 0 events remaining.

```

---

