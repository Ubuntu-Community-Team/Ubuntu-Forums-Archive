---
title: "Easy way to install software?"
date: 2014-11-03
forum: General Help
---

### Post by leilamoniz on 2014-11-03
hi all;

very new to ubuntu 14.04 LTS - wich i downloaded and installed over my windows for the simple fact that i enjoy confort of speed and browing quikly whilst using my machine.

just makes sense when all works well and fast !

so i installed ubuntu LTS 14 and all seems to be going well, up until when i decided to change the feel of ubntu to macbuntu.

i followed some instructions on youtube but when clicking on file extension install.sh (it doest give the option to run it from terminal) ?

I have been using windows all my life and i know it will take me some time to get fully integrated with commad lines as to clicking away and let the machine do its installation by itself.

Not that i dont want learn but is there any software that i can drop my files into and let the machine install the software/themes/apps and so on whithout the need of me having to babysit whilst installing ?

thanks in advance

---

### Post by nerdtron on 2014-11-03
Installing software in Ubuntu is mainly done from the software center. Just search the software you like, click install, provide password and just wait for it to finish installing. You don't need to baby sit during the installation as you can still use your computer while the computer is downloading/installing.


Installing software not from the software center can get a little tricky as in you case you are provided with a .sh file. I think that .sh can still be ran on the terminal. Just open a terminal window and then navigate to the folder, then run ./install.sh

---

### Post by Bucky Ball on 2014-11-03
*Thread moved to **General Help**.*

I have changed the title of your thread as it has nothing to do with installing Macbuntu. I moved the post on the strength of the title and then read the post and realised, and moved it back to here. :-k

---

### Post by leilamoniz on 2014-11-03
thanks for assistance.

getting frustrated, when i cant get simple tasks to work (think its a simple task)

i have tried to look for software / theme in update centre, but its not working ! 

then i folllowed this instruction but only manage to change start logo and added docky.

[http://www.noobslab.com/2014/04/macbuntu-1404-pack-is-released.html](http://www.noobslab.com/2014/04/macbuntu-1404-pack-is-released.html)

---

### Post by ian-weisser on 2014-11-03
You are adding non-Ubuntu software to your system. That's _not_ simple. That may be easy to do if you blindly follow instructions from the web, but *it is not a task suitable for beginners*.

This site is littered with the sorrow and frustration of new users who followed random-instructions-they-found-on-the-web. DON'T blindly follow instructions - learn what the instructions mean and what the instructions do.

Ubuntu is not a free, drop-in replacement for Windows, and is not trying to be. It does many things *differently*, and some important differences are in the ways Ubuntu installs, uninstalls, upgrades, and patches software.

Ubuntu has _two_ ways to install software with one click - Software Center and AptUrl. For free. All Ubuntu software uses it. Lots of non-Ubuntu software uses it too (Skype, Google Applications, etc). If a non-Ubuntu developer decides not to use those methods, that's not Ubuntu's fault. If that developer makes installation hard or puzzling instead of one-click, that's not Ubuntu's fault.

If that non-Ubuntu software breaks your system, that's not Ubuntu's fault. It's that software's fault.

---

### Post by CantankRus on 2014-11-03
With your level of experience I would stick to what you can customize using **unity-tweak-tool**.
Many instructions leave out the basics and you will be left scratching your head.
Nothing is stopping you from trying this sort of stuff but be prepared to do some research and learning
and possibly reinstall when something stuffs up.

As to your original question...
> when clicking on file extension install.sh (it doest give the option to run it from terminal) ?
You will have to change the way executable text files behave in the file manager.
**Edit > preferences > behaviou**r and change to "ask each time"
This behaviour has changed recently to  "view executable text files when they are opened" as default.

You will come across things like this in instructions all the time because Ubuntu/Linux is constantly evolving.
An instruction from 6 months ago may not work today.
Then newcomers like you to Linux get frustrated because nothing ever seems to work
and everything just seems too complicated.

---

### Post by leilamoniz on 2014-11-04
guys, thx so much for feedback...

i have reinstall ubuntu and following your advice on changing few things to my taste using unity tool and docky from software centre. (attached .jpeg)

coming back to original question regarding .sh file:
 i will change as advise by CantankRus preferences and work round from there.

guess what i was looking for was an easy way to make this OS make me fell comforable due to fact im all new to how to find my way round and also to be in charge

 (by simply cliking and being able to install programs that i currently using on windows)

so that i could have all soft that i use on regular basis on ubuntu as to windows.

at present pretty much i have to admit machine is still calling the shots :(

For instance (so it still in topic) ... if i was to install a software design for windows on ubuntu (e.g. exe file) what should i do?

every time i drag and drop this file into terminal, nothing happens ?

---

### Post by Penguin360 on 2014-11-04
> **leilamoniz said:**
> 
For instance (so it still in topic) ..._** if i was to install a software design for windows on ubuntu (e.g. exe file) what should i do?**_

every time i drag and drop this file into terminal, nothing happens ?

First of all, welcome to a different world from Windows.

Secondly, since it is a different OS, things work differently. For instance, if you switch from iPhone to Android phone, you cannot go to Apple's App Store to install your previous iPhone apps to Android phone, instead you will have to go to Google Play Store to _**see **_if there is an Android version of the app, right? It is the same between Windows and Ubuntu. You CANNOT just drag and drop (or double click) a Windows exe file to expect the software will be installed in Ubuntu. You will have to check if there is an Ubuntu (or Linux) version of the software, if there is, then you will need to use that version in Ubuntu. Does it make sense?

If there is no Ubuntu version, AND you really want to use that software, there are two ways to do:
1. Install a virtual machine i.e. VirtualBox, then install Windows in the virtual machine, then install your Windows software in Windows.
2. Install a program called WINE ([https://www.winehq.org/](https://www.winehq.org/)), this is an emulator which can provide an environment to run _**some **_Windows software. However, since it is an emulator, the performance will not be as good as in the native Windows environment. I personally don't recommend to use WINE unless you HAVE TO have the software AND THERE IS no Ubuntu alternative.

If you have trouble with some specific software, you may list here and we can try to help you.

---

### Post by CantankRus on 2014-11-04
You have to use [**_[COLOR="#B22222"]Wine[/COLOR]_**]("https://www.winehq.org/help/") to run exe files.
Wine is a compatibility layer capable of running some Windows applications.
Wine will run some applications but I would only use if there is some windows application you can't do without.
[**_[COLOR="#B22222"]Installing Wine[/COLOR]_**]("https://help.ubuntu.com/community/Wine")

You are much better off finding Linux alternatives to your Windows applications.
[**_[COLOR="#B22222"]The Linux Alternative Project[/COLOR]_**]("http://www.linuxalt.com/")

---

### Post by /ADM on 2014-11-04
Which Windows software are you trying to use?  Winehq has a list of which programs runs great and which 'not' so great.  We could help more and provide more information on your program in question.

---

### Post by leilamoniz on 2014-11-05
> **/ADM said:**
> Which Windows software are you trying to use?  Winehq has a list of which programs runs great and which 'not' so great.  We could help more and provide more information on your program in question.

my son is trying to log into college via citrus virtual machine, (to be able to use some apps such as photoshop, dreamweaver, etc...) however when we downloaded file _**"launch.ica"**_ we are presented with a lot of info but at end it just says gives cmmand like "unnable to start or launch"

its quite a big screen on terminal full of info, so will it be ok to post this info here for all to better understand what the machine is trying to say??

---

### Post by Bucky Ball on 2014-11-05
If you are posting code post it in [code] tags. See the last link in my signature for how.

If you are posting a screenshot, use 'Adv Reply' (or 'Go Advanced') and use the paperclip icon to attach.

---

### Post by leilamoniz on 2014-11-05
so i just another go at installation and had message saying to have this done in root....so google for this and saw some videos on youtube to clarify the root topic.

so i now tried 

sudo su

and then i copy and paste file "setupwfc" and follow instruction below and now im stuck in : ( * Starting Citrix USB daemon [fail] )

```
Microsoft, MS, MS-DOS, Outlook, Windows, Windows NT, and BackOffice are
either registered trademarks or trademarks of Microsoft Corporation in
the United States and other countries.

All other Trade Names referred to are the Servicemark, Trademark,
or Registered Trademark of the respective manufacturers.


Select a setup option:

 1. Install Citrix Receiver for Linux 11.100
 2. Remove Citrix Receiver for Linux 11.100
 3. Quit Citrix Receiver for Linux 11.100 setup

Enter option number 1-3 [1]: 1

Please enter the directory in which Citrix Receiver for Linux is to be installed.
[default /usr/lib/ICAClient] 
or type "quit" to abandon the installation: 

An installation of Citrix Receiver for Linux 11.100 
already exists in this directory. Re-installing will
overwrite that installation and all its configuration with 
Citrix Receiver for Linux 11.100.

Do you want to proceed? [default n]: y

You have chosen to install Citrix Receiver for Linux 11.100 in /usr/lib/ICAClient.

Proceed with installation? [default n]: y

CITRIX(R) LICENSE AGREEMENT

Use of this component is subject to the Citrix license covering the 
Citrix product(s) with which you will be using this component. This 
component is only licensed for use with such Citrix product(s).

CTX_code EP_T_A34320

Select an option:

 1. I accept
 2. I do not accept

Enter option number 1-2 [2]: 1
Installation proceeding...

Checking available disk space ...

    Disk space available 137932548 K 
    Disk space required 6923 K


Continuing ...
Core package...
Setting file permissions...
Integrating with browsers...
Browsers found.

Found entries in browser configuration(s) from an earlier installation.
Do you want these entries to point to the new installation? [default y]: y

Integration complete.

Found KDE or GNOME desktop entries from an earlier installation.
Do you want these entries to point to the new installation? [default y]: y
No GStreamer directories were found, skipping GStreamer integration.
Do you want to install USB support? [default n]: y
 * Starting Citrix USB daemon [fail]

 [fail]
```

---

### Post by CantankRus on 2014-11-05
[**_[COLOR="#B22222"]CitrixICAClientHowTo[/COLOR]_**]("https://help.ubuntu.com/community/CitrixICAClientHowTo")
I know nothing about this and again it looks a bit complicated for a new user.

eg 
>  4. Install the package(s) and dependencies

sudo dpkg -i icaclient-*.deb ctxusb-*.deb
sudo apt-get -f install  # Install dependencies and finish configuring the package(s)

Before the first command will work you must be in the directory where the downloaded deb files are.
So if you downloaded to your Downloads directory you need to, in the terminal change to that directory first...
```
cd ~/Downloads
```

---

### Post by leilamoniz on 2014-11-05
> **CantankRus said:**
> [**_[COLOR=#B22222]CitrixICAClientHowTo[/COLOR]_**]("https://help.ubuntu.com/community/CitrixICAClientHowTo")


ok thx all;

just one question b4 i proceed :

do i copy and paste all to terminal each line at the time as in this instructions [here]("http://mark911.wordpress.com/2014/06/27/how-to-install-citrix-receiver-icaclient-in-ubuntu-14-04-lts-64-bit-tested-and-working-using-mozilla-firefox/") ?

---

### Post by CantankRus on 2014-11-05
> **leilamoniz said:**
> ok thx all;

just one question b4 i proceed :

do i copy and paste all to terminal each line at the time as in this instructions [here]("http://mark911.wordpress.com/2014/06/27/how-to-install-citrix-receiver-icaclient-in-ubuntu-14-04-lts-64-bit-tested-and-working-using-mozilla-firefox/") ?
Try the guide here as you can more easily get help.
[**_[COLOR="#B22222"]The Comprehensive Guide to Making Citrix Receiver work on Kubuntu 13.10[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2181903")

Read the thread first to see how others have fared.
Terminal commands are entered one line at a time.
Good luck. ;)

---

### Post by leilamoniz on 2014-11-05
wow, most complicated .... but impressive at the same time.

ill continue my concerns over on the other thread so all issues continue organized in forum and avoid having repeated posts.

thx once again for all your replies and assistance

---

