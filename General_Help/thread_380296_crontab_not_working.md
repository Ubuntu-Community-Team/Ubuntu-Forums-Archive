---
title: "crontab not working?"
date: 2007-03-09
forum: General Help
---

### Post by matt91 on 2007-03-09
i am need to run a dns update client automatically. i can run this manually through the terminal however i cannot through a crontab. i followed the howto on the forum by doing a crontab -e and saving, it is shown as adding them when i save. here is the crontab i created using every 1min for testing;

MAILTO=matt@m91.co.uk
# m h  dom mon dow   comman
* * * * * echo "hello" > /root/test
* * * * * /usr/local/dnsmax/dnsmax.pl --updateip

the ip updating doesnt work and the echo to /root/test doesnt work. any ideas?

Thanks, Matt

---

### Post by llamakc on 2007-03-09
Your first entry for both minutes would look like this for every minute:

*/1
*/1

...like that.

---

### Post by matt91 on 2007-03-09
just noticed that the hello echo is working but it is the update which doesnt work still. the */1 doesnt make any difference.

---

### Post by matt91 on 2007-03-09
i have tried various other scripts and all that i have found to work is the echo. the dns update client is [http://www.dynamicdnsclient.com/perl/](http://www.dynamicdnsclient.com/perl/) and is fully functional when run manually.

---

### Post by konst88 on 2007-03-09
Are you running it as root?

---

### Post by llamakc on 2007-03-09
Is your script executable? Does the first line have the full path to your perl binary?

I've always just wrapped my scripts in a shell script. I know there are many ways to do things, but that's worked for me.

For example, I would make your script executable first.

Next, I'd create in /usr/local/bin this:

#!/bin/sh
## mywrapperdnsscript.sh

/usr/bin/perl /usr/local/dnsmax/dnsmax.pl --updateip

# end

Save that @ /usr/local/bin/mywrapperdnsscript.sh and make it executable. Then put THAT in my cron like:

*/1 * * * * /usr/local/bin/mywrapperdnsscript.sh 2>&1

Remember, cron is unaware of your ENV.

---

### Post by matt91 on 2007-03-09
just tried that and it doesnt work. iv tried adding putting /usr/bin/perl before the script in the crontab and this doesnt work iether. all the files are 0777 permissioned including the dnsmax config file. the hdd ticks on the server on the minute. i have been able to do a /etc/init.d/whatever stop from the crontab:confused:

---

### Post by llamakc on 2007-03-09
Cron doesn't run with the environment that your users have. 

Are you checking the logs while running the script?

Add this to the end of your crontab line: 

>> /path/to/test.log 2>&1

making sure /path/to/test.log is writable. Then, open a terminal and run:

tail -f /path/to/test.log 

to watch the output (standard and error).

---

### Post by matt91 on 2007-03-09
Thank you, that log helped. it was to do with the dnsmax configuration file being defined to the relative directory. i changed this to the full directory and it worked:)

---

### Post by WW on 2007-03-09
About ***/1** in the first column:  There is nothing wrong with doing that, but it is redundant.  Just plain ***** works fine, too.

EDIT: Oops, I just noticed matt91 already pointed that out a few posts back.

---

### Post by llamakc on 2007-03-09
> **WW said:**
> About ***/1** in the first column:  There is nothing wrong with doing that, but it is redundant.  Just plain ***** works fine, too.

Thanks! I didn't know that.

---

### Post by MemorX on 2007-10-31
Hi,

I am a debian user, and had this for my crontab on debian (working):

# m h  dom mon dow   command
0-59   *   *   *   * /usr/bin/startscript

The script is working perfectly (on ubuntu server), but it has to be started manually, crontab wont run it with the settings above.. Is there something wrong with them? The script should be run every minute.

I have tried some of the things suggested in the thread, and the only thing that seems to work is:

# m h  dom mon dow   command
0-59 * * * * /usr/bin/startscript >> /tmp/test.log 2>&1

However, the logfile has no errors, and I dont want it to be written, does anyone know what might be wrong?

---

