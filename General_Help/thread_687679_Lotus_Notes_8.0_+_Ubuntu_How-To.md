---
title: "Lotus Notes 8.0 + Ubuntu How-To"
date: 2008-02-04
forum: General Help
---

### Post by fatbuttlarry on 2008-02-04
[COLOR="Red"][B]This how-to was originally created for Ubuntu 7.10 (Gutsy Gibbon) + Lotus Notes 8.0

Since this thread was started, IBM has released Lotus Notes 8.5 Client Installer (beta) for Ubuntu 8.04 (link below), and plans to support Ubuntu moving forward, so this thread will soon become obsolete. (Thanks Cloud79)

Please continue to discuss here, but note that you are posting in the FORUM ARCHIVE and therefor any Ubuntu 8.04 (Hardy Heron) how-tos should be in a new thread and cross-linked!

Since Ubuntu 7.10 is still very prevalent, keep posting your success stories or struggles!  Many people are also running older versions of Lotus Notes (6.5, etc) in Wine, so Google around for that if you are still on an old version!

If you are here looking for Domino 8 Server on Ubuntu, look [here]("http://fatbuttlarry.blogspot.com/2008/07/domino-8-ubuntu-quickstart.html").

Thanks!

-Tres[/b][/color]

**Lotus Notes 8.5 Client For Ubuntu 32-bit (work-arounds needed for 64-bit):**
[https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?lang=en_US&source=swg-lnd85](https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?lang=en_US&source=swg-lnd85)

[img]http://img156.imageshack.us/img156/7518/lotusubuntudr1.png[/img]

[[img]http://ubuntuforums.org/attachment.php?attachmentid=58700&d=1202157734[/img]](http://img204.imageshack.us/img204/107/screenshotel7.png)

**            LOTUS NOTES 8.0 INSTALL: UBUNTU 7.10**
Created: 02/01/2008
Author:  A. Tres Finocchiaro


**                  BACKGROUND**
NOTE: IBM does not currently offer Ubuntu support for Lotus Notes 8.0 Client, so they will not be able to offer help with the client install if it fails.

Fortunately, the installer does work with Debian-based distributions with the following work-arounds.


**                 INSTRUCTIONS**
Download and extract the installer.  You can extract with fileroller, or you may use "tar -xvf", from terminal, to your disgression.

Link:  [[color=red]**Lotus Notes Client 8.0 for Linux**[/color]]("https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?S_PKG=C14SXEN&source=ESD-NTSDOMTRL&S_TACT=105AGX28&S_CMP=TRIALS") 449MB

Launch the installer from command line by typing the following in the terminal. $USERNAME is the username you're logged in as, NOT root.
```

    cd /home/$USERNAME/(folder you extracted to)
    chmod +x setup.sh
    sudo ./setup.sh
```

During install, take all defaults.

**ISSUE #1A**[COLOR="Red"]:**Locking assertion failure. Backtrace:**[/color] Cause: [[Ubuntu bug #192061](https://bugs.launchpad.net/ubuntu/+bug/193061)] Workaround:
```

    sudo ./setup.sh -console

```

**Issue #1B**:[COLOR="Red"]** Unreadable Installer GUI**[/COLOR]:  If the installer launches, but just shows a blank window (Does not effect Kubuntu), close it out and do the following.  Please skip this step if the installer looks fine.  *Note, if you do not want to install kwin, turning off desktop effects may remedy this also.*

```
    sudo apt-get install kwin
    kwin --replace &
    exit

```
Now try the installer again.  Once it completes, switch back to metacity:

```
    metacity --replace &
    exit
```

**Issue #2**:[COLOR="Red"]** Permissions and Links:**[/COLOR]  The installer does not set up all permissions and links properly in Debian. This step cannot be skipped.  Type the following:

```
    cd /opt/ibm/lotus/notes
    chmod +x lnotes
    sudo ln -s /opt/ibm/lotus/notes/*.so /usr/lib/notes/ 
    sudo chmod 755 /etc/lotus/notes/data/shared/ -R
```

Setup is complete. To launch notes, type the following into a terminal window:

```
    cd /opt/ibm/lotus/notes
    ./notes
```

Any questions, drop me a message!


**            ADDITIONAL INFORMATION**
**Issue #3**:  [COLOR="Red"]**Home path errors**[/COLOR]: If you accidentally ran "./notes" as root, you may end up with some un-writtable folders in your home directory.  If so, execute the following command in a terminal window, where $USERNAME is the name you are currently logged in as, NOT root.  Be very careful, as the "-R" switch recurses through all folders.
```

    sudo chown $USERNAME /home/$USERNAME/lotus/notes -R

```
**Issue #4**:  [COLOR="Red"]**Java Issues**[/COLOR]: Although shouldn't be needed, any Java, JVM, or JRE issues, please follow Sun or Ubuntu guidelines for installing Java Runtime Environment in Ubuntu Linux.  For starters, you can try: (Notes should already come bundled with its own version of Java).  If you simply have a blank screen during the installer, see[COLOR="Red"]** Issue #1**[/COLOR] above.

```
    sudo apt-get install sun-java6-jre
```

**Issue #5**:  [COLOR="Red"]**Connection issues:**[/COLOR]  If "apt-get" gives errors during download, please ensure your proxy is set up properly in your installation.  This can be set through Preferences >> Network Proxy, or alternately: (as an example, fill in with your proxy info)


```
    export http_proxy="http://192.168.0.1:9999"
```

Also make sure that you have enabled all optional repositories in Adimistration >> Synaptic Package Manager >> Settings.

**Issue #6:** [COLOR="Red"]** Server Not Responding**[/COLOR]: If you receive "Server not responding" after receiving the password prompt, rest assured, the application just needs to be restarted.

    ```
ps -e |grep notes
```

Look for **"[COLOR="Orange"][B]XXXXXX**[/COLOR] ? HH:MM:SS notes2w"[/B] where[COLOR="Orange"]** XXXXXX**[/COLOR] is the process ID of notes2w.  For example:
  ```
[COLOR="Orange"]**25999**[/COLOR] ? 00:00:10 notes2w
```

Issue kill command for that XXXXXX process:
    ```
kill -9 [COLOR="Orange"]**25999**[/COLOR]
```

*Alternately*, you can issue the "pkill" command, and kill it by name:
    ```
pkill -9 notes2w
```

Then restart notes.

**Issue #7:** [COLOR="Red"]**Could Not Launch Menu Item**[/color] Due to lack of permissions, the shortcut may complain that it cannot be executed.  This is a proposed fix, but has not yet been tested. Please use with caution. This effectively changes all files (through all sub folders) within the "notes" folder to Read and Execute.  It does not change Modify/Delete permissions.
   ```

   sudo chmod 755 /opt/ibm -R
   
```

> **vehka said:**
> I also had to delete the InstallShield folder at /root/, and once more delete the lotus folder at my home directory.

**Issue #8:** [COLOR="Red"]**License warning error reading "pernames.ntf".**[/color]  This is a proposed fix, but has not yet been tested.  Please use with caution.
   ```

   sudo chmod 755 /etc/notes -R
   
```

**Issue #9:** [COLOR="Red"]**Open, Edit, or View attachment dialog disappears**[/color] "When a customer clicks an attachment within the Lotus Notes® client for Linux®, the Open Attachment dialog box provides the customer with options to Open, Edit, or View the attachment. When any of these three options are opened the dialog box disappears and no action is taken.  Generally, this problem is seen with attachments that are not of a common file type in Linux. However, this problem can also occur for common Linux file types such as odt and pdf." -Harmony Pirate Blog

Do the following:
```

     sudo mv /opt/ibm/lotus/notes/openwith /opt/ibm/lotus/notes/openwith.old
     sudo ln -s $(which gnome-open) /opt/ibm/lotus/notes/openwith

```

If "gnome-open" is not installed, you may want to get it through Synaptic or Aptitude Package Managers.  You may also use "kde-open" if desired.


**ICONS**
[img]http://img179.imageshack.us/img179/374/lotuslo5.png[/img]
[img]http://img210.imageshack.us/img210/7441/lotusnotesxf7.png[/img]

Enjoy!

-Tres

---

### Post by fatbuttlarry on 2008-02-16
Helpful links:

[LIST]
[*][Install Lotus Notes 8 Beta 3 on Ubuntu 7.04 Feisty Fawn - Step by Step](http://coort.wordpress.com/2007/07/17/install-lotus-notes-8-beta-3-on-ubuntu-704-feisty-fawn-step-by-step/)
[*][[SOLVED] Lotus Notes 8 on Gutsy (7.10)](http://ubuntuforums.org/showthread.php?t=589672)
[/LIST]

:popcorn::guitar:

---

### Post by icechen1 on 2008-02-16
Mod should move this to howtos section.

---

### Post by K.Mandla on 2008-02-16
Moved to General Help.

Please remember that the Cafe is not for support threads or howtos.

---

### Post by fatbuttlarry on 2008-02-16
Thank you.

---

### Post by Coort on 2008-02-18
Ok, some advices, as repoted on my blog.

First, consider to enable the "root" user and not sudo for the installer. Even if it works, sudo cause problem when setting the permission on your user "lotus" directory. Launching the ".sh" using root solve this issue. After you can disable root again if you want (i've done it).

Use "bash", by default ubuntu use DASH, so you have to change "/bin/sh" from "/bin/dash" to "/bin/bash", when the installer has finished you can revert back safely.

Better, if you have time to wait, from release 8.5 IBM will give official support for Ubuntu (and with some luck it will come with the eclipse-based designer included).

BTW good how-to :)

NOTE for Notes technician: no administrator included in 8.0 or planned for 8.5, just to be clear :)

---

### Post by fatbuttlarry on 2008-02-18
> **Coort said:**
> Ok, some advices, as repoted on my blog.

First, consider to enable the "root" user and not sudo for the installer. Even if it works, sudo cause problem when setting the permission on your user "lotus" directory. Launching the ".sh" using root solve this issue. After you can disable root again if you want (i've done it).

Use "bash", by default ubuntu use DASH, so you have to change "/bin/sh" from "/bin/dash" to "/bin/bash", when the installer has finished you can revert back safely.

Better, if you have time to wait, from release 8.5 IBM will give official support for Ubuntu (and with some luck it will come with the eclipse-based designer included).

BTW good how-to :)

NOTE for Notes technician: no administrator included in 8.0 or planned for 8.5, just to be clear :)

Thanks.  How does one safely "enable" root user?

I would like to avoid setting root password, as sudo is better for system security.

Also what is the difference with sh bash and dash, does it fix a step for the installer?

-Tres

---

### Post by Coort on 2008-02-19
> **fatbuttlarry said:**
> Thanks.  How does one safely "enable" root user?

I would like to avoid setting root password, as sudo is better for system security.

Also what is the difference with sh bash and dash, does it fix a step for the installer?

-Tres

Enable root user:
```
sudo passwd root
```
You will be prompt for a root password, choose one, log in with root and start the installer, **when you're done with it you can safely disable again** with:
```
sudo passwd -l root
```
Actually this solve the permission issue on ~/lotus.

DASH vs BASH
In beta3 times this was a severe issue, using the installer with DASH several times lead to installation failures, because the product was intended only for SLED and RHEL that use BASH as default shell. I think something is changed with the gold release, but i think changing the link is a "best practice". Again, this is ONLY for the installation, then you can safely revert back (better: it is more safe for your system to revert back than leaving BASH as default shell).

Sry for my poor english :)

---

### Post by fatbuttlarry on 2008-02-19
> **Coort said:**
> Enable root user:
```
sudo passwd root
```
You will be prompt for a root password, choose one, log in with root and start the installer, **when you're done with it you can safely disable again** with:
```
sudo passwd -l root
```
Actually this solve the permission issue on ~/lotus.

DASH vs BASH
In beta3 times this was a severe issue, using the installer with DASH several times lead to installation failures, because the product was intended only for SLED and RHEL that use BASH as default shell. I think something is changed with the gold release, but i think changing the link is a "best practice". Again, this is ONLY for the installation, then you can safely revert back (better: it is more safe for your system to revert back than leaving BASH as default shell).

Sry for my poor english :)

Thank you for taking the time to explain.

So Debian uses "DASH" by default?

-Tres

---

### Post by Coort on 2008-02-19
> **fatbuttlarry said:**
> Thank you for taking the time to explain.

So Debian uses "DASH" by default?

-Tres

Sorry, i have no answer on that, i'm a beginner on linux and my experience on long term use is limited to Ubuntu, this level of technical detail on other distro is too much for me :) .

---

### Post by fatbuttlarry on 2008-02-20
Understood.

I'm reading the "sudo passwd root" instructions... where does the program install to?  I don't want to change them unless I'm sure it will still work.

-Tres

---

### Post by Coort on 2008-02-21
For me, nothing changed in term of "path", files installed with sudo where in the smae place when i've used "root".

---

### Post by fatbuttlarry on 2008-02-21
I'm pretty sure the ~/ permission errors were caused by *running* the application as root, not necessarily by installing it with sudo... Perhaps I'm wrong.  Its a shame there aren't more people installing this, or rather... giving feedback!

If you don't mind, I'll leave out the **passwd** instructions until we get some confirmation of errors.

I do however, thank you for your input, its very kind.

-Tres

---

### Post by Coort on 2008-02-21
For this i can give you a response, you cannot run notes8 as root or with sudo, it will exit after some loading even before asking you the password, saying tha "notes must be run as unprivileged user" or something like that.
The permission error is an installation issue for sure, 'cause i've installed the first time with sudo, and then run for the first time without sudo, and i got the permission error. :)

---

### Post by fatbuttlarry on 2008-02-21
Thank you for your detailed response.

Which permissions are you referring to, I may be misunderstanding you.


-Tres

---

### Post by dark_phantom on 2008-02-21
Very nice, I have to try and do this install.  First, I have to get a copy of it though. Is the client free to download?

---

### Post by fatbuttlarry on 2008-02-21
> **dark_phantom said:**
> Very nice, I have to try and do this install.  First, I have to get a copy of it though. Is the client free to download?

They do offer a demo for free, yes.

Link:  [[color=red]**Lotus Notes Client 8.0 for Linux**[/color]]("https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?S_PKG=C14SXEN&source=ESD-NTSDOMTRL&S_TACT=105AGX28&S_CMP=TRIALS") 449MB

Select the one that says > **IBM Lotus Domino 8.0 Trials for Multiplatforms eAssembly English**

It should download a file "C14SXEN.tar"

If you don't have an IBM account, just create a free one with the link they provide.

-Tres

---

### Post by Coort on 2008-02-21
> **fatbuttlarry said:**
> Thank you for your detailed response.

Which permissions are you referring to, I may be misunderstanding you.


-Tres

Ok when you first start notes with a user, it creates in user's home folder the "data" directory, so every user that at least start notes one time will have a "~/.lotus/". I don't know why, but installing notes with sudo create on the user currently "sudoing" the installer this "~/.lotus/" folder with messed up permission and in it's installation directory, the file are in the right place with the wrong perms. If i have to suppose why this is happening, my theory is: notes was designed for being installed with distro that not have "sudo" by default, 'cause sudo give you root privileges but does not make you really root (ie. environment vars).
To make it clear what i suppose: in windows version with "multiuser install" Notes create a "notes\data"  template directory, that use every time you configure new user (not only for this, in reality, but better to not waste time on windows now), so i think it will do similar on linux, using root user; so when you make an install with root it locate root home folder and place the template data directory, if you use sudo it will misunderstand your user with root and this lead to some issues later when configuring (when you make the first start of notes with your unprivileged user).

I hope my text is english readable :P

---

### Post by fatbuttlarry on 2008-02-21
Yes, very readable!

I guess my main concern is this...

If notes by default installs files in ~/, then it would pick /root/ when logged in as root.  Perhaps it does.  Perhaps the installer automatically tries to launch Lotus Notes once finished installing.

If I have enough time this week, I'll try to reinstall.  If anyone else beats me to it, please post the results.

:popcorn:

-Tres

---

### Post by rosslaird on 2008-02-21
I have tried to install notes on two different machines today, and I keep getting stopped at the login screen (after the install completes) with this error:

```
CLFRJ0010E: Notes initialization failed
```

I have tried the various suggestions over at the IBM forums (library files, init file, rebooting, etc.), but nothing has worked for me.
Ideas are welcome.

Ross

---

### Post by stoomaroo on 2008-02-21
FYI - works for Lotus Notes 8.0.1 also.  I had the Java GUI error however, and one other issue.

I needed to:

sudo chown *$username* /opt/ibm/lotus/notes -R   

(where *$username* was my logged-in user)

to get it to run from the Applications menu in Ubuntu.  Otherwise I was receiving a nasty "Could not launch menu item" error - due to lack of permissions.

stoomaroo

---

### Post by BrownieBoy on 2008-02-22
> **rosslaird said:**
> I have tried to install notes on two different machines today, and I keep getting stopped at the login screen (after the install completes) with this error:

```
CLFRJ0010E: Notes initialization failed
```

I have tried the various suggestions over at the IBM forums (library files, init file, rebooting, etc.), but nothing has worked for me.
Ideas are welcome.

Ross

I'm getting that same error on Gutsy.  Did you get any further with it?

---

### Post by fatbuttlarry on 2008-02-22
**stoomaroo**:
> **stoomaroo said:**
> FYI - works for Lotus Notes 8.0.1 also.  I had the Java GUI error however, and one other issue.

I needed to:

sudo chown *$username* /opt/ibm/lotus/notes -R   

(where *$username* was my logged-in user)

to get it to run from the Applications menu in Ubuntu.  Otherwise I was receiving a nasty "Could not launch menu item" error - due to lack of permissions.

stoomaroo

Thanks for the feedback.

This isn't recommended as it will prevent others from running the application.  Changing ownership to yourself will allow only yourself to run that application.

Instead, I recommend changing permissions so that all users can read and execute, which would be ```
sudo chmod 755 /opt/ibm/lotus/notes -R
```

Only after you reset your permissions back with ```
sudo chown root /opt/ibm/lotus/notes -R
```

But use with caution (and please double check the above commands, as I did not copy verbatim from console).

If there is a file that you explicitly need write permissions to, I suggest we find it and simply grant permissions of that file only to "777" (ower group and users can read, write and execute).

To do this:

```
sudo chmod 777 /path/to/file
```

Changing ownership to yourself may  work in short-term, but will break for all new users on your station, and can actually prevent "root" from accessing those.

**rosslaird**, I'd be happy to help.  What platform are you installing on? Please post up some system information, such as OS version, Kernel, Platform, Desktop, etc.  Also, are you receiving this error in console, or GUI?
```

#gets kernel
uname -r 
#gets OS
cat /etc/lsb-release

```

Platform will probably be "AMD64" or "Intel"
Desktop would be "KDE", "Gnome", "xfce".  If you're stock Ubuntu, then "Gnome".

-Tres

---

### Post by rosslaird on 2008-02-22
Tres;

Thanks for the offer. I'm using Gutsy (on both systems) with the 2.6.22-14-386 kernel.
The error comes after the Notes splash screen (so, in the GUI). Though I haven't tried in KDE, I have tried it with kwin under gnome, and with metacity/emerald under gnome. I have tried a reinstall (several times), and a reboot, and various other things. The ibm help page on this issue is not very helpful:

[http://www-1.ibm.com/support/docview.wss?rs=475&context=SSKTWP&dc=DB520&dc=DB560&uid=swg21266312&loc=en_US&cs=UTF-8&lang=en&rss=ct475lotus]("http://www-1.ibm.com/support/docview.wss?rs=475&context=SSKTWP&dc=DB520&dc=DB560&uid=swg21266312&loc=en_US&cs=UTF-8&lang=en&rss=ct475lotus")

I don't think the error can be hardware dependent, since it happens on both my laptop and my desktop. But other than that, I'm in the dark.

By the way, here are the kinds of things I see in the startup terminal:

Error loading libnoteswc.so - libnoteswc.so: cannot open shared object file:Too many levels of symbolic links
2008/02/22 16:42:51.776 SEVERE CLFMW0029E: Notes basic initialization and launch Failed

Caused by: javax.security.auth.login.LoginException:
CLFRJ0010E: Notes initialization failed at com.ibm.workplace.internal.notes.security.auth.NotesLoginModule.login(NotesLoginModule.java:353)

---

### Post by BrownieBoy on 2008-02-22
@Ross,

I think that the "CLFRJ0010E: Notes initialization failed" may have been due to clash between Notes and the standalone version of Lotus Symphony.  Do you have latter installed?  I had installed it seperately, before installing Notes.

I ran the de-installers for both Symphony and then Notes, and made sure all of the IBM and Lotus folders were gone.  I then ran the Notes installer again and got the permissions problem, which I didn't get before.  I used Tres's instructions to fix this and bingo!  All working now.

Thanks for your help, guys.

Cheers

---

### Post by rosslaird on 2008-02-23
> **BrownieBoy said:**
> @Ross,

I think that the "CLFRJ0010E: Notes initialization failed" may have been due to clash between Notes and the standalone version of Lotus Symphony.  Do you have latter installed?  I had installed it seperately, before installing Notes.

Cheers

Nope, I don't have Symphony installed.
I may try the uninstall route. This is starting to feel like the old days...

Ross

---

### Post by fatbuttlarry on 2008-02-23
> **rosslaird said:**
> Tres;

Thanks for the offer. I'm using Gutsy (on both systems) with the 2.6.22-14-386 kernel.
The error comes after the Notes splash screen (so, in the GUI). Though I haven't tried in KDE, I have tried it with kwin under gnome, and with metacity/emerald under gnome. I have tried a reinstall (several times), and a reboot, and various other things. The ibm help page on this issue is not very helpful:

[http://www-1.ibm.com/support/docview.wss?rs=475&context=SSKTWP&dc=DB520&dc=DB560&uid=swg21266312&loc=en_US&cs=UTF-8&lang=en&rss=ct475lotus]("http://www-1.ibm.com/support/docview.wss?rs=475&context=SSKTWP&dc=DB520&dc=DB560&uid=swg21266312&loc=en_US&cs=UTF-8&lang=en&rss=ct475lotus")

I don't think the error can be hardware dependent, since it happens on both my laptop and my desktop. But other than that, I'm in the dark.

By the way, here are the kinds of things I see in the startup terminal:

Error loading libnoteswc.so - libnoteswc.so: cannot open shared object file:Too many levels of symbolic links
2008/02/22 16:42:51.776 SEVERE CLFMW0029E: Notes basic initialization and launch Failed

Caused by: javax.security.auth.login.LoginException:
CLFRJ0010E: Notes initialization failed at com.ibm.workplace.internal.notes.security.auth.NotesLoginModule.login(NotesLoginModule.java:353)

Great!

The error "too many levels of symbolic links" is a sign that you have a circular reference to a shared object file.

In the windows world this would mean you have a link to a dll, point back to a link to a dll.

Do the following:

```

sudo updatedb (wait for it to finish, might take a while)
locate libnoteswc.so

```
You'll see some locations that have a file with that name.

Now, do the following for each file:
```

ls -al /path/to/libnoteswc.so

```

What you should get is a description of where the file is pointing.  There may have been a bad step in my instructions that caused a circular reference.  You can remove both instances of the file and try to restore the original.  My method at creating the symbolic links may have a better solution, such as adding the /opt/ibm files to the search path to Ubuntu.  Let me know what you find.

-Tres

---

### Post by rosslaird on 2008-02-23
Hi Tres;

Thanks for the feedback. (Don't feel that you have to explain everything as though I'm used to Windows; I've been a Linux user for almost a decade.)

> **fatbuttlarry said:**
> Great!

The error "too many levels of symbolic links" is a sign that you have a circular reference to a shared object file.



That's what I figured, and I just hadn't had time to look into it yet. 
Looks like I have a couple of files floating around/linked. Slocate gives me these:

/opt/ibm/lotus/notes/libnoteswc.so
/usr/lib/libnoteswc.so

The first one in not linked, but the second one gives me this:

```
lrwxrwxrwx 1 root root 13 2008-02-21 14:43 /usr/lib/libnoteswc.so -> libnoteswc.so
```

So, I think there is the problem. I will continue exploring; further feedback is welcome.

Ross

UPDATE:

Turns out I had a whole raft of files tagged with "Too many levels of symbolic links" in /usr/lib. I removed them all with thunar (which is great for this kind of thing).
Notes is still not working (same error), but at least my system feels cleaner now...

---

### Post by fatbuttlarry on 2008-02-24
Ross,

Thanks for the quick response. Makes perfect sense.  All of the IBM symlinks are probably broken.  You must have been in "/opt/ibm/lotus/notes/" when you ran the "ln -s" symlink command, or else the links wouldn't have known what names to use... so I'm a bit confused why they're broken... weird

The instructions verbatim say:
```

    cd /opt/ibm/lotus/notes
    chmod +x lnotes
    sudo ln -s *.so /usr/lib/

```

Perhaps you ran the uninstaller which broke them?

In theory, "/usr/lib/some_shared_object.so" should point to "/opt/ibm/lotus/notes/some_shared_object.so".  If you understand what the command does, you can recreate them manually, and it will probably fix it.

Maybe the command should say 
```

sudo ln -sf *.so /usr/lib/

```

I just hate using the -f (force) option because if it's typed wrong, it can really destroy stuff lol.

P.S.  If I dumb things down a little bit, its no disrespect to your knowledge, just might read a little clearer for the ones who aren't as savvy yet. :)

-Tres

---

### Post by rosslaird on 2008-02-24
Hi Tres;

Well, it does seem weird.

> **fatbuttlarry said:**
> You must have been in "/opt/ibm/lotus/notes/" when you ran the "ln -s" symlink command, or else the links wouldn't have known what names to use... so I'm a bit confused why they're broken... weird {/QUOTE]

Yup.

When I re-run the link command, I get the same symlink errors in /usr/lib.

{QUOTE]Perhaps you ran the uninstaller which broke them?{/QUOTE]

Nope. I have not yet tried that. I figure it might introduce more problems.

[QUOTE]In theory, "/usr/lib/some_shared_object.so" should point to "/opt/ibm/lotus/notes/some_shared_object.so".  If you understand what the command does, you can recreate them manually, and it will probably fix it. {/QUOTE]

I will try that. But I hardly ever use symlinks, so I'll have to look into how they work. I wonder if the ls entries in /usr/lib are a clue. The arrows point to a file without a path, and perhaps that means that there is no path on the symlink to /opt/ibm/...
Like so:

```
lrwxrwxrwx   1 root root        8 2008-02-23 22:37 xmlsr.so -> xmlsr.so
```

I wonder if that should say:

```
lrwxrwxrwx   1 root root        8 2008-02-23 22:37 xmlsr.so -> /opt/ibm/lotus/notes/xmlsr.so
```

{QUOTE]P.S.  If I dumb things down a little bit, its no disrespect to your knowledge, just might read a little clearer for the ones who aren't as savvy yet. :)

No worries. I just didn't want you to feel that you had to explain every tiny little detail. I'm used to working through these kinds of things.

Ross

---

### Post by BrownieBoy on 2008-02-24
@Ross,

Sorry my advice was of no help.   So, it wasn't Symphony then.

There's only one other thing that I can think of that I did differently for the last install (the one that worked).  Previously, I had been installing from a shared FAT32 drive that was accessed via a symbolic link.  (I use this drive to share data between Linux and Windows installs).

For the working install, I copied over the install folder from that drive to my main Linux partition - actually to my Desktop folder - and ran it from there.  I also renamed the install folder from Notes8.01 to just Notes.

It's a long shot I know, but sometimes it's the weirdest little things that trip you up...

Cheers.

---

### Post by fatbuttlarry on 2008-02-24
> **rosslaird said:**
> I wonder if that should say:```

lrwxrwxrwx   1 root root        8 2008-02-23 22:37 xmlsr.so -> /opt/ibm/lotus/notes/xmlsr.so

```


You are correct.  

The format for the command is:
```
ln -s /path/to/actual/file.so /path/to/desired/link.so
```

The reason I put those symlinks in /usr/lib, is because normally, Ubuntu doesn't look in the /opt/ folder.  I'm pretty confident though, we can add that location instead of creating the shortcuts, I just don't know the exact command.

-Tres

---

### Post by rosslaird on 2008-02-24
OK, this is quite weird. I have been following the exact command for the links:

    sudo ln -s *.so /usr/lib/

from within /opt/ibm/lotus/notes

Even when I remove the problem symlinks in /usr/lib after having run the above command, and re-create them using the same command again, I get the same problem "(too many."). So how is it possible that the command, which seems perfectly simple and reasonable, is not directing the symlinks in /usr/lib back to the correct directory? (/opt/ibm/lotus/notes) What am I missing here?

The only thing I can think of is that the files/links might already exist in /usr/lib, but that can't be the source of the issue because I have removed them manually. So the command is recreating the links, it's just misdirecting them to themselves (i.e. in /usr/lib) rather than back to the destination directory (opt/ibm.lotus/notes).

Stumped.

---

### Post by fatbuttlarry on 2008-02-24
> **rosslaird said:**
> OK, this is quite weird. I have been following the exact command for the links:

    sudo ln -s *.so /usr/lib/

from within /opt/ibm/lotus/notes

Even when I remove the problem symlinks in /usr/lib after having run the above command, and re-create them using the same command again, I get the same problem "(too many."). So how is it possible that the command, which seems perfectly simple and reasonable, is not directing the symlinks in /usr/lib back to the correct directory? (/opt/ibm/lotus/notes) What am I missing here?

The only thing I can think of is that the files/links might already exist in /usr/lib, but that can't be the source of the issue because I have removed them manually. So the command is recreating the links, it's just misdirecting them to themselves (i.e. in /usr/lib) rather than back to the destination directory (opt/ibm.lotus/notes).

Stumped.

It may be a behavior of "ln" on your computer.  Perhaps its not handling multiple files correctly.

I'd be happy to examine the files and links if you have an SSH account you can give me access with.  My AIM is "FatButtLarry" if you're interested.:guitar:

You could try to be more explicit with:
```

sudo ln -sf /opt/ibm/lotus/notes/*.so /usr/lib/*.so

```

When you do:```

cd  /opt/ibm/lotus/notes
ls -al *.so

```
Do any of the shared objects show as symlinks, or are they all regular files?

-Tres

---

### Post by rosslaird on 2008-02-24
OK, progress (at least, some clarity).

The .so files in /opt/ibm/lotus/notes are all regular files and not symlinked.

When I create a directory under /usr/lib, called /usr/lib/notes, and then run the original command (not the one suggested above, which actually threw a "Directory does not exist" error, even though the directory does exist), the symlinks were created correctly. So:

```
 sudo ln -sf /opt/ibm/lotus/notes/*.so /usr/lib/notes/
```

works perfectly. The files/symlinks in this directory have the following form:

```
lrwxrwxrwx 1 root root 29 2008-02-24 11:55 xywsr.so -> /opt/ibm/lotus/notes/xywsr.so
```

So, it's a matter of where the command is allowed to place the links. For some reason, /usr/lib just fails, whereas /usr/lib/notes does not. Very strange. Notes still doesn't work, of course. But at least some things are getting more clear.

Ross

---

### Post by fatbuttlarry on 2008-02-24
> **rosslaird said:**
> OK, progress (at least, some clarity).

The .so files in /opt/ibm/lotus/notes are all regular files and not symlinked.

When I create a directory under /usr/lib, called /usr/lib/notes, and then run the original command (not the one suggested above, which actually threw a "Directory does not exist" error, even though the directory does exist), the symlinks were created correctly. So:

```
 sudo ln -sf /opt/ibm/lotus/notes/*.so /usr/lib/notes/
```

works perfectly. The files/symlinks in this directory have the following form:

```
lrwxrwxrwx 1 root root 29 2008-02-24 11:55 xywsr.so -> /opt/ibm/lotus/notes/xywsr.so
```

So, it's a matter of where the command is allowed to place the links. For some reason, /usr/lib just fails, whereas /usr/lib/notes does not. Very strange. Notes still doesn't work, of course. But at least some things are getting more clear.

Ross

Great!  What error does notes give you now?

-Tres

---

### Post by rosslaird on 2008-02-24
Same error:

```
CLFRJ0010E: Notes initialization failed
```

I'm beginning to think that the error is actually not related to the symlinks at all...
(If it was, changing/fixing/modifying the symlinks would have had some effect on the error).

Here is what the error log says. This is the first error entry (there are several after this):

```

<CommonBaseEvent creationTime="2008-02-24T12:48:29.850-08:00" globalInstanceId="EL7f0001010001184d341b9800000001" msg="CLFMW0029E: Notes basic initialization and launch Failed" severity="50" version="1.0.1">
	<extendedDataElements name="CommonBaseEventLogRecord:level" type="noValue">
		<children name="CommonBaseEventLogRecord:name" type="string"> 
			<values>SEVERE</values>
		</children>
	</extendedDataElements>
	<extendedDataElements name="CommonBaseEventLogRecord:sourceClassName" type="string">
		<values>com.ibm.workplace.noteswc.NoteswcPlugin$1</values>
	</extendedDataElements>
	<extendedDataElements name="CommonBaseEventLogRecord:sourceMethodName" type="string">
		<values>done</values>
	</extendedDataElements>
	<sourceComponentId component="Expeditor 6.1" componentIdType="ProductName" instanceId="1203633542641" location="127.0.1.1" locationType="IPV4" subComponent="com.ibm.workplace.noteswc" threadId="11" componentType="http://www.w3.org/2001/XMLSchema-instance"/>
	<situation categoryName="ReportSituation">
		<situationType xmlns:xsi="ReportSituation" reasoningScope="INTERNAL" reportCategory="LOG"/>
	</situation>
</CommonBaseEvent>

```

It says nothing about not being able to find a file. Rather, it complains about something for which I have no knowledge (not being a programmer).

---

### Post by rosslaird on 2008-02-24
Results, finally. Using a tip from this thread:

[http://ubuntuforums.org/showthread.php?t=589672&highlight=lotus+notes]("http://ubuntuforums.org/showthread.php?t=589672&highlight=lotus+notes")

I changed ownership (to my home user) of the following directories:

/etc/ibm
/etc/lotus
/home/"usr"/lotus
/opt/ibm

This is probably some horrible security risk, but it solves the problem. Notes starts!

The basic command, if someone else is doing this, is:

sudo chown "user" /path/to/dir

("user", without the quotes, is your user name)

The only small glitch is that the interface fonts seem small hard to read (not all of them, though).
(Fixed: I changed the fonts in the preferences, installed all the versions of luxi available from apt-get, and restarted Notes; I doubt if the font installation was actually necessary.)

Ross

---

### Post by fatbuttlarry on 2008-02-26
You are correct, changing permissions for yourself are not desired, as it will break for all other users of that workstation.

What is a better solution is to open up permissions of that folder to anyone that needs access.  

I would highly recommend changing ownership back to root, and simply changing permissions.

For example, chmod 755 allows read and execute permissons to all, but just write permissions to root.

The important part is finding the files with the permission errors, so that we can open permissions for just them!

Thanks for the info, it will help others in their struggles.  I will post it to the how-to as soon as we get a more "proper" way of handing it across the board. :guitar:

-Tres

---

### Post by rosslaird on 2008-02-26
I am the only user of this workstation, so I'm not too worried. Normally I do use 755 for this kind of thing, but it seemed that in the other thread (the one where I got the tip) this method only worked with ownership and not permissions. So, rather than try to do a full experiment to see what would work and how (I have already spent way too much time on this), I just changed the ownership. Once all this gets sorted out for other users and there is a "proper" way, then I'll revisit the issue. For now, I;m just happy that it works.

Ross

---

### Post by fatbuttlarry on 2008-02-28
Understood.  Keep in mind though, people read these forums all the time without posting.  Figuring problems out is not just for a few people in a thread when you're using Ubuntu! :)  The world benefits when you figure something small out!

:popcorn::guitar:

-Tres

---

### Post by www.rzr.online.fr on 2008-03-06
Any success reguarding hardy ?

---

### Post by www.rzr.online.fr on 2008-03-09
> **fatbuttlarry said:**
> They do offer a demo for free, yes.

Link:  [[color=red]**Lotus Notes Client 8.0 for Linux**[/color]]("https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?S_PKG=C14SXEN&source=ESD-NTSDOMTRL&S_TACT=105AGX28&S_CMP=TRIALS") 449MB

Select the one that says 

It should download a file "C14SXEN.tar"

If you don't have an IBM account, just create a free one with the link they provide.

-Tres

Once installed on hardy I dont see the menu, and running /opt/IBM/.../notes show nothing ..
Any other version to test than C14SXEN.tar ?

---

### Post by fatbuttlarry on 2008-03-09
> **www.rzr.online.fr said:**
> Once installed on hardy I dont see the menu, and running /opt/IBM/.../notes show nothing ..
Any other version to test than C14SXEN.tar ?

Any error messages runnign from terminal (gnome-terminal, konsole)?

---

### Post by www.rzr.online.fr on 2008-03-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/193061](https://bugs.launchpad.net/ubuntu/+bug/193061) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **fatbuttlarry said:**
> Any error messages runnign from terminal (gnome-terminal, konsole)?

1st At install :

./setup.sh 
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x96b08767]
[https://bugs.launchpad.net/ubuntu/+bug/193061](https://bugs.launchpad.net/ubuntu/+bug/193061)

Workaound :
./setup.sh  -console

---

### Post by fatbuttlarry on 2008-03-11
> **www.rzr.online.fr said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/193061](https://bugs.launchpad.net/ubuntu/+bug/193061) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

1st At install :

./setup.sh 
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x96b08767]
[https://bugs.launchpad.net/ubuntu/+bug/193061](https://bugs.launchpad.net/ubuntu/+bug/193061)

Workaound :
./setup.sh  -console

Thank you! Noted on how-to.

---

### Post by vehka on 2008-04-09
Thanks to this thread I managed to install Notes 8 on Gutsy. However, there were some additional things I needed to do.

I wasn't taking notes (pardon the pun) and I tried many things before I got it to work, so take my advice with a grain of salt.

After installation, when trying to start Notes, nothing happened. When starting as root, it would start normally, but then complain about being started with root permissions, and exit. So I chmodded the /opt/ibm/ dir recursively to 755 as someone instructed here, but this was not enough. I also had to delete the InstallShield folder at /root/, and once more delete the lotus folder at my home directory.

Now it would start normally.

Also, a colleague of mine would get some weird license warning when starting Notes together with some error on permissions (the "pernames.ntf" file), but his problem was solved by chmodding the permissions of the /etc/notes folder

chmod 755 /etc/notes -R

like this.

Hope these are of use to somebody!

---

### Post by fatbuttlarry on 2008-04-09
Thanks!!

Changed issue 8 as described, with comment of deleting home folders.

Added issue 9 regarding licensing warning.

Please continue to post your problems or progress.

-Tres

---

### Post by svasie on 2008-04-28
For those who are having problems opening attachments by double clicking them:

[http://harmonypirate.blogspot.com/2008/01/ibm-attachments-do-not-open-from-lotus.html](http://harmonypirate.blogspot.com/2008/01/ibm-attachments-do-not-open-from-lotus.html)

I had this problem with Lotus Notes 8.0.1 and now is working.

---

### Post by fatbuttlarry on 2008-04-28
> **svasie said:**
> For those who are having problems opening attachments by double clicking them:

[http://harmonypirate.blogspot.com/2008/01/ibm-attachments-do-not-open-from-lotus.html](http://harmonypirate.blogspot.com/2008/01/ibm-attachments-do-not-open-from-lotus.html)

I had this problem with Lotus Notes 8.0.1 and now is working.

Perfect!  Thank you! Added to tutorial!

-Tres

---

### Post by antibios on 2008-05-01
Has anyone tried this on Ubuntu 8.04?

---

### Post by fatbuttlarry on 2008-05-02
Probably not, since it came out only a week ago. Can you try for us?  I'm eager to know the success!

-Tres

---

### Post by vehka on 2008-05-05
Tried installing notes 8.0 on a fresh install of hardy (8.04). The installation was almost vanilla, I just enabled the NVIDIA drivers and installed the nvidia-settings package.

I followed the steps of this howto.

First, the graphical installation failed to initialize, so tried

```
sudo ./setup.sh -console
```

instead. I did not mess with any settings, just selected the defaults.

The installation failed.

Next step was installing the Java Runtime Environment:

```
sudo apt-get install sun-java6-jre
```

Didn't help.

Then I googled, and found this:

[http://coort.wordpress.com/2008/02/29/how-to-lotus-notes-801-on-ubuntu-804-alpha5/](http://coort.wordpress.com/2008/02/29/how-to-lotus-notes-801-on-ubuntu-804-alpha5/)

Didn't work for me either.

The install.log at the root home folder ends with this line:

Tried installing notes 8.0 on a fresh install of hardy (8.04). The installation was almost vanilla, I just enabled the NVIDIA drivers and installed the nvidia-settings package.

I followed the steps of this howto.

First, the graphical installation failed to initialize, so tried

sudo ./setup.sh -console

instead. I did not mess with any settings, just selected the defaults.

The installation failed.

Next step was installing the Java Runtime Environment:

sudo apt-get install sun-java6-jre

Didn't help.

Then I googled, and found this:

[http://coort.wordpress.com/2008/02/29/how-to-lotus-notes-801-on-ubuntu-804-alpha5/](http://coort.wordpress.com/2008/02/29/how-to-lotus-notes-801-on-ubuntu-804-alpha5/)

This workaround didn't work for me either.

The last line of my install.log at the root folder is the following:

```
(May 5, 2008 10:05:00 AM), null, com.ibm.lex.lap.is11.PanelLAPUniversalSilentImpl, err, License not accepted

```

So, no working Notes 8 for me at the moment!

---

### Post by vehka on 2008-05-05
Update:

Managed to install Notes 8.0 on a fresh install of Hardy, thanks to a comment on this post:

[http://www.offthehill.org/articles/2007/12/12/installing-lotus-notes-8-on-ubuntu-710-gutsy/](http://www.offthehill.org/articles/2007/12/12/installing-lotus-notes-8-on-ubuntu-710-gutsy/)

1. First, I removed the old, failed installation attempt (deleted the files in /root/ and /opt/bin/).

2. Installed libstdc++5:

```
apt-get install libstdc++5
```

3. Then I encountered the Issue #1B, which was resolved according to the instructions in the first post.

4. During the install, I unchecked all the optional product components.

5. Fixed the permissions like this:

```
cd /opt/ibm/lotus/notes
sudo chmod +x lnotes
sudo chmod 755 /etc/lotus/notes/data/shared/ -R
sudo chmod 755 /opt/ibm -R
```

Then I tried to start the client from the applications menu, but nothing happened.

Next, I removed the lotus folder from my home folder:

```
cd ~
sudo rm -rf lotus
```

Tried again starting the application, and now it worked!

Except after entering the settings, I got the following error:

> Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.

So far, everything still seems to be working fine.

---

### Post by soxs on 2008-05-05
thisis because you removed lotus folder in ~/
You should try creating a new one and give 0777 permission.

---

### Post by fatbuttlarry on 2008-05-05
Great progress!  I'll need to create a new thread for 8.04 and cross-link.

-Tres

---

### Post by dhjohnson on 2008-05-05
> **soxs said:**
> thisis because you removed lotus folder in ~/
You should try creating a new one and give 0777 permission.

I chmodded the directory and am still getting the error message.

---

### Post by hazics on 2008-05-06
Add the directory ~/.mozilla/eclipse
[IBM Notes/Domino 8 Forum Notes 8.0.1 on Ubuntu 8.04]("http://www-10.lotus.com/ldd/nd8forum.nsf/DateAllThreadedWeb/c7e7d69f417c01d78525743e006b39c3?OpenDocument")

---

### Post by vehka on 2008-05-06
Yes, creating the eclipse-directory with 700 permissions worked, no more error dialogues when starting notes. So far, everything seems to work. Excellent!

---

### Post by fatbuttlarry on 2008-05-06
Thanks!

---

### Post by crtlbreak on 2008-05-07
To uninstall Lotus Notes 8 from your machine you will need to still be logged in as %username (your username - not root) and perform the following

cd /opt/ibm/lotus/notes/_uninst
sudo ./uninstaller.bin


Have not yet got it to work on 8.04 although worked fine on Gutsy.

---

### Post by fatbuttlarry on 2008-05-07
Good advice, thanks!

-Tres

---

### Post by crtlbreak on 2008-05-07
Good Day tres - I forgot to thank you in the last message for your help!.
by the way - I think it might also be important to know which tar file is being used.
Are you using C14SXEN.tar?
regards

---

### Post by fatbuttlarry on 2008-05-07
That is a very good point ctrlbreak.

The original how-to was written on the 8.0 Trial, C13T7ML.zip.

Installing another version will cause discrepancies in the how-to. A colleague recently downloaded "Lotus Notes Client 8.0.1 Linux Full", and that should probably be the target version for the how-to, if updated.

Future questions should include the **client version number**, and whether it is a **Trial or Full Install**.  If someone can iron this out on 7.10 from a fresh install it will guarantee the greatest success rate.

A VMWare instance would probably be the easiest method.

For the record, who's running what?

-Tres

---

### Post by vehka on 2008-05-08
I've been using a full install package called "C13NCEN.tar", titled "Lotus Notes Client 8.0 English (C13NCEN)".

---

### Post by crtlbreak on 2008-05-12
> **vehka said:**
> I've been using a full install package called "C13NCEN.tar", titled "Lotus Notes Client 8.0 English (C13NCEN)".

Good Day vehka - thank you - 
and the understanding is that you are using 8.04 or 7.10? 
regards
crtlbreak (not hijacking your threads tres!)

---

### Post by fatbuttlarry on 2008-05-12
> **crtlbreak said:**
> (not hijacking your threads tres!)

Its a collaboration, the more hijacking the merrier!! :)

-Tres

---

### Post by vehka on 2008-05-13
> **crtlbreak said:**
> understanding is that you are using 8.04 or 7.10? 


As you can see in my post above, I was installing Notes on 8.04. =)

---

### Post by fatbuttlarry on 2008-05-14
> **vehka said:**
> As you can see in my post above, I was installing Notes on 8.04. =)

Correct... pg. 6

> **vehka said:**
> Tried installing notes 8.0 on a fresh install of hardy (8.04)...

---

### Post by crtlbreak on 2008-05-15
Morning Tres
My obervations (and trial and error realities) are as follows
[LIST=1]
[*]There was no way for me to get Notes Client V7.x running on Ubuntu - due to Notes Client V7 wants to see Mozilla rather than Firefox by Mozilla - so after a week of fooling around with trying to install Mozilla on Ubuntu I gave up! and I dont like losing to these issues!
[*] Lotus Notes C14SXEN does not run on 8.04 Hefty - there is a permission issue in the /opt/ibm/lotus/notes/../notes file (which installs as root) and that file should not be changed as it is a common file. This delivers an error when starting
[*] C14SXEN on 8.04 (the one that you have sucessfully installed) has not yet worked for me.
[*]The installation of success for me is C19U2En on 7.10 - installed but not running at present.[/LIST]

There are a few Lotus Notes Client install files that are doing the rounds 
[LIST=2]
[*]C93D1NA.zip (v7.0) - dont bother on newer distributions such as 7.10 and 8.04 due to the Mozilla Browser issue - See Below
[*]C14SXEN.tar (v8.0) - this I have installed successfully on 7.10 (as per your detailed instructions) and it connects fine to Domino Server
[*]C19U2EN.tar (v8.0.1) have installed successfully but not yet got it to run successfully - I get the "CLFRJ0010E: Notes initialization failed" error when I try and run it.[/LIST]

I am going to (once I have made a harddrive recovery image of my present working machine) re-install 7.10 as fresh from scratch and try install C14SXEN.tar as you have done - then repeat 7.10 again as fresh and attempt C19U2EN.tar. Watch this space for more trial and errors.
Regards
crtlbreak

---

### Post by Cloud79 on 2008-05-17
Anyone got it to work on 64 bit hardy?

Seems to be problems with missing 32 bit libraries! 
Maybe 8.5 will be 64 bit native? Anyone got a release date for 8.5?

---

### Post by fatbuttlarry on 2008-05-19
> **crtlbreak said:**
> Morning Tres
My obervations (and trial and error realities) are as follows
[LIST=1]
[*]There was no way for me to get Notes Client V7.x running on Ubuntu - due to Notes Client V7 wants to see Mozilla rather than Firefox by Mozilla - so after a week of fooling around with trying to install Mozilla on Ubuntu I gave up! and I dont like losing to these issues!
[*] Lotus Notes C14SXEN does not run on 8.04 Hefty - there is a permission issue in the /opt/ibm/lotus/notes/../notes file (which installs as root) and that file should not be changed as it is a common file. This delivers an error when starting
[*] C14SXEN on 8.04 (the one that you have sucessfully installed) has not yet worked for me.
[*]The installation of success for me is C19U2En on 7.10 - installed but not running at present.[/LIST]

There are a few Lotus Notes Client install files that are doing the rounds 
[LIST=2]
[*]C93D1NA.zip (v7.0) - dont bother on newer distributions such as 7.10 and 8.04 due to the Mozilla Browser issue - See Below
[*]C14SXEN.tar (v8.0) - this I have installed successfully on 7.10 (as per your detailed instructions) and it connects fine to Domino Server
[*]C19U2EN.tar (v8.0.1) have installed successfully but not yet got it to run successfully - I get the "CLFRJ0010E: Notes initialization failed" error when I try and run it.[/LIST]

I am going to (once I have made a harddrive recovery image of my present working machine) re-install 7.10 as fresh from scratch and try install C14SXEN.tar as you have done - then repeat 7.10 again as fresh and attempt C19U2EN.tar. Watch this space for more trial and errors.
Regards
crtlbreak


This is very kind of you.  Thanks for the detailed response, it is very helpful!

-Tres

---

### Post by Snocrash on 2008-05-24
Hi All,

I am note able to get this running.

I am not running the official Ubuntu release. I am running TheeMahn's Ultimate Edition 1.8 X 64, which is built off of Hardy 8.04 x 64.

[Ultimate Edition Linux]("http://ultimateedition.info/")

Anyway, When I follow the instruction in this forum, The install gets to 73% and I get the following error...
------------------------

An error has occurred. See the log file
/root/lotus/notes/data/workspace/logs/error-log-0.xml.
-------------------------

Followed by....

----------------------------
Provisioning process failed. Process failed to launch or was terminated before status could be determined.

Lotus Notes 8.0.1 installation failed. See /opt/ibm/lotus/notes/framework/installer_logs/framework_install.log for more information. Click Finish to exit.
----------------------------

The last entry in error-log-0.xml is as follows....

-------------------------
2008-05-24T08:40:10.183-05:00	SEVERE	Application error	org.eclipse.osgi
-------------------------

However, I can start eclipse just fine.....

The other log file does not exist.

I am not sure which version on notes I am installing because my Admin changes the name to LinuxClient.tar. But he just downloaded it for me yesterday so it should be the current version.

Any ideas????

Guess I will keep Note 6.5 running in Crossover for a while longer :(

Thanks,

-Sno

---

### Post by fatbuttlarry on 2008-05-26
Snocrash, thanks for your feedback.

I haven't read any success stories for 8.04 yet, so I'm guessing distros built from 8.04 will have problems as well.

This thread is an ARCHIVE for 7.10, so downgrading your OS is a temporarily solution.

I have not yet upgraded to 8.04 in the workplace, so I don't have the means to test this.  Subscribe to this thread, and its likely that a solution, or a link to one will surface shortly.

To subscribe:  **Edit >> Go Advanced >> Thread Subscription**

The error you are seeing is not specific enough to pin-point the problem, but in short, the Eclipse version that you use --  an IDE to develop Java applications -- is separate from the Eclipse framework that comes bundled with Lotus Notes.  Chances are it is a class-path or permission issue within the Lotus application folder.  Let us know if you get to the root of it!

:guitar:

-Tres

---

### Post by Coort on 2008-05-29
Actually i have upgraded my gutsy to hardy (alpha) with notes 8.0, installed. There was some problem, as release approached it became more stable the i've upgraded to notes 8.01.
My experience is that notes 8.01 runs well on Hardy, although i ddn't a fresh install but an upgrade.

NOTE: i work ONLY with notes FULL CLIENTS. So no experience with trials.

---

### Post by crtlbreak on 2008-05-29
hmmm - i think having to install notes 8.0.1 on gutsy and then upgrade is like going from new york to florida via ohio.
:lolflag:

I think I need some more time and a few more attempts.

	:roll:

---

### Post by fatbuttlarry on 2008-05-29
Agreed, and agreed.

Glad to see there's a success story.  Just a matter of getting it accomplished from scratch now, that's all!

-Tres

---

### Post by crtlbreak on 2008-05-30
I have also found a peculiar oddity.
After installing Lotus Notes 8.0.1 on Hardy 8.04 (lost count of the amount) my blackberry has been giving connectivity issues - after uninstalling lotus notes client v 8.0.1 the connectivity returned for BarryBackup and MultiSync.
Now I am puzzled :confused:

---

### Post by fatbuttlarry on 2008-05-30
Ctrl - 

Are you referring to USB/BlueTooth connectivity, or BEZ-type connectivity?  That is definitely strange!

-Tres

---

### Post by crtlbreak on 2008-05-31
Apologies - I was so deeply involved.
It is the USB 2.0 type connection.

---

### Post by fatbuttlarry on 2008-05-31
So the tool you use to manage contacts/content on your blackberry malfunctioned during the time the Lotus Notes 8.0.1 application was installed on Ubuntu 8.04 distro?

Is the tool similar to BitPim?  I am not extremely familiar with the open source phone tools yet.

-Tres

---

### Post by Coort on 2008-06-03
Uhmm...i don't know if this is active even on linux, but notes 8 should have native support for some hand-held devices, so it is possible that messes up some sync software.
Note that i have seen this syncronization working only on windows, i don't know if this feature has been ported to linux.

---

### Post by fatbuttlarry on 2008-06-03
That could be the missing link.  Thanks coort!

Couldn't find anything with Google about it so we'll have to wait for further feedback.

:popcorn:

-Tres

---

### Post by Coort on 2008-06-08
Just some information about notes and Ubuntu: actually there's a Public Beta 1 of Lotus Notes 8.5 that have official support from IBM, and have .deb packages to install.
I've tried to install this version on a fresh 8.04 install, ad it works like a charm (at least the install).

---

### Post by crtlbreak on 2008-06-09
Thank you Coort - I will have a look for that one and give it a try.
It will be good to hear some people having installed and run it ok - also the finer details like "import" and "attachments" which dont work in the unsupported versions of Notes - well at least I havent got those extras to work. :confused:
So back to the drawing board!

---

### Post by fatbuttlarry on 2008-06-09
> **Coort said:**
> Just some information about notes and Ubuntu: actually there's a Public Beta 1 of Lotus Notes 8.5 that have official support from IBM, and have .deb packages to install.
I've tried to install this version on a fresh 8.04 install, ad it works like a charm (at least the install).

Great news, provide a link if you can!!!

---

### Post by Cloud79 on 2008-06-10
[https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?lang=en_US&source=swg-lnd85](https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?lang=en_US&source=swg-lnd85)

Tried it on x64 8.04, didnt work (had to copy files manually as it is meant for x86)

---

### Post by Coort on 2008-06-10
> **Cloud79 said:**
> [https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?lang=en_US&source=swg-lnd85](https://www14.software.ibm.com/webapp/iwm/web/preLogin.do?lang=en_US&source=swg-lnd85)

Tried it on x64 8.04, didnt work (had to copy files manually as it is meant for x86)

Doh!

Another hitn, download the readme PDF, it should contains some useful hints and know bugs.

---

### Post by Cloud79 on 2008-06-11
> **Coort said:**
> Doh!

Another hitn, download the readme PDF, it should contains some useful hints and know bugs.

I don't think that they support x64, at least not in the beta.

---

### Post by hackmeister on 2008-06-11
Great news! Going to try this out tonight.

---

### Post by Rever75 on 2008-07-02
OK,
  Not sure if anyone can help me here. I have installed 8.0.1 into my Hardy Desktop. All seems to be working except i cannot receive HTML e-mails. I get this error. 

```
The value of MOZILLA_FIVE_HOME : /usr/lib/xulrunner-addons, is not a correct path of Mozilla verion 1.8.* or later. DOMBrowser can not work.
```
My friend with the same install is not having any issues.

---

### Post by crtlbreak on 2008-07-03
It seems that Lotus Notes is looking for Mozilla - when it should be looking for firefox - there has to be a .conf file to tell Lotus Notes to look for Firefox rather than Mozilla.
Installing Mozilla is probably not a clever option.

---

### Post by Rever75 on 2008-07-03
Well I solved the problem by pointing my MOZILLA_FIVE_HOME to /usr/lib/xulrunner. I did this by putting a script in /etc/X11/Xsession.d/ telling it to export MOZILLA_FIVE_HOME=/usr/lib/xulrunner. I did not need Mozilla installed it was looking for the runtime environment to display HTML pages.

---

### Post by fatbuttlarry on 2008-07-05
> **Rever75 said:**
> Well I solved the problem by pointing my MOZILLA_FIVE_HOME to /usr/lib/xulrunner. I did this by putting a script in /etc/X11/Xsession.d/ telling it to export MOZILLA_FIVE_HOME=/usr/lib/xulrunner. I did not need Mozilla installed it was looking for the runtime environment to display HTML pages.

Good work.  I would have recommend creating a symbolic link from /usr/lib/xulrunner-addons to /usr/lib/xulrunner.

Another option is to set that ENV variable in the launch script for Lotus Notes.

Great detailed post, thank you!!!

Cheers.

-FBL

---

### Post by fatbuttlarry on 2008-07-22
Semi-related: My coworker did some work with [Domino 8 Server]("http://fatbuttlarry.blogspot.com/2008/07/domino-8-ubuntu-quickstart.html") for those interested. (This version is unsupported on Ubuntu).

-Tres

---

