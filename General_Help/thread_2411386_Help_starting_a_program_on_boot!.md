---
title: "Help starting a program on boot!"
date: 2019-01-29
forum: General Help
---

### Post by dsipe110 on 2019-01-29
I just recently built a slate server for API documentation and Im curious about getting this to start on boot.

OS Ubuntu 18.04
Command to start the server
    bundle exec middleman server

This command has no fork so it run actively in the session you have run the command in.
Ive tried using cron to run a small start script.

Start script: slate_start.sh

#!/bin/sh
cd ~/slate && bundle exec middleman server

This works if I run the command in terminal but does not start on boot as I would have hoped. I tried in both administrator and root crontabs. i have additionally copied this script to /etc/init.d, gave it the proper execute permissions and run the proper [COLOR=#242729][FONT=Consolas]update-rc.d command.
Nothing seems to be capable of running this program on boot.

My next thought was to run it in screen but I cannot find out how to open a screen and run the program on boot either.

Any help would be greatly appreciated.[/FONT][/COLOR]

---

### Post by yancek on 2019-01-29
Use @reboot followed by the full path to the executable file in a cron entry.

---

### Post by dsipe110 on 2019-01-29
I tried the following line in both administrator crontab as well as root crontab files.

[COLOR=#000000]@reboot ~/[/COLOR][COLOR=#000000]slate_start.sh

Neither worked.[/COLOR]

---

### Post by HermanAB on 2019-01-29
Well, do you want to run it at a fixed time OR at boot, or do you want to run it at boot only?

If only at boot, then put it in rc.local.

---

### Post by dsipe110 on 2019-01-30
Unfortunately this is still a no-go

Following are the contents of my rc.local file

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


cd ~/slate && bundle exec middleman server


exit 0



I think it has to do with this process not having a fork option. It seems to need an open screen to run.

username@slater-server:~$ sudo ./slate_start.sh
/usr/lib/ruby/vendor_ruby/builder/xchar.rb:111: warning: constant ::Fixnum is deprecated
== The Middleman is loading
== View your site at "http://slate-server:80", "http://x.x.x.x:80"
== Inspect your site configuration at "http://slate-server:80/__middleman", "http://x.x.x.x:80/__middleman"

Closing the session stops the process.

---

