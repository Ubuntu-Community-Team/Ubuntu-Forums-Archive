---
title: "ColdFusion MX Developer Edition on Ubuntu"
date: 2005-06-11
forum: General Help
---

### Post by jello on 2005-06-11
I'm thinking about making the Ubuntu plunge (from SuSE), but I'm worried about whether ColdFusion MX (6.1) Developer Edition will install and play nice w/Ubuntu.  

I have it happily installed on SuSE 9.2 Pro currently, but I think Macromedia said it was only supported up to SuSE 8.0.  It works fine though.

Anyway, I'm just fighting too much w/SuSE's package management.

I'd love to hear from any one else with experience installing CF on Ubuntu!

Thanks,
J

---

### Post by afonic on 2005-06-11
I haven't tried but I can make a little suggestion.

Get the trial version of VMware for Linux:
[http://www.vmware.com/download/](http://www.vmware.com/download/)

Install it in SuSE, then install Ubuntu in a virtual system. Try and see for yourself if Coldfusion works.

For my experience (I am running Ubuntu in a virtual system running in SuSE 9.3) most programs I had run just fine. Hopefull I'll change to "real" ubuntu soon as I am very pleased with it! :-)

---

### Post by Evoreth on 2005-06-12
Well, I don't know about MX6, but MX7 works like a charm. I haven't tried Custom Tags, CFX Tags or Java Applets yet, but I'm using the basic features for one or two months now. The installer is convenient, but I would like to have my "wwwroot" folder in my home directory. Is there any solution?

---

### Post by moonlight on 2005-06-20
Hey,

Can somebody explain in a bit more details how to install the 'ColdFusion MX 7 Developer Edition' ? 
More concrete after installing the binary (which is available for free), I could start ColdFusion, using ./coldfusion start.

```

laptop:/opt/coldfusionmx7/bin# ./coldfusion start
Starting ColdFusion MX 7...
The ColdFusion MX 7 server is starting up and will be available shortly.
======================================================================
ColdFusion MX 7 has been started.
ColdFusion MX 7 will write logs to /opt/coldfusionmx7/logs/cfserver.log
======================================================================

``` 

Next I have tried to login to the ColdFusion Administrator, however, I just receive a listing of the files :

```

http://localhost:8500/cfide/administrator/

```

Does anybody know what has to be configured additional ?

Cheers, Moonlight

---

### Post by ytseshred on 2005-11-01
the /administrator/ folder will list the files.  You server (whatever you are running) probably doesn't know to look for index.cfm by default.

If you go to
```
http://localhost:8500/cfide/administrator/index.cfm
```

Do you get anything?

---

### Post by engine on 2005-12-16
You've got farther than I have! I'm trying to download the Developer edition (with Firefox) - all I get is "Done" in the browser status bar, and no files :-{  Any hints or tips?

---

### Post by cached on 2005-12-23
[QUOTE=engine]You've got farther than I have! I'm trying to download the Developer edition (with Firefox) - all I get is "Done" in the browser status bar, and no files :-{  Any hints or tips?[/QUOTE]

Try again, I recommend with the DownThemAll extension (very nice download manager with multithreading).  If this fails to work, I can upload the file to a server of my own for you, after I check that this does not breach any agreement.

---

### Post by sdhoigt on 2006-07-19
> **moonlight said:**
> Hey,

Can somebody explain in a bit more details how to install the 'ColdFusion MX 7 Developer Edition' ? 
More concrete after installing the binary (which is available for free), I could start ColdFusion, using ./coldfusion start.

```

laptop:/opt/coldfusionmx7/bin# ./coldfusion start
Starting ColdFusion MX 7...
The ColdFusion MX 7 server is starting up and will be available shortly.
======================================================================
ColdFusion MX 7 has been started.
ColdFusion MX 7 will write logs to /opt/coldfusionmx7/logs/cfserver.log
======================================================================

``` 

Next I have tried to login to the ColdFusion Administrator, however, I just receive a listing of the files :

```

http://localhost:8500/cfide/administrator/

```

Does anybody know what has to be configured additional ?

Cheers, Moonlight

Did you read the logs?
/opt/coldfusionmx7/logs/cfserver.log

---

### Post by Bryce next on 2006-08-20
Hello all, 

Seems most of you have had more success than I installing CFMX 7 Developer version. I downloaded it (coldfusion-702-lin.bin) over night and attempted to install it as I always have in Windows -- double clicked on it. This doesn't get me very far, as the next window I see tells me the file is an exectuable  text file, but there's no actual installation going on. 

I'm guessing I'm missing something fundamental due to my newness with Ubuntu and for that matter, Linux/Unix. Could anyone help with that missing fundamental piece?

Thanks.

---

### Post by Interblaze on 2006-08-25
> **Bryce next said:**
> Hello all, 

Seems most of you have had more success than I installing CFMX 7 Developer version. I downloaded it (coldfusion-702-lin.bin) over night and attempted to install it as I always have in Windows -- double clicked on it. This doesn't get me very far, as the next window I see tells me the file is an exectuable  text file, but there's no actual installation going on. 

I'm guessing I'm missing something fundamental due to my newness with Ubuntu and for that matter, Linux/Unix. Could anyone help with that missing fundamental piece?

Thanks.

If you have not yet figured out how to install coldfusion in ubuntu type this in a terminal:

```
chmod 777 coldfusion-702-lin.bin
```

```
sudo ./coldfusion-702-lin.bin
```

*note: you can also run the graphical installer if you have a desktop installed by typing*

```
sudo ./coldfusion-702-lin.bin -i gui
```

---

### Post by reya276 on 2007-05-18
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595). [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				I tried following the instructions you guys provided and when it tried to install through command line or GUI I got the error below:

[COLOR=Red]grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.13148/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

[COLOR=Black]Any help with this issue would be greatly appreciated.[/COLOR]
[/COLOR]

---

### Post by Interblaze on 2007-05-23
Looks like you need to install the libc libraries. What version of ubuntu are you running?

---

### Post by Joshua Swink on 2007-05-25
> **reya276 said:**
> I tried following the instructions you guys provided and when it tried to install through command line or GUI I got the error below:

[COLOR=Red]grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.13148/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

[COLOR=Black]Any help with this issue would be greatly appreciated.[/COLOR]
[/COLOR]

I had the same problem (plus one other) in Ubuntu 7.04. It seems to be related to the use of LD_ASSUME_KERNEL - don't ask me what it's about, I just know it's bad.

The problems I had were:

1) The script sets LD_ASSUME_KERNEL, and then it can't run any programs.
2) My environment variable PS1 contains "\u", which a java program later tries to evaluate, resulting in "malformed \uxxxx" errors.

Here's a workaround. It worked for me.

[FONT="Courier New"]# cp coldfusion-702-lin.bin coldfusion-702-lin.bin.orig
# perl -pe 's/LD_ASSUME_KERNEL/LX_ASSUME_KERNEL/' coldfusion-702-lin.bin.orig > coldfusion-702-lin.bin
# PS1=whatever ./coldfusion-702-lin.bin[/FONT]

Then the installer ran successfully.

---

### Post by engine on 2007-05-26
As you'll see from the extract below, now I've upgraded from Dapper to Edgy I get the same sort of message:

```
ngn@nbox:~$ /opt/coldfusionmx7/bin/coldfusion start
ps: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
Starting ColdFusion MX 7...
The ColdFusion MX 7 server is starting up and will be available shortly.
sleep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
ps: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
There has been an error starting ColdFusion MX 7, please check the logs
```.

I've checked via synaptic, and appear to have libc6, libc6-dev and libc6-i686 all installed. See also:

```
ngn@nbox:~$ slocate libc.so.6
/lib/tls/i686/cmov/libc.so.6
/lib/libc.so.6
```

I've been using ColdFusion very happily up till now, and wouldn't want to lose it just because of an upgrade :-{ Hints, tips and clear instructions all appreciated!

Thanks in advance.

---

### Post by Joshua Swink on 2007-05-26
> **engine said:**
> I've been using ColdFusion very happily up till now, and wouldn't want to lose it just because of an upgrade :-{ Hints, tips and clear instructions all appreciated!

Thanks in advance.

This looks exactly like the problem that arises when LD_ASSUME_KERNEL gets set. When I disabled it during installation (see above), I got a coldfusion install that works in Feisty. The reason appears to be that two scripts retained the change, "LX_ASSUME_KERNEL". They are:

```

/opt/coldfusionmx7/bin/cfstat
/opt/coldfusionmx7/bin/coldfusion
```

I bet that if you disabled LD_ASSUME_KERNEL in those two scripts, your current install would start working. The following commands should do it:

```

cd /opt/coldfusionmx7/bin
perl -pi.orig -e 's/LD_ASSUME_KERNEL/LX_ASSUME_KERNEL/' cfstat coldfusion
```

---

### Post by engine on 2007-05-27
Outstanding reply! thank-you very much. (OK, so I wimped out and edited the two scripts by hand rather than letting perl loose on them, but the end result is as hoped for)

N

---

### Post by pliktrologos on 2008-02-19
I found these tutorials very helpful:
[http://www.tylermcmanus.com/2007/11/29/tutorial-adding-coldfusion-8-to-your-ubuntu-lamp-server/](http://www.tylermcmanus.com/2007/11/29/tutorial-adding-coldfusion-8-to-your-ubuntu-lamp-server/)
[http://www.compoundtheory.com/?action=displayPost&ID=233](http://www.compoundtheory.com/?action=displayPost&ID=233)

---

