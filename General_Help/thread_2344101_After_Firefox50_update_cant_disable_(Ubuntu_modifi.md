---
title: "After Firefox50 update cant disable (Ubuntu modifications plugin)??"
date: 2016-11-22
forum: General Help
---

### Post by funnyfuntimes on 2016-11-22
On Ubuntu 14.04, have not yet tested on my 16.04 systems. 

After doing usual system update via apt-get i got the new Firefox 50,
 i can no longer disable (ubuntu modifications plug-in) 
if attempting this, all i get in a constant blank white screen within the browser window?

is there a workaround?
For security purposes i run Firefox with minimal plug-ins.

---

### Post by &amp;KyT$0P# on 2016-11-22
Have you tried [turning off hardware acceleration in Firefox]("https://support.mozilla.org/kb/upgrade-graphics-drivers-use-hardware-acceleration#w_turning-off-hardware-acceleration")?

Have you tried the [official Mozilla build]("https://www.mozilla.org/firefox/all/") of Firefox?

---

### Post by #&amp;thj^% on 2016-12-01
[COLOR=#ff0000]***PLEASE NOTE THIS:***[/COLOR]
Ubuntu modifications plugin Brings in this:
  xul-ext-ubufox:

   >  Ubuntu-specific configuration defaults and apt support for Firefox.

    Adds Ubuntu-specific modifications to Firefox.

    Integrates the browser with Ubuntu to:

        Enable searching for missing plugins from Ubuntu software catalog
        Add the following options to the Help menu:
            Get help on-line
            Help translating Firefox
            Ubuntu Release Notes
        Set homepage to Ubuntu Start Page
        Display a restart notification after upgrading Firefox
        Add ask.com to the search engines.

    You can uninstall this if you prefer to use a pristine Firefox install._** But you will lose the above mentioned.**_

Homepage: [https://launchpad.net/ubufox](https://launchpad.net/ubufox)

I have uninstalled it with no bad side effects.

This will be removed:
```
sudo apt remove  xul-ext-ubufox*
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xul-ext-ubufox' for glob 'xul-ext-ubufox*'

The following packages will be REMOVED:
  xul-ext-ubufox
```

```
 apt policy  xul-ext-ubufox
xul-ext-ubufox:
  Installed: (none)
  Candidate: 3.2-0ubuntu1
  Version table:
     3.2-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu yakkety/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu yakkety/main i386 Packages
        100 /var/lib/dpkg/status


```
It is fair to mention **your milage may vary**.
So look carefully at what will be removed...if you choose this route.
Regards

---

