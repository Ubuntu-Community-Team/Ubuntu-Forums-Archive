---
title: "Can't download"
date: 2008-06-04
forum: General Help
---

### Post by Eric Weir on 2008-06-04
I'm trying to download the live CD for LinuxMint. I get a message which says there's not enough space on the drive/partition to save the file to /temp.

I ran the partition editor. The first time it said that all but 3.5 Mb of my 7.5 Gb partition was in use. The second time I ran it 2.2 Gb were available. When I try to download it still says there's not enough space on the drive/partition. The file is only 690 Mb.

Why is it trying to save when in the past I've been given the option to write to a CD? As it is now, I have no options. I'm not given any way to redirect the download. And why if 2.2 Gb are available is it saying there's not enough space for a save?

Any help would be appreciated.

Sincerely,

---

### Post by drs305 on 2008-06-04
Please post the results of the following:
```
df -h
```

---

### Post by Eric Weir on 2008-06-04
> **Eric Weir said:**
> Why is it trying to save when in the past I've been given the option to write to a CD? As it is now, I have no options. I'm not given any way to redirect the download. And why if 2.2 Gb are available is it saying there's not enough space for a save?

I rebooted and now it's saving.

---

### Post by Eric Weir on 2008-06-04
> **drs305 said:**
> Please post the results of the following:
```
df -h
```

Here it is. This is after I rebooted after posting my request.

```
Filesystem            Size  Used Avail Use% Mounted on 
/dev/sda1             7.4G  4.8G  2.3G  68% / 
varrun                236M  224K  236M   1% /var/run 
varlock               236M     0  236M   0% /var/lock 
udev                  236M   60K  236M   1% /dev 
devshm                236M     0  236M   0% /dev/shm 
lrm                   236M   38M  199M  16%  /lib/modules/2.6.24-17-generic/volatile 
/dev/sda6              29G  1.7G   25G   7% /home 
/dev/sdb1             9.0G  1.3G  7.3G  15% /media/sdb1 
```Thanks,

---

### Post by drs305 on 2008-06-04
I ran the above command and then reran it after deleting several large files. The numbers didn't change, which means files in the various trash folders don't count towards free space. They may be limiting the amount of available space even though not showing up. I do not know if deleted files would be overwritten should the space become necessary.

I would try emptying your normal trash folders and then also do a search for any folders named .Trash-1000 (or whatever your uid is), which may or may not be shown and deleted with your normal trash can.

---

### Post by Eric Weir on 2008-06-04
> **drs305 said:**
> I would try emptying your normal trash folders and then also do a search for any folders named .Trash-1000 (or whatever your uid is), which may or may not be shown and deleted with your normal trash can.

Thanks. I did a big delete a few days ago. Don't remember exactly when. For some reason it wasn't easy. Apparently some files with /root only permission. I ran my filemanager under sudo and thought I got rid of every thing, but I'm not certain. 

I have noticed at least one folder named .Trash. Don't think there's any number attached to it. Is it delete-able? 

Can you do wild card searches in Linux? How do I determine what my uid number is?

Thanks,

---

### Post by Eric Weir on 2008-06-04
> **Eric Weir said:**
> I ran my filemanager under sudo and thought I got rid of every thing, but I'm not certain.
I forgot to mention that there are several folders -- old  Thunderbird extention installations -- that I can't get deleted. They seem to have /root only permission, though I can't verify that. They won't delete in the filemanager, but when I run the filemanager under sudo they don't appear. How the hell do I get rid of them.

> Can you do wild card searches in Linux? How do I determine what my uid number is?Also, I have to confess I don't know how to/see a way to search for files/folders in Xubuntu. There's no search window in Thunar, and no search option anywhere on the menus. Don't see any other applications that might make searching available.

Thanks,

---

### Post by drs305 on 2008-06-04
> **Eric Weir said:**
> Thanks. I did a big delete a few days ago. Don't remember exactly when. For some reason it wasn't easy. Apparently some files with /root only permission. I ran my filemanager under sudo and thought I got rid of every thing, but I'm not certain. 

I have noticed at least one folder named .Trash. Don't think there's any number attached to it. Is it delete-able? 

Can you do wild card searches in Linux? How do I determine what my uid number is?

Thanks,

Since you were trying to download to /media/sdb1, let's start there:
```
cd /media/sdb1
```

Do you own this paritition? If so,
```
sudo find . | grep .Trash-1000/files
```
Take a look, if nothing looks important:
```
sudo find . | grep Trash-1000/files | xargs rm 
```

That will let you choose what to delete. You can also just let it run by itself if you are comfortable with the posted results. Remove the -i

A safe alternative for deleting files owned by root is to open nautilus with root privileges:
```
gksudo nautilus
```
This will let you browse all the computer folders and delete any you want (be careful). Don't forget to enable the *hidden file *option. You could manually go to the files found with the above terminal commands to delete the folders/files.

---

### Post by Eric Weir on 2008-06-04
> **drs305 said:**
> ```
find | grep Trash-1000/files | xargs rm -i
```Actually, I was able to complete the download. It was to sda1. This is the output of my effort to do what you suggested.

```
eric@eric-linux:~$ find | grep .trash-1000/files 
[FONT=-moz-fixed]find: ./temporary/tbprofileold/vzpc0ne5.kubuntu0408: Permission denied 
find: ./.kde/share/apps/konqueror/profiles: Permission denied 
eric@eric-linux:~$ 
eric@eric-linux:~$ 
eric@eric-linux:~$ 
eric@eric-linux:~$ find | grep trash-1000/files | xargs rm i 
find: ./temporary/tbprofileold/vzpc0ne5.kubuntu0408: Permission denied 
find: ./.kde/share/apps/konqueror/profiles: Permission denied 
rm: cannot remove `i': No such file or directory 
eric@eric-linux:~$[/FONT]
```[FONT=-moz-fixed]
I understand the first line. It was a backup of my Thunderbird profile from an earlier Kubuntu installation.I thought it had been deleted.

The other one I don't understand. I have /.kde and /.kde4 four folders in my home folder. I assume they got there when I installed some KDE applications. I believe I've uninstalled all of them.
[/FONT]
[quote]A safe alternative for deleting files owned by root is to open nautilus with root privilegesI've done that to clean out my trash folder, which contained a ton of folders and files with /root ownership. There is one group of files I can't get rid of. They're old installations of Thunderbird extentions. They show up in the filemanager when it's running normally. When I run it under sudo, they don't show up. As a result I can't get rid of them. They're not very large, but I'd like to get rid of them.

Thanks for your help,

---

### Post by drs305 on 2008-06-04
My bad. It's not the first time I left the command incomplete - I'll go back to the original post and correct it.

> **Eric Weir said:**
> There is one group of files I can't get rid of. They're old installations of Thunderbird extentions. They show up in the filemanager when it's running normally. When I run it under sudo, they don't show up. As a result I can't get rid of them. They're not very large, but I'd like to get rid of them.

Thanks for your help,

Can you give us the name and location of the folders. They may be temporary files created during operation and normally removed after the session is finished. The reason you don't see them when you run the app as root is that root's temporary files would be placed in another folder, not in yours.

---

### Post by Eric Weir on 2008-06-04
> **drs305 said:**
> My bad, and it's not the first time. The command was incomplete - I meant to use sudo. I'll go back to the original post and correct it.
If you could, let me know what the commands are doing. I'm not real clear about what's safe to delete.

Thanks,

---

### Post by drs305 on 2008-06-04
> **Eric Weir said:**
> If you could, let me know what the commands are doing. I'm not real clear about what's safe to delete.

Absolutely:

This command sends the terminal to your /media/sdb1 partition:
```
cd /media/sdb1
```

The next command tells find to look in the current directory and subdirectories. By changing to the lowest level possible to begin the search, you limit any damage from a botched or malicious command (as opposed to starting out a /, which could wipe out everything). The results of that search are then filtered by grep, which will display only the results that contain *.Trash-1000/files *
You can write the *find* command to do this with it's own delimiters without grep, it's just the way I started. I used sudo in most of my searches to avoid the 'permission denied' messages and because in this situation some of the deleted files may have belonged to root.
```
sudo find . | grep .Trash-1000/files
```

the intent of this command was to take the results from the previous search and allows xargs to run the remove command on the results once you agree to each deletion (-i). I wanted to make it interactive so that you would be comfortable deleting files via terminal. However, in my effort to do so I forgot that the remove command as I wrote it has trouble with xargs and the interactive mode.

Without the error-causing *-i* it would have deleted all the files found in the previous search.
```
sudo find . | grep Trash-1000/files | xargs rm 
```

As a precaution, I would always run the search part of a command without the rm command to make sure I knew the results before committing to the deletion. Same goes for most other commands joined to the find command. It's good to be cautious ;-)

---

### Post by Eric Weir on 2008-06-04
> **drs305 said:**
> ```
sudo find . | grep .Trash-1000/files
```the intent of this command was to take the results from the previous search and allows xargs to run the remove command on the results once you agree to each deletion (-1). I made a mistake here in that the remove command has trouble with xargs and the interactive mode the way I wrote it.

Without the error-causing *-i* it would have deleted all the files found in the previous search.
```
sudo find . | grep Trash-1000/files | xargs rm 
```
Thanks. This is reassuring. I really should be learning more about the command line, but I'm so caught up in just trying to get my system working while trying to get my real work done that I don't have time for it. 

"Not having time for it" on Linux is kind of self-destructive.

Regards,

---

### Post by Eric Weir on 2008-06-06
> **drs305 said:**
> 
```
sudo find . | grep Trash-1000/files | xargs rm 
```
I overlooked the fact that you **went back **and added sudo to the commands in your original post. I was waiting for a second posting of the instructions. My apologies.

In the interim I discovered that the trash folder on my second hd, which was previously the only hd on the machine, and on which I had installed Kubuntu, still contained the entire Kubuntu installation. It was what the search without sudo had turned up. I ran the file manager under sudo and managed to get the trash folder on the second drive emptied. 

I was hoping that that would reduce the amount of space used in the /root partition of my first drive. No such luck. I've still only got 380 Mb available on a 7.5 Gb partititon. 

This is doubly strange, first of all, that almost the entire /root partition would be used up under any circumstances, especially with Xubuntu, and secondly, because the last time was tinkering around on this issue I managed to get the space available back up to about 3 Gb. 

Why would I be using this much space in /root?

---

### Post by Eric Weir on 2008-06-06
> **Eric Weir said:**
> I was hoping that that would reduce the amount of space used in the /root partition of my first drive. No such luck. I've still only got 380 Mb available on a 7.5 Gb partititon. 

This is doubly strange, first of all, that almost the entire /root partition would be used up under any circumstances, especially with Xubuntu, and secondly, because the last time was tinkering around on this issue I managed to get the space available back up to about 3 Gb. 

Why would I be using this much space in /root?
I'm wondering if I should just do a fresh install of Xubuntu. It would be a lot of work reestablishing the current installation -- though I do have my /home folder on a separate partition -- but maybe less than trying to figure out why the /root partition is filling up.

Thanks,

---

### Post by Eric Weir on 2008-06-06
> **Eric Weir said:**
> In the interim I discovered that the trash folder on my second hd, which was previously the only hd on the machine, and on which I had installed Kubuntu, still contained the entire Kubuntu installation. It was what the search without sudo had turned up. I ran the file manager under sudo and managed to get the trash folder on the second drive emptied.
One last issue. My trash folder still contains eight folders, copies of old Thunderbird extension installations. All the files in them are owned by /root, so they can't be deleted. These were folders were not picked up by the find .trash-1000/files command, and when I run the filemanager under sudo they also fail to show up.

How can I get rid of them?

Thanks,

---

### Post by cariboo on 2008-06-06
Instead of downloading and saving files in / why not just setup a download directory in /home/user where user is your user name and then set Firefox preferences to download to the directory you just set up. That is what the home directory is for.

Jim

---

### Post by Eric Weir on 2008-06-06
> **cariboo907 said:**
> Instead of downloading and saving files in / why not just setup a download directory in /home/user where user is your user name and then set Firefox preferences to download to the directory you just set up. That is what the home directory is for.
This is a long and perhaps confusing thread. My apologies if I suggested, overtly or covertly, that I was downloading files to / . I'm not. I have folder in /home called mydownloads.

But thanks for the suggestion anyway.

Sincerely,

---

### Post by drs305 on 2008-06-06
Eric,

If you have a separate home folder and still haven't resolved this issue, the easiest solution would probably be to reinstall. If you do that, and you are happy with the programs you currently have on your computer, you can save that list and have them reinstalled on the new installation. I assume this works in Kubuntu as well as Ubuntu.

To save the list of installed apps:
```
sudo dpkg --get-selections >~/Desktop/mypackages
```

To restore the list to a new installation:
```
sudo dpkg --set-selections <~/Desktop/mypackages
sudo aptitude update

```

By the way, apologies for not pointing out a change to the earlier post. If I change something before the next post is entered I sometimes try to edit the post instead of making a new one. Probably not a good technique.

Settling down to watch Hudson battle the Phillies, 1-0 in the first...

---

### Post by Eric Weir on 2008-06-06
> **drs305 said:**
>  assume this works in Kubuntu as well as Ubuntu.
Actually, I'm running Xubuntu. However, I'm interested in another distribution -- maybe it should be called a remastering -- Linux Mint. It's based on Ubuntu, with a more selected set of applications, and tweaking related to proprietary drivers and codecs and networking already done, and with access to the Ubuntu repositories.

I've saved my installed programs list to the desktop. If I install Linux Mint instead of Xubuntu, I assume the command to restore my programs will work under it as well?

> Settling down to watch Hudson battle the Phillies, 1-0 in the first...I don't follow baseball much till the end of the season. [My ex always said, very proudly, "I'm not a *baseball *fan! I'm a *Cubs *fan!" She may not have been a baseball fan, but she definitely knew the game. And I imagine she's enjoying her favorite team lately.] I know The Braves had -- have? -- a pitcher named Hudson. So are you watching the Braves, or the team Hudson was traded to, or is that another Hudson?

Thanks for your help.

---

### Post by drs305 on 2008-06-06
I assume it will work in Xbuntu or Mint. If you look at the file it is a simply a list of apps and their status - most will be listed as 'installed'. As long as dpkg will run in Mint, which it should as dpkg is a standard debian-based command, it should be able to read the list.

Tim Hudson is the pitcher, 2-1 Braves in the 7th...

---

### Post by Eric Weir on 2008-06-06
> **drs305 said:**
> As long as dpkg will run in Mint, which it should as dpkg is a standard debian-based command, it should be able to read the list.
That was my guess. We'll see.

> Tim Hudson is the pitcher, 2-1 Braves in the 7th...So he wasn't traded. Are you in Atlanta, then?

Regards,

---

