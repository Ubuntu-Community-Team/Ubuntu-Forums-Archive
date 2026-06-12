---
title: "Can't get cronjob to run"
date: 2016-06-23
forum: General Help
---

### Post by schwim-dandy on 2016-06-23
Hi there everyone!

I've got a cron command that I use to change wallpaper at 15 minute intervals.  The script runs fine in the terminal, (set as executable and owned by the logged in user) and my cron command works across my other computers(Debian, Arch).

crontab -e

15 * * * * /home/schwim/.scripts/wallpaper_changer

I've tried restarting cron and it shows successful.  I'm not seeing anything in /var/log.  Could someone tell me what I can do to get the cronjob to run?

Thanks for your time!

---

### Post by Dennis N on 2016-06-23
```
15 * * * * /home/schwim/.scripts/wallpaper_changer
```

runs at 15 min past each hour.

You want

```
*/15 * * * * /home/schwim/.scripts/wallpaper_changer
```

to have it run every 15 minutes.

---

### Post by schwim-dandy on 2016-06-23
I should have mentioned that I tried both, neither work.  I also tried */1 for testing purposes.  I can not get cron to run the script.

---

### Post by vasa1 on 2016-06-23
Then please post the contents of the script. Maybe that'll provide a clue. There are quite a few reports of things running in a terminal but not as a cron job. Often, it has to do with escaping certain characters to allow cron to do its job.

---

### Post by schwim-dandy on 2016-06-23
Here's the script, which is running successfully via cron jobs in Deb and Arch:

```
#!/bin/bash# directory containing images
DIR="/home/schwim/Cloud/Mega/images/desktop"
# select a random jpg from the directory
PIC=$(ls $DIR/*.jpg | shuf -n1)
# use nitrogen to set wallpaper
nitrogen --set-zoom-fill $PIC

```

---

### Post by Dennis N on 2016-06-23
```
#!/bin/bash# directory containing images
```

is a bad line. Change it to two lines:

```
#!/bin/bash
# directory containing images
```

---

### Post by vasa1 on 2016-06-24
> **Dennis N said:**
> ```
#!/bin/bash# directory containing images
```

**is a bad line**. Change it to two lines:

```
#!/bin/bash
# directory containing images
```
I remember reading something like that but can't remember where. Do you have a nice link for that?

---

### Post by Dennis N on 2016-06-24
> **vasa1 said:**
> I remember reading something like that but can't remember where. Do you have a nice link for that?

No, it was just obvious as soon as I looked at it.

---

### Post by schwim-dandy on 2016-06-24
```
#!/bin/bash


DIR="/home/schwim/Cloud/Mega/images/desktop"


PIC=$(ls $DIR/*.jpg | shuf -n1)


nitrogen --set-zoom-fill $PIC
```

The issue persists.  The script still works fine from the terminal and hotkey but the cron entry does not run it.

---

### Post by vasa1 on 2016-06-24
```
export DISPLAY=":0"
```is suggested here: [https://www.reddit.com/r/archlinux/comments/1uv21h/need_help_with_a_cronnitrogen_script/](https://www.reddit.com/r/archlinux/comments/1uv21h/need_help_with_a_cronnitrogen_script/)

This person switched from GDM to lightdm to get it to work but subsequently could use GDM again: [http://crunchbang.org/forums/viewtopic.php?id=16929](http://crunchbang.org/forums/viewtopic.php?id=16929)

---

### Post by schwim-dandy on 2016-06-24
Problem is the same. Works everywhere but cron.  I'm clearly no expert, but it really seems like the issue has less to do with the script than cron itself, doesn't it?  I'm only saying this because it has worked everywhere I've used it but in one distro's cron system.

```
#!/bin/bash

export DISPLAY=":0"


DIR="/home/schwim/Cloud/Mega/images/desktop"


PIC=$(ls $DIR/*.jpg | shuf -n1)


nitrogen --set-zoom-fill $PIC
```

---

### Post by vasa1 on 2016-06-24
I have export DISPLAY=:0

instead of

export DISPLAY=":0"

in a couple of scripts I run via cron.

---

### Post by steeldriver on 2016-06-24
... another common issue is that the cron environment may have a limited PATH; where is 'nitrogen' located for example? It's good practice to explicitly define a suitable PATH or use absolute paths to any executables

---

### Post by Dennis N on 2016-06-24
I ran this test script:

```
#!/bin/bash
echo "changing Desktop background..."
export DISPLAY=:0
nitrogen --set-zoom-fill /home/dmn/work/mustang-1280x800.jpg
echo "background changed."

```
Lubuntu 16.04 - Nothing happened here, except the two messages. Same if export line is removed. No error messages.

---

### Post by vasa1 on 2016-06-24
See if anything here helps: [http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work](http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work)

---

### Post by Dennis N on 2016-06-24
Tried in Xubuntu 16.04, same script. Again, nothing happens. Preliminary conclusion: nitrogen does not work in Lubuntu or Xubuntu. To be clear, I did not use this in cron, just ran the script in the terminal.

But Xubuntu users can take advantage of it's capabilities: "Desktop Settings" provides automatic wallpaper switching at regular intervals set in minutes. No hassle. Check for this feature in Ubuntu. It may have it.

---

### Post by vasa1 on 2016-06-25
> **Dennis N said:**
> Tried in Xubuntu 16.04, same script. Again, nothing happens. Preliminary conclusion: nitrogen does not work in Lubuntu or Xubuntu. To be clear, I did not use this in cron, just ran the script in the terminal.

But Xubuntu users can take advantage of it's capabilities: "Desktop Settings" provides automatic wallpaper switching at regular intervals set in minutes. No hassle. Check for this feature in Ubuntu. It may have it.
I'm not into wallpapers, but I just installed nitrogen. It works in my Lubuntu 16.04 Openbox session:
```
nitrogen /usr/share/lubuntu/wallpapers
```Now I have to figure out how to get my original background back without logging out. That would be cheating ;)
```
hsetroot -tile /home/vasa1/Dropbox/Backgrounds/gray.png
```does it.

---

### Post by Dennis N on 2016-06-25
On Lubuntu 16.04, the script in post #14 and nitrogen work in Openbox session, but not the Lubuntu session.

The random-selection script (below) also worked in Openbox (but not Lubuntu) session:

```
#!/bin/bash
DIR=/usr/share/lubuntu/wallpapers
PIC=$(ls $DIR/*.jpg | shuf -n1)
echo $PIC
nitrogen --set-zoom-fill $PIC
echo "changed Desktop background..."

```
However, neither script runs in an Openbox cron job - even with the path to nitrogen supplied. 

**nitrogen <folder-with-background-images>** will open a GUI dialog in Openbox allowing selection.

---

### Post by Dennis N on 2016-06-25
> However, neither script runs in an Openbox cron job - even with the path to nitrogen supplied.

Not quite accurate - the scripts run to completion and the command containing nitrogen is executed, but there is no visible result. We can see this from journalctl.

---

