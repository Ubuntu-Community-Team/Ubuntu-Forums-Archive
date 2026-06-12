---
title: "Errors Installing ZoneMinder"
date: 2007-11-04
forum: General Help
---

### Post by coldstatue on 2007-11-04
I installed zoneminder via the guide here:

[http://www.howtoforge.com/video_surveillance_zoneminder_ubuntu](http://www.howtoforge.com/video_surveillance_zoneminder_ubuntu)

I did not confirm that my IP was still static before hand. It wasn't. (Lesson 1: never assume anything.) Being new to LAMP and zoneminder, I figured the easiest way to fix whatever settings were screwed up by me installing with the wrong IP was to reinstall LAMP and zoneminder. (After switching to static IP, which I did.) I should mention here that after the first install, I was able to get to the browser control interface for zoneminder. I cannot get to that point again, though I have tried to wipe out and reinstall all apache, mysql, php, and zoneminder files. Now I think I can reinstall everything fine except that I get an error when installing zoneminder:

```
Setting up zoneminder (1.22.3-8) ...
Starting ZoneMinder: no connection to syslog available
        - getservbyname failed for syslog/tcp and syslogng/tcp
        - /dev/log is not a socket
        - stream /dev/conslog is not writable
        - console is not writable at /usr/share/perl5/ZoneMinder/Debug.pm line 249
failure

invoke-rc.d: initscript zoneminder, action "start" failed.
dpkg: error processing zoneminder (--install):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 zoneminder
```

I know apache is working, as I can go (in a browser) to the hostname Ive set up and get the contents of my /var/www/ folder, as well as a directory for apche2-default. (Clicking on this one gives the message, "It works!".

I tried the test.php steps at this url:

[http://www.tweako.com/using_lamp_on_ubuntu_the_fun_way](http://www.tweako.com/using_lamp_on_ubuntu_the_fun_way)

and it did not work. if I go to my hostname, I see test.php, but clicking it prompts for a download of test.php.

I get no other installation or configuration errors in the course of the first guide I mentioned, until after the zoneminder install, which of course is what you would expect. I can't configure or restart apache, etc. (Only AFTER trying to install zm - it's partial installation is messing with apache in some way.)

Could the php test have anything to do with the zm error?

I'm pretty lost and totally new at this stuff. While I am more than willing to read and learn, it seems like pretty complicated stuff. I sure could use some help.

Thank you for any suggestions.

---

