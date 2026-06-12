---
title: "Copy a folder from one server to another one"
date: 2013-02-06
forum: General Help
---

### Post by alfirdaous on 2013-02-06
Hello there,

I tried to copy a folder from server1 to server2, but it doesnt work, so I connect with ssh to server1 terminal and copy the folder to server2

```

scp test server2@IP_SERVER2:/home/server2/test2 ssh: connect to host IP_SERVER2 port 22: Connection timed out lost connection

```

NB: I could connect with SSH to both servers without any trouble

Thanks for your help

---

### Post by sudodus on 2013-02-06
Since you can connect to both servers via ssh, you can use rsync, which uses ssh by default. Test with something like this (-n '--dry run' makes it only show what would be transferred)
```
rsync -avn user1@server1:/path/directory-to-be-copied-from/ user2@server2:/path/directory-to-be-copied-to
```
And perform the transfer with something like this
```
rsync -av user1@server1:/path/directory-to-be-copied-from/ user2@server2:/path/directory-to-be-copied-to
```

---

### Post by efflandt on 2013-02-06
Since it would be pointless to scp an empty folder (directory), you likely need to use **-r** scp option to copy the directory "and its contents".  See **man scp**

---

### Post by alfirdaous on 2013-02-06
I tried with rsync:

```

rsync -avn /home/server1/www/test/test.html server2@IP_SERVER2:/home/server2/test2/ -e "ssh -p 2225"
server2@IP_SERVER2's password: 
sending incremental file list
test.html

sent 37 bytes  received 15 bytes  11.56 bytes/sec
total size is 9  speedup is 0.17 (DRY RUN)

```

I could not find the file in the said directory

---

### Post by SlugSlug on 2013-02-06
remove the 'n'

```
rsync -av /home/server1/www/test/test.html server2@IP_SERVER2:/home/server2/test2/ -e "ssh -p 2225"
```

---

### Post by collisionystm on 2013-02-06
No. No. and No.

You need rsync -rqa

rsync -rqa /home/server1/www/test/test.html server2@IP_SERVER2:/home/server2/test2/ -e "ssh -p 2225"

You need the 'r' to tell it to use recursive mode and enter directories.

Remove the 'q' to see the output.

> Options
 -v, --verbose               increase verbosity
 -q, --quiet                 suppress non-error messages
     --no-motd               suppress daemon-mode MOTD (see manpage caveat)
 -c, --checksum              skip based on checksum, not mod-time & size
 -a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
     --no-OPTION             turn off an implied OPTION (e.g. --no-D)
 -r, --recursive             recurse into directories
 -R, --relative              use relative path names
     --no-implied-dirs       don't send implied dirs with --relative
 -b, --backup                make backups (see --suffix & --backup-dir)
     --backup-dir=DIR        make backups into hierarchy based in DIR
     --suffix=SUFFIX         set backup suffix (default ~ w/o --backup-dir)
 -u, --update                skip files that are newer on the receiver
     --inplace               update destination files in-place (SEE MAN PAGE)
     --append                append data onto shorter files
     --append-verify         like --append, but with old data in file checksum
 -d, --dirs                  transfer directories without recursing
 -l, --links                 copy symlinks as symlinks
 -L, --copy-links            transform symlink into referent file/dir
     --copy-unsafe-links     only "unsafe" symlinks are transformed
     --safe-links            ignore symlinks that point outside the source tree
 -k, --copy-dirlinks         transform symlink to a dir into referent dir
 -K, --keep-dirlinks         treat symlinked dir on receiver as dir
 -H, --hard-links            preserve hard links
 -p, --perms                 preserve permissions
 -E, --executability         preserve the file's executability
     --chmod=CHMOD           affect file and/or directory permissions
 -A, --acls                  preserve ACLs (implies --perms)
 -X, --xattrs                preserve extended attributes
 -o, --owner                 preserve owner (super-user only)
 -g, --group                 preserve group
     --devices               preserve device files (super-user only)
     --specials              preserve special files
 -D                          same as --devices --specials
 -t, --times                 preserve modification times
 -O, --omit-dir-times        omit directories from --times
     --super                 receiver attempts super-user activities
     --fake-super            store/recover privileged attrs using xattrs
 -S, --sparse                handle sparse files efficiently
 -n, --dry-run               perform a trial run with no changes made
 -W, --whole-file            copy files whole (without delta-xfer algorithm)
 -x, --one-file-system       don't cross filesystem boundaries
 -B, --block-size=SIZE       force a fixed checksum block-size
 -e, --rsh=COMMAND           specify the remote shell to use
     --rsync-path=PROGRAM    specify the rsync to run on the remote machine
     --existing              skip creating new files on receiver
     --ignore-existing       skip updating files that already exist on receiver
     --remove-source-files   sender removes synchronized files (non-dirs)
     --del                   an alias for --delete-during
     --delete                delete extraneous files from destination dirs
     --delete-before         receiver deletes before transfer, not during
     --delete-during         receiver deletes during transfer (default)
     --delete-delay          find deletions during, delete after
     --delete-after          receiver deletes after transfer, not during
     --delete-excluded       also delete excluded files from destination dirs
     --ignore-errors         delete even if there are I/O errors
     --force                 force deletion of directories even if not empty
     --max-delete=NUM        don't delete more than NUM files
     --max-size=SIZE         don't transfer any file larger than SIZE
     --min-size=SIZE         don't transfer any file smaller than SIZE
     --partial               keep partially transferred files
     --partial-dir=DIR       put a partially transferred file into DIR
     --delay-updates         put all updated files into place at transfer's end
 -m, --prune-empty-dirs      prune empty directory chains from the file-list
     --numeric-ids           don't map uid/gid values by user/group name
     --timeout=SECONDS       set I/O timeout in seconds
     --contimeout=SECONDS    set daemon connection timeout in seconds
 -I, --ignore-times          don't skip files that match in size and mod-time
     --size-only             skip files that match in size
     --modify-window=NUM     compare mod-times with reduced accuracy
 -T, --temp-dir=DIR          create temporary files in directory DIR
 -y, --fuzzy                 find similar file for basis if no dest file
     --compare-dest=DIR      also compare destination files relative to DIR
     --copy-dest=DIR         ... and include copies of unchanged files
     --link-dest=DIR         hardlink to files in DIR when unchanged
 -z, --compress              compress file data during the transfer
     --compress-level=NUM    explicitly set compression level
     --skip-compress=LIST    skip compressing files with a suffix in LIST
 -C, --cvs-exclude           auto-ignore files the same way CVS does
 -f, --filter=RULE           add a file-filtering RULE
 -F                          same as --filter='dir-merge /.rsync-filter'
                             repeated: --filter='- .rsync-filter'
     --exclude=PATTERN       exclude files matching PATTERN
     --exclude-from=FILE     read exclude patterns from FILE
     --include=PATTERN       don't exclude files matching PATTERN
     --include-from=FILE     read include patterns from FILE
     --files-from=FILE       read list of source-file names from FILE
 -0, --from0                 all *-from/filter files are delimited by 0s
 -s, --protect-args          no space-splitting; only wildcard special-chars
     --address=ADDRESS       bind address for outgoing socket to daemon
     --port=PORT             specify double-colon alternate port number
     --sockopts=OPTIONS      specify custom TCP options
     --blocking-io           use blocking I/O for the remote shell
     --stats                 give some file-transfer stats
 -8, --8-bit-output          leave high-bit chars unescaped in output
 -h, --human-readable        output numbers in a human-readable format
     --progress              show progress during transfer
 -P                          same as --partial --progress
 -i, --itemize-changes       output a change-summary for all updates
     --out-format=FORMAT     output updates using the specified FORMAT
     --log-file=FILE         log what we're doing to the specified FILE
     --log-file-format=FMT   log updates using the specified FMT
     --password-file=FILE    read daemon-access password from FILE
     --list-only             list the files instead of copying them
     --bwlimit=KBPS          limit I/O bandwidth; KBytes per second
     --write-batch=FILE      write a batched update to FILE
     --only-write-batch=FILE like --write-batch but w/o updating destination
     --read-batch=FILE       read a batched update from FILE
     --protocol=NUM          force an older protocol version to be used
     --iconv=CONVERT_SPEC    request charset conversion of filenames
 -4, --ipv4                  prefer IPv4
 -6, --ipv6                  prefer IPv6
     --version               print version number
(-h) --help                  show this help (-h works with no other options)

Use "rsync --daemon --help" to see the daemon-mode command-line options.
Please see the rsync(1) and rsyncd.conf(5) man pages for full documentation.
See [http://rsync.samba.org/](http://rsync.samba.org/) for updates, bug reports, and answers

---

### Post by alfirdaous on 2013-02-06
tanks, I did not pay attention to the 'n', I used 'r'

```

-avr

```

Are the chmod and chown will remain te same, for exemple:

```

-rw-r--r-- 1 server1 server1 9 2013-02-06 10:46 test.html

```

will become after sending:

```

-rw-r--r-- 1 server2 server2 9 2013-02-06 10:46 test.html

```

so the chmod will not change, the owner will remain the same user as the remote machine receiver

---

### Post by SlugSlug on 2013-02-06
> **collisionystm said:**
> No. No. and No.

You need rsync -rqa

rsync -rqa /home/server1/www/test/test.html server2@IP_SERVER2:/home/server2/test2/ -e "ssh -p 2225"

You need the 'r' to tell it to use recursive mode and enter directories.

Remove the 'q' to see the output.

You don't need the 'r' with the 'a' option

---

### Post by alfirdaous on 2013-02-06
so scp will not work??

---

### Post by SlugSlug on 2013-02-06
scp will work not sure about recursive on a folder tho I normally tar it up

```
tar cvf my_folder.tar /path/folder
```

---

### Post by alfirdaous on 2013-02-06
So I can end by using rsync instead of scp :p

---

### Post by alfirdaous on 2013-02-07
soryy I faced a new problem:

```

rsync -arv Medias/ server2@IP_SERVER2:/home/server2/www/Downloads/Medias/ -e 'ssh -p 2225'
server2@IP_SERVER2's password: 
sending incremental file list
./
rsync: failed to set times on "/home/server2/www/Downloads/Medias/.": Operation not permitted (1)
Folder1/
rsync: recv_generator: mkdir "/home/server2/www/Downloads/Medias/Folder1" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***


```

---

### Post by alfirdaous on 2013-02-07
Sorry: The based name folder owner was root, changed to the current owner

---

