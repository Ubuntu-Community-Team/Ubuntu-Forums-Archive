---
title: "File explorer contents not matching command line contents"
date: 2021-08-24
forum: General Help
---

### Post by sniper8752 on 2021-08-24
I have a smb share.  Here is how it is mounted on my server: 
```
//192.168.2.13/share/syncthing/Sync/pixel3a_camera/OpenCamera on /home/syncthing/Camera type cifs (rw,relatime,vers=3.1.1,cache=strict,username=<user>,uid=1001,forceuid,gid=1001,forcegid,addr=192.168.2.13,file_mode=0777,dir_mode=0755,soft,nounix,serverino,mapposix,rsize=4194304,wsize=4194304,bsize=1048576,echo_interval=60,actimeo=1)

```
Here is how I am accessing it: 
```
smb://<user>@192.168.2.13/share/syncthing/Sync/pixel3a_camera/OpenCamera/
```

Doing an ls in the directory, I get 390 items.  In my file explorer (Dolphin), I only see 254 files on that shared drive.  
Why don't the contents match up? I create a folder in the command line, and it shows up in my explorer.

---

### Post by TheFu on 2021-08-26
caching?
.files?
.directories?

Also, the ls will show . and .. directories. Those 2 aren't usually shown in GUI tools.

---

### Post by GhX6GZMB on 2021-08-26
Is your File Explorer set to show hidden files? That's usually a menu option.

---

### Post by TheFu on 2021-08-26
> **ml9104 said:**
> Is your File Explorer set to show hidden files? That's usually a menu option.


There is no "hidden files" in Unix. There isn't any Unix permissions or attributes that say "hidden".  MS-DOS/PC-DOS/DR-DOS have hidden files.  Not Unix. FAT12, FAT16, FAT32 and other MS-Windows file systems support those for backwards compatibility, though I don't know if a filename like .dotfile.txt is allowed on MS-Windows file systems or not.  There are a few characters forbidden on Windows in filenames, like anything with a :.

On any Unix-like POSIX file system, there are files that begin with a dot (.) which aren't always shown, unless requested. This is a convenience, since those are usually configuration files and directories that we seldom need/want to touch.  If there is a menu item to toggle this in a program, then the GUI programmer should be taught about Unix file systems, IMHO.  "Show .dot files" would be technically correct.  Let's show this in action:

```
~$ mkdir -p /tmp/foo/

~$ cd /tmp/foo/

/tmp/foo$ touch file1 .file2

/tmp/foo$ \ls -l
total 0
-rw-rw-r-- 1 thefu thefu 0 Aug 26 21:11 file1

/tmp/foo$ \ls -[COLOR="#FF0000"]a[/COLOR]l
total 8
drwxrwxr-x  2 thefu   thefu   4096 Aug 26 21:11 .
drwxrwxrwt 12 root root 4096 Aug 26 21:11 ..
-rw-rw-r--  1 thefu   thefu      0 Aug 26 21:11 file1
-rw-rw-r--  1 thefu   thefu      0 Aug 26 21:11 .file2

```
It will work the same for directories, as we see in the last 2 **ls** commands.  I used the **\ls** to show what a non-aliased **ls** command would do.  I have an alias for ls for my convenience. Using the escape '\' is how to tell bash NOT to use an alias for a command.  BTW, this command has worked the same for 40+ yrs, at least. I would expect it has worked the same since the early 1970s, so 50 yrs.

The "attributes" for files in Unix **file systems** are documented in the chattr manpage.  Use lsattr {file} to see them. chattr to change them.

Some file systems have *extended attributes*.  XFS, ext3/4 and most other Unix file systems do.  With these, we can set user-defined tags to files, but we have to take extra care to maintain those *extended attributes* in mv, cp, rsync, and most backup tools.  I've only seen these used in highly specialized situations where a programmer really didn't want to re-invent the wheel by creating a separate text/db file to contain the desired information.
[https://www.linuxtoday.com/blog/linux-extended-file-attributes/](https://www.linuxtoday.com/blog/linux-extended-file-attributes/)  getfattr/setfattr.

I seldom use these attribute commands, unless I'm fighting with a determined cracker on a server.  Then, making some files *immutable* can be fun, through I have also been known to mount a file system read-only too.  The bad part about using the immutable attribute is that I've usually forgotten about it and commands that I expect to work don't. Because the attributes are seldom used, it isn't the first thing I'll check in my troubleshooting, especially of the modification was 2 yrs ago.

Unix and Linux is full of these little commands that are seldom used, but exist. Until you run into them or have some training that covers the odd things in file systems, people don't usually learn about these.  This is yet another way that Unix is different from Windows that isn't obvious.

Update - the **ls** manpage:
```
       -a, --all
              do not ignore entries starting with .
```

---

### Post by GhX6GZMB on 2021-08-27
Well, silly me!
Please forward your answer to the PCManFM-Qt designers/programmers, who have impudently placed a menu tick box called "Show Hidden" in the program. Such cheek, really! They must be told off.
And the people who invented the -a option for the ls command. What were they thinking of?

Whether it's called "hidden" or "don't show" for a file/directory starting with "." is to me pure nitpicking.

---

### Post by sniper8752 on 2021-08-28
How do I check if it is caching?

---

