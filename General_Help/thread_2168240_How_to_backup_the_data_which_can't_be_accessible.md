---
title: "How to backup the data which can't be accessible?"
date: 2013-08-17
forum: General Help
---

### Post by Sriram_Sampathkumar on 2013-08-17
My Ubuntu 12.04 Desktop doesn't boot, so I am trying to get my data from the old Ubuntu using Live USB(**RUNNING UBUNTU FROM THE USB WITHOUT INSTALLING**).  But when I try to copy some files I get error as " You have no  permission to access this". So what is the way that I have to handle to  backup my data. I have taken screenshot of it take a look *_[http://i41.tinypic.com/sbk6ef.png%5B/IMG%5D](http://i41.tinypic.com/sbk6ef.png%5B/IMG%5D)_* 

Please help me.

Thank you

---

### Post by carl4926 on 2013-08-17
In situations like that I've always used parted magic

But I'm wondering... if the live user : ubuntu
Could chown -R the directory in question... not too sure

---

### Post by ajgreeny on 2013-08-17
Three comments to make.


[LIST=1]
[*]What seems to be the problem with booting? Is it getting to a point where you can login to command line, and what about recovery mode? 
[*]You will need another USB drive to back up the files to as you will not be able to write to the live USB 
[*]You should use a **sudo cp** command to copy the data or start the file manager as root with command ```
gksudo nautilus
``` which will enable you to copy the files you want to anywhere with write permissions, ie your second USB drive. 
[/LIST]

You can then, perhaps, try to recover your old OS, though if it is too complicated it may just be simpler to reinstall the whole OS; your choice.

---

