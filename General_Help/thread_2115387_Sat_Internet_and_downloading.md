---
title: "Sat Internet and downloading"
date: 2013-02-12
forum: General Help
---

### Post by CWM on 2013-02-12
Ok.. OLDDOS closed the post before I even could reply

I am on satalite internet... Thats all I can get out here.... 

And I asked about a program that I could set to download big files that I need during my free FAP time beteen 12 AM CST to 5 am CST.

 I used the wrong example saying download youtube vids.. I just couldnt think of anything BIG at the time that I wrote the orginal post. 

I just meant something I can set between 12:01 AM CST to 4:58 AM CST to download HUGE FILES... as in... Programs for my pc or files that I need to run my system. 

Just set it and forget it. And know that at 4:58 AM it will stop or pause the downloads so it doesnt cut into my FAP.

That way I could go to bed and I dont have to be up half the night waiting and hoping what I need downloaded is downloading. 

Thank you,
Christopher

---

### Post by Impavidus on 2013-02-13
For torrents, see this thread: [http://ubuntuforums.org/showthread.php?t=913376](http://ubuntuforums.org/showthread.php?t=913376)
It's old but it looks like it still works the same.

For other downloads, I'm sure there's something available, but for me finding one would probably take longer (and certainly be less fun) than writing a script to do it myself. Something like: 
1) User creates a file with URLs to download and directories to save to;
2) User adds script to crontab to run at 0:05 (allowing for offsets in the clock);
3) Script running at night reads lines from the file and calls wget to download the files, maximum N simultaniously;
4) After a download finishes, remove from the list;
5) After 4:00, don't start new downloads.

If I wanted something clever, I could terminate all running instances of wget at 4:55, making sure the script would resume the downloads the next night.

Concerning updates: I think it's possible to set yout update manager to download automatically any updates and do that at night (cron job owned by root). You can install them during the day, after you've inspected the updates. It happens that people complain `Something went wrong after an update but I don't remember what was updated.' Better to look first.

---

### Post by pqwoerituytrueiwoq on 2013-02-13
assuming it will download in the alloted time you could use a simple script as a cron job
```
crontab -e
```make it run this script
```
#!/bin/sh
cd ~/Downloads
file="./list.txt"
if [ -f $file ]; then
   for i in $(cat $file);do 
      wget -nc $i
   done
fi

```it will read list.txt from your downloads folder which should contain a list of URLs it will then download each one in order

you could add a second cron job to kill the script when the unlimited time is up using hte killall command

---

### Post by CWM on 2013-02-14
> **pqwoerituytrueiwoq said:**
> assuming it will download in the alloted time you could use a simple script as a cron job
```
crontab -e
```make it run this script
```
#!/bin/sh
cd ~/Downloads
file="./list.txt"
if [ -f $file ]; then
   for i in $(cat $file);do 
      wget -nc $i
   done
fi

```it will read list.txt from your downloads folder which should contain a list of URLs it will then download each one in order

you could add a second cron job to kill the script when the unlimited time is up using hte killall command



Thanks!!

---

