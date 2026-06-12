---
title: "need some general linux / script help"
date: 2018-09-01
forum: General Help
---

### Post by mafia1245 on 2018-09-01
Hi All,

THANK YOU in advance for whatever help you can give me.

**_The Problem:_**
0. FYI running 14.04.2 LTS trusty 
1. I have a mhddfs pool (0.1.38) that drops out randomly -- i have seen that this is an issue for mhddfs and it doesn't look like it will be fixed anytime soon.
2. other than this issue my setup works and I know my wife hates it when i try to update and 'something' breaks and then i end up spending a lot of time to 'fix' something that was basically fine to begin with (im sure others here have been though this very issue).

**_Current Fix:_**
1. ssh into pc and unmount the mhddfs pool location 
2. ```
sudo umount -l /storage
``` 
3. (followed by entering PW)
4. ```
sudo mount -a
```
5. ```
exit 
```

**_What I have tried (but it doesn't seem to be working):_**
1. I put in the following (see below) in a .sh file to see if i could automate this process and had it run every 10 mins in cron

```
#! /bin/bash
if ! [ -e '/storage/' ]; then
    sudo umount -l /storage
    echo **PW** | cmd 
    sudo mount -a
fi
```


2. crontab -e
```
*/10 * * * * bash ~/Documents/restor.sh
```

What i would like:
1. check and see if /storage is accessible 
2. if it is then do nothing 
3. if it isn't then mount it (run mount -a cmd)
4. and probably run this check every 10/15 mins since it really is random of when the pool drops out (sometime its days other times its hrs)



Thanks again!

---

### Post by TheFu on 2018-09-01
You can add a specific mount command with all the options to the sudoers file(s), then you can run the specific sudo command without being prompted.

Running a task that removes a mount every 10 minutes probably isn't a good idea.

But if this is a media server, most media server solutions don't require huge single volumes and haven't for years.  They understand using multiple file systems and will merge the content into a single view.  Kodi does this.  So does Plex.  Yesterday, one of my 3 huge disks was getting close to full, so I moved 100G to another volume, then ran an rsync backup for the media.  Plex found the files in the new location and kept the watched/unwatched status, all was fine.  

Nothing says that my method is better than yours, but there it is for consideration.

---

### Post by Impavidus on 2018-09-01
I don't know whether putting such a script in crontab is the best solution to your problem and I've no experience with mhddfs pools, but I see a few problems with the script.

- If the storage is not mounted, /storage should still exist as an empty directory, so the test will return true and the following lines won't be executed. (I don't know what exactly happens when your storage drops out.) You could test for an empty directory or put a simple file in /storage that gets hidden whenever the storage gets mounted and check for the presence of this file.

- Don't assume you've got any environment when using crontab. Use the full paths to the commands.

- Don't use sudo and a plain-text password in the script. Instead, put the script in root's crontab and run the entire script with root permissions. Obviously, a script executed by root shouldn't be stored in a location writable by ordinary users.

Finally, Ubuntu 14.04 has 7 months of support left. Your wife may not like upgrades, but within the next 7 months you'll have to upgrade anyway. Or rather fresh install, so you can skip 16.04 and move directly to 18.04

---

### Post by mafia1245 on 2018-09-01
ok thanks --- im assuming your first line is correct that /storage is still existing as an empty directory and therefore the rest of the script isn't running.. do you have anything (code wise) that i should change this line to in order to correct it? Thanks again

---

### Post by TheFu on 2018-09-01
```
if ! [ -e '/storage/' ]; then
```

should probably be

```
if [ ! -e "/storage" ] ; then
```

Sometimes spacing matters with bash in odd ways.  I tend to validate that a file exists inside the expected mount.  Been burned checking just  the directory a few times. I place a zero-length file  into the mount directory. If it exists, then the extra storage HAS NOT been mounted.  Mounts will hide a file inside the mount directory.

So, I'd use a /storage/.not-mounted file as my test.

```
if [ -f "/storage/.not-mounted" ] ; then 
# mount the storage
fi 
```

If you want to test for existence of a directory, use -d. the **test** manpage has more of these.

---

