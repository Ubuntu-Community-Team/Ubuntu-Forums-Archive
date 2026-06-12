---
title: "Remote rdiff-backup - how to define a different ssh port ?"
date: 2024-01-07
forum: General Help
---

### Post by freeflyjohn on 2024-01-07
When performing a remote backup using rdiff-backup, how do I define a different SSH port ?

I am using Wiregaurd VPN to connect the source machine (Ubuntu server) and destination machine (iMac).

Below is the script I am using, but this won't work because it assumes the SSH port is the default 22.

Despite reading the rdiff-backup manual, I can't work out the syntax required in my bash script to define a different port.

```

# Source (Ubuntu server):     /media/storage 
# Destination (iMac):    /Volumes/OSB_Storage/

/opt/homebrew/bin/rdiff-backup -v4 --print-statistics\
    --exclude-special-files \
    --exclude ignorecase:'**.ini' \
    --exclude ignorecase:'**.DS_Store' \
    --exclude ignorecase:'**\$RECYCLE.BIN' \
    --exclude ignorecase:'**.AppleDouble' \
    --exclude ignorecase:'**.localized' \
    --include /media/storage \
    --exclude '**' user@192.168.6.1::/media/storage \
    /Volumes/OSB_Storage

```

A diagram of the setup is shown below...
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293285&stc=1[/IMG]




I've got rsync to work with a different ssh port as shown in the bash script below (using SSH port 12345 as an example).  

I am trying to do the same with rdiff-backup, but the syntax is different to rsync.

```

# Source (Ubuntu server):     /media/storage 
# Destination (iMac):    /Volumes/OSB_Storage

/usr/bin/rsync/rsync -a --progress -l --delete [COLOR=#ff0000]--rsh='ssh -p 12345'[/COLOR]\
    --exclude '*.ini' \
    --exclude '*.DS_Store' \
    --exclude '$RECYCLE.BIN' \
    --exclude '*.AppleDouble' \
    --exclude '*.localized' \
    user@192.168.6.1:/media/storage \
    /Volumes/OSB_TEST

```

---

### Post by Holger_Gehrke on 2024-01-07
If I read the [man-page]("https://github.com/rdiff-backup/rdiff-backup/blob/master/docs/rdiff-backup.1.adoc") (section 'Remote Operation') right, then you can use 'ssh://user@192.168.6.1:port::/media/storage' instead of 'user@192.168.6.1::/media/storage'.

Holger

---

### Post by freeflyjohn on 2024-01-07
> **Holger_Gehrke said:**
> If I read the [man-page]("https://github.com/rdiff-backup/rdiff-backup/blob/master/docs/rdiff-backup.1.adoc") (section 'Remote Operation') right, then you can use 'ssh://user@192.168.6.1:port::/media/storage' instead of 'user@192.168.6.1::/media/storage'.

Holger

Thanks Holger, that seems to have worked

Now I just need to somehow implement a #define (like in C) so that I can have a local source and destination (when performing the initial backup locally) or a remote source and destination (when performing incremental backups remotely).

But I dont know how you do this in a bash script.

At the moment I have to comment/uncomment the parameters **rdiff_cmd**, **src_prefix** and **dest_path** for either a local backup or a remote backup.

The script is shown below, where in this case I am using the remote backup definitions...

```

# for local backup
#**rdiff_cmd**=/usr/bin/rdiff-backup
#**src_prefix**=
#**dest_path**=/media/user/OSB_Storage

# for remote backup[B]
rdiff_cmd[/B]=/opt/homebrew/bin/rdiff-backup
**src_prefix**=ssh://user@192.168.6.1:12345::
**dest_path**=/Volumes/OSB_Storage

**$rdiff**_cmd -v4 --print-statistics \
    --exclude-special-files \
    --exclude ignorecase:'**.ini' \
    --exclude ignorecase:'**.DS_Store' \
    --exclude ignorecase:'**\$RECYCLE.BIN' \
    --exclude ignorecase:'**.AppleDouble' \
    --exclude ignorecase:'**.localized' \
    --include /media/storage \
    --exclude '**' **$src_prefix**/media/storage \
    **$dest_path**

```

In C I would do it using #define and simply comment or uncomment #define LOCAL..

```


#define LOCAL

#ifdef LOCAL
  rdiff_cmd=/usr/bin/rdiff-backup
  src_prefix=
  dest_path=/media/user/OSB_Storage
#else
  rdiff_cmd=/opt/homebrew/bin/rdiff-backup 
  src_prefix=ssh://user@192.168.6.1:12345::
  dest_path=/Volumes/OSB_Storage
#endif

```

---

### Post by Holger_Gehrke on 2024-01-07
The shell has "if" for conditions and scripts can access parameters passed on the command line as numerical parameters ($1, $2, $3, ...).

So you can do something like

```

if [ "local" = $1 ] ; then
**  rdiff_cmd**=/usr/bin/rdiff-backup
**  src_prefix**=
**  dest_path**=/media/user/OSB_Storage
else
  **rdiff_cmd**=/opt/homebrew/bin/rdiff-backup
  **src_prefix**=ssh://user@192.168.6.1:12345::
  **dest_path**=/Volumes/OSB_Storage
fi

```
and then call the script with 'local' as a parameter to run a local backup.


Holger

---

### Post by freeflyjohn on 2024-01-08
Many thanks Holger, that worked :P

---

### Post by TheFu on 2024-01-08
Use a ~/.ssh/config file for the ssh connection parameters.  

The ssh_config file is the manpage for that personal file.

All ssh-based tools honor the ~/.ssh/config settings, so there's no need to use IPs, users, ports, specific ssh keys in any command. Store those in the ~/.ssh/config for the userid running the command - in 20.04 and later, if you use sudo, then /root/.ssh/config is the file if you don't use a root-equivalent ... which you probably should rather than root, but that's a different thing.

Hint: for any variable in bash, quote them.  This is basic bash.  There are millions of example bash scripts on the internet and 500 on your box already.  If you actually want to learn, google this: "ABSG bash"

---

