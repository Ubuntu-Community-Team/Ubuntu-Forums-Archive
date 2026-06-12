---
title: "A Cleaner for Linux"
date: 2007-01-22
forum: General Help
---

### Post by Knewguy on 2007-01-22
Hello,

In XP I'd use Ccleaner and other programs to "clean" my Windows use. Is there a program for Linux that cleans Internet and program use history?

Thanks.

---

### Post by bruenig on 2007-01-22
For firefox there is a lot you can do in edit>preferences>privacy for clearing history and cache. If you want something easier, you can write a script to clear all of this stuff. I have a script that clears trash and thumbnails and recently used at once. I am sure you can add on to that to include whatever else you want to clear.

---

### Post by ardchoille42 on 2007-01-22
Here is a script that I use to clean up some things. You can learn a bit of bash and add to the script:

```

# Empty the trash
if [ -e /home/USERNAME/.Trash/* ]
then
    rm -r /home/USERNAME/.Trash/*
fi

# Delete thumbnails
if [ -d /home/USERNAME/.thumbnails ]
then
    rm -r /home/USERNAME/.thumbnails
fi

# Clear the recently used list
if [ -e /home/USERNAME/.recently-used ]
then
    rm /home/USERNAME/.recently-used
fi

# Delete the xsession errors file
if [ -e /home/USERNAME/.xsession-errors ]
then
    rm /home/USERNAME/.xsession-errors
fi

# Clear the gedit search list
if [ -e /home/USERNAME/.gconf/apps/gnome-settings/gedit/%gconf.xml ]
then
    rm /home/USERNAME/.gconf/apps/gnome-settings/gedit/%gconf.xml
fi

# Clear the Run Applications list
if [ -e /home/USERNAME/.gconf/apps/gnome-settings/gnome-panel/%gconf.xml ]
then
    rm /home/USERNAME/.gconf/apps/gnome-settings/gnome-panel/%gconf.xml
fi

# Delete any existing CSS files
if [ -d /home/USERNAME/.dvdcss ]
then
    rm -r /home/USERNAME/.dvdcss
fi

# Clear bash history
echo "" > /home/USERNAME/.bash_history


```

You'll need to change all instances of "USERNAME" to your user name before running it.
I use that as part of a larger backup script that cleans things out and then backs up my $HOME directory to a tarball on another drive.

---

### Post by lucia_engel on 2007-01-22
[ HOWTO: Cleaning up all those unnecessary junk files...]("http://www.ubuntuforums.org/showthread.php?t=140920")

---

### Post by ardchoille42 on 2007-01-22
> **lucia_engel said:**
> [ HOWTO: Cleaning up all those unnecessary junk files...]("http://www.ubuntuforums.org/showthread.php?t=140920")

Wowsers! Thanks for that link :)

---

### Post by Knewguy on 2007-01-22
Thanks for the link and script, guys. 

Much appreciated.

I'm diggin' this Ubuntu/Linux OS bigtime! :cool: (I'm using M$ less and less....)

---

