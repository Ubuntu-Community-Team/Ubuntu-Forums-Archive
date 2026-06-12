---
title: "A suggestion on what to do when you break your system"
date: 2008-04-16
forum: General Help
---

### Post by unutbu on 2008-04-16
The following will certainly not solve all problems, but it can help pinpoint some problems. 

Suppose your system is working fine, then you get adventurous and change or install something which it leaves your system in an undesireable state. 

I suggest the first thing you do is

```
sudo find / -mmin -10 > ~/changed-files
```

This will take a while, but you will be left with a list of all the files that have been modified in the last 10 minutes. 

changed-files will contain a lot of lines starting with /proc, /dev, /sys and maybe a few find error messages. I use the follow perl script to weed out the junk:

```
#!/usr/bin/perl
use strict;
use warnings;

open(FILE,"<","$ENV{HOME}/changed-files") || die;
while (<FILE>) {
    if (!(m|^/dev| or m|^/sys| or m|^/proc| or m|^find:|)) {
	print;
    }
}
close(FILE)
```

You are left with a manageable list of the suspects for what is breaking your machine.

Of course this won't help you one bit if your problem comes from having deleted a file or files. In that case reinstallation of a package may work, or if it was a personal config file, hopefully you've made backups.

---

### Post by unutbu on 2008-04-16
Here is the particular blunder I found myself in, and how the above technique saved me:

I was trying to find a solution to a problem someone posted on ubuntuforums. I thought maybe what was needed was an edited .xsession file. I don't use an .xsession file, so I created a simple one. I logged out, logged back in, found out I don't know enough to replicate a normal gnome session and so I figured my attempt at a solution would not work. 

I figured I'd just delete the .xsession and everything would return to normal. 

Wrong! Upon logging in, I found that I had only half of my gnome panels. The top half in particular. 

I had no idea how to get my gnome panel back. I didn't want to re-install the whole package, because I figured it was something simple that has changed. 

The find command worked like a charm. (By the way, I got this idea from Wayne Pollock. See [http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm))

I found which files in ~/.gconfd had changed recently. I deleted them one at a time on the assumption that whatever was missing would be reinstalled to some default setting. On my second try, I deleted 

```
~/.gconf/apps/panel/applets/window_list_screen0/prefs/%gconf.xml
```
  
and that solved my problem.

---

