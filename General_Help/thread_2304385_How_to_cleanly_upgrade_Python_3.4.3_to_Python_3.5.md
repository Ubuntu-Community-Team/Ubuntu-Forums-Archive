---
title: "How to cleanly upgrade Python 3.4.3 to Python 3.5"
date: 2015-11-26
forum: General Help
---

### Post by Cbhihe on 2015-11-26
[FONT=arial]I have Python 2.7.6 and Python 3.4.3 installed and functional on Trusty 14.04.3.
 
2.7.6 is there for keeps. However I'd like to upgrade version 3.4.3 to 3.5.0 in a clean way, i.e. not just piling up a new python version on top of the already installed packages but cleaning up leftovers from 3.4.3 after installing 3.5.0.   I am a little confused as to how I should proceed and I need help.
To be clear, I _*do not*_ need this minor (?) upgrade. I want to conduct it for the sale of learning how to do it properly.

 The easiest route is probably to just use `synaptic' to install the appropriate 3.5.0 packages: [/FONT]
[FONT=courier new]    python3.5
    python3.5-minimal
    python3.5-complete
[/FONT]and all suggested dependencies, and to redirect the soft link in [FONT=courier new]/usr/bin/[/FONT]     
     [FONT=courier new] 0 lrwxrwxrwx 1 root root  9 May  9  2014 python3 -> python3.4*[/FONT]
to what I imagine would probably be [FONT=courier new][FONT=arial]the newly installed: [/FONT]/usr/bin/python3.5[FONT=arial]

But then what should I do with version 3.4.3 specific archives?  
Can I rid my system of them in a systematic and clean way, i.e. without playing havoc with the ressources meant to stay and needed.?

What I have seen is that if I mark [FONT=courier new]python3.4[/FONT] packages for [/FONT]"complete removal"[FONT=arial] using `synaptic[/FONT][/FONT][FONT=arial]', also removing many reverse dependencies is problematic as they include:
       [FONT=courier new]apparmor, apport, bluez,..., libreoffice,... unity8[/FONT]. So that's off. [/FONT]
[FONT=arial]
Background: I installed Python 3.4.3 manually (from the [FONT=courier new]Python-3.4.3.tar.xz[/FONT] tar ball I still have in storage) back in May 2015.
However I do not remember the install steps I followed, for not having documented them (very unlike me). 
What I do know is I did ***not*** use [FONT=courier new]python-pip[/FONT]. In fact at this point I still do not have `pip' installed.

Pointers, advice and guidance welcome. 
[SIZE=1](Some sort of a tutorial is lacking on the subject. At least I have not seen one that could help me.)[/SIZE]
Thanks.-ced. 
[/FONT]

---

### Post by Cbhihe on 2015-11-27
_**Update**_: 
Finally I resorted to installing the `python 3.5' package and its **2908** library files using Synaptic on top of my existing functional 3.4 install. 
Looking at the result:
[FONT=courier new] $ cd /usr/bin
 $ ls -lsAFi python*
393463       0 lrwxrwxrwx 1 root root        18 Jul  2  2014 python -> /usr/bin/python2.7*
394201       0 lrwxrwxrwx 1 root root         9 May  9  2014 python2 -> python2.7*
393228  3272 -rwxr-xr-x 1 root root  3345416 Jun 22 20:51 python2.7*
394075       0 lrwxrwxrwx 1 root root        33 Jun 22 20:51 python2.7-config -> x86_64-linux-gnu-python2.7-config*
398355       0 lrwxrwxrwx 1 root root        16 Dec 21  2013 python2-config -> python2.7-config*
394203       0 lrwxrwxrwx 1 root root         9 Nov 27 11:04 python3 -> python3.5*
394046  3628 -rwxr-xr-x 2 root root  3709944 Oct 14 23:42 python3.4*
394046  3628 -rwxr-xr-x 2 root root  3709944 Oct 14 23:42 python3.4m*
395645  3672 -rwxr-xr-x 2 root root  3754696 Sep 17 19:03 python3.5*
396673       0 lrwxrwxrwx 1 root root        33 Sep 17 19:03 python3.5-config -> x86_64-linux-gnu-python3.5-config*
396677       0 lrwxrwxrwx 1 root root        11 Sep 17 19:03 python3.5-dbg -> python3.5dm*
396678       0 lrwxrwxrwx 1 root root        37 Sep 17 19:03 python3.5-dbg-config -> x86_64-linux-gnu-python3.5-dbg-config*
396676 13164 -rwxr-xr-x 1 root root 13455475 Sep 17 18:58 python3.5dm*
396679       0 lrwxrwxrwx 1 root root        35 Sep 17 19:03 python3.5dm-config -> x86_64-linux-gnu-python3.5dm-config*
395645  3672 -rwxr-xr-x 2 root root  3754696 Sep 17 19:03 python3.5m*
396674       0 lrwxrwxrwx 1 root root        34 Sep 17 19:03 python3.5m-config -> x86_64-linux-gnu-python3.5m-config*
394206       0 lrwxrwxrwx 1 root root        10 Nov 27 11:12 python3m -> python3.5m*
398354       0 lrwxrwxrwx 1 root root        16 Dec 21  2013 python-config -> python2.7-config*[/FONT]

--> ...  symbolic links (normal for any python install, I believe) and two hard link (inode:[FONT=courier new]394046 [FONT=arial]and[/FONT] [/FONT][FONT=courier new]395645[/FONT]).

My questions become:
  - What is the purpose of files [FONT=courier new]pythonX.Y[/FONT] and [FONT=courier new]pythonX.Ym[/FONT] co-existing ?
    [FONT=courier new]python3.4[/FONT] and [FONT=courier new]python3.4m[/FONT] point to the same stored content with two names (hard link). 
    The same can be said of [FONT=courier new]python3.5[/FONT] and [FONT=courier new]python3.5m[/FONT].
    So what is the use of [FONT=courier new]python3.4m[/FONT] and [FONT=courier new]python3.5m[/FONT] ?
  - Can I get rid of [FONT=courier new]/usr/bin/python3.4*[/FONT] as well as of [FONT=courier new]python3.4[/FONT] libraries and how should I proceed ?

Tx -ced

---

