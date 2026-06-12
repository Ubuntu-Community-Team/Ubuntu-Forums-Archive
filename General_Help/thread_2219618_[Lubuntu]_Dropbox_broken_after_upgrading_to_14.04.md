---
title: "[Lubuntu] Dropbox broken after upgrading to 14.04"
date: 2014-04-24
forum: General Help
---

### Post by raen on 2014-04-24
Hello. I just upgraded my Acer Aspire One today from Lubuntu 13.10 to 14.04 and I'm already having some issues. Right now, I can't get Dropbox to run (although Copy is working fine, go figure).

[FONT=courier new]$ dropbox status[/FONT]
told me
[FONT=courier new]Dropbox isn't running!
[/FONT]and neither
[FONT=courier new]$ dropbox start[/FONT]
nor
[FONT=courier new]$ dropbox start -i[/FONT]
nor
[FONT=courier new]$ sudo apt-get install dropbox[/FONT]
worked.

I tried re-downloading the .deb from the Dropbox site but when I opened it, I got the status message [B]"Error: Breaks existing package 'nautilus-dropbox' conflict: dropbox()"

[/B]As I was installing the upgrade, I made a sketchy note about "re-enable 3rd party w/ 'software-properties' or package manager" but I can't find where to do that.

Another thing that popped up while I was installing the upgrade (but didn't make a note about because I thought the "Forward>" button would lead me to something helpful instead of returning me to the upgrade, *sigh*) said something about restarting a thing before the upgrade continued so that users wouldn't be locked out (???) I had the vague impression it had something to do with screensaver-related things. Sorry this is so nebulous! I don't think it's caused any problems (yet), so maybe it worked itself out.

Insights would be appreciated.
Thank you,
raen

---

### Post by raen on 2014-04-27
Here's the kicker, though: When I log in, [I get this prompt]("http://i.imgur.com/ldGumzR.png").

Am I going to have to do a fresh install of the system? I'm pretty sure I have it set up so that the system is on a different partition than my data. How do I confirm this?

---

### Post by bapoumba on 2014-04-27
How did you install dropbox ?

Using nautilus-dropbox from the multiverse repositories installs dropbox with integration in the file manager (PCManFM here, works nicely). Lets you connect to your account and syncs everything.

---

### Post by raen on 2014-04-27
> **bapoumba said:**
> How did you install dropbox ?

Using nautilus-dropbox from the multiverse repositories installs dropbox with integration in the file manager (PCManFM here, works nicely). Lets you connect to your account and syncs everything.

According to Synaptic Package manager, I already have nautilus-dropbox 1.6.1-1 installed.

Given the lack of .deb file in my Downloads folder, I probably installed Dropbox originally via either apt-get or Lubuntu Software Center.

---

### Post by bapoumba on 2014-04-27
> **raen said:**
> According to Synaptic Package manager, I already have nautilus-dropbox 1.6.1-1 installed.

Given the lack of .deb file in my Downloads folder, I probably installed Dropbox originally via either apt-get or Lubuntu Software Center.
OK, same version here. 

Make sure you do not have the dropbox package from the web site installed, not sure what the name will be as the site shows 2 dropbox_1.6.0 for both 32 and 64-bit installs.
```
dpkg -l *dropbox*
```

If there is only nautilus-dropbox showing up, and as **dropbox start** does not let you log in and set up your computer (has it been already set up ?), I would purge nautilus-dropbox and install it again.

---

### Post by raen on 2014-04-27
> **bapoumba said:**
> OK, same version here. 

Make sure you do not have the dropbox package from the web site installed, not sure what the name will be as the site shows 2 dropbox_1.6.0 for both 32 and 64-bit installs.
```
dpkg -l *dropbox*
```

If there is only nautilus-dropbox showing up, and as **dropbox start** does not let you log in and set up your computer (has it been already set up ?), I would purge nautilus-dropbox and install it again.

DB package from web site not installed: check. It wouldn't let me when I tried.

Are you saying I should type ```
dpkg -l *dropbox*
``` into a terminal? What will that do?

Where would be the best place to purge nautilus-dropbox? Go into Synaptic, mark for (complete) removal, then re-install?

Thanks.

---

### Post by bapoumba on 2014-04-27
> **raen said:**
> DB package from web site not installed: check. It wouldn't let me when I tried.

Are you saying I should type ```
dpkg -l *dropbox*
``` into a terminal? What will that do?
Just double checking you only have nautilus-dropbox installed. Yes, enter the code in terminal, it will list all installed packages that have dropbox in their name.
> **raen said:**
> 
Where would be the best place to purge nautilus-dropbox? Go into Synaptic, mark for (complete) removal, then re-install?

Thanks.
Once you have checked there is only nautilus-dropbox installed, please run :
```
sudo apt-get remove --purge nautilus-dropbox
```

---

### Post by raen on 2014-04-27
> **bapoumba said:**
> Just double checking you only have nautilus-dropbox installed. Yes, enter the code in terminal, it will list all installed packages that have dropbox in their name.

Once you have checked there is only nautilus-dropbox installed, please run :
```
sudo apt-get remove --purge nautilus-dropbox
```

```

$ dpkg -l *dropbox*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  dropbox        <none>       <none>       (no description available)
ii  nautilus-dropb 1.6.1-1      i386         Dropbox integration for Nautilus

```

Not sure if the other information is good or bad.

---

### Post by bapoumba on 2014-04-27
OK, you only have nautilus-dropbox, so please purge it (the code is above) and try to reinstall it.

---

### Post by raen on 2014-04-27
> **bapoumba said:**
> OK, you only have nautilus-dropbox, so please purge it (the code is above) and try to reinstall it.

Purged. What's the best way to re-install it? Symantec?

Thanks.

---

### Post by bapoumba on 2014-04-27
> **raen said:**
> Purged. What's the best way to re-install it? Symantec?

Thanks.

I installed it using the lubuntu software center, I never use it and wanted to see how it looked ilke :)
If you wish, you can use the terminal and run :
```
sudo apt-get install nautilus-dropbox
```
Using synaptic is also fine. All are front-ends to apt-get, so use the one that pleases you.

---

### Post by raen on 2014-04-27
That worked! :-D Thank you so much for patiently walking me through this. (I swear I'm great with helping my friends and family with their computers, but whenever I upgrade my own system, my IQ drops about 50 points.)

---

### Post by bapoumba on 2014-04-27
> **raen said:**
> That worked! :-D Thank you so much for patiently walking me through this. (I swear I'm great with helping my friends and family with their computers, but whenever I upgrade my own system, my IQ drops about 50 points.)

No worries, just happened to me today.. My voodoo search skills seam to be quite broken when working for my own stuff, fortunately a friend was around ^^

Please mark your thread as solved (under Thread Tools) thanks!

---

### Post by lesilvestre on 2014-04-27
Same thing happened to me in two computers after upgrading to 14.04. I'm surprised it isn't happening to everybody.

I also solved it with the instructions above. Thanks :)

---

### Post by bapoumba on 2014-04-27
> **lesilvestre said:**
> Same thing happened to me in two computers after upgrading to 14.04. I'm surprised it isn't happening to everybody.

I also solved it with the instructions above. Thanks :)

You are welcome!

Do you know at what point you got stopped ? It is quite intriguing to me that so many people have problems installing dropbox, and I would like to know what happens, thanks.

---

### Post by lesilvestre on 2014-04-28
I had Dropbox working since a long time ago (probably a few Ubuntu versions back). When rebooting after the upgrade to 14.04 I got the dialog saying that Nautilus needed to be restarted. I clicked OK, the icons on the desktop disappeared, but they did not reappear until I click to open Nautilus manually (opening my home directory). Dropbox did not start. It happened to me in two different computers. I'm using one right now for which dropbox is still not working (I'm about to purge and reinstall now).

---

### Post by bapoumba on 2014-04-28
> **lesilvestre said:**
> I had Dropbox working since a long time ago (probably a few Ubuntu versions back). When rebooting after the upgrade to 14.04 I got the dialog saying that Nautilus needed to be restarted. I clicked OK, the icons on the desktop disappeared, but they did not reappear until I click to open Nautilus manually (opening my home directory). Dropbox did not start. It happened to me in two different computers. I'm using one right now for which dropbox is still not working (I'm about to purge and reinstall now).

Does this work from a terminal ? ```
dropbox start
```

---

### Post by lesilvestre on 2014-04-28
Before I reinstall Dropbox, I can do some test of what's going on. When I type "dropbox start" in a terminal I get this

```
Starting Dropbox...Traceback (most recent call last):
  File "dropbox/client/main.py", line 13, in <module>
  File "autogen_explicit_imports.py", line 13, in <module>
  File "ui/common/selective_sync.py", line 6, in <module>
  File "arch/__init__.py", line 28, in <module>
  File "arch/linux/tracing.py", line 8, in <module>
  File "hard_trace.py", line 6, in <module>
  File "client_api/connection_hub.py", line 21, in <module>
  File "client_api/kv_connection.py", line 23, in <module>
  File "pylinux/__init__.py", line 71, in <module>
  File "cffi/api.py", line 311, in verify
  File "dropbox/overrides.py", line 398, in load_library
  File "cffi/verifier.py", line 69, in load_library
  File "cffi/verifier.py", line 154, in _load_library
  File "cffi/vengine_cpy.py", line 124, in load_library
VerificationError: importing '/home/luis/pylinux/__pycache__/_cffi__xa0c4f46bx1d95b4de.so': No module named _cffi__xa0c4f46bx1d95b4de

```

There is no folder named pylinux in my home directory. I can tell you that.

---

### Post by bapoumba on 2014-04-28
I can also tell you I have nothing with pylinux it its name on my machine either..

Looking for such pattern suggests these files are used during the install procedure and are probably removed afterwards.
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=734628](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=734628) suggests a fix :
```
sudo rm -rf /var/lib/dropbox/.dropbox-dist
dropbox start -i
```
You may try that before purging/reinstalling.

---

### Post by lesilvestre on 2014-04-28
> 
[COLOR=#000000]You may try that before purging/reinstalling.
[/COLOR]

Next time ;)

---

### Post by bapoumba on 2014-04-28
> **lesilvestre said:**
> Next time ;)
Hopefully you wont need to :)

---

### Post by Madman1978 on 2014-04-28
Hello Gm.  Thank you some of the instructions.  I attempted to install DropBox and something went very wrong! I ended up with a broken package that broke so many other things!   I have lost Ubuntu Software Center and oddly, I have lost my program for text files.

---

### Post by bapoumba on 2014-04-28
> **Madman1978 said:**
> Hello Gm.  Thank you some of the instructions.  I attempted to install DropBox and something went very wrong! I ended up with a broken package that broke so many other things!   I have lost Ubuntu Software Center and oddly, I have lost my program for text files.

Well, I think it would be better you start a new thread of your own if there are more issues than just dropbox :)
Please use a descriptive title and add as much info as possible on what happened, thanks.

---

### Post by Madman1978 on 2014-04-28
done!

---

