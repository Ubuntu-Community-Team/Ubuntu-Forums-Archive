---
title: "Why would cron write to /etc/passwd file?"
date: 2023-03-29
forum: General Help
---

### Post by thomo2710 on 2023-03-29
Hi,

My EDR threw up an alert last night on my Ubuntu 22.04 web server.

Cron wrote to /etc/passwd for some reason.

Ive looked at the file and dont see anything unusual.

[https://ibb.co/w7WpxM0](https://ibb.co/w7WpxM0)

Looked at the crontab log and there is nothing launched at that time job wise.

username was logged as root:root

Checked modified time of the file and it looks about the last time it would have been modified, certainly not last nigths date[URL="https://https://ibb.co/wYq3XsN"]

[/URL][https://ibb.co/wYq3XsN](https://ibb.co/wYq3XsN)

Im no Ubuntu expert, primarily Windows based, so looking to the community for any pointers.

My EDR has a habit of throwing up a lot of nosie and false positives so dont know if im chasing my tail and its something legit or not.

Any steer or input is appreciated

Many Thanks

---

### Post by TheFu on 2023-03-29
If the file date hasn't changed, then it wasn't modified.  
Please don't use images when text will do.  This isn't MS-Windows.  When posting text, especially from a terminal, use the forum code-tags so columns line up and the monospaced font is used (along with other formatting options).  Adv-Reply (#) for code tags.

---

### Post by SeijiSensei on 2023-03-29
Many applications read /etc/passwd. If your system detects that fact, you'll get a lot of notifications. The fact that it doesn't appear to be altered suggests a false positive.

I'd create a backup copy of the file so if this happens again, you can run 
```
diff /etc/passwd /etc/passwd.bak
```
and see exactly what, if any, changes were made. If you're really paranoid, you can make the backup "immutable" with
```
sudo chattr +i /etc/passwd.bak
```
so it cannot be changed under any circumstances, even by users with write permissions. See "man chattr" for details.

---

### Post by philhughes on 2023-03-29
It is possible to change the access and modification time with "touch". Check the various file timestamps with the "stat" command, in particular the change time:

```
$ echo something > testfile
$ ll testfile
-rw------- 1 phil phil 10 2023-03-29 20:15 testfile
$ stat testfile
  File: testfile
  Size: 10        	Blocks: 8          IO Block: 4096   regular file
Device: 10302h/66306d	Inode: 52695281    Links: 1
Access: (0600/-rw-------)  Uid: ( 1000/    phil)   Gid: ( 1000/    phil)
Access: 2023-03-29 20:15:32.211103864 +0100
Modify: 2023-03-29 20:15:32.211103864 +0100
Change: 2023-03-29 20:15:32.211103864 +0100
 Birth: 2023-03-29 20:15:32.211103864 +0100
```

```
$ touch --date="2023-01-01 01:00:00" testfile
$ ll testfile
-rw------- 1 phil phil 10 2023-01-01 01:00 testfile
$ stat testfile
  File: testfile
  Size: 10        	Blocks: 8          IO Block: 4096   regular file
Device: 10302h/66306d	Inode: 52695281    Links: 1
Access: (0600/-rw-------)  Uid: ( 1000/    phil)   Gid: ( 1000/    phil)
Access: 2023-01-01 01:00:00.000000000 +0000
Modify: 2023-01-01 01:00:00.000000000 +0000
Change: 2023-03-29 20:16:16.383567787 +0100
 Birth: 2023-03-29 20:15:32.211103864 +0100
```

Notice that although I have set the access and modification times back, the change time records the time at which I made the modification.

---

### Post by TheFu on 2023-03-29
/etc/passwd is owned by root, so only root can modify it or the inode for it which is where the file stats are stored.
```
$ ll /etc/passwd*
-r**w**-r--r-- 1 **root** root 2972 May 21  2022 /etc/passwd
```

---

### Post by philhughes on 2023-03-29
If someone has gained access, anything is possible.

---

### Post by thomo2710 on 2023-03-30
@[COLOR=#000000]SeijiSensei - thanks for the suggestion, ill do this as i monitor over the coming days.[/COLOR]
@philhughes - checked the file with stat and the change dates look like they marry up with what id expect, which isnt the other night.

I think it a false positive but ill keep my eye on it.

Thanks everyone for the input

---

