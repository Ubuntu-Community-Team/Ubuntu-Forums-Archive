---
title: "While renaming a directory on a mnt, my root partition filled up and now is full"
date: 2017-12-11
forum: General Help
---

### Post by xrintrahx on 2017-12-11
I think I need to figure out what is using all my space in my root partition. I am running a headless Ubuntu server 17.04 as a Plex Media Server. I have 3 4TB drives for media (one for snapraid parity). And the OS and system files are running on a 250GB SSD. I created a root partition of 40GB, and everything has been fine for 6 months. Earlier today I had attempted to rename a fresh blu-ray rip directory (~30GB) with the mv command. It failed at the end and said I had run out of space on device. So I ran a df and saw both the HDD mnts had tons of space on them, but my root partition was 100% full (dev/mapper/***--vg-root). The directory in question I was trying to rename was on a HDD mnt, not on the SSD.  Now, bash auto-complete/tab is no longer working because root is full. I tried rebooting, thinking maybe something was just being cached, but that didn't fix it. It may be a coincidence that root filled upwhile running that mv command, but I doubt it. I've tried running sudo du -h / | grep -P '^[0-9\.]+G' but it spat out all my media directories, and was hard to navigate because the results were so long and included the HDDs. I can't figure out how to limit my search to just the root partition. And maybe the clue that this happened while trying to  rename a large directory with the mv command may be a big hint on what happened to my space.

Thanks,.

---

### Post by dragonfly41 on 2017-12-11
Looking for clues ..
```
history 10
```
gives print of last 10 commands run in terminal

---

### Post by VMC on 2017-12-11
The tool I use for disk usage is 'ncdu'. Its a small program.

---

### Post by xrintrahx on 2017-12-11
I cannot install new programs because of this disk space issue. 

As for the last 10 commands, that well, I got this:

```
 2022  cd working.directory/ 2023  ll
 2024  cd ..
 2025  ll
 2026  sudo mv working.directory/ /Season\ 3/
 2027  ll
 2028  cd w
 2029  cd wor
 2030  ll
 2031  cd working.directory/
 2032  ll
 2033  cd ..
 2034  ll
 2035  sudo mv working.directory/
 2036  sudo mv working.directory/ /storage/TV/Showname/
 2037  ll
 2038  cd ..
 2039  ll
 2040  tmux attach
 2041  ll
 2042  cd ~
 2043  ll
 2044  df -H
 2045  cd ..
 2046  ll
 2047  cd ..
 2048  ll
 2049  ncdu
 2050  du / | sort -nr
 2051  sudo du -h / | grep -P '^[0-9\.]+G'
 2052  df -H
 2053  sudo du -h /dev | grep -P '^[0-9\.]+G'
 2054  sudo du -h /dev/mapper/servername--vg-root | grep -P '^[0-9\.]+G'
 2055  cd /dev/
 2056  cd mapper
 2057  cd servername--vg-root
 2058  ll
 2059  sudo du -h /dev | grep -P '^[0-9\.]+G'
 2060  tmux attaach
 2061  tmux attach
 2062  cd /usr/
 2063  ll
 2064  sudo du -h /dev | grep -P '^[0-9\.]+G'
 2065  cd /var/
 2066  ll
 2067  cd lib
 2068  ll
```

---

### Post by VMC on 2017-12-11
Try this:
```
sudo du -ah / | sort -n -r | head -n 10
```

---

### Post by xrintrahx on 2017-12-11
```
sort: write failed: /tmp/sort9FCeUE: No space left on device
```

---

### Post by xrintrahx on 2017-12-11
I just deleted two install packages that were in my user home directory and ran autoremove, but it didn't seem to free any space, or not enough to bring the 100% down, nor let that du command work, nor bash autocomplete. It probably freed at least 400MB.

---

### Post by xrintrahx on 2017-12-11
Ok, I figured it out, it was this command ```
[COLOR=#000000][FONT=&quot]sudo mv working.directory/ /Season\ 3/
```.

[/FONT][/COLOR]It had instead of renaming the working.directory, it copied it to a new folder at the $ level with the name Season 3 (and that happened to be the root partition even though my working directory was on a HDD mount). Didn't catch that earlier. Now I'm back down to 17% on my root partition, after deleting that folder.

---

### Post by oldfred on 2017-12-11
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

I am no expert on / use in commands. I find I end up with trailing slash and issues of folder under folder or if using / at beginning often copy folder into /.
Do you now have /season and /storage folder now in /?
cd /
ll

I find best to always use full path in commands, but also do as you do in changing to folder.

---

### Post by xrintrahx on 2017-12-11
That forward slash may have killed me, or maybe I needed full directory path. I don't normally rename directories, just individual files. SO I used the same method I use for that, do disastrous consequences. I had the season folder in /, but I deleted it. All is good now. 

Consequently, I couldn't figure out how to properly rename the folder in CLI, so I did it through samba and Windows Explorer. Slow click twice, type in the name, done. I'm getting used to CLI and don't mind it in most instances, but for file control (moving/renaming/deleting) I prefer a GUI. But due to permissions, I can't always do that through my samba share.

---

### Post by yancek on 2017-12-11
> [COLOR=#000000][FONT=&amp]sudo mv working.directory/ /Season\ 3/[/FONT][/COLOR]

The forward slash at the beginning of "/Season\ 3" is telling the system to move that directory to the root of the filesystem.  If you wanted to rename working.directory to Season\ 3, leave off the forward slash and it should be renamed in the same directory in which 'working.directory' now exists, that is if you are running the command from that directory.  You could also from the directory in which 'working.directory' exists used the full path.  The command did exactly what you told it to do.  If you are renaming files/folders on a windows partition why not use windows?

Also, if you had not used sudo in the mv command, you would have received a permission denied message which would probably have been a clue.

---

### Post by xrintrahx on 2017-12-11
Thanks for the tips. I have not had much success moving or renaming files without sudo, so I have got in the habit of always typing it. I think literally every time I use mv or rm, I get a "no permission" message. So I always type sudo before those commands. Is there just a 'rename' command? I think using that would have also avoided accidentally moving 30GBs to the root partition. And it isn't a windows partition. I have set up samba so I can view the media library as a networked drive, something I rarely do. These drives are physically in my server, and were set up via Ubuntu.

---

### Post by yancek on 2017-12-11
Ubuntu and other  Linux distributions are designed as multi-user system which means that the only area you can expect to be able to make these kind of changes is in your /home/username directory.  Substitute your actual 'username'.  Anywhere else, you need root privileges (sudo).  If you have a separate partition with media folders/files, you can change ownership of that mount point and then have access as a user.

If you right click a folder/file, you should see an option to 'rename' and clicking that will get you a box in which to enter the new name, click OK and you're done.  If the folder/file is outside the user home directory, you will again need root/sudo.

Yes there is a rename command, at least two one of which is written in perl and I believe is better than the standard.  You would have to do some reading on how either work     To have changed your working.directory to Season 3 as in your post, you would need to navigate to the directory in which you have 'working.directory' and if it is outside the /home/username, you would need root/sudo privileges.  If it's in your /home/username directory running the following would do it.  You can either use the escape \ character for blank spaces or use quotes as below.  

> rename working.directory 'Season 3' working.directory

---

