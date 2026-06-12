---
title: "Automated Screenshots"
date: 2007-05-22
forum: General Help
---

### Post by nami on 2007-05-22
Is it possible to take automated screenshots of the desktop at set intervals?  Lets say I want a screenshot taken every hour.  Is it possible to automate this without any user interaction?

---

### Post by eentonig on 2007-05-22
Just put the screenshot command in a little bash script and schedule that to run with cron

To create the script, open a teksteditor at choice and type

> #!/bin/bash
#
# Little script to capture screen images
<command goes here> <options you want to include>



Save the file and check up on how to schedule cron jobs

---

### Post by nami on 2007-05-22
Thanks, I will try this out asap.

---

### Post by nami on 2007-05-22
In the bash file, what command and options do I need to use?

I check the help files for "gnome-panel-screenshot" and there seems to be no option for setting a file name and disabling all user interaction?

---

### Post by Nesman on 2007-09-12
I know this is old, but even if the original poster is no longer interested, maybe it will help someone else.

I used this script to caputre screenshots on a Slackware machine.  It might be more complicated than you wanted, but it worked nicely.  When run, it takes a screenshot every 5 seconds for 25 seconds.

```
#!/bin/bash
#import -window root -display Slacker:2 /home/nesman/public_html/screenshots/`date +%a%d%b%H%M`.jpg
i=0
DISPLAY=:0
export DISPLAY
HOME=/home/nesman
export HOME

while [ $i -lt 5 ]; do
        #import -window root -geometry 800x600 -display localhost:0 -silent /home/nesman/bin/screenshots/`date +%b%d%a%H%M`-$i.jpg
        import -window root -geometry 800x600 -silent /home/nesman/bin/screenshots/`date +%b%d%a%H%M`-$i.jpg

        sleep 5
        i=$((i+1))
done

```

---

### Post by nami on 2007-09-13
I'm still interested!  I'll give this a try asap.  Thanks

---

