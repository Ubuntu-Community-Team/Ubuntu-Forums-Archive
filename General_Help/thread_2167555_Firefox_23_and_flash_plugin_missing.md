---
title: "Firefox 23 and flash plugin missing"
date: 2013-08-14
forum: General Help
---

### Post by mortuk on 2013-08-14
Having severe issues getting flash working after upgrading firefox.

I have tried copying the flash .so file into various locations suggested by people here and on google but no joy.

I have tried removing both firefox and flash and reinstalling from synaptic.

I have tried the firefox plugin finder service which just returns 'No suitable plugins were found'.

Flash is working fine in Chrome, just wont work in Firefox and its driving me nuts, any ideas?

---

### Post by A Bunny on 2013-08-14
You could try installing gnash and browser-plugin-gnash. That got flash working in Midori and I think it will get flash working in Firefox as well.

Hope this helps.

---

### Post by Gilad_Pellaeon on 2013-08-14
Have you tried resetting your firefox profile by deleting the profile data (including profiles.ini) in /.mozilla/firefox and see if it will detect the installled adobe flash plugin then? Because it almost sounds to me like your firefox profile data is messed up somehow and since Google Chrome uses it's own internal flash plugin called Pepperflash that's why it works.

---

### Post by mortuk on 2013-08-20
I'll try deleting my profile, see if that works.

And will try gnash if that doesn't work, although seems like normal flash should just work, just need to confirm exactly where I should be copying the .so file

---

### Post by daniel-matthis on 2013-09-12
I have same issue. deleting the profile seems a little heavy handed though. The issue seems to be that the logical link for the flash plugin is not in /usr/lib/firefox-addon/plugins

Here is my work around:

What I have done to resolve it on my Ubuntu 13.04 x86_64 system.

1: Download Adobe Flash Player 11.2 (tar.gz) from Adobe website. [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect)
2: From command line
> $ cd {location of download}
$ sudo mkdir /opt/flash_11
$ sudo tar -xvf  install_flash_player_11_linux.x86_64.tar.gz -C /opt/flash_11

3: Now you can create a symbolic link to the Flash plugin
> $ cd /usr/lib/firefox-addons/plugins
$ sudo ln -s /opt/flash_11/libflashplayer.so 

Now you need ot restart Firefox and test your flash.

Not sure where the issue came in though. If Firefox 23 just dropped the plugin or if something with the plugin on Ubuntu is at issue.

---

### Post by philinux on 2013-09-12
No need to delete straight away. Back up bookmarks is a good idea though.

1. close firefox and remove all flash .so files that were manually set up.
2. just rename the firefox profile folder from .mozilla to .mozilla.backup
3. start firefox which will create a new profile folder. Then see if flash can be installed/reinstalled.

If the above works then it's simply a matter of restoring bookmarks from the backup and setting up any needed addons.

Alternatively try from terminal 

```
firefox  --safe-mode
```

---

### Post by Mark_Solaris on 2013-09-16
Firefox moved the tree into the browser directory, see this link for details:   [http://www.ghacks.net/2013/05/15/why-you-may-have-lost-access-to-plugins-or-extensions-in-firefox-21/](http://www.ghacks.net/2013/05/15/why-you-may-have-lost-access-to-plugins-or-extensions-in-firefox-21/)  Then do this: ```
 host:/ root# cd /usr/lib/firefox
``````
host:/usr/lib/firefox root# cp -r plugins browser/.
``````
host:/usr/lib/firefox root# ls -al browser/plugins/ 
``` Anyone else notice the markup lang here is fubar? SIgh.

---

