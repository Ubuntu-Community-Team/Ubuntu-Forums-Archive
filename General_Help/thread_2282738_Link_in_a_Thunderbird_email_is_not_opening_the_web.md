---
title: "Link in a Thunderbird email is not opening the web page"
date: 2015-06-16
forum: General Help
---

### Post by ineuw on 2015-06-16
In Xubuntu 14.04, I updated Thunderbird to 38.0.1, and clicked a link to a web page in a message, but it only opens the browser's home page. (Firefox is the default) In previous versions of TB, it would not even open the browser. I also suspect that this problem is somehow related to my previous post here about default browser problem. 
[http://ubuntuforums.org/showthread.php?t=2282264&p=13302931#post13302931](http://ubuntuforums.org/showthread.php?t=2282264&p=13302931#post13302931)

---

### Post by ajgreeny on 2015-06-16
This is a long term bug that some users have managed to overcome in a variety of ways so have a look and try them out.
[https://bugs.launchpad.net/ubuntu/+source/exo/+bug/1427144](https://bugs.launchpad.net/ubuntu/+source/exo/+bug/1427144)

See also thraed about this at [http://ubuntuforums.org/showthread.php?t=2267439](http://ubuntuforums.org/showthread.php?t=2267439)

Also in TB go to **Edit ->Preferences ->Advanced ->General ->Config Editor**, accept the warning and search for **network.protocol-handler.warn-external.http** (and **warn-external.https**) and if needed change it from **false** to **true** by double clicking on it.  See if that helps.

---

### Post by ineuw on 2015-06-17
ajgreeny, thanks for the links and all the info. Strangely, I got it working but in the process of digging, my proverbial shovel hit the x-www-browser file which is maintained by the "update-alternatives" and I managed to corrupt the file. It's where I spent that last three hours - trying to find a way to rebuild/recreate it because the browser alternatives info exists in some master file. I used "sudo update-alternatives --force --all" which showed me the browser info from somewhere - but also told me that my file is corrupt. On top of it, the apt-get system also found a failed and corrupt installation of Firefox 39.0 beta and it's unable to get rid of it. So I have my work cut out for the next few days. . . But definitely thanks again.

---

### Post by ineuw on 2015-06-17
Is it possible to regenerate the corrupted x-www-browser file? I see that the information is stored somewhere because when I use "sudo update-alternatives --force --all" it lists the browsers and their settings. The command below generates the error:

```

sudo update-alternatives --config x-www-browser
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: unexpected end of file while trying to read master file

```

---

### Post by steeldriver on 2015-06-17
I don't think the information is stored anywhere apart from the indicated file: you can check its contents with

```

cat -net /var/lib/dpkg/alternatives/x-www-browser

```

It could be as simple as adding the missing newline

---

### Post by ajgreeny on 2015-06-17
Which x-www-browser file was it that was corrupt?

I have three such files:-

/etc/alternatives/x-www-browser
/usr/bin/x-www-browser
/var/lib/dpkg/alternatives/x-www-browser

The first is a shell script which looks as if it is from firefox, though the list of installed files from FF does not include it, the second is just a link to the first and the third is a configuration for the update-alternatives, listing browsers installed on the system.

What happens if you re-install firefox and any other browsers you have; does it give you a new x-www-browser file, and what about making a change in your preferred applications for web-browser; maybe that will also rebuild the now corrupt file.

---

### Post by Frogs Hair on 2015-06-17
Threads *Merged*

---

### Post by ineuw on 2015-06-17
ajgreeny, thanks again for spending so much time on trying to help me. I do have a lot of answers, as well as some questions. The current status is, I don't have any browsers in Xubuntu, and there is an unrepairable error related to installations. 

```

ineuw@SANFRANCISCO:~$ sudo dpkg --configure -a
Setting up firefox (39.0~b6+build1-0ubuntu0.14.04.1~ricotz1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: invalid status
dpkg: error processing package firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox

ineuw@SANFRANCISCO:~$ sudo apt-get update && sudo apt-get upgrade
.......
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up firefox (39.0~b6+build1-0ubuntu0.14.04.1~ricotz1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: invalid status
dpkg: error processing package firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Some of the answers:

The above FF 39b is a beta FF which I tried to install two days ago and the installation crashed. This is what prevents me from any installations.
Until I get the above fixed, I will not have a working x-www-browser file. It is a file generated by the browser installation.
Think I tried everything in the book to repair the damage but couldn't.

---

### Post by ineuw on 2015-06-18
Finally managed to install Firefox 39b using Synaptic but the error message persists. Reason for using the beta is because the standard release version of FF 38.0 kept crashing

dpkg: error processing package firefox (--configure):
subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox

All problems related to these posts were solved and eliminated installation errors

---

