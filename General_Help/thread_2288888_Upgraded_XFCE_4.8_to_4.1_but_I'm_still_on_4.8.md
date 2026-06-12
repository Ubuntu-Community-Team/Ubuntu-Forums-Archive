---
title: "Upgraded XFCE 4.8 to 4.1 but I'm still on 4.8"
date: 2015-07-30
forum: General Help
---

### Post by Ace..... on 2015-07-30
This was the guide I used:

[http://ubuntuportal.com/2012/05/easy-way-to-install-xfce-4-10-desktop-environment-in-ubuntu-12-04.html](http://ubuntuportal.com/2012/05/easy-way-to-install-xfce-4-10-desktop-environment-in-ubuntu-12-04.html)

[COLOR=#666666][FONT=Titillium]To upgrading XFCE 4.8 to XFCE 4.10 in Xubuntu 12.04, Add the PPA  XFCE 4.10, with following commands below:[/FONT][/COLOR]
```
[FONT=inherit]sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10[/FONT]
[FONT=inherit]sudo apt-get update[/FONT]
[FONT=inherit]sudo apt-get dist-upgrade

[/FONT]
```It was a long process.... a good ten minutes.
He suggests:

[COLOR=#666666][FONT=Titillium]If you have problems after install  XFCE 4.10, or the upgrade itself.  just running the command below to solve the problem:[/FONT][/COLOR]
```
[FONT=inherit]sudo apt-get install ppa-purge[/FONT]
[FONT=inherit]sudo ppa-purge ppa:xubuntu-dev/xfce-4.10

[/FONT]
```However, I thought I'd best ask to see what's going on. first.

The Ubuntu version is 12.04LTS.
I haven't upgraded to 14.04 yet, as I'm concerned about my laptop having the power to run it.

It was for this reason that I've been trying XFCE.

4.8 seemed to have one or two issues..... so I figured an update might solve them.
Anyway 'about' informs me I'm still on 4.8.

Anybody know where I went wrong?

:)

---

### Post by dino99 on 2015-07-30
try that one:

ppa:jblgf0/xfce-4.10-1

---

### Post by mc4man on 2015-07-30
> Anybody know where I went wrong?
There is no such ppa, try what dino suggested. When you ran that command didn't you notice - 
```
$ sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
Cannot add PPA: 'ppa:xubuntu-dev/xfce-4.10'.
Please check that the PPA name or format is correct.
```

---

### Post by Ace..... on 2015-07-30
Thanks for those responses.

First attempt stated something like 'cannot access'.
2nd attempt it went through and began the download.
Like I stated....... a whole load of data was downloaded... at least ten minutes worth.

What on earth did I download?

Should we have a look?
How might I retrieve the data log?

Everything seems to be working.
I'll hold off, until we discover what I downloaded.... if that's interesting.
:)

---

### Post by Ace..... on 2015-07-31
> **Ace..... said:**
> 
I'll hold off, until we discover what I downloaded.... if that's interesting.


Okay..... so I launched XFCE.
It was glitching.
Windows wouldn't minimise, or come to the fore, when clicked...... but I managed to input 
```
[COLOR=#000000]ppa:jblgf0/xfce-4.10-1[/COLOR]
```

It installed, but on reboot, a dialogue box informed me that the data time panel would have to be restarted or permanently removed.

Yikes!
It wouldn't re-start, so was forced to click remove.

Tried loading it from menu..... no joy.
Tried another date time module called 'orange'...... same problem.

I've got my 4 workplaces back, and prog windows perform as normal.

The web browser STILL cannot be set as the default...... every time it loads it asks to be set as default (which I click) but it never works..... even in 4.1

So the glitches 'seem' not to have been fixed, and I've now lost date and time, from the top bar.

Anybody any thoughts?

Edit: rebooted.... tried unlocking panel and adding date time.... no go.
Note: date time works in Ubuntu.

---

### Post by Frogs Hair on 2015-07-31
That ppa was once included on the linked page , but it seems the focus is now on 4.12 for newer versions of Ubuntu. The linked instructions in post #1 are from 2012.

[https://launchpad.net/~xubuntu-dev/+archive/ubuntu/xfce-4.12](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/xfce-4.12)

---

### Post by Ace..... on 2015-08-01
I re-downloaded 4.12:
Still on 4.1
lost my preferred apps browser (strange)
still no date and time.

Also ran:
```
sudo ln -s /usr/lib/i386-linux-gnu/libxfce4panel-1.0.so.4 /usr/lib/i386-linux-gnu/libxfce4panel-1.0.so.3
ln: failed to create symbolic link `/usr/lib/i386-linux-gnu/libxfce4panel-1.0.so.3': File exists

```

I've also alerted xfce by joining their forum.


Here is the full 4.12 (developer page) download listing:
```
Xfce 4.12 packages for currently supported versions of Xubuntu. These packages come with no guarantee of functionality or support. For supported versions, please install Xubuntu 15.04 or newer which comes packaged with Xfce 4.12.
 More info: https://launchpad.net/~xubuntu-dev/+archive/ubuntu/xfce-4.12
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpm6_J88/secring.gpg' created
gpg: keyring `/tmp/tmpm6_J88/pubring.gpg' created
gpg: requesting key 142986CE from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpm6_J88/trustdb.gpg: trustdb created
gpg: key 142986CE: public key "Launchpad PPA for Xubuntu Developers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
mark@mark-eME644:~$ sudo apt-get update
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://dl.google.com stable Release.gpg                                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://fr.archive.ubuntu.com precise Release.gpg                           
Get:1 http://fr.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://fr.archive.ubuntu.com precise-backports Release.gpg                 
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://fr.archive.ubuntu.com precise Release                               
Get:3 http://fr.archive.ubuntu.com precise-updates Release [196 kB]            
Hit http://ppa.launchpad.net precise/main Sources                              
Get:4 http://security.ubuntu.com precise-security Release [54.3 kB]            
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Translation-en                       
Hit http://ppa.launchpad.net precise/main Translation-en                       
Hit http://ppa.launchpad.net precise/main Translation-en                       
Hit http://ppa.launchpad.net precise/main Translation-en                       
Get:5 http://security.ubuntu.com precise-security/main Sources [133 kB]        
Hit http://fr.archive.ubuntu.com precise-backports Release                     
Hit http://fr.archive.ubuntu.com precise/main Sources                          
Hit http://fr.archive.ubuntu.com precise/restricted Sources                    
Hit http://fr.archive.ubuntu.com precise/universe Sources                      
Hit http://fr.archive.ubuntu.com precise/multiverse Sources                    
Hit http://fr.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://fr.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://fr.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://fr.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://fr.archive.ubuntu.com precise/main i386 Packages                    
Hit http://fr.archive.ubuntu.com precise/restricted i386 Packages              
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit https://private-ppa.launchpad.net precise Release                          
Ign http://dl.google.com stable/main Translation-en_US                         
Get:6 http://security.ubuntu.com precise-security/restricted Sources [3,759 B] 
Get:7 http://security.ubuntu.com precise-security/universe Sources [43.8 kB]   
Get:8 http://security.ubuntu.com precise-security/multiverse Sources [2,199 B] 
Get:9 http://security.ubuntu.com precise-security/main amd64 Packages [539 kB] 
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://dl.google.com stable/main Translation-en                            
Hit http://fr.archive.ubuntu.com precise/universe i386 Packages                
Hit http://fr.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://fr.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://fr.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://fr.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://fr.archive.ubuntu.com precise/universe TranslationIndex             
Get:10 http://fr.archive.ubuntu.com precise-updates/main Sources [492 kB]      
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:11 https://private-ppa.launchpad.net precise/main TranslationIndex [360 B] 
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:12 http://security.ubuntu.com precise-security/restricted amd64 Packages [8,943 B]
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Get:13 http://security.ubuntu.com precise-security/universe amd64 Packages [124 kB]
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Get:14 http://fr.archive.ubuntu.com precise-updates/restricted Sources [7,981 B]
Get:15 http://fr.archive.ubuntu.com precise-updates/universe Sources [122 kB]  
Get:16 http://fr.archive.ubuntu.com precise-updates/multiverse Sources [9,714 B]
Get:17 http://fr.archive.ubuntu.com precise-updates/main amd64 Packages [925 kB]
Get:18 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,697 B]
Get:19 http://security.ubuntu.com precise-security/main i386 Packages [587 kB] 
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [8,939 B]
Get:21 http://security.ubuntu.com precise-security/universe i386 Packages [132 kB]
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,864 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Get:23 http://fr.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.6 kB]
Get:24 http://fr.archive.ubuntu.com precise-updates/universe amd64 Packages [268 kB]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:25 http://fr.archive.ubuntu.com precise-updates/multiverse amd64 Packages [16.5 kB]
Get:26 http://fr.archive.ubuntu.com precise-updates/main i386 Packages [977 kB]
Get:27 http://fr.archive.ubuntu.com precise-updates/restricted i386 Packages [13.6 kB]
Get:28 http://fr.archive.ubuntu.com precise-updates/universe i386 Packages [278 kB]
Get:29 http://fr.archive.ubuntu.com precise-updates/multiverse i386 Packages [16.7 kB]
Hit http://fr.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://fr.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://fr.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://fr.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://fr.archive.ubuntu.com precise-backports/main Sources                
Hit http://fr.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://fr.archive.ubuntu.com precise-backports/universe Sources            
Hit http://fr.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://fr.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://fr.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://fr.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://fr.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://fr.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://fr.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://fr.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://fr.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://fr.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://fr.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://fr.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://fr.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://fr.archive.ubuntu.com precise/main Translation-en         
Hit http://fr.archive.ubuntu.com precise/multiverse Translation-en   
Hit http://fr.archive.ubuntu.com precise/restricted Translation-en   
Hit http://fr.archive.ubuntu.com precise/universe Translation-en     
Hit http://fr.archive.ubuntu.com precise-updates/main Translation-en 
Hit http://fr.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://fr.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://fr.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://fr.archive.ubuntu.com precise-backports/main Translation-en
Hit http://fr.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://fr.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://fr.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 4,977 kB in 15s (323 kB/s)                                             
Reading package lists... Done

```

---

### Post by mc4man on 2015-08-01
> Here is the full 4.12 (developer page) download listing:
Xfce 4.12 packages for currently supported versions of Xubuntu
12.04 is  not supported so adding that ppa did nothing other than adding a useless source. Usually better to ck. a ppa page first before adding.
(- it only has trusty & vivid packages.. scr.

---

### Post by Ace..... on 2015-08-01
> **mc4man said:**
> 12.04 is  not supported so adding that ppa did nothing other than adding a useless source. Usually better to ck. a ppa page first before adding.
(- it only has trusty & vivid packages.. scr.

Ah...... thanks for that.
I guess I've lost date and time for nothing.

Life eh!

:)

---

### Post by mc4man on 2015-08-01
> **Ace..... said:**
> Ah...... thanks for that.
I guess I've lost date and time for nothing.

Life eh!

:)
I guess, unless the version you did install from that other ppa can be fixed??
Or you could - 
1. install & use ppa-purge on that other ppa, (ppa:jblgf0/xfce-4.10-1) to return to where you started with current 12.04 packages
2. go to Xubuntu 14.04 (I'd not do a release upgrade, rather a fresh install after testing live cd/usb session

(- i've no 12.04 install so really can't help with fixing the missing date & time deal..

---

### Post by Ace..... on 2015-08-01
> **mc4man said:**
> I guess, unless the version you did install from that other ppa can be fixed??
Or you could - 
1. install & use ppa-purge on that other ppa, (ppa:jblgf0/xfce-4.10-1) to return to where you started with current 12.04 packages
2. go to Xubuntu 14.04 (I'd not do a release upgrade, rather a fresh install after testing live cd/usb session

(- i've no 12.04 install so really can't help with fixing the missing date & time deal..

That's an interesting idea.
So it would be:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:jblgf0/xfce-4.10-1

```

..... and this would take me back to 4.8?

I'm prepared to try that ;)

---

### Post by mc4man on 2015-08-01
> **Ace..... said:**
> That's an interesting idea.
So it would be:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:jblgf0/xfce-4.10-1

```

..... and this would take me back to 4.8?

I'm prepared to try that ;)
That should work as long as that ppa is still enabled, if it isn't still enabled (ppa-purge will tell you), then re-add it, update your sources & try ppa-purge again.


(- you can also remove that dev ppa as it has nothing for you - for that just run this at any convenient   time - 
```
sudo add-apt-repository -r ppa:xubuntu-dev/xfce-4.12
```
(- then update sources - sudo apt-get update

---

### Post by Ace..... on 2015-08-01
> **mc4man said:**
> That should work as long as that ppa is still enabled, if it isn't still enabled (ppa-purge will tell you), then re-add it, update your sources & try ppa-purge again.

(- you can also remove that dev ppa as it has nothing for you - for that just run this at any convenient   time - 
```
sudo add-apt-repository -r ppa:xubuntu-dev/xfce-4.12
```
(- then update sources - sudo apt-get update

That sounds a good path to take.

Just checked my xsession error log to see where date time has gone.

It seems to state that the file is missing.

```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
xfce4-session-Message: ssh-agent is already running
xrandr: cannot find mode 1680x1050


(polkit-gnome-authentication-agent-1:2133): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed


(polkit-gnome-authentication-agent-1:2133): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


(xfce4-indicator-plugin:2137): libindicator-WARNING **: IndicatorObject class does not have an accessible description.


(xfce4-indicator-plugin:2137): libindicator-WARNING **: IndicatorObject class does not have an accessible description.


(xfdesktop:2111): GLib-GIO-CRITICAL **: g_file_get_path: assertion `G_IS_FILE (file)' failed


(xfdesktop:2111): GLib-GIO-CRITICAL **: g_file_get_path: assertion `G_IS_FILE (file)' failed
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area


(xfce4-indicator-plugin:2137): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed


(xfce4-indicator-plugin:2137): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
** Message: applet now removed from the notification area
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-4gG9f6/pkcs11: No such file or directory


(xfdesktop:2111): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed


(evolution:2243): camel-CRITICAL **: camel_session_add_service: assertion `uri_string != NULL' failed


(process:2315): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)


(process:2315): xfce4-panel-wrapper-CRITICAL **: Wrapper datetime-7: Failed to open plugin module "/usr/lib/xfce4/panel/plugins/libdatetime.so": libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory.
xfce4-panel-Message: Plugin datetime-7 has been automatically restarted after crash.


(process:2316): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)


(process:2316): xfce4-panel-wrapper-CRITICAL **: Wrapper datetime-7: Failed to open plugin module "/usr/lib/xfce4/panel/plugins/libdatetime.so": libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory.


(process:2317): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)


(process:2317): xfce4-panel-wrapper-CRITICAL **: Wrapper datetime-7: Failed to open plugin module "/usr/lib/xfce4/panel/plugins/libdatetime.so": libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory.
[2326:2326:0801/115849:ERROR:nss_util.cc(856)] After loading Root Certs, loaded==false: NSS error code: -8018
libGL error: open uki failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
[2326:2465:0801/115920:ERROR:get_updates_processor.cc(243)] PostClientToServerMessage() failed during GetUpdates


(xfce4-terminal:2595): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[2689:2689:0801/120939:ERROR:nss_util.cc(856)] After loading Root Certs, loaded==false: NSS error code: -8018
[WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED
[WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED


(exo-helper-1:3138): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
[2326:2357:0801/154730:ERROR:channel.cc(300)] RawChannel read error (connection broken)
[3179:3179:0801/154736:ERROR:nss_util.cc(856)] After loading Root Certs, loaded==false: NSS error code: -8018
libGL error: open uki failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
[3179:3350:0801/154754:ERROR:get_updates_processor.cc(243)] PostClientToServerMessage() failed during GetUpdates
[3179:3210:0801/155546:ERROR:channel.cc(300)] RawChannel read error (connection broken)


(process:3590): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)


(process:3590): xfce4-panel-wrapper-CRITICAL **: Wrapper datetime-29: Failed to open plugin module "/usr/lib/xfce4/panel/plugins/libdatetime.so": libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory.
xfce4-panel-Message: Plugin datetime-29 has been automatically restarted after crash.


(process:3591): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)


(process:3591): xfce4-panel-wrapper-CRITICAL **: Wrapper datetime-29: Failed to open plugin module "/usr/lib/xfce4/panel/plugins/libdatetime.so": libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory.


(process:3592): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)


(process:3592): xfce4-panel-wrapper-CRITICAL **: Wrapper datetime-29: Failed to open plugin module "/usr/lib/xfce4/panel/plugins/libdatetime.so": libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory.


(process:3594): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)


(process:3594): xfce4-panel-wrapper-CRITICAL **: Wrapper datetime-31: Failed to open plugin module "/usr/lib/xfce4/panel/plugins/libdatetime.so": libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory.
xfce4-panel-Message: Plugin datetime-31 has been automatically restarted after crash.


(process:3595): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)


(process:3595): xfce4-panel-wrapper-CRITICAL **: Wrapper datetime-31: Failed to open plugin module "/usr/lib/xfce4/panel/plugins/libdatetime.so": libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory.


(process:3600): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)


(process:3600): xfce4-panel-wrapper-CRITICAL **: Wrapper datetime-42: Failed to open plugin module "/usr/lib/xfce4/panel/plugins/libdatetime.so": libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory.
xfce4-panel-Message: Plugin datetime-42 has been automatically restarted after crash.


(process:3601): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)


(process:3601): xfce4-panel-wrapper-CRITICAL **: Wrapper datetime-42: Failed to open plugin module "/usr/lib/xfce4/panel/plugins/libdatetime.so": libxfce4panel-1.0.so.3: cannot open shared object file: No such file or directory.


(polkit-gnome-authentication-agent-1:2133): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.


wrapper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfrun4: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
[3214:3214:0801/164700:ERROR:x11_util.cc(82)] X IO error received (X server probably went away)
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.


(xfce4-panel:2105): Gtk-CRITICAL **: IA__gtk_main_quit: assertion `main_loops != NULL' failed
The application 'xfce4-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.


** (zeitgeist-datahub:2145): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
** Message: PID 2166 (we are 2166) sent signal 15, shutting down...
xfce4-terminal: Fatal IO error 2 (No such file or directory) on X server :0.0.


(nm-applet:2166): libappindicator-WARNING **: Unable to send signal for NewStatus: The connection is closed


** (evolution:2243): CRITICAL **: connection_closed_cb: assertion `connection != pconnection' failed
[3179:3179:0801/164700:ERROR:chrome_browser_main_extra_parts_x11.cc(56)] X IO error received (X server probably went away)


(evolution:2243): GConf-WARNING **: Got Disconnected from DBus.




** (evolution:2243): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/interface/': The connection is closed


** (evolution:2243): CRITICAL **: DBus AddMatch for dconf path '/org/gnome/desktop/interface/': The connection is closed


(evolution:2243): Gdk-WARNING **: evolution: Fatal IO error 0 (Success) on X server :0.0.

```

---

### Post by Ace..... on 2015-08-02
So I've completed the purge.g
It reports that it was successful.

I'll post the full code, in case there was a problem, and then I'll reboot:

```
mark@mark-eME644:~$ sudo apt-get install ppa-purge[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-77 linux-headers-3.2.0-77-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libio-string-perl libparse-debianchangelog-perl libsub-name-perl ppa-purge
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,924 kB of archives.
After this operation, 9,049 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://fr.archive.ubuntu.com/ubuntu/ precise/main libboost-iostreams1.46.1 amd64 1.46.1-7ubuntu3 [39.2 kB]
Get:2 http://fr.archive.ubuntu.com/ubuntu/ precise/main libcwidget3 amd64 0.5.16-3.1ubuntu1 [406 kB]
Get:3 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main aptitude amd64 0.6.6-1ubuntu1.2 [2,372 kB]
Get:4 http://fr.archive.ubuntu.com/ubuntu/ precise/main libsub-name-perl amd64 0.05-1build2 [9,656 B]
Get:5 http://fr.archive.ubuntu.com/ubuntu/ precise/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:6 http://fr.archive.ubuntu.com/ubuntu/ precise/main libio-string-perl all 1.08-2 [12.0 kB]
Get:7 http://fr.archive.ubuntu.com/ubuntu/ precise/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Get:8 http://fr.archive.ubuntu.com/ubuntu/ precise/universe ppa-purge all 0.2.8+bzr56 [4,360 B]
Fetched 2,924 kB in 8s (339 kB/s)                                              
Selecting previously unselected package libboost-iostreams1.46.1.
(Reading database ... 1171397 files and directories currently installed.)
Unpacking libboost-iostreams1.46.1 (from .../libboost-iostreams1.46.1_1.46.1-7ubuntu3_amd64.deb) ...
Selecting previously unselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.1ubuntu1_amd64.deb) ...
Selecting previously unselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.6-1ubuntu1.2_amd64.deb) ...
Selecting previously unselected package libsub-name-perl.
Unpacking libsub-name-perl (from .../libsub-name-perl_0.05-1build2_amd64.deb) ...
Selecting previously unselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.34-1_all.deb) ...
Selecting previously unselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously unselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb) ...
Selecting previously unselected package ppa-purge.
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr56_all.deb) ...
Processing triggers for man-db ...
Setting up libboost-iostreams1.46.1 (1.46.1-7ubuntu3) ...
Setting up libcwidget3 (0.5.16-3.1ubuntu1) ...
Setting up aptitude (0.6.6-1ubuntu1.2) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up libsub-name-perl (0.05-1build2) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libio-string-perl (1.08-2) ...
Setting up libparse-debianchangelog-perl (1.2.0-1ubuntu1) ...
Setting up ppa-purge (0.2.8+bzr56) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
mark@mark-eME644:~$ sudo ppa-purge ppa:jblgf0/xfce-4.10-1
Updating packages lists
PPA to be removed: jblgf0 xfce-4.10-1
comm: file 2 is not in sorted order
Package revert list generated:
 exo-utils/precise gigolo/precise libexo-1-0/precise libexo-common/precise 
libexo-helpers/precise libgarcon-1-0/precise libgarcon-common/precise 
libthunarx-2-0/precise libxfce4ui-1-0/precise libxfce4ui-utils/precise 
libxfce4util6/precise libxfce4util-bin/precise libxfce4util-common/precise 
libxfcegui4-4/precise libxfconf-0-2/precise orage/precise parole/precise 
thunar/precise thunar-data/precise thunar-volman/precise xfburn/precise 
xfce4-appfinder/precise xfce4-cpugraph-plugin/precise 
xfce4-datetime-plugin/precise xfce4-dict/precise xfce4-indicator-plugin/precise 
xfce4-mailwatch-plugin/precise xfce4-netload-plugin/precise xfce4-notes/precise 
xfce4-notes-plugin/precise xfce4-notifyd/precise xfce4-panel/precise 
xfce4-places-plugin/precise xfce4-power-manager/precise 
xfce4-power-manager-data/precise xfce4-quicklauncher-plugin/precise 
xfce4-screenshooter/precise xfce4-session/precise xfce4-settings/precise 
xfce4-systemload-plugin/precise xfce4-taskmanager/precise 
xfce4-terminal/precise xfce4-verve-plugin/precise xfce4-weather-plugin/precise 
xfce4-xkb-plugin/precise xfce-keyboard-shortcuts/precise xfconf/precise 
xfdesktop4/precise xfdesktop4-data/precise xfwm4/precise 
xubuntu-default-settings/precise xubuntu-desktop/precise


Disabling jblgf0 PPA from 
/etc/apt/sources.list.d/jblgf0-xfce-4_10-1-precise.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release 'precise' for 'libxfce4ui-utils' was not found
E: Release 'precise' for 'libxfce4util6' was not found
Unable to find an archive "precise" for the package "libxfce4ui-utils"
Unable to find an archive "precise" for the package "libxfce4util6"
Unable to find an archive "precise" for the package "libxfce4ui-utils"
Unable to find an archive "precise" for the package "libxfce4util6"
The following packages will be DOWNGRADED:
  exo-utils gigolo libexo-1-0 libexo-common libexo-helpers libgarcon-1-0 
  libgarcon-common libthunarx-2-0 libxfce4ui-1-0 libxfce4util-bin 
  libxfce4util-common libxfcegui4-4 libxfconf-0-2 orage parole thunar 
  thunar-data thunar-volman xfburn xfce-keyboard-shortcuts xfce4-appfinder 
  xfce4-cpugraph-plugin xfce4-datetime-plugin xfce4-dict 
  xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-netload-plugin 
  xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel 
  xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data 
  xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session 
  xfce4-settings xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal 
  xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf 
  xfdesktop4 xfdesktop4-data xfwm4 xubuntu-default-settings xubuntu-desktop 
The following NEW packages will be installed:
  xfce4-utils{a} 
The following packages will be REMOVED:
  libxfce4ui-utils{u} libxfce4util6{u} linux-headers-3.2.0-77{u} 
  linux-headers-3.2.0-77-generic{u} 
0 packages upgraded, 1 newly installed, 50 downgraded, 4 to remove and 0 not upgraded.
Need to get 19.8 MB of archives. After unpacking 60.3 MB will be freed.
Do you want to continue? [Y/n/?] y
Get: 1 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xubuntu-desktop amd64 2.152 [3,790 B]
Get: 2 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-session amd64 4.8.3-0ubuntu2 [1,222 kB]
Get: 3 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce-keyboard-shortcuts all 4.8.1-1 [4,128 B]
Get: 4 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libxfcegui4-4 amd64 4.8.1-5ubuntu1 [230 kB]
Get: 5 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-settings amd64 4.8.3-1ubuntu3 [488 kB]
Get: 6 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libgarcon-common all 0.1.11-0ubuntu1 [50.9 kB]
Get: 7 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libgarcon-1-0 amd64 0.1.11-0ubuntu1 [45.8 kB]
Get: 8 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfconf amd64 4.8.1-1 [109 kB]
Get: 9 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libxfconf-0-2 amd64 4.8.1-1 [30.7 kB]
Get: 10 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-appfinder amd64 4.8.0-3 [59.0 kB]
Get: 11 http://fr.archive.ubuntu.com/ubuntu/ precise/universe exo-utils amd64 0.6.2-4 [57.0 kB]
Get: 12 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-terminal amd64 0.4.8-1ubuntu1 [1,214 kB]
Get: 13 http://fr.archive.ubuntu.com/ubuntu/ precise/universe thunar-volman amd64 0.6.1-0ubuntu1 [145 kB]
Get: 14 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfwm4 amd64 4.8.3-1ubuntu1 [1,164 kB]
Get: 15 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-notes amd64 1.7.7-2ubuntu1 [103 kB]
Get: 16 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-notes-plugin amd64 1.7.7-2ubuntu1 [48.5 kB]
Get: 17 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-netload-plugin amd64 1.1.0-1 [56.8 kB]
Get: 18 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-dict amd64 0.6.0-5 [168 kB]
Get: 19 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-quicklauncher-plugin amd64 1.9.4-9 [25.7 kB]
Get: 20 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-weather-plugin amd64 0.7.4-3 [462 kB]
Get: 21 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-verve-plugin amd64 1.0.0-1 [39.5 kB]
Get: 22 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-indicator-plugin amd64 0.4.0-0ubuntu2 [26.4 kB]
Get: 23 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-mailwatch-plugin amd64 1.1.0-5 [329 kB]
Get: 24 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-panel amd64 4.8.6-2ubuntu2 [1,087 kB]
Get: 25 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libthunarx-2-0 amd64 1.2.3-3ubuntu2 [85.0 kB]
Get: 26 http://fr.archive.ubuntu.com/ubuntu/ precise/universe thunar amd64 1.2.3-3ubuntu2 [311 kB]
Get: 27 http://fr.archive.ubuntu.com/ubuntu/ precise/universe thunar-data all 1.2.3-3ubuntu2 [3,127 kB]
Get: 28 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-power-manager amd64 1.0.11-0ubuntu2 [111 kB]
Get: 29 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-power-manager-data all 1.0.11-0ubuntu2 [550 kB]
Get: 30 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfburn amd64 0.4.3-4ubuntu1 [417 kB]
Get: 31 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfdesktop4 amd64 4.8.3-2ubuntu7 [150 kB]
Get: 32 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfdesktop4-data all 4.8.3-2ubuntu7 [1,026 kB]
Get: 33 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libexo-1-0 amd64 0.6.2-4 [461 kB]
Get: 34 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libxfce4ui-1-0 amd64 4.8.1-1 [79.6 kB]
Get: 35 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libexo-common all 0.6.2-4 [501 kB]
Get: 36 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libexo-helpers amd64 0.6.2-4 [19.0 kB]
Get: 37 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-notifyd amd64 0.2.2-1 [73.7 kB]
Get: 38 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-utils amd64 4.8.3-1ubuntu2 [640 kB]
Get: 39 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xubuntu-default-settings all 12.04.11 [19.2 kB]
Get: 40 http://fr.archive.ubuntu.com/ubuntu/ precise/universe parole amd64 0.2.0.6-1 [340 kB]
Get: 41 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-systemload-plugin amd64 1:1.0.0-1ubuntu1 [37.1 kB]
Get: 42 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libxfce4util-bin amd64 4.8.2-1 [6,176 B]
Get: 43 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-xkb-plugin amd64 0.5.4.3-1ubuntu1 [540 kB]
Get: 44 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-places-plugin amd64 1.2.0-3 [58.3 kB]
Get: 45 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-screenshooter amd64 1.8.0-2 [1,673 kB]
Get: 46 http://fr.archive.ubuntu.com/ubuntu/ precise/universe gigolo amd64 0.4.1-3 [142 kB]
Get: 47 http://fr.archive.ubuntu.com/ubuntu/ precise/universe libxfce4util-common all 4.8.2-1 [52.6 kB]
Get: 48 http://fr.archive.ubuntu.com/ubuntu/ precise/universe orage amd64 4.8.3-1 [2,122 kB]
Get: 49 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-cpugraph-plugin amd64 1.0.1-2 [48.7 kB]
Get: 50 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-datetime-plugin amd64 0.6.1-3ubuntu1 [23.7 kB]
Get: 51 http://fr.archive.ubuntu.com/ubuntu/ precise/universe xfce4-taskmanager amd64 1.0.0-2 [63.6 kB]
Fetched 19.8 MB in 40s (490 kB/s)                                               
Extracting templates from packages: 100%
dpkg: warning: downgrading xubuntu-desktop from 2.152+ppa2 to 2.152.
(Reading database ... 1171586 files and directories currently installed.)
Preparing to replace xubuntu-desktop 2.152+ppa2 (using .../xubuntu-desktop_2.152_amd64.deb) ...
Unpacking replacement xubuntu-desktop ...
dpkg: warning: downgrading xfce4-session from 4.10.1-0ubuntu1~ppa0.12.04.1 to 4.8.3-0ubuntu2.
Preparing to replace xfce4-session 4.10.1-0ubuntu1~ppa0.12.04.1 (using .../xfce4-session_4.8.3-0ubuntu2_amd64.deb) ...
Unpacking replacement xfce4-session ...
dpkg: warning: downgrading xfce-keyboard-shortcuts from 4.10.0-0ubuntu1~ppa1 to 4.8.1-1.
Preparing to replace xfce-keyboard-shortcuts 4.10.0-0ubuntu1~ppa1 (using .../xfce-keyboard-shortcuts_4.8.1-1_all.deb) ...
Unpacking replacement xfce-keyboard-shortcuts ...
dpkg: warning: downgrading libxfcegui4-4 from 4.10.0-0ubuntu1~ppa1 to 4.8.1-5ubuntu1.
Preparing to replace libxfcegui4-4 4.10.0-0ubuntu1~ppa1 (using .../libxfcegui4-4_4.8.1-5ubuntu1_amd64.deb) ...
Unpacking replacement libxfcegui4-4 ...
dpkg: warning: downgrading xfce4-settings from 4.10.1-1ubuntu1~ppa0.12.04.1 to 4.8.3-1ubuntu3.
Preparing to replace xfce4-settings 4.10.1-1ubuntu1~ppa0.12.04.1 (using .../xfce4-settings_4.8.3-1ubuntu3_amd64.deb) ...
Unpacking replacement xfce4-settings ...
dpkg: warning: downgrading libgarcon-common from 0.2.1-0ubuntu1~ppa0.12.04.1 to 0.1.11-0ubuntu1.
Preparing to replace libgarcon-common 0.2.1-0ubuntu1~ppa0.12.04.1 (using .../libgarcon-common_0.1.11-0ubuntu1_all.deb) ...
Unpacking replacement libgarcon-common ...
dpkg: warning: downgrading libgarcon-1-0 from 0.2.1-0ubuntu1~ppa0.12.04.1 to 0.1.11-0ubuntu1.
Preparing to replace libgarcon-1-0 0.2.1-0ubuntu1~ppa0.12.04.1 (using .../libgarcon-1-0_0.1.11-0ubuntu1_amd64.deb) ...
Unpacking replacement libgarcon-1-0 ...
dpkg: warning: downgrading xfconf from 4.10.0-0ubuntu1~ppa1 to 4.8.1-1.
Preparing to replace xfconf 4.10.0-0ubuntu1~ppa1 (using .../xfconf_4.8.1-1_amd64.deb) ...
Unpacking replacement xfconf ...
dpkg: warning: downgrading libxfconf-0-2 from 4.10.0-0ubuntu1~ppa1 to 4.8.1-1.
Preparing to replace libxfconf-0-2 4.10.0-0ubuntu1~ppa1 (using .../libxfconf-0-2_4.8.1-1_amd64.deb) ...
Unpacking replacement libxfconf-0-2 ...
dpkg: warning: downgrading xfce4-appfinder from 4.10.1-0ubuntu1~ppa0.12.04.1 to 4.8.0-3.
Preparing to replace xfce4-appfinder 4.10.1-0ubuntu1~ppa0.12.04.1 (using .../xfce4-appfinder_4.8.0-3_amd64.deb) ...
Unpacking replacement xfce4-appfinder ...
dpkg: warning: downgrading exo-utils from 0.10.2-0ubuntu1~ppa0.12.04.1 to 0.6.2-4.
Preparing to replace exo-utils 0.10.2-0ubuntu1~ppa0.12.04.1 (using .../exo-utils_0.6.2-4_amd64.deb) ...
Unpacking replacement exo-utils ...
dpkg: warning: downgrading xfce4-terminal from 0.6.3-1ubuntu1~ppa0.12.04.1 to 0.4.8-1ubuntu1.
Preparing to replace xfce4-terminal 0.6.3-1ubuntu1~ppa0.12.04.1 (using .../xfce4-terminal_0.4.8-1ubuntu1_amd64.deb) ...
Unpacking replacement xfce4-terminal ...
dpkg: warning: downgrading thunar-volman from 0.8.0-0ubuntu1~ppa1 to 0.6.1-0ubuntu1.
Preparing to replace thunar-volman 0.8.0-0ubuntu1~ppa1 (using .../thunar-volman_0.6.1-0ubuntu1_amd64.deb) ...
Unpacking replacement thunar-volman ...
dpkg: warning: downgrading xfwm4 from 4.10.1-0ubuntu1~ppa0.12.04.1 to 4.8.3-1ubuntu1.
Preparing to replace xfwm4 4.10.1-0ubuntu1~ppa0.12.04.1 (using .../xfwm4_4.8.3-1ubuntu1_amd64.deb) ...
Unpacking replacement xfwm4 ...
dpkg: warning: downgrading xfce4-notes from 1.7.7-2ubuntu1+ppa1 to 1.7.7-2ubuntu1.
Preparing to replace xfce4-notes 1.7.7-2ubuntu1+ppa1 (using .../xfce4-notes_1.7.7-2ubuntu1_amd64.deb) ...
Unpacking replacement xfce4-notes ...
dpkg: warning: downgrading xfce4-notes-plugin from 1.7.7-2ubuntu1+ppa1 to 1.7.7-2ubuntu1.
Preparing to replace xfce4-notes-plugin 1.7.7-2ubuntu1+ppa1 (using .../xfce4-notes-plugin_1.7.7-2ubuntu1_amd64.deb) ...
Unpacking replacement xfce4-notes-plugin ...
dpkg: warning: downgrading xfce4-netload-plugin from 1.2.0-0ubuntu1~ppa1 to 1.1.0-1.
Preparing to replace xfce4-netload-plugin 1.2.0-0ubuntu1~ppa1 (using .../xfce4-netload-plugin_1.1.0-1_amd64.deb) ...
Unpacking replacement xfce4-netload-plugin ...
dpkg: warning: downgrading xfce4-dict from 0.7.0-1~ppa12.04.1 to 0.6.0-5.
Preparing to replace xfce4-dict 0.7.0-1~ppa12.04.1 (using .../xfce4-dict_0.6.0-5_amd64.deb) ...
Unpacking replacement xfce4-dict ...
dpkg: warning: downgrading xfce4-quicklauncher-plugin from 1.9.4-9+ppa1 to 1.9.4-9.
Preparing to replace xfce4-quicklauncher-plugin 1.9.4-9+ppa1 (using .../xfce4-quicklauncher-plugin_1.9.4-9_amd64.deb) ...
Unpacking replacement xfce4-quicklauncher-plugin ...
dpkg: warning: downgrading xfce4-weather-plugin from 0.8.5-2 to 0.7.4-3.
Preparing to replace xfce4-weather-plugin 0.8.5-2 (using .../xfce4-weather-plugin_0.7.4-3_amd64.deb) ...
Unpacking replacement xfce4-weather-plugin ...
dpkg: warning: downgrading xfce4-verve-plugin from 1.0.0-1+ppa1 to 1.0.0-1.
Preparing to replace xfce4-verve-plugin 1.0.0-1+ppa1 (using .../xfce4-verve-plugin_1.0.0-1_amd64.deb) ...
Unpacking replacement xfce4-verve-plugin ...
dpkg: warning: downgrading xfce4-indicator-plugin from 0.4.0-0ubuntu2+ppa1 to 0.4.0-0ubuntu2.
Preparing to replace xfce4-indicator-plugin 0.4.0-0ubuntu2+ppa1 (using .../xfce4-indicator-plugin_0.4.0-0ubuntu2_amd64.deb) ...
Unpacking replacement xfce4-indicator-plugin ...
dpkg: warning: downgrading xfce4-mailwatch-plugin from 1.2.0-1~ppa0.12.04.1 to 1.1.0-5.
Preparing to replace xfce4-mailwatch-plugin 1.2.0-1~ppa0.12.04.1 (using .../xfce4-mailwatch-plugin_1.1.0-5_amd64.deb) ...
Unpacking replacement xfce4-mailwatch-plugin ...
dpkg: warning: downgrading xfce4-panel from 4.10.1-0ubuntu1~ppa0.12.04.1 to 4.8.6-2ubuntu2.
Preparing to replace xfce4-panel 4.10.1-0ubuntu1~ppa0.12.04.1 (using .../xfce4-panel_4.8.6-2ubuntu2_amd64.deb) ...
Unpacking replacement xfce4-panel ...
dpkg: warning: downgrading libthunarx-2-0 from 1.6.3-0ubuntu1~ppa0.12.04.1 to 1.2.3-3ubuntu2.
Preparing to replace libthunarx-2-0 1.6.3-0ubuntu1~ppa0.12.04.1 (using .../libthunarx-2-0_1.2.3-3ubuntu2_amd64.deb) ...
Unpacking replacement libthunarx-2-0 ...
dpkg: warning: downgrading thunar from 1.6.3-0ubuntu1~ppa0.12.04.1 to 1.2.3-3ubuntu2.
Preparing to replace thunar 1.6.3-0ubuntu1~ppa0.12.04.1 (using .../thunar_1.2.3-3ubuntu2_amd64.deb) ...
Unpacking replacement thunar ...
dpkg: warning: downgrading thunar-data from 1.6.3-0ubuntu1~ppa0.12.04.1 to 1.2.3-3ubuntu2.
Preparing to replace thunar-data 1.6.3-0ubuntu1~ppa0.12.04.1 (using .../thunar-data_1.2.3-3ubuntu2_all.deb) ...
Unpacking replacement thunar-data ...
dpkg: warning: downgrading xfce4-power-manager from 1.2.0-1ubuntu1.1~ppa1 to 1.0.11-0ubuntu2.
Preparing to replace xfce4-power-manager 1.2.0-1ubuntu1.1~ppa1 (using .../xfce4-power-manager_1.0.11-0ubuntu2_amd64.deb) ...
Unpacking replacement xfce4-power-manager ...
dpkg: warning: downgrading xfce4-power-manager-data from 1.2.0-1ubuntu1.1~ppa1 to 1.0.11-0ubuntu2.
Preparing to replace xfce4-power-manager-data 1.2.0-1ubuntu1.1~ppa1 (using .../xfce4-power-manager-data_1.0.11-0ubuntu2_all.deb) ...
Unpacking replacement xfce4-power-manager-data ...
dpkg: warning: downgrading xfburn from 0.5.0-0ubuntu1~ppa0.12.04.1 to 0.4.3-4ubuntu1.
Preparing to replace xfburn 0.5.0-0ubuntu1~ppa0.12.04.1 (using .../xfburn_0.4.3-4ubuntu1_amd64.deb) ...
Unpacking replacement xfburn ...
dpkg: warning: downgrading xfdesktop4 from 4.10.2-0ubuntu1~ppa0.12.04.1 to 4.8.3-2ubuntu7.
Preparing to replace xfdesktop4 4.10.2-0ubuntu1~ppa0.12.04.1 (using .../xfdesktop4_4.8.3-2ubuntu7_amd64.deb) ...
Unpacking replacement xfdesktop4 ...
dpkg: warning: downgrading xfdesktop4-data from 4.10.2-0ubuntu1~ppa0.12.04.1 to 4.8.3-2ubuntu7.
Preparing to replace xfdesktop4-data 4.10.2-0ubuntu1~ppa0.12.04.1 (using .../xfdesktop4-data_4.8.3-2ubuntu7_all.deb) ...
Unpacking replacement xfdesktop4-data ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
(Reading database ... 1172825 files and directories currently installed.)
Removing libxfce4ui-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
dpkg: warning: downgrading libexo-1-0 from 0.10.2-0ubuntu1~ppa0.12.04.1 to 0.6.2-4.
(Reading database ... 1172820 files and directories currently installed.)
Preparing to replace libexo-1-0 0.10.2-0ubuntu1~ppa0.12.04.1 (using .../libexo-1-0_0.6.2-4_amd64.deb) ...
Unpacking replacement libexo-1-0 ...
dpkg: warning: downgrading libxfce4ui-1-0 from 4.10.0-0ubuntu1~ppa1 to 4.8.1-1.
Preparing to replace libxfce4ui-1-0 4.10.0-0ubuntu1~ppa1 (using .../libxfce4ui-1-0_4.8.1-1_amd64.deb) ...
Unpacking replacement libxfce4ui-1-0 ...
dpkg: warning: downgrading libexo-common from 0.10.2-0ubuntu1~ppa0.12.04.1 to 0.6.2-4.
Preparing to replace libexo-common 0.10.2-0ubuntu1~ppa0.12.04.1 (using .../libexo-common_0.6.2-4_all.deb) ...
Unpacking replacement libexo-common ...
dpkg: warning: downgrading libexo-helpers from 0.10.2-0ubuntu1~ppa0.12.04.1 to 0.6.2-4.
Preparing to replace libexo-helpers 0.10.2-0ubuntu1~ppa0.12.04.1 (using .../libexo-helpers_0.6.2-4_amd64.deb) ...
Unpacking replacement libexo-helpers ...
dpkg: warning: downgrading xfce4-notifyd from 0.2.4-2~ppa0.12.04.1 to 0.2.2-1.
Preparing to replace xfce4-notifyd 0.2.4-2~ppa0.12.04.1 (using .../xfce4-notifyd_0.2.2-1_amd64.deb) ...
Unpacking replacement xfce4-notifyd ...
Selecting previously unselected package xfce4-utils.
Unpacking xfce4-utils (from .../xfce4-utils_4.8.3-1ubuntu2_amd64.deb) ...
dpkg: warning: downgrading xubuntu-default-settings from 12.04.11+ppa2 to 12.04.11.
Preparing to replace xubuntu-default-settings 12.04.11+ppa2 (using .../xubuntu-default-settings_12.04.11_all.deb) ...
Unpacking replacement xubuntu-default-settings ...
dpkg: warning: downgrading parole from 0.5.4-0ubuntu1~ppa0.12.04.1 to 0.2.0.6-1.
Preparing to replace parole 0.5.4-0ubuntu1~ppa0.12.04.1 (using .../parole_0.2.0.6-1_amd64.deb) ...
Unpacking replacement parole ...
dpkg: warning: downgrading xfce4-systemload-plugin from 1:1.1.1-1ubuntu1~ppa1 to 1:1.0.0-1ubuntu1.
Preparing to replace xfce4-systemload-plugin 1:1.1.1-1ubuntu1~ppa1 (using .../xfce4-systemload-plugin_1%3a1.0.0-1ubuntu1_amd64.deb) ...
Unpacking replacement xfce4-systemload-plugin ...
dpkg: warning: downgrading libxfce4util-bin from 4.10.1-0ubuntu1~ppa0.12.04.1 to 4.8.2-1.
Preparing to replace libxfce4util-bin 4.10.1-0ubuntu1~ppa0.12.04.1 (using .../libxfce4util-bin_4.8.2-1_amd64.deb) ...
Unpacking replacement libxfce4util-bin ...
dpkg: warning: downgrading xfce4-xkb-plugin from 1:0.5.6-1~ppa0.12.04.1 to 0.5.4.3-1ubuntu1.
Preparing to replace xfce4-xkb-plugin 1:0.5.6-1~ppa0.12.04.1 (using .../xfce4-xkb-plugin_0.5.4.3-1ubuntu1_amd64.deb) ...
Unpacking replacement xfce4-xkb-plugin ...
dpkg: warning: downgrading xfce4-places-plugin from 1.6.0-1~ppa0.12.04.1 to 1.2.0-3.
Preparing to replace xfce4-places-plugin 1.6.0-1~ppa0.12.04.1 (using .../xfce4-places-plugin_1.2.0-3_amd64.deb) ...
Unpacking replacement xfce4-places-plugin ...
dpkg: warning: downgrading xfce4-screenshooter from 1.8.1-1~ppa1 to 1.8.0-2.
Preparing to replace xfce4-screenshooter 1.8.1-1~ppa1 (using .../xfce4-screenshooter_1.8.0-2_amd64.deb) ...
Unpacking replacement xfce4-screenshooter ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for gconf2 ...
(Reading database ... 1173049 files and directories currently installed.)
Removing libxfce4util6 ...
Removing linux-headers-3.2.0-77-generic ...
Removing linux-headers-3.2.0-77 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dpkg: warning: downgrading gigolo from 0.4.2-1~ppa0.12.04.1 to 0.4.1-3.
(Reading database ... 1150999 files and directories currently installed.)
Preparing to replace gigolo 0.4.2-1~ppa0.12.04.1 (using .../gigolo_0.4.1-3_amd64.deb) ...
Unpacking replacement gigolo ...
dpkg: warning: downgrading libxfce4util-common from 4.10.1-0ubuntu1~ppa0.12.04.1 to 4.8.2-1.
Preparing to replace libxfce4util-common 4.10.1-0ubuntu1~ppa0.12.04.1 (using .../libxfce4util-common_4.8.2-1_all.deb) ...
Unpacking replacement libxfce4util-common ...
dpkg: warning: downgrading orage from 4.10.0-1~ppa0.12.04.1 to 4.8.3-1.
Preparing to replace orage 4.10.0-1~ppa0.12.04.1 (using .../orage_4.8.3-1_amd64.deb) ...
Unpacking replacement orage ...
dpkg: warning: downgrading xfce4-cpugraph-plugin from 1.0.5-0ubuntu1~ppa1 to 1.0.1-2.
Preparing to replace xfce4-cpugraph-plugin 1.0.5-0ubuntu1~ppa1 (using .../xfce4-cpugraph-plugin_1.0.1-2_amd64.deb) ...
Unpacking replacement xfce4-cpugraph-plugin ...
dpkg: warning: downgrading xfce4-datetime-plugin from 0.6.2-0ubuntu1~ppa0.12.04.1 to 0.6.1-3ubuntu1.
Preparing to replace xfce4-datetime-plugin 0.6.2-0ubuntu1~ppa0.12.04.1 (using .../xfce4-datetime-plugin_0.6.1-3ubuntu1_amd64.deb) ...
Unpacking replacement xfce4-datetime-plugin ...
dpkg: warning: downgrading xfce4-taskmanager from 1.0.1-1~ppa0.12.04.1 to 1.0.0-2.
Preparing to replace xfce4-taskmanager 1.0.1-1~ppa0.12.04.1 (using .../xfce4-taskmanager_1.0.0-2_amd64.deb) ...
Unpacking replacement xfce4-taskmanager ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Setting up libexo-common (0.6.2-4) ...
Installing new version of config file /etc/xdg/xfce4/helpers.rc ...
Setting up libexo-helpers (0.6.2-4) ...
Setting up libexo-1-0 (0.6.2-4) ...
Setting up xfconf (4.8.1-1) ...
Setting up libxfconf-0-2 (4.8.1-1) ...
Setting up xfce-keyboard-shortcuts (4.8.1-1) ...
Installing new version of config file /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml ...
Setting up libxfce4ui-1-0 (4.8.1-1) ...
Setting up thunar-data (1.2.3-3ubuntu2) ...
Installing new version of config file /etc/xdg/Thunar/uca.xml ...
Setting up libthunarx-2-0 (1.2.3-3ubuntu2) ...
Setting up exo-utils (0.6.2-4) ...
Setting up thunar (1.2.3-3ubuntu2) ...
Setting up thunar-volman (0.6.1-0ubuntu1) ...
Setting up libgarcon-common (0.1.11-0ubuntu1) ...
Installing new version of config file /etc/xdg/menus/xfce-applications.menu ...
Setting up libgarcon-1-0 (0.1.11-0ubuntu1) ...
Setting up xfce4-appfinder (4.8.0-3) ...
Setting up xfce4-notifyd (0.2.2-1) ...
Setting up xfce4-panel (4.8.6-2ubuntu2) ...
Installing new version of config file /etc/xdg/xfce4/panel/default.xml ...
Setting up xfce4-settings (4.8.3-1ubuntu3) ...
Installing new version of config file /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml ...
Setting up xfce4-session (4.8.3-0ubuntu2) ...
Installing new version of config file /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml ...
Installing new version of config file /etc/xdg/xfce4/xinitrc ...
Setting up xfce4-terminal (0.4.8-1ubuntu1) ...
Setting up xfce4-utils (4.8.3-1ubuntu2) ...
Setting up xfdesktop4-data (4.8.3-2ubuntu7) ...
Setting up xfdesktop4 (4.8.3-2ubuntu7) ...
Setting up xfwm4 (4.8.3-1ubuntu1) ...
Setting up xubuntu-default-settings (12.04.11) ...
Installing new version of config file /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu ...
Setting up xubuntu-desktop (2.152) ...
Setting up libxfcegui4-4 (4.8.1-5ubuntu1) ...
Setting up xfce4-notes (1.7.7-2ubuntu1) ...
Setting up xfce4-notes-plugin (1.7.7-2ubuntu1) ...
Setting up xfce4-netload-plugin (1.1.0-1) ...
Setting up xfce4-dict (0.6.0-5) ...
Setting up xfce4-quicklauncher-plugin (1.9.4-9) ...
Setting up xfce4-weather-plugin (0.7.4-3) ...
Setting up xfce4-verve-plugin (1.0.0-1) ...
Setting up xfce4-indicator-plugin (0.4.0-0ubuntu2) ...
Setting up xfce4-mailwatch-plugin (1.1.0-5) ...
Setting up xfce4-power-manager-data (1.0.11-0ubuntu2) ...
Setting up xfce4-power-manager (1.0.11-0ubuntu2) ...
Installing new version of config file /etc/xdg/autostart/xfce4-power-manager.desktop ...
Setting up xfburn (0.4.3-4ubuntu1) ...
Setting up parole (0.2.0.6-1) ...
Setting up xfce4-systemload-plugin (1:1.0.0-1ubuntu1) ...
Setting up libxfce4util-bin (4.8.2-1) ...
Setting up xfce4-xkb-plugin (0.5.4.3-1ubuntu1) ...
Setting up xfce4-places-plugin (1.2.0-3) ...
Setting up xfce4-screenshooter (1.8.0-2) ...
Setting up gigolo (0.4.1-3) ...
Setting up libxfce4util-common (4.8.2-1) ...
Setting up orage (4.8.3-1) ...
Setting up xfce4-cpugraph-plugin (1.0.1-2) ...
Setting up xfce4-datetime-plugin (0.6.1-3ubuntu1) ...
Setting up xfce4-taskmanager (1.0.0-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
PPA purged successfully using aptitude fallback



```

---

### Post by Ace..... on 2015-08-02
**Success!**
I'm now back to 4.8 and I've been able to add date & time to the panel :)

I note:
```
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-77 linux-headers-3.2.0-77-generic
Use 'apt-get autoremove' to remove them.

```

Hmmm!
It looks like it left everything:
```
$ sudo apt-get autoremove
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

Fine!

I think this thread can be marked solved.
Thanks to everybody for accompanying me on this journey :)

While it's possible to say "I've wasted my time, by arriving back at the exact same point of departure".
I would disagree.

I've learned a great deal from it...... so it was very worthwhile ;)

:p

---

