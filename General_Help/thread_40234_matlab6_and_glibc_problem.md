---
title: "matlab6 and glibc problem"
date: 2005-06-08
forum: General Help
---

### Post by dukeleto on 2005-06-08
Hi everyone,
I had a working version of matlab 6 on my ubuntu hoary,
I updated this morning not very wide awake (i.e. without
looking exactly what was being updated) and now my matlab
no longer starts, with the following error message: 

/var/tmp/lm_TMW.ld: relocation error: /var/tmp/lm_TMW.ld: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

I suppose this is due to an update in the glibc?
If so, how hard would it be retrograde my glibc back to last week's version?
Also, just out of curiosity, does synaptic have a log file that can tell me its last 
operations?

Thanks,
Olivier

---

### Post by kleeman on 2005-06-08
I am using matlab 6.5 on a completely updated hoary system without any of the problems you describe. That error looks pretty wierd- have you been loading much third part software?

---

### Post by dukeleto on 2005-06-08
Hi Kleeman, and thanks for the fast answer!
uhh, yeah, I suppose I have a fair bit of "universe" software on the machine,
but I'm pretty sure none of that got updated: I only have the "hoary-updates" activated most of the time.
Well, at least it's encouraging if yours is still working!
Olivier

---

### Post by kleeman on 2005-06-08
I found this bug report in Fedora for matlab with your eror message

[https://bugzilla.redhat.com/bugzilla/long_list.cgi?buglist=110610](https://bugzilla.redhat.com/bugzilla/long_list.cgi?buglist=110610)


The problem appeared to be java and the workaround was to install a different version of java. FWIW my java is

sun-j2sdk1.5 and the installed package version is 1.5.0 update02

---

### Post by [pl]ice on 2005-06-09
hope that fix works :) i got matlab 7.0.1 and does the same thing. I tried one fix, and no no.
  P.s. u know when u open matlab under shell; would it open from KDE menu? my doesn't like that, and won't open. just wondering.

thanks.

---

### Post by kleeman on 2005-06-09
Sorry don't know about that (kde) I always open from a shell. CLI junk I guess....

---

### Post by dukeleto on 2005-06-09
Oof, finally got matlab working again: it was actually due to my updating my g++4.0...
thanks for you help!
Otherwize, yes, I'd already had to update the java version used by matlab although 
I was obliged to use an older version than yours, Kleeman: with jdk1.5 either the keyboard or the mouse didn't work (can't remember which). Did it work straight away for you? (or maybe you don't use the java ui?)
Olivier

---

### Post by 89c51 on 2005-08-15
im having similar problems with matlab 7.0.0

after the instalation (that went quite fine -the cd rom wasnt ejecting but opening a terminal and with the command eject cdrom i solved it)

at first it gave me a segmentation error

i restarted matlab but when i execute the following equation 
```
d=det(s*E-A)
``` 

i get the following message
```
Unable to load mex file: /usr/local/Matlab_7/toolbox/symbolic/maplemex.mexglx.
/usr/local/Matlab_7/bin/glnx86/libmaple.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
??? Invalid MEX-file '/usr/local/Matlab_7/toolbox/symbolic/maplemex.mexglx': .

Error in ==> maple at 104
[result,status] = maplemex(statement);

Error in ==> sym.maple at 85
[result,status] = maple(statement);

Error in ==> sym.mtimes at 17
   X = reshape(maple('scalarmul',B(:),A),size(B));

Error in ==> gener at 22
p=det(s*E-A)
``` 

where s is a symbol (syms s)
and E and A nxn matrices

any idea on how to solve this????

also when i type matlab in the command line in order to start matlab i get the following message but matlab start fine

```
Inconsistency detected by ld.so: rtld.c: 1259: dl_main: Assertion `_rtld_local._dl_rtld_map.l_prev->l_next == _rtld_local._dl_rtld_map.l_next' failed!
```

---

### Post by remi.a on 2005-09-07
Hi 89c51,

I had the same problem as you (errors with the maple symbolic toolbox).

Try with the command :

export LD_ASSUME_KERNEL=2.4.1 

in the shell, and then start matlab on the same shell, it's worked fine for me.



Now I have a question : Is somebody has troubles with fortran mex files ? I have fortran mex files which compile and run perfectly on a other platform and dist, and these sames mex file compile and CRASH matlab on my hoary. (More generaly all my mex files crash on horay even the simplest).

my config : 
-kernel 2.6.8.1
-matlab 7.0.0
-g77 3.3 (archive 1:3.3.4-9)
-gcc 3.3


cheers

---

### Post by remi.a on 2005-09-07
oops,

I made a mistake, I do not have a hoary but a warty....

Sorry.

---

### Post by kwisatz on 2005-10-18
I had the same problem on starting "lmstart". I have just modified this script adding:
export LD_ASSUME_KERNEL=2.4.1
and now all it works!
Thank you guys!

---

### Post by david_e on 2006-01-06
THX remi.a I had this problem to with Matlab 7.0.0 R14 and I solved this problem with ur suggestion. :D

---

### Post by m4rqz on 2006-10-04
Hello guys
The solution mentioned here does not work with Edgy Eft, I get this error:
```
$ LD_ASSUME_KERNEL=2.4.1 matlab
/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
```

Someone with a better (or equally good, but works with edgy..) solution?

cheers

---

### Post by yosefm on 2006-10-28
I have the same issue. It worked in dapper, but after an upgrade to Edgy, matlab will not run with any assumed kernel other than 2.6.x, which doesn't help. Though Matlab runs, the Symbolic Math Toolbox complains:

> symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference.

And its not lying. running 'readelf -s /lib/libc-2.4.so | grep errno' shown that it's really not there. Also, neither this libc nor the /lib/tls/** libc have ABI information, as far as I could see (with readelf -A and -n).

There's a reference to ths problem in the mathworks support site: [http://www.mathworks.com/support/solutions/data/1-1BDU5.html?1-1BDU5]("http://www.mathworks.com/support/solutions/data/1-1BDU5.html?1-1BDU5")

They suggest as an extreme measure instaling an older libc in parallel, but the Edgy repositories have only one libc, and I can't seem to manage an install from source-code of the suggested libc-2.2.5. Also, it seems that they rely on linuxthreads rather than NPTL, but I'm not sure if it's relevant today.

Can anyone package a working libc that will co-operate with the LD_ASSUME_KERNEL mechanism?

---

### Post by Alex.Gorban on 2006-11-28
I've the same problem and no idea how to make to work symbolic math in matlab under Edgy.

---

### Post by dnz on 2007-04-11
I think I've solved the problem (for Edgy - Matlab 7.0.0 R14)

download this library

[http://www.mathworks.com/support/solutions/attachment.html?resid=1-32V31N&solution=1-1BDU5](http://www.mathworks.com/support/solutions/attachment.html?resid=1-32V31N&solution=1-1BDU5)

after unzip copy libmaple.so to (to your mathlab)/bin/glnx86 folder

it worked for me


[http://www.mathworks.com/support/solutions/data/1-1BDU5.html](http://www.mathworks.com/support/solutions/data/1-1BDU5.html)

---

### Post by lucas.barcelos on 2007-11-13
> **dnz said:**
> I think I've solved the problem (for Edgy - Matlab 7.0.0 R14)

download this library

[http://www.mathworks.com/support/solutions/attachment.html?resid=1-32V31N&solution=1-1BDU5](http://www.mathworks.com/support/solutions/attachment.html?resid=1-32V31N&solution=1-1BDU5)

after unzip copy libmaple.so to (to your mathlab)/bin/glnx86 folder

it worked for me


[http://www.mathworks.com/support/solutions/data/1-1BDU5.html](http://www.mathworks.com/support/solutions/data/1-1BDU5.html)

Thanks a lot! Worked like a charm in kubuntu as well!

---

