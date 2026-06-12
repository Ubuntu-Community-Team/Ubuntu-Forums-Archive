---
title: "Need help with bash script I wrote"
date: 2008-03-16
forum: General Help
---

### Post by Madstone on 2008-03-16
I have a simple script I created that is not working properly in cron.  Any help will be appreciated

When I execute the file from the command line it works properly but from within cron only the first line executes and then it stops

The script is set with 755 permissions
The cron job is set up like this 00 06 * * * /home/mynamehere/blocklst/blocklst.script

Here is the entire script

#!/bin/bash

rm /home/mynamehere/.Blocklst/level1.txt      <<< this works then it stops

/usr/bin/wget [http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz) -o blocklst.log

gunzip level1.gz

mv level1 level1.txt

---

### Post by cmnorton on 2008-03-16
The only thing that comes to mind is your script must have the same environment that you have when you login. Check your .bashrc and .bash_profile. What gets defined there that your script also needs?

---

### Post by thinkdez on 2008-03-17
Try sending the output of your script to a log file both independently and through cron.  Hopefully you should get some idea of what is happening.  Maybe part of the process is halting.

It is also advisable that you use full paths so you should have:

```

#!/bin/bash
/bin/rm /home/mynamehere/.Blocklst/level1.txt <<< this works then it stops
/usr/bin/wget http://www.bluetack.co.uk/config/level1.gz -o blocklst.log
/bin/gunzip level1.gz
/bin/mv level1 level1.txt

```

This should eliminate any issues with finding the the specified file.

Another thing to note is who is the script running as?  root?  you? someone else?
Check the permissions on the folder '.Blocklst'  It could be that permission is failing someplace causing line 2 not to execute.

Another thing to check is if the script is closing?  Do you see multiple versions running when you do a
```
ps -ef|grep blocklst.script
```

This would indicate that the script is hanging, otherwise the script is completing but with errors and you will need to find out what those are by sending the output to a log file and determining the problem from there.

Good Luck

---

### Post by jocko on 2008-03-17
```
 #!/bin/bash

rm /home/mynamehere/.Blocklst/level1.txt      <<< this works then it stops

/usr/bin/wget [http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz) -o [COLOR=Red]blocklst.log[/COLOR]

gunzip [COLOR=Red]level1.gz[/COLOR]

mv [COLOR=Red]level1 level1.txt[/COLOR]
```You may need to specify the full path to the files in red to make sure everything is run where you want it.

Or:
```
 #!/bin/bash

[COLOR=Red]cd /home/mynamehere/.Blocklst/[/COLOR]
rm level1.txt

/usr/bin/wget [http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz) -o blocklst.log

gunzip level1.gz

mv level1 level1.txt
```
if all commands should be run in the same directory.

---

