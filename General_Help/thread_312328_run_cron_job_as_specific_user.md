---
title: "run cron job as specific user"
date: 2006-12-04
forum: General Help
---

### Post by harty83 on 2006-12-04
I need to run a cron job as a specific user because it will not run correctly as root.  I've created an executable script in /etc/cron.hourly to run another script like this:

```
#!/bin/sh
sudo -u alan /usr/bin/web-snapshot
```

The script web-snapshot works fine if I run it from the command line as the user.  But, it will not work when ran by a cron job by root even with the sudo -u alan option.  

cron is running.

Any ideas?

Thanks!
Alan

---

### Post by evilghost on 2006-12-04
Login as that user that you wish to run the application as.  Run "crontab -e" and create a new Cron line.

You can also use sudo:
```

echo your_password|sudo -u your_username -S your_command.sh

```

---

### Post by evilghost on 2006-12-04
Side note, it could be your script is fine but Cron is freaking out.  It appears that it doesn't like files with an extension.  See [http://www.ubuntuforums.org/showthread.php?t=263842](http://www.ubuntuforums.org/showthread.php?t=263842)

---

### Post by harty83 on 2006-12-04
I tried crontab -e and added ```
# m h  dom mon dow   command
* * * * * /usr/bin/web-snapshot

```

---

### Post by evilghost on 2006-12-04
Is websnapshot a bash script?   Mind posting the contents if not binary?

---

### Post by harty83 on 2006-12-04
> **evilghost said:**
> Is websnapshot a bash script?   Mind posting the contents if not binary?

it is a bash script:

```
#!/bin/bash

#directory you want the snapshots to be kept
LOCATION="/home/alan/Background/"

#website to make a snapshot of
WEBSITE="http://www.google.com"

#check for an internet connection; if not connected, use backup of last successful snapshot
x=`ping -c1 google.com 2>&1`

if [ "$x" = "ping: unknown host google.com" ]; then
	if [ -f $LOCATION/background-2.png ]; then	
		cp $LOCATION/background-2.png $LOCATION/background-1.png
	fi
		
else 
	#work around for cannot talk to klauncher problem - kills other kde start up programs
	#rm /home/alan/.DCOPserver_*__0
	#use kwebdesktop to get a snapshot of the webpage
	/usr/bin/kwebdesktop 1200 600 $LOCATION/background-1.png "$WEBSITE"

	if [ -f $LOCATION/background-1.png ]; then	
		cp $LOCATION/background-1.png $LOCATION/background-2.png
	fi
fi

#use gconftool to set the updated snapshot
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$LOCATION/background-2.png"
#change it twice so that it updates to the new snapshot
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$LOCATION/background-1.png"
gconftool-2 -t str --set /desktop/gnome/background/picture_options "centered"

```

---

### Post by evilghost on 2006-12-04
Code looks fine, very odd.  When it was in /etc/cron.hourly did "run-parts --list /etc/cron.hourly" show it?

---

### Post by PriceChild on 2006-12-04
Sorry for fouling up the previous post....
> **harty83 said:**
> I tried crontab -e and added ```
# m h  dom mon dow   command
* * * * * /usr/bin/web-snapshot

```I think that's your problem... Don't you need to change one of those asterisks to tell it to run some time?

---

### Post by harty83 on 2006-12-05
> **PriceChild said:**
> Sorry for fouling up the previous post....
I think that's your problem... Don't you need to change one of those asterisks to tell it to run some time?

I was under the impression that with all stars it means that it will run every minute of every hour of every day of the week of every day of the month of every month.  :-)

> Code looks fine, very odd. When it was in /etc/cron.hourly did "run-parts --list /etc/cron.hourly" show it?

Yes it is:

```
alan@hartyslaptop:~$ run-parts --list /etc/cron.hourly
/etc/cron.hourly/background

```

---

### Post by harty83 on 2006-12-05
Maybe I've found the problem.

```
alan@hartyslaptop:~$ sudo /etc/init.d/anacron stop
 * Stopping anac(h)ronistic cron: anacron                                                                                            [ ok ] 
alan@hartyslaptop:~$ sudo /etc/init.d/anacron start
 * Starting anac(h)ronistic cron: deferred while on battery power.

```

I am almost always on battery power with my laptop.  How do I get around this?

---

### Post by harty83 on 2006-12-06
Got the cron job to work.

However, it is still not ran as the user.  I need a kde program to run under gnome.  If I run it in a shell by the specific user, it works fine.  But if I run it as a cron job, it still runs as root and gives a "cannot connect to X server" error.  

Any ideas?

Thanks!
Alan

---

