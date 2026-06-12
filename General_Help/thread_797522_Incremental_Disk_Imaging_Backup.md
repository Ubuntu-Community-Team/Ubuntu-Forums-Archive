---
title: "Incremental Disk Imaging Backup"
date: 2008-05-17
forum: General Help
---

### Post by Cerin on 2008-05-17
Hi,

Does anyone know of an open source application that can make incremental disk images for creating a daily backup of an entire machine? The only software I know can do this is Acronis True Image and Norton Ghost, but they're both expensive, proprietary, and don't run on Linux natively. I've looked at Ghost-4-Linux and Partimage, neither seemed designed for backups, and don't support incremental images.

---

### Post by ibuclaw on 2008-05-17
Have you considered a cronjob for the task?

Linux has the tools for the job, you just need to thread it all together to get it to work.

ie:
[LIST]
[*]mkisofs -J -r -o image.iso  file1 file2 file3 - Will create ISO images of multiple files.
[*]date +%d-%b/%y - Will make a named date ie:"17-May/08"
[/LIST]

Now the places you'll need to backup (if you choose an entire system backup) I would recommend to be:
[LIST]
[*]/bin
[*]/boot
[*]/etc
[*]/home
[*]/lib
[*]/usr/bin
[/LIST]
that plus a file output of this command (display all installed packages):
```
dpkg -l | grep ii | awk '{print $2" "}' | tr -d '\n'
```
To save it to a file use "** > filename**" at the end of the line.

So if your system does crash, then all you'll need is to restore the above locations and run "apt-get install `cat packages`" to re-install everything again (as backing up **every** file is a bit extreme/waste of space).

If you would like help on a general script.
I'm happy to help.

Regards
Iain

---

### Post by CanonKen on 2008-05-17
Have a look at [Quickstart]("http://quickstart.phpbb.net/index.php")

---

### Post by HalPomeranz on 2008-05-17
I use rsync for this-- typically for disk-to-disk backups between my file server and the various other machines on my network.

For example, let's suppose I'm backing up my machine called "elk".  On my file server, I'll create a directory for saving the initial backup of the entire system:

        sudo mkdir -p -m 700 /backups/elk/20080517

Now run rsync on the file server to take an initial copy of the whole file system of the remote server:

        sudo rsync -avH --exclude-from=/backups/elk/exclude elk:/ /backups/elk/20080517/

Note that for this command to work, the file server will need to be able to SSH into elk with root privileges.  Let me know if you're unsure how to make that happen.

The --exclude-from option allows you to specify a file containing files and/or directories that you don't want to be included in the backup.  For example:

        /dev/shm/
        /proc/
        /sys/
        /media/
        /var/run/
        /var/lock/
        *.iso

Notice that you can specify file names with wildcards.  The last line shown above will prevent you from backing up any files whose name ends with ".iso".

So the above rsync command will get you the initial "full" backup, but what about the incrementals?  It's pretty much the same rsync command, but we'll be adding the highly magical --link-dest option:

        sudo mkdir -p -m 700 /backups/elk/20080518
        sudo rsync -avH --link-dest=/backups/elk/20080517 --exclude-from=/backups/elk/exclude elk:/ /backups/elk/20080518/

Notice that the "target" directory is now the new 20080518 directory we created for the next day's incremental backup and we're using the previous day's directory (20080517) as the argument for the --link-dest option.  What --link-dest does is tell rsync to only copy the file from the remote system if the contents of the file have changed.  If the file is unchanged, rsync simply creates a hard link from the new directory (20080518 in this case) back to the original file in the directory specified as the argument to --link-dest (20080517 in our example).

The upshot is that the new "incremental" directory ends up being mostly hard links back to our original full backup, and hence uses up very little space.  There is some space overhead, because rsync has to create the entire system directory structure under the new 20080518 directory, but this is normally very minor.  OTOH, the 20080518 appears to be a "full" backup and you can navigate through the directories and see the "files" in their usual positions thanks to the magic of hard links.

The next time you want to do an incremental, create another directory and run rsync again, but this time use the last incremental as the target for --link-dest:

        sudo mkdir -p -m 700 /backups/elk/20080519
        sudo rsync -avH --link-dest=/backups/elk/20080518 --exclude-from=/backups/elk/exclude elk:/ /backups/elk/20080519/

I've got a basic script that I use for doing backups on my home network, which I'll attach to this message.

---

### Post by Cerin on 2008-05-17
tinivole,

Thanks, I wasn't aware of the mkisofs command. It looks like it even supports incremental iso generation using the -old-root option. However, I'm a little wary of creating my own backup script, just for reliability reasons. I'd like to find a tool that's dedicated to this task, and used by others so the kinks can be worked out. I had been using Duplicity with a custom script, and it worked reasonably well, but switched to Areca Backup since it has a GUI that really helps streamline administration. However, neither of those tools are designed for disk imaging.

---

### Post by Cerin on 2008-05-17
CanonKey,
Thanks, that project looks interesting. It seems a bit new, but I'll have to check it out.

---

### Post by Cerin on 2008-05-17
HalPomeranz,
Thanks for the in-depth howto. I was using Duplicity to do essentially the same thing. However, I'm trying to get away from relying on custom scripts, because I've found they're just too easy to break while being difficult to maintain.

---

### Post by CanonKen on 2008-05-18
> **Cerin said:**
> CanonKey,
Thanks, that project looks interesting. It seems a bit new, but I'll have to check it out.

It all [started on here]("http://ubuntuforums.org/showthread.php?t=613462") but now he's set a site up specially for it

---

