---
title: "how to install ColdFusion ?????"
date: 2007-11-28
forum: General Help
---

### Post by myharshdesigner on 2007-11-28
i have ColdFusion.bin file

i have installed apache2 , mysql , java , php , phpmyadmin.

now i want to install ColdFusion and set port no 4444 for ColdFusion.


can any one help me ?

---

### Post by zacbarton on 2007-11-28
myharshdesigner,

Try this link for help. [http://www.compoundtheory.com/?action=displayPost&ID=233](http://www.compoundtheory.com/?action=displayPost&ID=233)

---

### Post by myharshdesigner on 2007-11-29
thanks i will try

---

### Post by TylerMcManus on 2007-11-29
i just spent the evening installing coldfusion 8 on a similar setup, and thought i would post a tutorial for anyone that could use it. i hope this helps you.

[http://www.tylermcmanus.com/2007/11/29/tutorial-adding-coldfusion-8-to-your-ubuntu-lamp-server/]("http://www.tylermcmanus.com/2007/11/29/tutorial-adding-coldfusion-8-to-your-ubuntu-lamp-server/")

as far as changing the port, i haven't done it, but you could try this:

[http://livedocs.adobe.com/coldfusion/7/htmldocs/wwhelp/wwhimpl/common/html/wwhelp.htm?context=ColdFusion_Documentation&file=00000017.htm]("http://livedocs.adobe.com/coldfusion/7/htmldocs/wwhelp/wwhimpl/common/html/wwhelp.htm?context=ColdFusion_Documentation&file=00000017.htm")

---

### Post by myharshdesigner on 2007-11-29
thanks for the tutoril i have install coldfusion but when i try to topen this link i am getting this error :-
[PHP]
http://localhost/CFIDE/administrator/index.cfm
[/PHP]


error is in attachement pl see.
thanks.




> **TylerMcManus said:**
> i just spent the evening installing coldfusion 8 on a similar setup, and thought i would post a tutorial for anyone that could use it. i hope this helps you.

[http://www.tylermcmanus.com/2007/11/29/tutorial-adding-coldfusion-8-to-your-ubuntu-lamp-server/]("http://www.tylermcmanus.com/2007/11/29/tutorial-adding-coldfusion-8-to-your-ubuntu-lamp-server/")

as far as changing the port, i haven't done it, but you could try this:

[http://livedocs.adobe.com/coldfusion/7/htmldocs/wwhelp/wwhimpl/common/html/wwhelp.htm?context=ColdFusion_Documentation&file=00000017.htm]("http://livedocs.adobe.com/coldfusion/7/htmldocs/wwhelp/wwhimpl/common/html/wwhelp.htm?context=ColdFusion_Documentation&file=00000017.htm")

---

### Post by myharshdesigner on 2007-11-29
any one can help me to solve this problem?

---

### Post by TylerMcManus on 2007-11-30
> **myharshdesigner said:**
> thanks for the tutoril i have install coldfusion but when i try to topen this link i am getting this error :-
[PHP]
http://localhost/CFIDE/administrator/index.cfm
[/PHP]


error is in attachement pl see.
thanks.
well the coldfusion service is running because that error screenshot you attached was produced by coldfusion itself, so thats a good thing at least. couple questions:

1. when it asked where to install the coldfusion administrator, what did you enter?

2. when it was installing in the terminal window, did you get the message saying the first part of the installation was complete? if you did, what was the url it told you to open in your browser?

3. can you post the output of this command: ls /var/www/

---

### Post by myharshdesigner on 2007-11-30
1. when it asked where to install the coldfusion administrator, what did you enter?

the dir is :-

> /home/harsh/web/coldfusion

---

### Post by myharshdesigner on 2007-11-30
now i have reinstall my ubuntu BOX.

now i wana install

1. apache2

2. php

3. tomcat

4. coldfusion

5. mysql

6. phpmyadmin

so can you help me out how to instal these thing and make it work. ?

and i also wana provide my own DIR like [PHP]/home/username/web/tomcat[/PHP] for tomcat

[PHP]/home/username/web/php[/PHP] for PHP

[php]/home/username/web/coldfusion[/php] for coldfusion.

can we do that ?

and thanks for your Gr8 Help




> **TylerMcManus said:**
> well the coldfusion service is running because that error screenshot you attached was produced by coldfusion itself, so thats a good thing at least. couple questions:

1. when it asked where to install the coldfusion administrator, what did you enter?

2. when it was installing in the terminal window, did you get the message saying the first part of the installation was complete? if you did, what was the url it told you to open in your browser?

3. can you post the output of this command: ls /var/www/

---

### Post by TylerMcManus on 2007-12-01
when you said your coldfusion admin directory was: /home/harsh/web/coldfusion, is that your apache web root as well? if so, i'm curious as to why you'd want to restrict your apache to your own user folder, instead of say /var/www/. either way, wherever your apache web root is should be where your cf admin is located.

couple things you could try before you uninstall anything, especially since we know your coldfusion server is working lol.

1. make a link from your CFIDE folder into your apache web root folder. you'll need root to do this, so in a terminal, type:

sudo nautilus

when it comes up, navigate to where your CFIDE folder is, right click on the folder itself, then click 'make link'. then right click and copy that new link. now go to your apache web root folder and paste the link in there, then rename it to 'CFIDE'. then the url you were trying to get to should work properly.

2. if for some reason, that doesn't work, maybe try copying the whole CFIDE folder into your apache web root. again, you'd need root privileges to do this.

the number 1 option above worked just fine for me when i tested it just now, but if for some reason it doesn't work, or you just want to reinstall everything anyway, i wrote another tutorial for a LAMP setup that might help you here:

[http://www.tylermcmanus.com/2007/11/28/lamp-server-on-ubuntu-desktop/]("http://www.tylermcmanus.com/2007/11/28/lamp-server-on-ubuntu-desktop/")

that link, followed by the coldfusion tutorial you were already using should help you do everything you're trying to do, with the exception of tomcat. i've never used tomcat so can't help you there.

as far as having the different languages in their own folder, what i do is have both coldfusion and php run off the main apache web root, then i just make subfolders within that root designating one as 'php' and the other as 'cf', even though technically speaking, i could put both languages in either folder and it would still work because they're just sub folders within the web root, but this way my projects are more organized.

good luck.

---

### Post by myharshdesigner on 2007-12-01
can you guide how to setup and these servers :-

apache2

php

and

coldfusion  on ubuntu 7.10 ?

i have formated my pc and already don fress installection .


Thanks
Harsh

---

### Post by TylerMcManus on 2007-12-01
hi.

i think you might have missed what i just posted :)

---

### Post by myharshdesigner on 2007-12-01
> **TylerMcManus said:**
> hi.

i think you might have missed what i just posted :)

ok i will see thanks :)

thanks for your gr8  help

---

### Post by engine on 2007-12-30
After an unhappy run-in with the repositories and an spectacularly unsuccessful attempt at upgrading, I've had to do a complete install to get 7.10 up and running; so now I'm trying to re-install various apps and get back to where I was.
Enough of the whinge! the relevant questions are:
[LIST]
[*]is there a recommended starting-point for installing ColdFusionMX 7? I mean, where should I save the coldfusion-702-lin.bin file?
[*]will putting coldfusion-702-lin.bin in this "right" place solve the libraries problem?
[/LIST]

The code below shows the messages I get when trying to run the installer, plus as much information as I know how to look for about where/whether the "No such object" objects appear to be ...

I've tried the various ColdFusion references mentioned earlier in this thread, but not found what I'm looking for. Thanks in advance for any help!

engine

```
[prompt] /opt$ sudo ./coldfusion-702-lin.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.6358/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

[prompt] slocate libm.so.6
/lib/tls/i686/cmov/libm.so.6
/lib/libm.so.6
[prompt] slocate libc.so.6
/lib/tls/i686/cmov/libc.so.6
/lib/libc.so.6
[prompt] slocate librt.so.1
/lib/librt.so.1
/lib/tls/i686/cmov/librt.so.1
[prompt] slocate libpthread.so.0
/lib/libpthread.so.0
/lib/tls/i686/cmov/libpthread.so.0

```

---

### Post by engine on 2008-01-01
OK, problem avoided ... installed ColdFusion 8 instead. Worked like a charm.

---

