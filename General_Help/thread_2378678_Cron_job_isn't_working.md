---
title: "Cron job isn't working"
date: 2017-11-25
forum: General Help
---

### Post by tharpa on 2017-11-25
cron is running, and I can get it to open leafpad, for example.   I can also run the following command ```
aplay /home/tharpa/wav/clock-grandfather.wav
``` outside of cron (on the command line) and it plays the sound.  However, if I add it as a cron job, using the following line, ```
* * * * * aplay /home/tharpa/wav/clock-grandfather.wav
```it does not play.  I have tried using play instead of aplay, I tried not entering and entering ```
sudo - s
``` before running ```
crontab - e
```.  I have tried installing and using Gnome-schedule, etc.  Any suggestions?

---

### Post by shag00 on 2017-11-25
Code:

 	```
* * * * * aplay /home/tharpa/wav/clock-grandfather.wav
```

I think some of the * need to have values.

The cron job can be run as a normal user and is edited:
```
crontab -e
```
or as superuser
```
sudo crontab -e
```

---

### Post by SeijiSensei on 2017-11-25
Specify the full path to aplay in the cron entry.  It's probably /usr/bin/aplay, but check to make sure.

---

### Post by tharpa on 2017-11-25
Thanks, Shag, but I believe that all *'s are allowable (to run it every minute) unless you're sure otherwise, or can show me documentation to this effect.  Yes, I tried it both ways, with and without sudo.

---

### Post by shag00 on 2017-11-25
tharpa, indeed you are correct, "An asterisk (*) can be used so that every instance (every hour, every weekday, every month, etc.) of a time period is used."

In that case I would follow [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")'s line of thinking, is the cron pointing to an executable file. Not sure what happens in this instance where you have a audio file with some audio playing application set as default player.

---

### Post by tharpa on 2017-11-25
Thanks, Seiji.  I just tried that, but it did not help.

---

### Post by Yellow Pasque on 2017-11-25
[https://askubuntu.com/a/92195](https://askubuntu.com/a/92195)

---

### Post by yancek on 2017-11-25
Are you creating your cron entry in a terminal as a normal user:  crontab -e
then saving it in the vi editor?  If you then do crontab -l, do you see the entry you created.

I just tried this using crontab -e on a sound file as recommended by SeijiSensei and it worked as expected with the full path to aplay but NOTd if I do not have the full path to aplay.  Entry below.  Not sure why it doesn't work for you, check the entry carefully again.

 > * * * * *  /usr/bin/aplay /usr/share/sounds/Oxygen-Im-Nudge.ogg

---

### Post by tharpa on 2017-11-25
Thanks [SIZE=3]**[FONT=arial][[COLOR=#000000]Temüjin[/COLOR]]("https://ubuntuforums.org/member.php?u=327594")[/FONT]**[/SIZE][COLOR=#000000] [/COLOR], I went through the page carefully, but nothing helped.

---

### Post by Yellow Pasque on 2017-11-25
I was pointing out the export DISPLAY tip, since someone specifically mentioned it was needed for aplay. You tried that one, correct?

---

### Post by tharpa on 2017-11-25
Thanks, yancek, I had already tried the full path, but I just tried it again, and it didn't help.  I even picked a file from that same folder.

---

### Post by tharpa on 2017-11-25
Hah, Temujin.  That was it!  play seems to require it too.  Who'd a thunk it?  :cool:

---

