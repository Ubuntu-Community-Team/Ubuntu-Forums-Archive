---
title: "Auto-reverting motd"
date: 2007-02-06
forum: General Help
---

### Post by Werner_vd_Walt on 2007-02-06
Referring to a couple of older threads which do not seemed to have been answered, I am bringing up the issue of the auto-reverting motd text again.

After changing the motd text in either /etc/motd (which is just a link in any case) or /var/run/motd directly everything works okay until the box has to be restarted. After the reboot the motd reverts back to the original install text. I have grepped through all the files to try and find the source file feeding this text but the only thing that is found is /var/run/motd itself.

The problem is that this behaviour is not consistant as on different boxes it will sometimes keep the changes through a reboot after the initial customization. If you then later on want to further customize you can forget it as it will now just keep on reverting back to the 1st custom version.

Bizarre... if any knows what is feeding the original text for the motd after the initial install it will be of great help. Alternatively if anyone knows whether the text is being cached somewhere during a session maybe one can clear the cache forcing it to re-read the changes?

Thanks.

Werner

---

### Post by Werner_vd_Walt on 2007-02-07
Okay seeing as this seems to be a problem experienced by a couple of people I did some research and came up with the following. If anything is incorrect or you disagree then you're more than welcome to jump in on the thread :)

In /etc/init.d/ there is a file bootmisc.sh that runs at boot time. In the file there is a section that addresses the update of motd during the boot. Basically what it will do is take a portion of the uname string value and then concatenates the text from the /etc/motd.tail file to it. So whatever is in your motd will just be overwritten with those values. In actual fact it seems like this is the process that actually creates the /var/run/motd file in the first place on the fly at every boot. If you comment these commands out, reboot and check, then you'll see that there is no /var/run/motd.

So to prevent the overwrite of your custom message the best option is:
1. Place the text you want to display in the /etc/motd.tail file and not in the /etc/motd file as everyone always suggests (this is for Ubuntu, I have not checked if it works the same on other distributions).

I tried to comment out the lines in /etc/init.d/bootmisc.sh and then manually create my own /var/run/motd file with the text in it. It seems however there is a clean-up script that runs (I presume at shutdown?) that removes the motd file, so whatever you created there is going to disappear in any case. I haven't been able to figure out which script removes it yet but will post the answer when I have it :)

I hope this helps.

Werner

---

