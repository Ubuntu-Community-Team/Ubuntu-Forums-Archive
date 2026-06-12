---
title: "Computer saying disk space is full even though it isn't"
date: 2013-02-05
forum: General Help
---

### Post by acarnagey on 2013-02-05
Hi all,

I am having issues to where I can't use my computer after a couple of days unless I restart the computer.  Ubuntu is saying that my HD is full even though its not.  Not sure what is causing this any ideas would be awesome.  Here is a before and after snapshot after restarting that seems to be a temporary workaround to the problem, looking for a permanent solution to this so I don't have to reboot every time this happens.

before
[http://farm9.staticflickr.com/8374/8449701648_1e08879511_c.jpg](http://farm9.staticflickr.com/8374/8449701648_1e08879511_c.jpg)

after
[http://farm9.staticflickr.com/8355/8449702576_557b4e59bb_c.jpg](http://farm9.staticflickr.com/8355/8449702576_557b4e59bb_c.jpg)

Thanks,
Adam

---

### Post by papibe on 2013-02-05
Hi acarnagey. Welcome to the forums ):P

Could you post the result of these 2 commands?
```
df -h

df -i
```
Regards.

---

### Post by oldfred on 2013-02-06
If you are looking at the 100% at the top that is just saying that that is 100% of your partition and then it shows the % of that 100% that is each folder. It is not saying that you have used 100%.

To me the commands posted by papibe are more clear. Or use gparted to see partitions & use.

---

### Post by rnerwein on 2013-02-06
> **oldfred said:**
> If you are looking at the 100% at the top that is just saying that that is 100% of your partition and then it shows the % of that 100% that is each folder. It is not saying that you have used 100%.

To me the commands posted by papibe are more clear. Or use gparted to see partitions & use.
hi
sound for me there is a hidden file. that means:
if a file is created and then remove by any body but the creator is still running and don't close the file the diskspace is still used (there for the disk looks ok after reboot). you can find such files with the command lsof.
sudo lsof > bla
sudo sort -rn --key=7 bla | more
look in the output for "(deleted)" . kill the creator and the disk space is freed.
but it must be a very, very big file ! (some system processes uses hidden files too !)
cheers

---

### Post by acarnagey on 2013-02-06
@papibe: Thanks for the welcome!  I need to wait until the disk space issue reoccurs before running the df commands, just yesterday I had restarted my computer to temporarily fix the disk space issue. Will run the df commands when the issue happens again.

@rnerwein: This sounds like it could be the issue? So some more background on this. About a month ago I noticed my ~/.xsession-errors file was pretty huge (like 400GB or something crazy like that, taking up all my free space I had, the file grew pretty quickly) so I created a cron job to constantly check if its there and delete it.

e.g.

sudo crontab -e
*/10 * * * * rm -rf /home/adam/.xsession-errors

So quite possibly I need to  kill the creator?  Anyhow I will run those commands and report back when the issue occurs again.

Thanks guys!

---

### Post by Impavidus on 2013-02-07
This explains a lot.  .xsession-errors is deleted (technically speaking unlinked), so it's no longer present in the file system, but stays on disk until the last program using is closes the file, just as rnerwein explained. Unfortunately this program could very well be something important, so killing it may kill your desktop. Better to find out why it writes so many errors to the log and fix that.

I've also seen people who made a symbolic link from .xsession-errors to /dev/null. This will redirect all error messages directly to the memory hole, without filling disk space. Not so nice as fixing the thing that causes the errors, but it prevents full disks.

---

### Post by rnerwein on 2013-02-07
> **acarnagey said:**
> @papibe: Thanks for the welcome!  I need to wait until the disk space issue reoccurs before running the df commands, just yesterday I had restarted my computer to temporarily fix the disk space issue. Will run the df commands when the issue happens again.

@rnerwein: This sounds like it could be the issue? So some more background on this. About a month ago I noticed my ~/.xsession-errors file was pretty huge (like 400GB or something crazy like that, taking up all my free space I had, the file grew pretty quickly) so I created a cron job to constantly check if its there and delete it.

e.g.

sudo crontab -e
*/10 * * * * rm -rf /home/adam/.xsession-errors

So quite possibly I need to  kill the creator?  Anyhow I will run those commands and report back when the issue occurs again.

Thanks guys!
ups
most people don't know thinks about hidden files ( by the side - this is a very old trick from hackers to have a conversation between processes). but in your case you must get rid of the error messages. post a couple lines of that errors. and another tricky is to see what is in the hidden files (some times very useful if you delete a file and 1. the creator is still running and you want back the contens). 
cd /proc/PID_of_the process/fd
cat the fd-number of the deleted file e.g.: cat 6 >/tmp/bla and you get the contens ;-)
and remember: rm -rf don't solve your problem. and !!!!!! don't play with "-rf" a little error and your system is gone ! (just use "rm" thats should be enougth)
cheers

---

### Post by acarnagey on 2013-02-07
Hmm ok, I'll put the cron job on ice and have a look at the tail of .xsession-errors, figure out how to actually fix the error instead of 
ln -s .xsession-errors /dev/null it

Then I'll repost back with the repeat error thats spam appending to that file.

Thanks yall.

---

### Post by acarnagey on 2013-02-09
Issue happened again, here are the results:

adam@ubuntu-saturn:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       455G  432G     0 100% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           791M  1.2M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  184K  2.0G   1% /run/shm
cgroup          2.0G     0  2.0G   0% /sys/fs/cgroup

Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda5      30269440 342622 29926818    2% /
udev             495676    547   495129    1% /dev
tmpfs            506121    521   505600    1% /run
none             506121      4   506117    1% /run/lock
none             506121      8   506113    1% /run/shm
cgroup           506121      9   506112    1% /sys/fs/cgroup

adam@ubuntu-saturn:~$ sudo sort -rn --key=7 bla | more
zeitgeist  2670            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
vino-serv  2459            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
update-no  2765            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
update-ma  4367            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
telepathy  2663            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
sh         2529            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
polkit-gn  2461            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
nm-applet  2464            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
nautilus   2454            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gtk-windo  2530            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gnome-ter 12268            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gnome-set  2439            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gnome-ses  2374            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gnome-scr  2671            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gnome-fal  2455            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gdu-notif  2658            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
evolution  2695            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
empathy   27474            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
deja-dup-  2900            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
compiz     2447            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
bluetooth  2456            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
...

The .xsession-errors file wasn't in ~/ anymore even though I put rm -rf .xsession-errors on ice.

Any thoughts?

---

### Post by rnerwein on 2013-02-09
> **acarnagey said:**
> Issue happened again, here are the results:

adam@ubuntu-saturn:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       455G  432G     0 100% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           791M  1.2M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  184K  2.0G   1% /run/shm
cgroup          2.0G     0  2.0G   0% /sys/fs/cgroup

Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda5      30269440 342622 29926818    2% /
udev             495676    547   495129    1% /dev
tmpfs            506121    521   505600    1% /run
none             506121      4   506117    1% /run/lock
none             506121      8   506113    1% /run/shm
cgroup           506121      9   506112    1% /sys/fs/cgroup

adam@ubuntu-saturn:~$ sudo sort -rn --key=7 bla | more
zeitgeist  2670            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
vino-serv  2459            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
update-no  2765            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
update-ma  4367            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
telepathy  2663            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
sh         2529            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
polkit-gn  2461            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
nm-applet  2464            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
nautilus   2454            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gtk-windo  2530            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gnome-ter 12268            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gnome-set  2439            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gnome-ses  2374            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gnome-scr  2671            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gnome-fal  2455            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
gdu-notif  2658            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
evolution  2695            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
empathy   27474            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
deja-dup-  2900            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
compiz     2447            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
bluetooth  2456            adam    2w      REG                8,5 448007909376   20578469 /home/adam/.xsession-errors (deleted)
...

The .xsession-errors file wasn't in ~/ anymore even though I put rm -rf .xsession-errors on ice.

Any thoughts?
hi 
now you see (look at the file size 448007909376) what a hidden file is. you can't see it with "ls" but it is there ! (that's why with rm you only delete the inode-entry in the directory and the file is still open by some processes - system-file table !)
but sorry the error messages don't say nothing to me because they come from your 
"rm" command. 
hint: cd /proc/2670/fd  (you can take every PID - here it is the pid of zeitgeist)
ls -l
tail -f the_number_of_the_link_to_your_.xsession-errors (e.g. 2) 
post the output (as you see the file exists !)
run: touch .xsession-errors then logout and login again and watch the .xsession-errors file. then post the output of the last 20 or 30 lines.
have more fun
cheers

---

### Post by acarnagey on 2013-02-09
Ok did a sudo reboot after doing a touch .xsession-errors now I am seeing

adam@ubuntu-saturn:~$ tail -n 50 .xsession-errors

** (vino-server:1919): WARNING **: Deferring authentication of 'vps-3618.united-hoster.de' for 5 seconds


** (vino-server:1919): WARNING **: VNC authentication failure from 'vps-3618.united-hoster.de'

09/02/2013 05:53:12 PM rfbAuthPasswordChecked: password check failed
09/02/2013 05:53:13 PM [IPv4] Got connection from client vps-3618.united-hoster.de
09/02/2013 05:53:13 PM   other clients:
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM Client Protocol Version 3.4
09/02/2013 05:53:13 PM Ignoring minor version mismatch

** (vino-server:1919): WARNING **: Deferring authentication of 'vps-3618.united-hoster.de' for 5 seconds


** (vino-server:1919): WARNING **: VNC authentication failure from 'vps-3618.united-hoster.de'

09/02/2013 05:53:18 PM rfbAuthPasswordChecked: password check failed
09/02/2013 05:53:19 PM [IPv4] Got connection from client vps-3618.united-hoster.de
09/02/2013 05:53:19 PM   other clients:
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM Client Protocol Version 3.4
09/02/2013 05:53:19 PM Ignoring minor version mismatch

** (vino-server:1919): WARNING **: Deferring authentication of 'vps-3618.united-hoster.de' for 5 seconds

File is growing super fast.

---

### Post by rnerwein on 2013-02-10
> **acarnagey said:**
> Ok did a sudo reboot after doing a touch .xsession-errors now I am seeing

adam@ubuntu-saturn:~$ tail -n 50 .xsession-errors

** (vino-server:1919): WARNING **: Deferring authentication of 'vps-3618.united-hoster.de' for 5 seconds


** (vino-server:1919): WARNING **: VNC authentication failure from 'vps-3618.united-hoster.de'

09/02/2013 05:53:12 PM rfbAuthPasswordChecked: password check failed
09/02/2013 05:53:13 PM [IPv4] Got connection from client vps-3618.united-hoster.de
09/02/2013 05:53:13 PM   other clients:
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM      vps-3618.united-hoster.de
09/02/2013 05:53:13 PM Client Protocol Version 3.4
09/02/2013 05:53:13 PM Ignoring minor version mismatch

** (vino-server:1919): WARNING **: Deferring authentication of 'vps-3618.united-hoster.de' for 5 seconds


** (vino-server:1919): WARNING **: VNC authentication failure from 'vps-3618.united-hoster.de'

09/02/2013 05:53:18 PM rfbAuthPasswordChecked: password check failed
09/02/2013 05:53:19 PM [IPv4] Got connection from client vps-3618.united-hoster.de
09/02/2013 05:53:19 PM   other clients:
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM      vps-3618.united-hoster.de
09/02/2013 05:53:19 PM Client Protocol Version 3.4
09/02/2013 05:53:19 PM Ignoring minor version mismatch

** (vino-server:1919): WARNING **: Deferring authentication of 'vps-3618.united-hoster.de' for 5 seconds

File is growing super fast.
hi
i see - the time stamps - first stop your vino-server --> PID 1919. i think this process is, i'll call it a run-away.
check out what you can do against this message:
09/02/2013 05:53:19 PM Client Protocol Version 3.4
09/02/2013 05:53:19 PM Ignoring minor version mismatch
is it really ignored ??
if this message is coming from "vps-3618.united-hoster.de" - concratulation you create a DOS attack on both sides - yours too.
:-)   :-)  ;-)
cheers

---

