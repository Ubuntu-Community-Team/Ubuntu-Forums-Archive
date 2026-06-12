---
title: "flash content invisible on Firefox"
date: 2016-12-14
forum: General Help
---

### Post by ardouronerous on 2016-12-14
[ATTACH=CONFIG]272703[/ATTACH]

Flash content isn't visible on Firefox, however, Chromium doesn't have this problem.
Please refer to the attachment for symptoms of the problem.

I'm running Xubuntu 16.04.

---

### Post by &amp;KyT$0P# on 2016-12-14
Does that happen in Firefox [Safe Mode]("http://kb.mozillazine.org/Safe_Mode")?
Does it occur in a new, clean [profile]("http://kb.mozillazine.org/Profile") with no extensions added and all defaults?

---

### Post by ardouronerous on 2016-12-14
[ATTACH=CONFIG]272707[/ATTACH]
I've tried it on SafeMode and creating a new fresh profile, it's the same result, see attachment.

---

### Post by &amp;KyT$0P# on 2016-12-14
Chromium uses a different Flash plugin than Firefox.  What if you use that one in Firefox?

Quit Firefox before proceeding.

Assuming your Flash is the [FONT=Courier New]adobe-flashplugin[/FONT] package from the Canonical Partners repository, run these commands in Terminal -
```
sudo apt-get --no-install-recommends install browser-plugin-freshplayer-pepperflash
sudo update-alternatives --remove-all flash-mozilla.so
sudo update-alternatives --install /usr/lib/mozilla/plugins/flashplugin-alternative.so mozilla-flashplugin /usr/lib/browser-plugin-freshplayer-pepperflash/libfreshwrapper-flashplayer.so 50
```

Now select freshwrapper/PPAPI Flash with this command -
```
sudo update-alternatives --config mozilla-flashplugin
```
Choose the number associated with [FONT=Courier New]libfreshwrapper-flashplayer.so[/FONT] (manual mode).

Are you able to see Flash content now?

If not, you can get back to where you were by -
1) Quit Firefox and re-run ```
sudo update-alternatives --config mozilla-flashplugin
```
But this time use the number associated with [FONT=Courier New]libflashplayer.so[/FONT] (manual mode) instead.

2) Uninstall freshwrapper -
```
sudo apt-get purge browser-plugin-freshplayer-pepperflash
```

---

### Post by ardouronerous on 2016-12-15
> **halogen2 said:**
> Chromium uses a different Flash plugin than Firefox.  What if you use that one in Firefox?

Quit Firefox before proceeding.

Assuming your Flash is the [FONT=Courier New]adobe-flashplugin[/FONT] package from the Canonical Partners repository, run these commands in Terminal -
```
sudo apt-get --no-install-recommends install browser-plugin-freshplayer-pepperflash
sudo update-alternatives --remove-all flash-mozilla.so
sudo update-alternatives --install /usr/lib/mozilla/plugins/flashplugin-alternative.so mozilla-flashplugin /usr/lib/browser-plugin-freshplayer-pepperflash/libfreshwrapper-flashplayer.so 50
```

Now select freshwrapper/PPAPI Flash with this command -
```
sudo update-alternatives --config flashplugin-alternative
```
Choose the number associated with [FONT=Courier New]libfreshwrapper-flashplayer.so[/FONT] (manual mode).

Are you able to see Flash content now?

No, that didn't work. Here's the results from the Terminal;

```
~$ sudo apt-get --no-install-recommends install browser-plugin-freshplayer-pepperflash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libevent-core-2.0-5 libevent-pthreads-2.0-5
Recommended packages:
  pepperflashplugin-nonfree
The following NEW packages will be installed:
  browser-plugin-freshplayer-pepperflash libevent-core-2.0-5
  libevent-pthreads-2.0-5
0 upgraded, 3 newly installed, 0 to remove and 10 not upgraded.
Need to get 442 kB of archives.
After this operation, 1,498 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main i386 libevent-core-2.0-5 i386 2.0.21-stable-2 [73.9 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/main i386 libevent-pthreads-2.0-5 i386 2.0.21-stable-2 [5,482 B]
Get:3 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 browser-plugin-freshplayer-pepperflash i386 0.3.4-3 [362 kB]
Fetched 442 kB in 3s (117 kB/s)                                 
Selecting previously unselected package libevent-core-2.0-5:i386.
(Reading database ... 260462 files and directories currently installed.)
Preparing to unpack .../libevent-core-2.0-5_2.0.21-stable-2_i386.deb ...
Unpacking libevent-core-2.0-5:i386 (2.0.21-stable-2) ...
Selecting previously unselected package libevent-pthreads-2.0-5:i386.
Preparing to unpack .../libevent-pthreads-2.0-5_2.0.21-stable-2_i386.deb ...
Unpacking libevent-pthreads-2.0-5:i386 (2.0.21-stable-2) ...
Selecting previously unselected package browser-plugin-freshplayer-pepperflash.
Preparing to unpack .../browser-plugin-freshplayer-pepperflash_0.3.4-3_i386.deb ...
Unpacking browser-plugin-freshplayer-pepperflash (0.3.4-3) ...
Setting up libevent-core-2.0-5:i386 (2.0.21-stable-2) ...
Setting up libevent-pthreads-2.0-5:i386 (2.0.21-stable-2) ...
Setting up browser-plugin-freshplayer-pepperflash (0.3.4-3) ...
update-alternatives: using /usr/lib/browser-plugin-freshplayer-pepperflash/libfreshwrapper-flashplayer.so to provide /usr/lib/mozilla/plugins/flash-mozilla.so (flash-mozilla.so) in auto mode
Processing triggers for libc-bin (2.23-0ubuntu5) ...
~$ sudo update-alternatives --remove-all flash-mozilla.so
~$ sudo update-alternatives --install /usr/lib/mozilla/plugins/flashplugin-alternative.so mozilla-flashplugin /usr/lib/browser-plugin-freshplayer-pepperflash/libfreshwrapper-flashplayer.so 50
~$ sudo update-alternatives --config flashplugin-alternative
update-alternatives: error: no alternatives for flashplugin-alternative
```

> **halogen2 said:**
> If not, you can get back to where you were by -
1) Quit Firefox and re-run ```
sudo update-alternatives --config flashplugin-alternative
```
But this time use the number associated with [FONT=Courier New]libflashplayer.so[/FONT] (manual mode) instead.

2) Uninstall freshwrapper -
```
sudo apt-get purge browser-plugin-freshplayer-pepperflash
```

Running sudo update-alternatives --config flashplugin-alternative gave me an error;

```
~$ sudo update-alternatives --config flashplugin-alternative
update-alternatives: error: no alternatives for flashplugin-alternative
```

---

### Post by &amp;KyT$0P# on 2016-12-15
Sorry, I meant mozilla-flashplugin.  Fixed above.

---

### Post by ardouronerous on 2016-12-15
Method 1 and 2 didn't work, still the same result. NPAPI Flash for Firefox just got updated on my system, so it's now 24.0.0.186, but it's still the same, invisible content.  I'm not sure but, it must have been something I did a few months ago, because I just installed abobe-flashplugin via Canonical Partners on LiveCD of Xubuntu and it works.  Is there a way to purge all files and configurations of Firefox and Adobe Flash completely so I get a fresh install of both?

---

### Post by &amp;KyT$0P# on 2016-12-15
> **ardouronerous said:**
> Is there a way to purge all files and configurations of Firefox and Adobe Flash completely so I get a fresh install of both?
1) Run in Terminal
```
sudo apt-get purge adobe-flashplugin firefox browser-plugin-freshplayer-pepperflash
```

2) Clean up your home folder - **move** the following files and folders elsewhere -
```
~/.mozilla
~/.config/freshwrapper-data
~/.config/freshwrapper.conf
~/.adobe
~/.macromedia
```
(If any of those paths don't exist, don't worry about it.)  Also, delete [FONT=Courier New]~/.cache/mozilla/firefox[/FONT]

3) Since we played with the update-alternatives before, let's make sure that's cleaned up too -
```
sudo update-alternatives --remove-all flash-mozilla.so
sudo update-alternatives --remove-all mozilla-flashplugin
```


That should do it, I think.  If the problem returns upon reinstalling, the cause is likely external to Firefox and Flash.

---

### Post by ardouronerous on 2016-12-15
Didn't work.
Thanks for the help Halo.

What could be the problem?

---

### Post by ardouronerous on 2016-12-16
Good news, I've just opened my computer just now, Flash content on Firefox is visible again. :)
Was a reboot all that it needed?

Will be observing it though.

---

### Post by &amp;KyT$0P# on 2016-12-16
> **ardouronerous said:**
> Thanks for the help Halo.
You're welcome. :KS

> What could be the problem?
Not sure.  If it happens again, please start Firefox from a Terminal, run one invisible Flash content, and post the full terminal output here.

---

### Post by ardouronerous on 2016-12-16
So far so good, Flash content is visible. Based on m observations, the complete purging of Firefox and Adobe Flash and the reinstallation and rebooting seems to have fixed the issue.

Thanks for the help Halo, and Merry Christmas to you!  :D

 I guess I'll mark this as solved, until such a time that it happens again, I'll start Firefox on Terminal and paste the output on here.

---

