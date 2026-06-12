---
title: "Disable next run of cron job"
date: 2014-11-27
forum: General Help
---

### Post by quadrplax on 2014-11-27
I have a cronjob on my home server that runs an rtcwake command to turn it off overnight, but sometimes I would like to disable that for a night, ex if I'm uploading a YouTube video. Is there any easy way to do this?

---

### Post by coldcritter64 on 2014-11-27
In a terminal use ```
crontab -e
``` this will open your users crontab in the terminal in a text editor (nano usually).

Put a # symbol at the start of the line controlling your "rtcwake command". This is called "commenting out" a line ("#" = "shift + 3" on the keyboard), and will stop that line from being processed (stops your job running). 

**Example:** from one of my old crontabs, this entry was used as a wake up alarm, my computer would play the track "Burn It To The Ground" by Nickleback at 6.45 am every morning unless the # symbol was inserted in the entry (I got to sleep in when the # was in the line :p) ...
> ```
#45 06  * * *   play -v 0.8 '/home/yeti/Burn-It-To-The-Ground.mp3' >/dev/null 2>&1
```

To turn the job back on, same process, but with removing the # symbol.

To save an entry/any changes, in nano press, CTRL + o (lower case "O".) then press "Enter" to actually save the file.
Press CTRL + x, to exit the nano editor.
Press CTRL + d, to exit the terminal.
Done.

**Info Note:** the code ">/dev/null 2>&1"in my crontab command above is an error redirect to "/dev/null" to stop any errors from the actual command and sound playback affecting cron. 
It is for "dumping the errors/verbose terminal output" from the "play" command only. Not usually needed but is sometimes handy to use.

If your job is not in your user's crontab, check out the root crontab with ```
sudo crontab -e
```

Let us know if you can't find the entry, as there may be other locations for it to be set. 
Usually the crontab command is easiest method to add cron entries for a user but there are other ways.

---

### Post by ian-weisser on 2014-11-27
Another way is to put the cron job in it's own file.
- Use root crontab nomen (specify the user)
- Store the file in your /home dir.
```
# My sometimes crontab: /home/yeti/sometimes_cron_job

# m h dom mon dow user  command
45 06  * * * yeti  /usr/bin/play -v 0.8 '/home/yeti/Burn-It-To-The-Ground.mp3' >/dev/null 2>&1
#
```


To enable the cron job, copy or link it to /etc/cron.d
To disable the cron job, delete the copy or link
```
sudo ln /home/yeti/sometimes_cron_job /etc/cron.d/     # Enable the cron job
sudo rm /etc/cron.d/sometimes_cron_job                 # Disable the cron job
```

---

### Post by coldcritter64 on 2014-11-27
> **ian-weisser said:**
> Another way is to put the cron job in it's own file.
- Use root crontab nomen (specify the user)
- Store the file in your /home dir.
```
# My sometimes crontab: /home/yeti/sometimes_cron_job

# m h dom mon dow user  command
45 06  * * * yeti  /usr/bin/play -v 0.8 '/home/yeti/Burn-It-To-The-Ground.mp3' >/dev/null 2>&1
#
```


To enable the cron job, copy or link it to /etc/cron.d
To disable the cron job, delete the copy or link
```
sudo ln /home/yeti/sometimes_cron_job /etc/cron.d/     # Enable the cron job
sudo rm /etc/cron.d/sometimes_cron_job                 # Disable the cron job
```This OP, is much easier for quick switching on/off.

Some notes,

1. I used "sudo **nano** /home/yeti/sometimes_cron_job" to create a root owned file in my home folder. NO use of the crontab command at all for creating the file.

2. Copied, pasted and altered to suit the "sometimes_cron_job" example contents to the file in nano. Tested by setting the time only a few minutes into the future by the desktop clock. Saved and exited.

3. Kept getting an invalid link warning with the linking, tried a symlink (ln -s) and it took.

4. A few minutes later the song fired up.

OP, note how ian-weisser has included the full path to the application /usr/bin/play and has also specified my user name in this example "yeti" in the line.

@ ian-weisser, thanks for the tip. I will be using that myself in future, a far easier technique than full manual editing. Cheers, coldcritter64 :)

---

