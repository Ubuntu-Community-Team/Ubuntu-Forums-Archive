---
title: "vfat filename case bug"
date: 2006-11-02
forum: General Help
---

### Post by david.birch on 2006-11-02
Hi all,
  i have found a strange issue with vfat - all uppercase directory or filenames are displayed/handled as lowercase, i.e if you create a file  "TESTING" it will be stored as "testing" - mixed case is a-ok, i.e. "Testing" will be stored/viewed as "Testing".

my mount command is:
/dev/hda7 /data vfat gid=1000,umask=002,noexec,nosuid 0 0

i am running kernel 2.6.17.10-generic, though this issue has existed for at least a year or more (can't be sure beyond that)

any ideas?

thanks

---

### Post by rattking on 2006-11-02
Hello
check the mount manpage
under Mount options for vfat
I found this

shortname=[lower|win95|winnt|mixed] 
 Defines the behaviour for creation and display of filenames which fit into 8.3 characters. If a long name for a file exists, it will always be preferred display. There are four modes: 


lower 
 Force the short name to lower case upon display; store a long name when the short name is not all upper case. 
win95 
 Force the short name to upper case upon display; store a long name when the short name is not all upper case. 
winnt 
 Display the shortname as is; store a long name when the short name is not all lower case or all upper case. 
mixed 
 Display the short name as is; store a long name when the short name is not all upper case. 
 The default is "lower".

hope that helps

---

### Post by ostorezio on 2008-05-08
Great! I'm having the same problem with Gutsy.

And the solution works, i.e. if I manually mount the VFAT device with the following command, the filename capitalization is OK:

mount -t vfat -o rw,nosuid,nodev,noatime,flush,uid=500,utf8,shortname=mixed /dev/sdc1 /mnt/USB20GB

BUT, how can I tell the mount command that the "shortname=mixed" option is the default for the automatic mount when the device is plugged-in?

Cheers,

              Ezio

---

### Post by ostorezio on 2008-05-26
Serendipity led me to the right solution.

[LIST=1]
[*]Right-click on the desktop icon showing the plugged-in device
[*]Select "Properties"
[*]Go to the "Mounting" tab
[*]There we go, there is a "Shot names" li'l pull-down menu
[*]Select "Mixed"
[*]That's it
[/LIST]

           Ezio

---

