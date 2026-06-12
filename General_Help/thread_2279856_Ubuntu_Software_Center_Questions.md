---
title: "Ubuntu Software Center Questions"
date: 2015-05-26
forum: General Help
---

### Post by drm200 on 2015-05-26
I'm running Ubuntu 14.04 (64 bit) with all the latest updates.

Recently I tried to install NetActView by downloading the deb package (netactview_0.6.4-1_amd64.deb) from the program web site and installing this package using the Ubuntu Software Center.

The install worked without problem and the program functions as expected.  I decided however, I wanted to remove the package.  I went back to the Ubuntu Software Center and was unable to find this package using search.  I then clicked on "history" in the software center and was surprised that there was no history of NetActView of ever having been installed.

If I double clicked on the original deb package again, the software center confirms that NetActView is installed but offers only to re-install.  It does not offer to remove the installation.  If I search the Ubuntu Software Center again for the letters "net" ... it again fails to find the installed package.

I then uninstalled NetActView using the command: sudo apt-get remove --purge netactview

This uninstalled the package.  I then reinstalled the same package again using the Ubuntu Software Center and reconfirmed that the Ubuntu Software Center "history" fails to identify that NetActView has been installed.


So my question is this:  Why does the Ubuntu Software Center fail to find a package that has been installed and why does it not show up in history?

More importantly, how do I know that other programs have not been maliciously installed if I am unable to look at the history and find recent changes?  Is there another method to view history that would provide a definitive list of changes?

---

### Post by corti-nico on 2015-05-26
You can see all the log of your installed package with the command:
```

cat /var/log/apt/history.log

```

I know that it is not a fancy way to see it, but it's of sure the most complete list.

---

### Post by drm200 on 2015-05-26
> **corti-nico said:**
> You can see all the log of your installed package with the command:
```

cat /var/log/apt/history.log

```

I know that it is not a fancy way to see it, but it's of sure the most complete list.


I ran the command:  cat /var/log/apt/history.log

It is interesting because it does NOT show that I installed the package.  Yet I know the package is installed because it runs and works.

This is the last three entries in my log file:

Start-Date: 2015-05-26  19:11:55
Commandline: apt-get remove --purge netactview
Purge: netactview:amd64 (0.6.4-1)
End-Date: 2015-05-26  19:11:59


Start-Date: 2015-05-26  19:13:07
Commandline: apt-get autoremove
Remove: libgconf2-4:amd64 (3.2.6-0ubuntu2)
End-Date: 2015-05-26  19:13:08


Start-Date: 2015-05-26  19:21:22
Commandline: aptdaemon role='role-install-file' sender=':1.107'
Install: libgconf2-4:amd64 (3.2.6-0ubuntu2, automatic)
End-Date: 2015-05-26  19:21:24

      The first entry is when I removed the package "netactview".   The second entry is when I auto-removed the remaining library libgconf2.   The third entry is the libgconf2 being reinstalled after i had re-installed the "netactview" package.   So missing is the line showing I had reinstalled "NetActView".

---

### Post by corti-nico on 2015-05-26
Are there other entries before the 3 that you have posted?
Anyway for a more detailed log have a view at
```

cat /var/log/dpkg.log

```

---

### Post by drm200 on 2015-05-26
> **corti-nico said:**
> Are there other entries before the 3 that you have posted?
Anyway for a more detailed log have a view at
```

cat /var/log/dpkg.log

```

Yes there are many entries prior to the 3 ..... but I did the successful purge at 19:11:55 and there is nothing really relevant prior to that time.  The previous install looks the same as the install that happened after the purge.

[COLOR=#000000]Below is the log of the cat/var/log/dpkg.log (I've eliminated data prior to 19:11).  You can see the re-install that began at 19:21.  [/COLOR][COLOR=#000000]The dpkg log shows that NetActView was installed at 19:21:32 ... 

So back to my original question:

Why does Ubuntu Software Manager History fail to show that NetActView has been installed and fail to find it when searched?    Is this normal that software that is installed by the Software Center fails to show up as installed when searched?   It also results in the software center providing no means or method to remove the software (since it can not be found as installed).

I would also worry that this is a security concern ... 
[/COLOR]
[COLOR=#000000]
[/COLOR]

[COLOR=#000000]cat/var/log/dpkg.log :[/COLOR]

```
2015-05-26 19:11:55 startup packages purge
2015-05-26 19:11:55 status installed netactview:amd64 0.6.4-1
2015-05-26 19:11:56 remove netactview:amd64 0.6.4-1 <none>
2015-05-26 19:11:56 status half-configured netactview:amd64 0.6.4-1
2015-05-26 19:11:56 status half-installed netactview:amd64 0.6.4-1
2015-05-26 19:11:56 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-05-26 19:11:56 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-05-26 19:11:56 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-05-26 19:11:56 status half-installed netactview:amd64 0.6.4-1
2015-05-26 19:11:56 status triggers-pending bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-05-26 19:11:56 status half-installed netactview:amd64 0.6.4-1
2015-05-26 19:11:56 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-05-26 19:11:56 status config-files netactview:amd64 0.6.4-1
2015-05-26 19:11:56 status config-files netactview:amd64 0.6.4-1
2015-05-26 19:11:56 status config-files netactview:amd64 0.6.4-1
2015-05-26 19:11:56 status not-installed netactview:amd64 <none>
2015-05-26 19:11:56 trigproc man-db:amd64 2.6.7.1-1ubuntu1 <none>
2015-05-26 19:11:56 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-05-26 19:11:56 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-05-26 19:11:56 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 <none>
2015-05-26 19:11:56 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-05-26 19:11:56 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-05-26 19:11:56 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 <none>
2015-05-26 19:11:56 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-05-26 19:11:56 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-05-26 19:11:56 trigproc bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1 <none>
2015-05-26 19:11:56 status half-configured bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-05-26 19:11:56 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-05-26 19:11:57 trigproc mime-support:all 3.54ubuntu1.1 <none>
2015-05-26 19:11:57 status half-configured mime-support:all 3.54ubuntu1.1
2015-05-26 19:11:57 status installed mime-support:all 3.54ubuntu1.1
2015-05-26 19:13:07 startup packages remove
2015-05-26 19:13:07 status installed libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:13:07 remove libgconf2-4:amd64 3.2.6-0ubuntu2 <none>
2015-05-26 19:13:07 status half-configured libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:13:07 status half-installed libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:13:07 status config-files libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:13:07 status config-files libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:13:08 status config-files libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:13:08 status not-installed libgconf2-4:amd64 <none>
2015-05-26 19:21:22 startup archives unpack
2015-05-26 19:21:22 install libgconf2-4:amd64 <none> 3.2.6-0ubuntu2
2015-05-26 19:21:22 status half-installed libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:21:22 status unpacked libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:21:22 status unpacked libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:21:23 startup packages configure
2015-05-26 19:21:23 configure libgconf2-4:amd64 3.2.6-0ubuntu2 <none>
2015-05-26 19:21:23 status unpacked libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:21:23 status half-configured libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:21:23 status installed libgconf2-4:amd64 3.2.6-0ubuntu2
2015-05-26 19:21:30 startup archives install
2015-05-26 19:21:30 install netactview:amd64 <none> 0.6.4-1
2015-05-26 19:21:30 status half-installed netactview:amd64 0.6.4-1
2015-05-26 19:21:30 status triggers-pending gnome-menus:amd64 3.10.1-0ubuntu2
2015-05-26 19:21:30 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-05-26 19:21:30 status half-installed netactview:amd64 0.6.4-1
2015-05-26 19:21:30 status triggers-pending bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-05-26 19:21:30 status half-installed netactview:amd64 0.6.4-1
2015-05-26 19:21:30 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-05-26 19:21:31 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-05-26 19:21:31 status unpacked netactview:amd64 0.6.4-1
2015-05-26 19:21:32 status unpacked netactview:amd64 0.6.4-1
2015-05-26 19:21:32 configure netactview:amd64 0.6.4-1 0.6.4-1
2015-05-26 19:21:32 status unpacked netactview:amd64 0.6.4-1
2015-05-26 19:21:32 status half-configured netactview:amd64 0.6.4-1
2015-05-26 19:21:32 status triggers-awaited netactview:amd64 0.6.4-1
2015-05-26 19:21:32 trigproc gnome-menus:amd64 3.10.1-0ubuntu2 3.10.1-0ubuntu2
2015-05-26 19:21:32 status half-configured gnome-menus:amd64 3.10.1-0ubuntu2
2015-05-26 19:21:32 status installed gnome-menus:amd64 3.10.1-0ubuntu2
2015-05-26 19:21:32 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 0.22-1ubuntu1
2015-05-26 19:21:32 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-05-26 19:21:32 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-05-26 19:21:32 trigproc bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1 0.5.1+14.04.20140409-0ubuntu1
2015-05-26 19:21:32 status half-configured bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-05-26 19:21:32 status installed netactview:amd64 0.6.4-1
2015-05-26 19:21:32 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
2015-05-26 19:21:32 trigproc mime-support:all 3.54ubuntu1.1 3.54ubuntu1.1
2015-05-26 19:21:32 status half-configured mime-support:all 3.54ubuntu1.1
2015-05-26 19:21:32 status installed mime-support:all 3.54ubuntu1.1
2015-05-26 19:21:32 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-05-26 19:21:32 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-05-26 19:21:32 status installed man-db:amd64 2.6.7.1-1ubuntu1
```

---

### Post by drm200 on 2015-06-02
I'd still like an understanding of this problem.  

[COLOR=#000000]The problem is:

A deb package that I installed via the Ubuntu Software Manager fails to show up in Ubuntu Software Manager History.  It also fails to show up during search. Because there is no method to find the package after installation, there is no method to remove it using the Ubuntu Software manager>

Is this a bug that needs resolution or is this considered acceptable for Ubuntu 14.04?

I consider this also to be a security concern because a deb package could be installed nefariously ... and the user would not be able to see this using the history in the Ubuntu Software manager.

I'd like to close this as "solved" but can not do so until I understand if this is a feature or bug.

[/COLOR]

---

### Post by ian-weisser on 2015-06-02
Software Center should be able to locate and uninstall any installed .deb package on your system, regardless of install application.

I think you have independently discovered bug #1346872: [https://bugs.launchpad.net/software-center/+bug/1346872](https://bugs.launchpad.net/software-center/+bug/1346872)
If you agree that seems to be the problem, please click on the '*Does this bug affect you?*' link on the bug report.

If you don't have a Launchpad account, you will be prompted to create one. It's free.
You should NOT leave a 'me too' comment, unless you have useful information to add. Clicking on the link is enough to move the process forward.

---

