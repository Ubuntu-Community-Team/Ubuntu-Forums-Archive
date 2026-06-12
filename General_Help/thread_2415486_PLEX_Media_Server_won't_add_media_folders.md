---
title: "PLEX Media Server won't add media folders"
date: 2019-03-26
forum: General Help
---

### Post by lilithcrazygirl on 2019-03-26
Hi:

First of all a little background. . . I used to use Ubuntu for my daily needs for 3 years and then switched to mac and used mac for 9 years long. My mac got broken recently and i don't want to use Windows for my daily needs and tasks. So i decided to go back to the good old days and use Ubuntu again. I have installed and configured most of my main apps and so far i am pleased with the performance that Ubuntu gives me (i am currently running 18.04 LTS)but i have an issue that has been nagging me for 2 weeks. . .

I haven't been able to get Plex to add my folders. It's a 2 TB external drive that i formatted to ext4 and that has many folders for different kind of content (tv shows, anime and so on) But when i try to add those folders to PLEX it just won't find the media or even go inside the main folder. Normally the external drive gets mounted at /user/media/"External Drive Name"

I have tried changing the permissions and even the ownership related to the user plex with chmod and chown. I have even tried changing my user like this [COLOR=#F06464][FONT=Consolas]PLEX_MEDIA_SERVER_USER="my user" [/FONT][/COLOR]in the configuration file. I have tried many of the things described in posts with users with similar problems.
- [https://forums.plex.tv/t/plex-wont-read-folders-files-on-mounted-drive-in-linux-mint/69278/23](https://forums.plex.tv/t/plex-wont-read-folders-files-on-mounted-drive-in-linux-mint/69278/23)
- [https://support.plex.tv/articles/200288596-linux-permissions-guide/](https://support.plex.tv/articles/200288596-linux-permissions-guide/)
- [https://forums.plex.tv/t/i-cant-add-my-media-folder-to-the-my-plex-media-server/214701](https://forums.plex.tv/t/i-cant-add-my-media-folder-to-the-my-plex-media-server/214701)

Please help me I don't want to go to windows, i want to solve this and have a very nice welcome back to Ubuntu. I will gladly send any log, screenshot or information you may need to help me solve this issue. Any suggestions, comments and help are highly appreciated.

Cheers

---

### Post by #&amp;thj^% on 2019-03-26
This is how I normally set mine up: [https://forums.plex.tv/t/using-ext-or-ntfs-drives-internal-or-external-on-linux/198544](https://forums.plex.tv/t/using-ext-or-ntfs-drives-internal-or-external-on-linux/198544)
Just what you wanted another link to read right? :)
There is lots of info there read with understanding. Good Luck

---

### Post by TheFu on 2019-03-26
Please post the file permissions for each of the top directories using** ls -la**.  About 99.9% of the time, it is a permissions issue.  Not using NTFS is an aid, if that is true.  Please prove it.  Here's how:

Also, best if you put the config file back to the original. I've never edited.

And a **df -Th** that shows the storage were Plex DBs are kept, Plex metadata is kept and where any of the "libraries" for media are located is needed too.

And when posting cmd output, please always, 
a) show the exact command run
AND
b) the relevant output. Non-relevant output just muddies of stuff.  For example, df cmds will produce lots of "loop" devices that are completely unimportant, unless plex is installed into one of them - like a snap might.  All the other loop devices are useless.
AND
c) wrap the output in 'code tags' so it is readable, lines up just like in the terminal.  The Adv Reply with # is how you get that.

---

### Post by lilithcrazygirl on 2019-03-26
> **1fallen said:**
> This is how I normally set mine up: [https://forums.plex.tv/t/using-ext-or-ntfs-drives-internal-or-external-on-linux/198544](https://forums.plex.tv/t/using-ext-or-ntfs-drives-internal-or-external-on-linux/198544)
Just what you wanted another link to read right? :)
There is lots of info there read with understanding. Good Luck

Wow, this link was really helpful. Plex was able to see the folders and  read the media.  But i just got one little side effect. . .
Whenever i plug the external drive it mounts on /disks/media3, but now  if i want to add files or do general movements on the drive, hmmm how do  i explain this. . . 
In the file explorer normally all the drives appear at the left in the  locations section and their name appears for easy access and the unmount  button (with a button that looks similar to when you take out a dvd  from a dvd player) and it seems i lost this little part. How could i fix  this little unwanted side effect?

Cheers

---

### Post by #&amp;thj^% on 2019-03-27
Sorry I'm having a hard time making out what your trying to explain, can you show a screenshot.

---

### Post by lilithcrazygirl on 2019-03-27
> **1fallen said:**
> Sorry I'm having a hard time making out what your trying to explain, can you show a screenshot.

Hi:

I am at work and my computer is at home, but i was able to find an image on the internet that explains this perfectly.

I think its normal behaviour in ubuntu that when you connect an external drive it shows like this in the file explorer. But now my external drive works on Plex perfectly but won't show like this.

Cheers

---

### Post by TheFu on 2019-03-27
When you mount through the fstab, it is mounted differently than when a GUI is used to mount, which almost always uses mounts in a fuse mode.  One uses the 'mount' command and the other uses gvfs to access the storage.  If the mount is used, the disk looks like local, permanent, storage, and has kernel performance for non-NTFS/FAT-whatever mounts. 

It might be possible to add the _x-gvfs-show_ option to the fstab line to get that storage to show up in Gnome GUI places.  I don't know if this will allow a normal user to fusermount -u and un-mount it or not.  The 'user,unhide' options might help with that, or perhaps the 'users.unhide' options.  IMHO, mounting and unmounting isn't something that end users should be allowed to do.

Don't know if this is helpful, but it is always good to check what the manpage has to say about the command and specific options:```

              For  more  details,  see fstab(5).  Only the user that mounted a
              filesystem can unmount it again.  If any user should be able  to
              unmount  it,  then  use users instead of user in the fstab line.
              The owner option  is  similar  to  the  user  option,  with  the
              restriction that the user must be the owner of the special file.
              This may be useful e.g. for /dev/fd if a login script makes  the
              console user owner of this device.  The group option is similar,
              with the restriction that the user must be member of  the  group
              of the special file.
....
       user   Allow an ordinary user to mount the filesystem.  The name of the
              mounting  user  is  written  to the mtab file (or to the private
              libmount file in /run/mount on systems without a  regular  mtab)
              so  that  this same user can unmount the filesystem again.  This
              option implies the options noexec,  nosuid,  and  nodev  (unless
              overridden   by  subsequent  options,  as  in  the  option  line
              user,exec,dev,suid).
...
       users  Allow any user to mount and to unmount the filesystem, even when
              some other ordinary user mounted it.  This  option  implies  the
              options  noexec,  nosuid, and nodev (unless overridden by subse&#8208;
              quent options, as in the option line users,exec,dev,suid).

       x-*    All options prefixed with "x-" are interpreted as comments or as
              userspace  application-specific  options.  These options are not
              stored in the mtab file, nor sent to the mount.type helpers  nor
              to  the  mount(2)  system  call.  The suggested format is x-app&#8208;
              name.option (e.g. x-systemd.automount).


```

 [https://wiki.gnome.org/Projects/gvfs](https://wiki.gnome.org/Projects/gvfs) has information about gvfs.

I avoid gvfs because it has been very slow and doesn't work on servers. There have attempts to make it faster in the last year. I don't know if those attempts have actually helped.
Usually, people use gvfs to access remote samba shares. This is where most of the performance complaints have been.  Also, not all applications recognize gvfs mounts, which isn't a problem, until it is.  

Just for clarification to lurkers, Un-mounting uses the **umount** (no 'n') command and requires sudo access.  End-user mounts of fuse file systems uses the **fusermount -u** command to un-mount fuse file systems.

---

### Post by ajgreeny on 2019-03-27
When using an external drive for plex I always quickly ran a command to unmount the disk and then remount it in my home; it didn't matter where in my home as long as it was one of the folders in the plex folder setup. That always worked fine.

Here's the command I used for this ```
sudo umount /dev/sdf1 && sudo mount /dev/sdf1 /home/$USER/Plex/USB/
``` It worked faultlessly for me so a version of it with the correct partition used (not my sdf1)

---

### Post by lilithcrazygirl on 2019-03-30
Hi:

I copied all my files to a new drive just in case everything got deleted, mostly as a caution because i was editing mount points and all the stuff you told me and it seemed a little scary. (i like to be safe when i am experimenting and besides its 2TB of my beloved content which i didn't want to risk). But right now everything is working wonderful. I don't know how to mark this thread as SOLVED, but i confirm with this reply that it is indeed everyhting working excellent.

Cheers

---

### Post by ajgreeny on 2019-04-01
Great news! You can mark the thread as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. 

It is a great help to users searching the forum in future.

---

