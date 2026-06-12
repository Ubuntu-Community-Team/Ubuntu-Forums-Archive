---
title: "Thunderbird 2.0"
date: 2007-04-20
forum: General Help
---

### Post by CheeseQueen452 on 2007-04-20
Thunderbird 2.0 was just released, so I was wondering how soon we can expect the update?

---

### Post by Swab on 2007-04-20
I guess it will be in Gutsy.  Maybe we'll get it in backports at some point.

---

### Post by CheeseQueen452 on 2007-04-20
But shouldn't we get it via the security updates within a week or 2?

> **Swab said:**
> I guess it will be in Gutsy.  Maybe we'll get it in backports at some point.

---

### Post by Swab on 2007-04-20
> **CheeseQueen452 said:**
> But shouldn't we get it via the security updates within a week or 2?

No because Thunderbird 2.0 is a new version of Thunderbird, not a security update.  Version 1.5 will still be supported with security updates for a while yet.

---

### Post by Swab on 2007-04-20
You can of course download Thunderbird 2.0 from Mozilla and install it yourself.

---

### Post by CheeseQueen452 on 2007-04-20
I don't know how to do that, I'm afraid of messing something up. Is there a repository I can add to my sources where I can get it?

> **Swab said:**
> You can of course download Thunderbird 2.0 from Mozilla and install it yourself.

---

### Post by CheeseQueen452 on 2007-04-20
But didn't we get Firefox 2.0 shortly after it was released?

> **Swab said:**
> No because Thunderbird 2.0 is a new version of Thunderbird, not a security update.  Version 1.5 will still be supported with security updates for a while yet.

---

### Post by Swab on 2007-04-20
> **CheeseQueen452 said:**
> But didn't we get Firefox 2.0 shortly after it was released?

Not sure about that one, can't remember :)

---

### Post by Swab on 2007-04-20
> **CheeseQueen452 said:**
> I don't know how to do that, I'm afraid of messing something up. Is there a repository I can add to my sources where I can get it?

It's not so much of an install as an unpacking.  Seriously download the file, untar somewhere in your home folder, and run it.  Won't mess up anything.

---

### Post by Hollydragon on 2007-04-20
> **Swab said:**
> It's not so much of an install as an unpacking.  Seriously download the file, untar somewhere in your home folder, and run it.  Won't mess up anything.

I'm having trouble with the 'run it' bit. There are many files, two of which are -bin/five of which are executables, none of which respond to double click, or 'open with Add/Install'. 

The Thunderbird ReadMe points you to a website that tells you to 'run thunderbird' and nothing more useful than that and all the FAQs I can find on installation run on about application streams and .debs and dependancies then say 'Can't help you with pre-made installation bins'.

I'm sure the 'run' thing is totally obvious and simple once you know how, but I don't know how yet.

(the other thing is that I don't have permission to extract it to the home folder. You're not allowed to log in as root, after all, and the untar application doesn't let you act as root. I am assuming tmp is still ok.)

---

### Post by wordsmithereens on 2007-04-20
I had the same question yesterday, I found the answer in this thread: 

[http://ubuntuforums.org/showthread.php?t=413908&referrerid=274104](http://ubuntuforums.org/showthread.php?t=413908&referrerid=274104)

wordsmithereens :)

---

### Post by Hollydragon on 2007-04-20
Thanks, that's great! I never seem to find the threads I need when I search the Many Websites of Linux. :)

---

### Post by aysiu on 2007-04-21
> **CheeseQueen452 said:**
> But didn't we get Firefox 2.0 shortly after it was released? No, we didn't. In fact, as far as I know, Ubuntu 6.06 (Dapper Drake) *still* doesn't have 2.0. We got Firefox 2.0 once 6.10 (Edgy Eft) was released because that was the current Firefox version available at the time.

If you want to install 2.0, here are instructions:
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

That page contains manual instructions (if you like copying and pasting a lot of commands) and an automated script.

Two caveats about the script:
1. If you did a fresh install of Feisty beta and upgraded until final release, you might not have an /opt folder. Create one first before running the script: ```
sudo mkdir /opt
```
2. If you used a similar method to get 1.5 installed from Mozilla (not the standard Ubuntu 1.5), then you may get an "error" at the end saying it couldn't create a link to /usr/bin/thunderbird because the location already exists. That's okay. The installation will still work.

I've already contacted the script's author about updating it with those two issues in mind. Not sure when it will be updated, though.

---

### Post by in_flu_ence on 2007-04-21
It doesn't seem to work for me.

I have

~/Desktop$ thunderbird

(thunderbird-bin:6364): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

and it never load.

Any idea?

---

### Post by amo-ej1 on 2007-04-21
basicly you do the following. Download the tarball, extract it. This will create a directory 'thunderbird'. Go to this directory. In this directory you will find a binary called thunderbird which you should execute. So in a console you would type:

```

# tar -zxvf downloader.tgz
# cd thunderbird
# ./thunderbird

```

et voila ;)

---

### Post by in_flu_ence on 2007-04-21
apparently if i use the console to run, there is nothing. but if i click and run from krusader root, I can make it work. strange.

i tried sudo thunderbird either but doesn't work

---

### Post by CheeseQueen452 on 2007-04-21
I tried both the script & manual installation, but neither worked. When I launch TB from the button on my taskbar, it still opens 1.5.0.10. Now what?

> **aysiu said:**
> 
If you want to install 2.0, here are instructions:
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

That page contains manual instructions (if you like copying and pasting a lot of commands) and an automated script.

Two caveats about the script:
1. If you did a fresh install of Feisty beta and upgraded until final release, you might not have an /opt folder. Create one first before running the script: ```
sudo mkdir /opt
```
2. If you used a similar method to get 1.5 installed from Mozilla (not the standard Ubuntu 1.5), then you may get an "error" at the end saying it couldn't create a link to /usr/bin/thunderbird because the location already exists. That's okay. The installation will still work.

I've already contacted the script's author about updating it with those two issues in mind. Not sure when it will be updated, though.

---

### Post by CheeseQueen452 on 2007-04-21
If you're talking about manually running TB from a directory, I don't want that. I want to launch TB the normal way, from the button on my taskbar.

> **amo-ej1 said:**
> basicly you do the following. Download the tarball, extract it. This will create a directory 'thunderbird'. Go to this directory. In this directory you will find a binary called thunderbird which you should execute. So in a console you would type:

```

# tar -zxvf downloader.tgz
# cd thunderbird
# ./thunderbird

```

et voila ;)

---

### Post by michael_montrief on 2007-04-21
Hi CheeseQueen,

You mean that the TB 2 is actually working but you can only launch it from the directory? and the taskbar button launch TB 1.5?

----
Michael Montrief

---

### Post by CheeseQueen452 on 2007-04-21
I don't know if TB 2.0 is working, I never tried launching it from the directory(where ever that is). The taskbar button launches 1.5, that's all I know. I tried installing 2.0 from the instructions at the link posted above, but it didn't work.

> **michael_montrief said:**
> Hi CheeseQueen,

You mean that the TB 2 is actually working but you can only launch it from the directory? and the taskbar button launch TB 1.5?

----
Michael Montrief

---

### Post by aysiu on 2007-04-21
Can you post the output of these commands? ```
cd /opt
ls
cd thunderbird
ls
./thunderbird
```

---

### Post by in_flu_ence on 2007-04-21
I have solved one problem in my 32bit laptop.

If people facing a segmentation fault, most likely it is due to your scim
add the line 

export GTK_IM_MODULE=xim

at the first line after /bin/sh for both run-mozilla.sh and thunderbird in the opt/thunderbird folder.

I will solve the other problem on my 64bit desktop

---

### Post by chio on 2007-04-21
> **Hollydragon said:**
> I'm having trouble with the 'run it' bit. There are many files, two of which are -bin/five of which are executables, none of which respond to double click, or 'open with Add/Install'. 

The Thunderbird ReadMe points you to a website that tells you to 'run thunderbird' and nothing more useful than that and all the FAQs I can find on installation run on about application streams and .debs and dependancies then say 'Can't help you with pre-made installation bins'.

I'm sure the 'run' thing is totally obvious and simple once you know how, but I don't know how yet.

(the other thing is that I don't have permission to extract it to the home folder. You're not allowed to log in as root, after all, and the untar application doesn't let you act as root. I am assuming tmp is still ok.)

You need to download it into /home/yourname and then extract it there, you'll end up with /home/yourname/thunderbird or similar. In there, there'll be a file just called "thunderbird". Double-click that and it'll ask you whether you want to open it or run it. Choose "run" and up pops your Thunderbird. 

If you want it in your applications menu, go to System, Preferences, Main Menu and select the Internet category, then "new item". Set it up similar to how you'd set up a Windows shortcut -- enter "/home/yourname/thunderbird/thunderbird" as the command and just Thunderbird as the name. 

Hope this helps :)

---

### Post by CheeseQueen452 on 2007-04-21
Here's what it says:
```

chrome              libfreebl3.so    libsoftokn3.so          removed-files
components          libldap50.so     libssl3.so              res
defaults            libmozjs.so      libxpcom_compat.so      run-mozilla.sh
dependentlibs.list  libnspr4.so      libxpcom_core.so        thunderbird
dictionaries        libnss3.so       libxpcom.so             thunderbird-bin
extensions          libnssckbi.so    libxpistub.so           updater
greprefs            libplc4.so       license.html            updater.ini
icons               libplds4.so      LICENSE.txt             updates
init.d              libprldap50.so   mozilla-installer-bin   xpicleanup
isp                 libsmime3.so     mozilla-xremote-client
libfreebl3.chk      libsoftokn3.chk  README.txt

```

> **aysiu said:**
> Can you post the output of these commands? ```
cd /opt
ls
cd thunderbird
ls
./thunderbird
```

---

### Post by aysiu on 2007-04-21
And then after that...? When you do ```
cd /opt/thunderbird
./thunderbird
``` what happens?

---

### Post by CheeseQueen452 on 2007-04-21
TB 2.0 launched, but when I closed it & clicked on the launch button in the taskbar, 1.5 came up again.

> **aysiu said:**
> And then after that...? When you do ```
cd /opt/thunderbird
./thunderbird
``` what happens?

---

### Post by aysiu on 2007-04-21
> **CheeseQueen452 said:**
> TB 2.0 launched, but when I closed it & clicked on the launch button in the taskbar, 1.5 came up again.
Can you paste these commands into the terminal? If the second set of commands doesn't work, that's fine--they're just in case (an unlikely event) you happened to have the old launcher linked to the *thunderbird* command. The first two commands should not return any errors, though. If they do, please post the errors: ```
sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo dpkg-divert --divert /usr/bin/thunderbird.ubuntu --rename /usr/bin/thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
```

---

### Post by CheeseQueen452 on 2007-04-21
Now TB won't run! HELP!!!!

> **aysiu said:**
> Can you paste these commands into the terminal? If the second set of commands doesn't work, that's fine--they're just in case (an unlikely event) you happened to have the old launcher linked to the *thunderbird* command. The first two commands should not return any errors, though. If they do, please post the errors: ```
sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo dpkg-divert --divert /usr/bin/thunderbird.ubuntu --rename /usr/bin/thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
```

---

### Post by aysiu on 2007-04-21
You need to be a little more specific than that. Remember: I'm not looking over your shoulder. All I can see is what you type.

First of all, did the commands run successfully? Did you get any errors? If so, what were they? Paste them back here.

Secondly, what happens when you try to run the command ```
thunderbird
```? What happens when you try to run the command ```
mozilla-thunderbird
```? And what happens when you try to run the command ```
mozilla-thunderbird.ubuntu
```?

---

### Post by CheeseQueen452 on 2007-04-21
There were no errors, except when I tried this:
```

mozilla-thunderbird
run-mozilla.sh: Cannot execute /opt/thunderbird/mozilla-thunderbird-bin.

mozilla-thunderbird.ubuntu

run-mozilla.sh: Cannot execute /usr/lib/mozilla-thunderbird/mozilla-thunderbird.ubuntu-bin.
```

Typing in "thunderbird" launched 2.0

> **aysiu said:**
> You need to be a little more specific than that. Remember: I'm not looking over your shoulder. All I can see is what you type.

First of all, did the commands run successfully? Did you get any errors? If so, what were they? Paste them back here.

Secondly, what happens when you try to run the command ```
thunderbird
```? What happens when you try to run the command ```
mozilla-thunderbird
```? And what happens when you try to run the command ```
mozilla-thunderbird.ubuntu
```?

---

### Post by CheeseQueen452 on 2007-04-21
Ok, I got 2.0 running by changing the command in the taskbar button properties. The command was "mozilla-thunderbird", & I changed it to "thunderbird".

---

### Post by aysiu on 2007-04-21
Well, that workaround will have to work for now. Not sure why the other command isn't working.

---

### Post by CheeseQueen452 on 2007-04-21
After I entered those 4 commands you gave me in the terminal, that's when it stopped working. These are the commands I'm referring to:
```

sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo dpkg-divert --divert /usr/bin/thunderbird.ubuntu --rename /usr/bin/thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird

```

> **aysiu said:**
> Well, that workaround will have to work for now. Not sure why the other command isn't working.

---

### Post by CheeseQueen452 on 2007-04-27
Ok, I now have TB 2.0 working via the "mozilla-thunderbird" command. I downloaded the script from the following link, which worked without errors :) I also have the FF script handy for when that gets updated as well :)

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)

---

### Post by jmaryinchina on 2007-09-11
How did you find the trick please ?

---

### Post by nanotube on 2007-09-11
> **jmaryinchina said:**
> How did you find the trick please ?

what trick are you talking about?

---

### Post by Paucus on 2007-09-21
I just installed 6.06 on a Macintosh Powerbook G3. Everything seems to be working like a charme. I'm new to Linux in general and I never tried it on a mac. I tried to install Thunderbird 2 but I always get an error message about the architecture (PPC rather than i366). Can anyone point me to some instruction to solve this problem (or just tell me it's not possible and I stop trying).
Thanks...

---

### Post by ozzyprv on 2007-09-22
> **chio said:**
> You need to download it into /home/yourname and then extract it there, you'll end up with /home/yourname/thunderbird or similar. In there, there'll be a file just called "thunderbird". Double-click that and it'll ask you whether you want to open it or run it. Choose "run" and up pops your Thunderbird. 

If you want it in your applications menu, go to System, Preferences, Main Menu and select the Internet category, then "new item". Set it up similar to how you'd set up a Windows shortcut -- enter "/home/yourname/thunderbird/thunderbird" as the command and just Thunderbird as the name. 

Hope this helps :)


Thank you chio!.

O.

---

### Post by nanotube on 2007-09-22
> **Paucus said:**
> I just installed 6.06 on a Macintosh Powerbook G3. Everything seems to be working like a charme. I'm new to Linux in general and I never tried it on a mac. I tried to install Thunderbird 2 but I always get an error message about the architecture (PPC rather than i366). Can anyone point me to some instruction to solve this problem (or just tell me it's not possible and I stop trying).
Thanks...

mozilla doesn't release ppc binaries anymore, so your best bet is to try to compile from source. the procedure for doing this would /probably/ be similar to the one here:
[https://wiki.ubuntu.com/CompileThunderbirdNewVersion?highlight=%28compile%29%7C%28thunderbird%29](https://wiki.ubuntu.com/CompileThunderbirdNewVersion?highlight=%28compile%29%7C%28thunderbird%29)

or you could search around on google for the freshest instructions for compiling.

---

