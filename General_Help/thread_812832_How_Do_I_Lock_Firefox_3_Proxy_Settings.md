---
title: "How Do I Lock Firefox 3 Proxy Settings?"
date: 2008-05-30
forum: General Help
---

### Post by Matthew Wiebelhaus on 2008-05-30
I was wondering if anyone knows how to lock the firefox 3 beta 5 proxy settings because we are using dansgaurding which uses a proxy for content filtering. If you cannot lock the proxy settings in firefox users can change it back to direct connection which bypasses the web content filtering. So my question is simple how do I lock firefox 3 beta 5 proxy settings? There is a way to do it in firefox 2 but I cant find one in firefox 3 beta 5.

---

### Post by rosslaird on 2008-09-15
Did you ever find out how to do this?

Ross

---

### Post by Dr Small on 2008-09-15
Generally, Squid and DansGuardian need to be placed on the same system as the firewall. This way, when a user connects, all packets unknowingly are passed through the gateway, through DansGuardian, through Squid and to the internet.

---

### Post by kesomir on 2008-12-10
That doesn't fix the issue if the proxy / dansguardian is installed on the same machine that you are using rather than a dedicated proxy which has to be routed through.

Have you tried taking root ownership of the firefox settings file for the user you wish to lock out? I don't know if this would stop firefox loading, but if it doesn't, the file should be unwriteable the normal user.

It should be in home under .mozilla (hidden folder)

---

### Post by Dr Small on 2008-12-10
> **kesomir said:**
> That doesn't fix the issue if the proxy / dansguardian is installed on the same machine that you are using rather than a dedicated proxy which has to be routed through.



If Squid + Dansguardian are running on the same system as Firefox, a few iptables rules can route all traffic through Dansguardian.

---

### Post by capt_kirk on 2009-08-29
I finally figured out how to lock the proxy settings in Firefox 3 under Ubuntu.  I've posted a little longer note in my blog, and if I get updates, I'll post them there: [http://kirksblog.steffensenfamily.com/archives/24](http://kirksblog.steffensenfamily.com/archives/24)

1.  Create a file called loadcustom.js in /usr/lib/firefox-3.0.x/defaults/preferences/, where 3.0.x will be something like 3.0.11 or 3.0.14 depending on your current version.  

 Put the following in /usr/lib/firefox-3.0.x/defaults/preferences/loadcustom.js

 [FONT=Courier New]// tell firefox to load customized config file
pref("general.config.obscure_value", 0);
pref("general.config.filename", "firefox.cfg"); 

[/FONT] 2.  Create a file called firefox.cfg in /usr/lib/firefox-3.0.x/ with the following content (the first line in both files must start with a comment):

 [FONT=Courier New]// Lock specific preferences in Firefox so that users cannot edit them
lockPref("app.update.enabled", false);
lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", 8080);
lockPref("network.proxy.type", 1);
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1, 192.168.1.0/24");
lockPref("network.proxy.share_proxy_settings", true);
lockPref("browser.startup.homepage", "http://www.desiredhomepage.com/"); 
[/FONT]
3.  Restart Firefox, and the preferences should be locked down.  You should be able to use this to lock down any setting in about:config.

---

### Post by jglepage on 2009-09-02
I'm attempting to lock firefox preferences, specifically network.proxy.type.

My technique works, but breaks when upgrades happen.  Here's how I do it:

append the following to /etc/firefox-3.0/pref/firefox.js:
//
pref("general.config.obscure_value", 0); // for MCD .cfg files
pref("general.config.filename", "firefox.cfg");

...then put firefox.cfg in /usr/lib/firefox-3.0.x/, where 3.0.x is the currently installed version.
Contents of firefox.cfg:
//
lockPref("network.proxy.type", 4);


This works.  The network settings are locked at "automatically detect network settings".  However, upon upgrade, the firefox.cfg is NOT copied to the new installation directory.  Also, apt is unable to delete the old installation directory, probably because the new firefox.cfg file is not by apt.

How do you manage to lock settings and NOT have things break upon upgrade?

I Need to be able to manage dozens of machines, and I would prefer not to have to reconfigure everytime firefox upgrades.

---

### Post by capt_kirk on 2009-09-02
Here is an updated procedure to overcome the fact that the Firefox installation directory changes during a Firefox version update.  Thanks to jglepage for developing the perl script to create the symlink.

1.  Add the following to the end of  /etc/firefox-3.0/pref/firefox.js:
 ```
// tell firefox to load customized config file
pref("general.config.obscure_value", 0);
pref("general.config.filename", "firefox.cfg");

```2.  Create a file called firefox.cfg in /etc/firefox-3.0/pref/ with the following content (the first line in both files must start with a comment):
 ```
// Lock specific preferences in Firefox so that users cannot edit them
lockPref("app.update.enabled", false);
lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", 8080);
lockPref("network.proxy.type", 1);
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1, 192.168.1.0/24");
lockPref("network.proxy.share_proxy_settings", true);
lockPref("browser.startup.homepage", "http://www.desiredhomepage.com/");

```3. Create another file in /etc/firefox-3.0/pref/ called copyfirefox.cfg.pl with the following contents (Thanks to Jeffrey LePage for this script):
 ```
# start of file
use strict;

# this gets the current firefox version
my $fire_ver = `/usr/bin/firefox -v`;

# this parses the version
chomp($fire_ver);
$fire_ver =~ s/^\s*Mozilla\s+Firefox\s+([\d\.]+).*$/$1/;
#Mozilla Firefox 3.0.13, Copyright (c) 1998 - 2009 mozilla.org

# this looks for firefox.cfg
if( -e "/usr/lib/firefox-$fire_ver/firefox.cfg" )
{
 # firefox.cfg exists - this is good, no action is necessary
}
else
{
 # make a symlink
 symlink("/etc/firefox-3.0/pref/firefox.cfg", "/usr/lib/firefox-$fire_ver/firefox.cfg");
}
# end of  file 
```4. Open the root crontab editor by typing the following in a terminal window:
 ```
sudo crontab -e
```Add the following to the end of the root crontab in the crontab editor:
 ```
# Copy firefox.cfg to the current Firefox binary directory
# to keep it working following an upgrade until this bug is fixed.
* * * * * /usr/bin/perl /etc/firefox-3.0/pref/copyfirefox.cfg.pl /dev/null 2>&1
```This script will create a symlink to firefox.cfg every minute in the current Firefox binary directory (/usr/lib/firefox-3.0.x where x is the version number) to protect againt upgrades where the directory changes to x+1.  This is a very short script, so running it every minute will have almost no CPU overhead.  But if you want even less CPU overhead, you could change the first asterisk in the crontab entry to */5 to make it run every 5 minutes instead of every minute, or */10 for every 10 minutes, etc.

 5. Wait a minute for the crontab to fire.  Then restart Firefox, and the preferences should be locked down.  You should be able to use this to lock down any setting in about:config.
 
This doesn't fix the problem where apt can't delete the old Firefox installation directory during an update, but it does fix the problem where firefox.cfg doesn't get copied over to the new installation directory.

---

### Post by tsaowang on 2009-11-05
Thanks a lot for this procedure... you made my day !!!

;)

---

### Post by gohsthb on 2009-12-21
This procedure didn't work for me.  I am on Ubuntu 9.10.  It seems they have changed some things.
I edited the file /etc/firefox-3.0/pref/ubufox.js, by adding the following lines.

```
// Lock specific preferences in Firefox so that users cannot edit them
lockPref("app.update.enabled", false);
lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", 8080);
lockPref("network.proxy.type", 1);
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1, 192.168.1.0/24");
lockPref("network.proxy.share_proxy_settings", true);
lockPref("browser.startup.homepage", "http://www.desiredhomepage.com/");
```

This had the same effect as the previous procedure.
I wonder now if it will work through upgrades?

---

### Post by AlexanderDGreat on 2010-01-03
Hi I'm using Firefox 3.5, will this work? Also will this work (not break) when Firefox updates? Thanks. I'm only using Squid as proxy server and Karmic as my server.

---

### Post by TyTiger on 2011-10-10
Newer versions of Ubuntu (10.x at least) no longer use the firefox-3.0 named folder, instead its simply Firefox. I have edited this to suite newer versions of Ubuntu where this change is present.

1.  Add the following to the end of  /etc/firefox/pref/firefox.js:
 ```
// tell firefox to load customized config file
pref("general.config.obscure_value", 0);
pref("general.config.filename", "firefox.cfg");

```2.  Create a file called firefox.cfg in /etc/firefox/pref/ with the following content (the first line in both files must start with a comment):
 ```
// Lock specific preferences in Firefox so that users cannot edit them
lockPref("app.update.enabled", false);
lockPref("network.proxy.http", "127.0.0.1");
lockPref("network.proxy.http_port", 8080);
lockPref("network.proxy.type", 1);
lockPref("network.proxy.no_proxies_on", "localhost, 127.0.0.1, 192.168.1.0/24");
lockPref("network.proxy.share_proxy_settings", true);
lockPref("browser.startup.homepage", "http://www.desiredhomepage.com/");

```
3. Create another file in /etc/firefox/pref/ called copyfirefox.cfg.pl with the following contents (Thanks to Jeffrey LePage for this script):
 ```
# start of file
use strict;

# this gets the current firefox version
my $fire_ver = `/usr/bin/firefox -v`;

# this parses the version
chomp($fire_ver);
$fire_ver =~ s/^\s*Mozilla\s+Firefox\s+([\d\.]+).*$/$1/;
#Mozilla Firefox 3.0.13, Copyright (c) 1998 - 2009 mozilla.org

# this looks for firefox.cfg
if( -e "/usr/lib/firefox-$fire_ver/firefox.cfg" )
{
 # firefox.cfg exists - this is good, no action is necessary
}
else
{
 # make a symlink
 symlink("/etc/firefox/pref/firefox.cfg", "/usr/lib/firefox-$fire_ver/firefox.cfg");
}
# end of  file 
```
4. Open the root crontab editor by typing the following in a terminal window:
 ```
sudo crontab -e
```Add the following to the end of the root crontab in the crontab editor:
 ```
# Copy firefox.cfg to the current Firefox binary directory
# to keep it working following an upgrade until this bug is fixed.
* * * * * /usr/bin/perl /etc/firefox/pref/copyfirefox.cfg.pl /dev/null 2>&1
```This script will create a symlink to firefox.cfg every minute in the current Firefox binary directory (/usr/lib/firefox-3.0.x where x is the version number) to protect againt upgrades where the directory changes to x+1.  This is a very short script, so running it every minute will have almost no CPU overhead.  But if you want even less CPU overhead, you could change the first asterisk in the crontab entry to */5 to make it run every 5 minutes instead of every minute, or */10 for every 10 minutes, etc.

 5. Wait a minute for the crontab to fire.  Then restart Firefox, and the preferences should be locked down.  You should be able to use this to lock down any setting in about:config.

---

