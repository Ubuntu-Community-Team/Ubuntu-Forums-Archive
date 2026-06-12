---
title: "Software Center Crashes On Start [Ubuntu Gnome 3.8]"
date: 2013-05-05
forum: General Help
---

### Post by BossDj on 2013-05-05
I'm running ubuntu gnome (*cough remix) with the 3.8 ppa.

I've been running this setup for a while, and have been using gdebi and synaptic, so I'm not TOO concerned, but I was under the impression that software-center should be up and running. Mine never has and still is not.

Here is the output:

2013-05-04 17:57:31,746 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-05-04 17:57:33,379 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Geoclue.Master was not provided by any .service files'
2013-05-04 17:57:33,871 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-05-04 17:57:33,886 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-05-04 17:57:33,919 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-05-04 17:57:33,919 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-05-04 17:57:33,991 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

(software-center:6663): Gdk-ERROR **: The program 'software-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 1850 error_code 9 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)

While the screen is up temporarily, the ad banner doesn't load, and some of the menu text looks very distorted.

I have attempted reinstalling, purging, clearing my ppa's (I don't know why), and clearing software-center's cache folder. Does anybody have any other suggestions?


Let me know what other info you need!

---

### Post by DisappearingOak on 2013-05-10
I have the exact problem. Menu text distorted. Frequently crashes. And window size is also small. in Gnome 3.8. But the ad banner loads, and can install stuff but often crashes/disappears.

---

### Post by DisappearingOak on 2013-05-10
After today's upgrades libgtk and some stuff got installed, and the menu text works now. Not sure if the crashes are solved.. will have to test. I'm purging software center to see if the window size issue goes away.

---

### Post by BossDj on 2013-05-12
After that update, the text menu distortion is gone, but it is still crashing.

Upon reinstall after purging, I get the text:

WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application.

This is already a bug.

---

### Post by Frogs Hair on 2013-05-13
3.8 is pretty much use at your own risk at the moment . I tried it twice and am back on 3.6. When I ran the ppa purge my last attempt on  5-11 many packages were not down graded and after a couple of hours in synaptic I decided that a re-installation would have been done already.  That is always a last resort, but I feel better about a clean installation than not repairing the system properly .

---

### Post by charlescarroll1 on 2013-05-28
Have we come to any solution other than doing a clean installation? 

I upgraded Ubuntu GNOME 13.04 to GNOME 3.8. Is there an easy way to reverse it?

---

### Post by eode on 2013-06-02
> **charlescarroll1 said:**
> Have we come to any solution other than doing a clean installation? 

I upgraded Ubuntu GNOME 13.04 to GNOME 3.8. Is there an easy way to reverse it?

You can use the awesome ppa-purge utility:

```
sudo apt-get install ppa-purge
ppa-purge ppa:gnome3-team/gnome3  
```

---

### Post by charlescarroll1 on 2013-06-02
> **eode said:**
> You can use the awesome ppa-purge utility:

```
sudo apt-get install ppa-purge
ppa-purge ppa:gnome3-team/gnome3  
```

I initially did a clean install of Ubuntu GNOME and upgraded to GNOME 3.8 after. The only desktop environment I have is GNOME. If I run this command, will it simply revert back to the previous version of GNOME? I just want to be sure I don't break my system.

---

### Post by markbl on 2013-06-02
ppa-purge should remove the gnome 3 ppa without issue. Then you will be back on stock ubuntu 13.04 with gnome shell 3.6.

I don't see why people would go back to gnome shell 3.6 just because of the software center problem. You can use synaptic, aptitude, etc to review and install packages. Gnome shell 3.8 scales windows in the overview much better than gnome shell 3.6 so I think that is a worthwhile to keep (although I personally think the messaging menu changes in 3.8 are a step backwards).

---

### Post by charlescarroll1 on 2013-06-02
I've been installing applications via terminal. I actually don't mind using terminal to install apps (it's fun using terminal), but I may end up wanting to switch to a more stable version of GNOME if I still get some bugs with 3.8. I absolutely love the changes in 3.8  which is why I probably won't switch back.

Thanks for answering my question, BTW!

---

### Post by eode on 2013-06-02
..the temptation for me lies in that I've bought applications from the software center, and I've bought a couple of humble indie bundles.   ..the humble bundles have packages on the site, but things bought directly from Ubuntu don't -- and I don't know how to install packages I've bought previously but don't have on my system without software center.

..nevertheless, Gnome 3.8, and its awesomeness.. ..hehehe.  :-)  ..so I'm still using that, myself.  But you should be safe to switch back via ppa-purge.  You can do that with any PPA.  The exceptions that cause problems are if an individual program's settings have changed, and the new configuration file format is greek to the old version of the app.  ..if that happens, though, you can generally just reinstall the ppa and the app.

---

### Post by MARP1961 on 2013-06-10
I've had the same problem and I don't want to roll back to Gnome 3.6 so I installed 'gnome-software-manager' via Synaptic and removed Ubuntu Software Center. I can live without it. I don't miss it's slow loading anyway.

---

### Post by sazawal on 2013-06-28
sudo apt-get install --reinstall software-center

This worked for me in Ubuntu  13.04. Thanks to askubuntu.com

[http://askubuntu.com/questions/295313/ubuntu-software-center-in-ubuntu-13-04-crashes-when-opened](http://askubuntu.com/questions/295313/ubuntu-software-center-in-ubuntu-13-04-crashes-when-opened)

---

### Post by markbl on 2013-06-28
> **sazawal said:**
> sudo apt-get install --reinstall software-center

This worked for me in Ubuntu  13.04.
Doesn't work for me. Software Center still crashes immediately.

---

