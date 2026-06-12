---
title: "about rsync command"
date: 2016-12-30
forum: General Help
---

### Post by satimis on 2016-12-30
Hi all,

About rsync

I'm running following command to copy directories and files from local pc to remote pc on internal network.

&#10219; rsync -r -a -v -e "ssh -l satimis" Transfer_Directory/* 192.168.xx.xxx:/media/satimis/Temp_Storage/

It works seamlessly for me for years.  The problem is "I have to copy all directories including files to "Transfer_Directory".  Is there any way avoiding this step.

e.g.
local directories
/home/satimis/AAA_directory/files

If I expect to copy all files in AAA_directory including AAA_directory but excluding /home/satimis, what flags need to be up in rsync?

Thanks in advance

Regards
satimis

---

### Post by sudodus on 2016-12-30
Did you try listing those directories instead of the Transfer_Directory?

You can test with a dry run (the option -n).

---

### Post by satimis on 2016-12-30
Thanks for your advice.

> **sudodus said:**
> Did you try listing those directories instead of the Transfer_Directory?
"Transfer_Directory" was specifically created for transferring. The data to be transferred to the remote pc are copied to this directory first.  I'll delete it if I can find a solution.

> You can test with a dry run (the option -n).
Thanks.  It'll take quite sometimes to finish because there are many subdirectories and files to be transferred

Regards
satimis

---

### Post by sudodus on 2016-12-30
```
man rsync
```

offers the following options to specify the directories or files, if it will be 'too much' to list in the command line:

```
       --include-from=FILE
              This  option  is  related to the --include option, but it specifies a FILE that contains
              include patterns (one per line).  Blank lines in the file and lines starting with ’;’ or
              ’#’ are ignored.  If FILE is -, the list will be read from standard input.

       --files-from=FILE
              Using  this  option  allows  you to specify the exact list of files to transfer (as read
              from the specified FILE or - for standard input).  It also tweaks the  default  behavior
              of rsync to make transferring just the specified files and directories easier:

              o      The  --relative (-R) option is implied, which preserves the path information that
                     is specified for each item in the file (use --no-relative or --no-R if  you  want
                     to turn that off).

              o      The --dirs (-d) option is implied, which will create directories specified in the
                     list on the destination rather than  noisily  skipping  them  (use  --no-dirs  or
                     --no-d if you want to turn that off).

              o      The  --archive (-a) option’s behavior does not imply --recursive (-r), so specify
                     it explicitly, if you want it.

              o      These side-effects change the default state of rsync,  so  the  position  of  the
                     --files-from  option  on the command-line has no bearing on how other options are
                     parsed (e.g. -a works the same before or after --files-from, as does  --no-R  and
                     all other options).

              The  filenames  that  are  read  from the FILE are all relative to the source dir -- any
              leading slashes are removed and no ".." references are allowed to  go  higher  than  the
              source dir.  For example, take this command:

                 rsync -a --files-from=/tmp/foo /usr remote:/backup

              If  /tmp/foo  contains the string "bin" (or even "/bin"), the /usr/bin directory will be
              created as /backup/bin on the remote host.  If it contains  "bin/"  (note  the  trailing
              slash),  the  immediate contents of the directory would also be sent (without needing to
              be explicitly mentioned in the file -- this began in version 2.6.4).  In both cases,  if
              the  -r  option was enabled, that dir’s entire hierarchy would also be transferred (keep
              in mind that -r needs to be specified explicitly with  --files-from,  since  it  is  not
              implied by -a).  Also note that the effect of the (enabled by default) --relative option
              is to duplicate only the path info that is read from the file -- it does not  force  the
              duplication of the source-spec path (/usr in this case).

              In addition, the --files-from file can be read from the remote host instead of the local
              host if you specify a "host:" in front of the file (the host must match one end  of  the
              transfer).  As a short-cut, you can specify just a prefix of ":" to mean "use the remote
              end of the transfer".  For example:

                 rsync -a --files-from=:/path/file-list src:/ /tmp/copy

              This would copy all the files specified in the /path/file-list file that was located  on
              the remote "src" host.

              If  the  --iconv and --protect-args options are specified and the --files-from filenames
              are being sent from one host to another, the filenames will be translated from the send&#8208;
              ing host’s charset to the receiving host’s charset.

              NOTE:  sorting  the list of files in the --files-from input helps rsync to be more effi&#8208;
              cient, as it will avoid re-visiting the path elements that are shared  between  adjacent
              entries.   If  the input is not sorted, some path elements (implied directories) may end
              up being scanned multiple times, and rsync will eventually unduplicate them  after  they
              get turned into file-list elements.

```

---

### Post by satimis on 2016-12-30
> **sudodus said:**
> ```
man rsync
```

offers the following options to specify the directories or files, if it will be 'too much' to list in the command line:

```
       --include-from=FILE
              This  option  is  related to the --include option, but it specifies a FILE that contains
              include patterns (one per line).  Blank lines in the file and lines starting with &#8217;;&#8217; or
              &#8217;#&#8217; are ignored.  If FILE is -, the list will be read from standard input.

       --files-from=FILE
              Using  this  option  allows  you to specify the exact list of files to transfer (as read
              from the specified FILE or - for standard input).  It also tweaks the  default  behavior
              of rsync to make transferring just the specified files and directories easier:

              o      The  --relative (-R) option is implied, which preserves the path information that
                     is specified for each item in the file (use --no-relative or --no-R if  you  want
                     to turn that off).

              o      The --dirs (-d) option is implied, which will create directories specified in the
                     list on the destination rather than  noisily  skipping  them  (use  --no-dirs  or
                     --no-d if you want to turn that off).

              o      The  --archive (-a) option&#8217;s behavior does not imply --recursive (-r), so specify
                     it explicitly, if you want it.

              o      These side-effects change the default state of rsync,  so  the  position  of  the
                     --files-from  option  on the command-line has no bearing on how other options are
                     parsed (e.g. -a works the same before or after --files-from, as does  --no-R  and
                     all other options).

              The  filenames  that  are  read  from the FILE are all relative to the source dir -- any
              leading slashes are removed and no ".." references are allowed to  go  higher  than  the
              source dir.  For example, take this command:

                 rsync -a --files-from=/tmp/foo /usr remote:/backup

              If  /tmp/foo  contains the string "bin" (or even "/bin"), the /usr/bin directory will be
              created as /backup/bin on the remote host.  If it contains  "bin/"  (note  the  trailing
              slash),  the  immediate contents of the directory would also be sent (without needing to
              be explicitly mentioned in the file -- this began in version 2.6.4).  In both cases,  if
              the  -r  option was enabled, that dir&#8217;s entire hierarchy would also be transferred (keep
              in mind that -r needs to be specified explicitly with  --files-from,  since  it  is  not
              implied by -a).  Also note that the effect of the (enabled by default) --relative option
              is to duplicate only the path info that is read from the file -- it does not  force  the
              duplication of the source-spec path (/usr in this case).

              In addition, the --files-from file can be read from the remote host instead of the local
              host if you specify a "host:" in front of the file (the host must match one end  of  the
              transfer).  As a short-cut, you can specify just a prefix of ":" to mean "use the remote
              end of the transfer".  For example:

                 rsync -a --files-from=:/path/file-list src:/ /tmp/copy

              This would copy all the files specified in the /path/file-list file that was located  on
              the remote "src" host.

              If  the  --iconv and --protect-args options are specified and the --files-from filenames
              are being sent from one host to another, the filenames will be translated from the send&#8208;
              ing host&#8217;s charset to the receiving host&#8217;s charset.

              NOTE:  sorting  the list of files in the --files-from input helps rsync to be more effi&#8208;
              cient, as it will avoid re-visiting the path elements that are shared  between  adjacent
              entries.   If  the input is not sorted, some path elements (implied directories) may end
              up being scanned multiple times, and rsync will eventually unduplicate them  after  they
              get turned into file-list elements.

```

Thanks.

Hi,

I have made some search before posting.  Following link is quite useful.

Rsync (Remote Sync): 10 Practical Examples of Rsync Command in Linux
[http://www.tecmint.com/rsync-local-remote-file-synchronization-commands/](http://www.tecmint.com/rsync-local-remote-file-synchronization-commands/)

What I expect to do is to copy a directory including all subdirectories and files on local pc to the remote pc and automatically create a new directory with same name.

e.g.
 
&#10219; rsync -r -a -v -e "ssh -l satimis" /home/satimis/data/directoryAAA  192.168.xx.xxx:/media/satimis/Temp_Storage/

directoryAAA will be created automatically on the remote pc (/media/satimis/Temp_Storage/directoryAAA).  But the directories /home/satimis/data/ won't be copied to the remote pc as well.

satimis

---

### Post by oldfred on 2016-12-30
I just created a script with each folder I wanted to copy. But all my data is in a separate /mnt/data partition, so I want all of each of those.
Then I create an exclusion list for /home backup.

[https://ubuntuforums.org/showthread.php?t=2260658&p=13207429#post13207429](https://ubuntuforums.org/showthread.php?t=2260658&p=13207429#post13207429)

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by SeijiSensei on 2016-12-30
I just use --include-from, --files-from and --exclude-from to manage which files and directories are transferred.  For instance, on machines where I'm backing up from the root of the filesystem, I'll have a file of exclusions like this:
```

/proc/
/sys/
/dev/
/run/
/mnt/
/media/

```

I also don't know why you're using "ssh -e" in the command.  Rsync uses ssh by default as the current user.  Usually I've found that "rsync -av" is sufficient to do a complete transfer, or just "rsync -a" if I don't need the list of files transferred.

---

### Post by Keith_Helms on 2016-12-30
> **satimis said:**
> Hi all,

About rsync

I'm running following command to copy directories and files from local pc to remote pc on internal network.

&#10219; rsync -r -a -v -e "ssh -l satimis" Transfer_Directory/* 192.168.xx.xxx:/media/satimis/Temp_Storage/

It works seamlessly for me for years.  The problem is "I have to copy all directories including files to "Transfer_Directory".  Is there any way avoiding this step.

e.g.
local directories
/home/satimis/AAA_directory/files

If I expect to copy all files in AAA_directory including AAA_directory but excluding /home/satimis, what flags need to be up in rsync?

Thanks in advance

Regards
satimis

Rsync starts where you tell it and will go down from that point, assuming you use the recursive option -r.  It does not back up to any higher level directories.  If you tell it to start at /home/satimis/AAA_directory, it will NOT copy files from /home or /home/satimis.

---

### Post by satimis on 2017-01-03
> **Keith_Helms said:**
> Rsync starts where you tell it and will go down from that point, assuming you use the recursive option -r.  It does not back up to any higher level directories.  If you tell it to start at /home/satimis/AAA_directory, it will NOT copy files from /home or /home/satimis.
Hi,

Thanks for your advice.  I have tested it.

If I expect including AAA_directory to be copied to the remote pc which flag should be up for such a purpose.

Regards
satimis

---

### Post by Keith_Helms on 2017-01-03
> **satimis said:**
> Hi,

Thanks for your advice.  I have tested it.

If I expect including AAA_directory to be copied to the remote pc which flag should be up for such a purpose.

Regards
satimis

I don't quite understand what you're asking here.

The -r flag (recursive) will copy everything below the specified directory.
The -a flag (archive) will also copy everything below and adds options to preserve file ownership, permissions, and times and to handle symbolic links.

I'd start by using -avn, which is archive plus v for verbose and n for dry run.  Dry run won't actually copy any files, so using that plus verbose will allow you to see exactly what the command would do without actually doing it.

EDIT: If you want the directory named AAA_directory to also be copied then don't put a trailing slash after if.
Will copy the AAA_directory and everything under it
```
rsync -avn /home/satimis/AAA_directory *target*
``` 
Will only copy files and directories under AAA_directory 
```
rsync -avn /home/satimis/AAA_directory/  *target*
```

---

### Post by satimis on 2017-01-03
> **Keith_Helms said:**
> I don't quite understand what you're asking here.
- delete - 
I expect to copy the AAA_directory to the remote pc as well, instead to create AAA_directory on the remote pc and move all files back to AAA_directory afterwards.

satimis

---

### Post by Keith_Helms on 2017-01-03
Then don't put a slash after AAA_directory in your command.

Use
/home/satimis/AAA_directory

and not
/home/satimis/AAA_directory/

---

### Post by satimis on 2017-01-03
> **Keith_Helms said:**
> Then don't put a slash after AAA_directory in your command.

Use
/home/satimis/AAA_directory

and not
/home/satimis/AAA_directory/

Thanks

satimis

---

### Post by satimis on 2017-01-03
> **Keith_Helms said:**
> Then don't put a slash after AAA_directory in your command.

Use
/home/satimis/AAA_directory

and not
/home/satimis/AAA_directory/

Thanks

satimis

---

