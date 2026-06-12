---
title: "Bash script error handling."
date: 2016-03-17
forum: General Help
---

### Post by Roasted on 2016-03-17
Hi friends. Long story short, my dad runs Ubuntu, has an external hard drive, and I'm trying to set up a crazy simple bash script that I can tie in to a custom desktop file with its own icon. This would allow him to plug in his drive, run the backup "utility", and simply rsync the data to the backup drive. I've gotten everything accomplished, though there's one piece I want to figure out yet. I want there to be a notification in the event an rsync error occurs. Here's the current script.

```
#!/bin/bash
if grep -qs '/media/jason/Backup' /etc/mtab; then
    notify-send "Backup Started"
    rsync -a --progress --delete /home/jason/Desktop/Test /media/jason/Backup/
    notify-send "Backup Complete. Please eject the backup drive."
else
    notify-send "Backup drive not found. Please plug in the backup drive and restart the backup application.";
    exit
fi

```

The mount vs unmounted thing works great. Rsync works great. But let's say, just for sake of argument, that /media/jason/Backup was owned by root:root, thereby giving me no permissions to write to the Backup drive. I want there to be a notification, something simple like "Error backing up." That way he gives me a call and I can look deeper.

I assume I want to tie in another if statement. Something like if rsync error code is 0, proceed to notify-send "Backup Complete" etc etc, else rsync error code (anything but 0) then "notify-send "Error Backing Up""

I'm kind of drawing a blank on how exactly I'd tie that in. Anybody have any suggestions?

---

### Post by HermanAB on 2016-03-18
I solve this type of problem a different way.  Instead of placing a backup widget on the desktop, which then has to deal with missing media and different paths to different media, I put a backup script on the backup disk drive/memory stick itself.  That ensure that the user has to plug it in, wait for the pop-up, open the fie browser and click the backup script - at which point it is all guaranteed to work.

---

### Post by Roasted on 2016-03-18
That's one way to do it. Truth be told in the end I may just write a udev rule to auto execute this process once the drive is plugged in. That said, I'm still looking to learn the proper procedure for this (I have a lengthy "linux notes" text file that I wouldn't mind adding this to).

---

### Post by mcgess on 2016-03-18
Hi

To find out if a bash command has failed check the variable $?, zero is success otherwise its failed.
You might also want the error messages so how about

```
rsync -a --progress --delete /home/jason/Desktop/Test /media/jason/Backup/ 2> >(tee -a ~/error_text >&2)

```

You can then check in file ~/error_text later on to see what went wrong

Martin

---

### Post by Roasted on 2016-03-18
Another thing I just thought about was maybe doing what I already do at home, which appends the date/time to a text file (acting as a backup log file) pending the last successful backup.

This has worked well because in the event there's a failure, due to me having set -e in the top of the script, *everything* below it fails if an issue surfaces. So if I see the date/time as being recent, I know the backup was good.

This may be good for dad since that would provide him with a visual of when the last backup ran. That way he can make his own judgment calls on when to run it again, etc. I could store this txt file on the drive itself, making sure he would never get confused on where it may be located.

---

### Post by mcgess on 2016-03-18
```
#!/bin/bash
if grep -qs '/media/jason/Backup' /etc/mtab; then
    notify-send "Backup Started"
    rsync -a --progress --delete /home/jason/Desktop/Test /media/jason/Backup/ 2> >(tee ~/error_text >&2)
    errval=$?
    if [[ "$errval" == "0" ]]; then
        notify-send "Backup Complete. Please eject the backup drive."
    else
        notify-send "Error Backing Up - check ~/error_text for details"
#email failure file
        from=dads_account@gmail.com
        user=dads_account
        password=dads_gmail_password
        smtp_server=smtp.gmail.com
        to=your_email@whatever.com
        subject="Dads backup failed"
        now=`date +%Y_%m_%d_%H_%M_%S`
        message="Dads backup failed "$now
        sendemail -f $from -t $to -u $subject -m $message -s $smtp_server -o tls=yes -xu $user -xp $password -a ~/error_text
    fi
else
    notify-send "Backup drive not found. Please plug in the backup drive and restart the backup application.";
    exit
fi
```

---

### Post by Roasted on 2016-03-18
> **mcgess said:**
> ```
#!/bin/bash
if grep -qs '/media/jason/Backup' /etc/mtab; then
    notify-send "Backup Started"
    rsync -a --progress --delete /home/jason/Desktop/Test /media/jason/Backup/ 2> >(tee ~/error_text >&2)
    errval=$?
    if [[ "$errval" == "0" ]]; then
        notify-send "Backup Complete. Please eject the backup drive."
    else
        notify-send "Error Backing Up - check ~/error_text for details"
#email failure file
        from=dads_account@gmail.com
        user=dads_account
        password=dads_gmail_password
        smtp_server=smtp.gmail.com
        to=your_email@whatever.com
        subject="Dads backup failed"
        now=`date +%Y_%m_%d_%H_%M_%S`
        message="Dads backup failed "$now
        sendemail -f $from -t $to -u $subject -m $message -s $smtp_server -o tls=yes -xu $user -xp $password -a ~/error_text
    fi
else
    notify-send "Backup drive not found. Please plug in the backup drive and restart the backup application.";
    exit
fi
```

Wow. Looks great! Thanks so much for the added suggestion. In order to make this work, I assume sendmail (or some equivalent) would need to be installed -- yes?

---

### Post by mcgess on 2016-03-18
Either search for sendemail in synaptic package manager or in a terminal

```
sudo apt-get install sendemail
```

---

### Post by papibe on 2016-03-18
Hi Roasted.

I've encountered some problems using grep-mtab to see if a disk is mounted. Basically any substring of an already mounted directory would yield a false positive. I started using 'mountpoint' instead:
```
# Check if external disk is mounted.                                            
if ! mountpoint -q "$BU_MOUNT_POINT" ; then                                     
    echo "Backup drive not mounted. Stoping."                                   
    exit 1                                                                      
fi  
```
Just a thought. Hope it helps.
Regards.

---

### Post by Roasted on 2016-03-19
You guys had some great suggestions. Thank you for that! I tinkered with the script a bit more after thinking about some of the aspects I want in it. The email idea looked attractive, but truth be told my dad isn't enough of an email user to warrant it. He'd be best served with a message on his screen indicating that there was either A) an error or B) the backup is complete. Through an additional google search, I found a high ranked answer in terms of identifying mount points. I ran with it and here's what I came up with:

```
#!/bin/bash
if mount | grep /media/jason/Backup > /dev/null; then
notify-send "Backup Started"
rsync -a --progress --delete /home/jason/Desktop/Test /media/jason/Backup
errval=$?	
if [[ "$errval" == "0" ]]; then
notify-send "Backup complete. Please eject the backup drive."
else
notify-send "Error: Backup Failed"
fi
else
notify-send "Backup drive not found. Please plug in the backup drive and run the backup utility again.";
exit
fi
```

A couple key points I'm noticing with its behavior:

1) Ubuntu auto mounts the drive based on its label (Backup) to /media/username, providing me with a consistent mount point for the drive unless the drive would ever get renamed. As such, once ejected, /media/jason/Backup disappears, whereas when mounted, /media/jason/Backup exists.
2) errval seems to work consistently. I tested this by changing ownership if the destination. Changing it to root:root yields a backup error. Changing it to jason:jason yields a successful message.
3) Unplugging the drive, plugged it in, etc etc etc brings in the same results each time. If the drive is mounted, it'll rsync. If rsync errors out, I get the error message. If rsync succeeds, it says successful.

I'm not sure what else I want out of this, aside from adding a line under the "Backup Complete" message to append date/time to a backup_logs.txt file that'll be stored on the drive just for sake of knowing when the last backup was.

Does anybody see any issues with the way I formulated the script above? So far, all of my testing makes me think it's good to go, but I'm also far from a bash expert and wanted to make sure. The only part I'm not sure of looking at the script is the semicolons. I have 3 lines with notify-send, but only the 3rd notify-send line ends with a semicolon. Do the other two notify-send lines not need to end with ;?

Thanks again for any and all help!

---

### Post by btindie on 2016-03-19
The below is not safe as it would effectively match '*/media/jason/Backup*' which is not what you want.
```
grep -qs '/media/jason/Backup' /etc/mtab
```

To solve that you need to pass the '-w' option to grep to get it to only look on word boundaries.

However the mount point can't always be relied upon. It'd be more robust if you based it on the UUID of the partition which by it's nature is unique. You can find that out using the below
```
MOUNTPOINT="/media/jason/Backup"
mount | awk '$3 == "'"$MOUNTPOINT"'"{print $1}' | xargs -r blkid -o value -s UUID
```
That would output something like ```
14413fd5-afb4-48ed-a391-d07cb7a53ca5
``` which is the UUID value for that partition. Just use that in your other script and provided you don't 'format' the partition, it'll remain the same.

And a function to lookup the mount point based on the UUID
```
function getMountPointByUUID()
{
  local UUID="$1"

  local DEVICE
  DEVICE=$(blkid -l -o device -t UUID=$UUID)
  if [[ $? -eq 0 ]]; then

    local MOUNTPOINT
    MOUNTPOINT=$(mount | awk '$1 == "'"$DEVICE"'"{f=1; print $3} END{exit !f}')
    [[ $? -eq 0 ]] && { echo -n "$MOUNTPOINT"; return 0; }

  fi

  return 1
}
```

As an example of how you could use it:
```
UUID=14413fd5-afb4-48ed-a391-d07cb7a53ca5

MOUNTPOINT=$(getMountPointByUUID "$UUID")
if [[ $? -ne 0 ]]; then
  echo "Failed to find the mount point for UUID=$UUID"
  exit 1
fi

echo "Found mount point \"$MOUNTPOINT\" for UUID=$UUID"
```

At that point you know the correct partition is mounted and at what point.

It would probably also be worth while checking that the source directory exists before running rsync
```
if [ ! -d ~/Desktop/Test ]; then
  echo "Source directory for backup doesn't exist!" >&2
  exit 1
fi
```

That would then be fine if it was ran manually. However if you were to > I may just write a udev rule to auto execute you would face additional issues as the script would be run as *root. *(I'm not that familiar with udev and not sure if it's possible to have it run as another user)For instance I think the *notify-send *command uses environment variables to connect to the display. Assuming you got it to work, you'd have the issue of it always running whenever you plugged it in which may not be ideal.

You can check the owner of a file/directory with: ```
if [[ $(stat -c %U $MOUNTPOINT) != "$USER" ]]; then
  echo "$MOUNTPOINT not owned by $USER" >&2
fi
```
And it's probably also worth checking that the directory is writeable before rsync'ing just to be safe. ```
if [ ! -w $MOUNTPOINT ]; then
  echo "$MOUNTPOINT not writeable by $USER"
fi
```
The $USER variable contains the currently logged in username.

> ```
#!/bin/bash
if mount | grep /media/jason/Backup > /dev/null; then
  notify-send "Backup Started"
  rsync -a --progress --delete /home/jason/Desktop/Test /media/jason/Backup
  errval=$?    
  if [[ "$errval" == "0" ]]; then
    notify-send "Backup complete. Please eject the backup drive."
  else
    notify-send "Error: Backup Failed"
  fi
else
  notify-send "Backup drive not found. Please plug in the backup drive and run the backup utility again."
  exit
fi
```
The only part I'm not sure of looking at the script is the semicolons. I have 3 lines with notify-send, but only the 3rd notify-send line ends with a semicolon. Do the other two notify-send lines not need to end with ;?
You don't need to use semi-colons if there's only one command on a line, unlike with PHP. It would be more readable if it was indented as in the above.

---

### Post by Roasted on 2016-03-20
The discussion in this thread made me look deeper into my desktop's backup script. I made some edits, though I am running into a problem. The basic synopsis is this...

1) System logs in and auto launches rsync script as part of a startup application
2) The system rsync's my home directory to a second data drive in my desktop (listed as local backup in the script below)
3) Once complete, the system rsync's my home directory to my NAS (listed as remote backup in the script below)

So overall I have two rsync jobs running in this script, but I want them to flag an error message as discussed earlier in this thread.

The problem: If I stage my local sync (number 2 above) to fail by changing permissions of the local backup drive to be too restrictive, BUT keep the remote sync in working order (number 3 above), it still says the remote sync failed. What I expected was to see local backup failed + remote backup complete. Instead, both local + remote say they fail. If I paste *just* the rsync command for the remote sync into a terminal, it works fine.

I've read over the script a few times, but with my limited understanding of bash, I'm not sure where I goofed. Any ideas?

```
#!/bin/bash
notify-send "Local Backup Started"
rsync -a --progress --delete --exclude=".*" --exclude=".*/" /home/jason/ /media/jason/backup/
errval=$?
if [[ "$errval" == "0" ]]; then
notify-send "Local Backup Complete"
else
notify-send "Local Backup Failed"
fi
sleep 10s
notify-send "Remote Backup Started"
rsync -a --progress --delete --exclude=".*" --exclude=".*/" --exclude="VirtualBox VMs" --exclude="No_Remote_Sync" --exclude="ownCloud*" /home/jason/ jason@192.168.1.200:/media/vault/backups/jason/desktop_ubuntu
if [[ "$errval" == "0" ]]; then
notify-send "Remote Backup Complete"
else
notify-send "Remote Backup Failed";
exit
fi
```

---

### Post by sisco311 on 2016-03-20
Hi, Roasted!

You have to update the value of `errval' with the exit status of the second rsync command. 

```

#!/bin/bash

notify-send "Local Backup Started"
rsync -a --progress --delete --exclude=".*" --exclude=".*/" /home/jason/ /media/jason/backup/
errval=$?
if [[ "$errval" == "0" ]]; then
    notify-send "Local Backup Complete"
else
    notify-send "Local Backup Failed"
fi

sleep 10s

notify-send "Remote Backup Started"
rsync -a --progress --delete --exclude=".*" --exclude=".*/" --exclude="VirtualBox VMs" --exclude="No_Remote_Sync" --exclude="ownCloud*" /home/jason/ jason@192.168.1.200:/media/vault/backups/jason/desktop_ubuntu
[color=red]errval=$?[/color]
if [[ "$errval" == "0" ]]; then
    notify-send "Remote Backup Complete"
else
    notify-send "Remote Backup Failed"
exit
fi

```

---

### Post by Roasted on 2016-03-20
> **sisco311 said:**
> Hi, Roasted!

You have to update the value of `errval' with the exit status of the second rsync command. 

```

#!/bin/bash

notify-send "Local Backup Started"
rsync -a --progress --delete --exclude=".*" --exclude=".*/" /home/jason/ /media/jason/backup/
errval=$?
if [[ "$errval" == "0" ]]; then
    notify-send "Local Backup Complete"
else
    notify-send "Local Backup Failed"
fi

sleep 10s

notify-send "Remote Backup Started"
rsync -a --progress --delete --exclude=".*" --exclude=".*/" --exclude="VirtualBox VMs" --exclude="No_Remote_Sync" --exclude="ownCloud*" /home/jason/ jason@192.168.1.200:/media/vault/backups/jason/desktop_ubuntu
[color=red]errval=$?[/color]
if [[ "$errval" == "0" ]]; then
    notify-send "Remote Backup Complete"
else
    notify-send "Remote Backup Failed"
exit
fi

```

Ah, man, I should have caught that. Thanks for your insight! Script is working great. :)




EDIT BELOW:

After some more curiosity and a little bit more reading, I found another idea that I think I may run with. It was suggested to me by some bash folks to look into findmnt. After looking into findmnt, I saw that it can check the mount via UUID, which sounded a bit more straight forward to me as there shouldn't be any false positives with UUIDs, and likewise, the UUID should only change in the event the backup drive is formatted. The edited script is below, which after testing, seems to work well:

```
#!/bin/bash
if findmnt UUID=0631210c-ec45-45e8-a02a-d861be893374 > /dev/null; then
notify-send "Backup Started"
rsync -a --progress --delete --exclude=".gvfs" /home/jeff /media/jeff/Backup/
errval=$?	
if [[ "$errval" == "0" ]]; then
notify-send "Backup complete. Please eject the backup drive."
date >> /media/jeff/Backup/Backup_Logs.txt
else
notify-send "Error: Backup Failed"
fi
else
notify-send "Backup drive not found. Please plug in the backup drive and run the backup utility again.";
exit
fi
```

---

