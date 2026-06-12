---
title: "Basic rsync script help."
date: 2015-05-16
forum: General Help
---

### Post by Roasted on 2015-05-16
Hello friends. I utilize a home server running OpenMediaVault. I keep everything stored there and sort things like pictures as needed. Basically what I do in this case is I put the SD card in the laptop from our camera and hit a hot key, which launches an rsync script. It syncs all pictures to a TO BE SORTED folder. Later on I'll drag/drop the items in that folder to their final destination elsewhere. Having them on the server already makes drag/drop instant, as opposed to syncing them to my laptop and drag/dropping them to different folders on the server later where I can stack up 3, 5, 10 transfers at once, which takes some time. Here is the script.

```
#!/bin/bash
set -e
notify-send "Camera Sync Started"
rsync -a /media/jason/SDCARD/DCIM/ jason@192.168.1.20:/media/2g780da3-263d-493f-af11-cc945e3158ef/pictures/TO_BE_SORTED/
notify-send "Camera Sync Complete"

```

This works fine with the exception of the "Camera Sync Complete" line. The actual sync completes (as in new pictures arrive on the server), however I never get a notification that it completed. 

If I remove set -e, it "works", however based on my reading, set -e is a good measure to have so if the rsync command itself fails, it does not pass the "Camera Sync Complete" command through in a false manner. Just now I unmounted the SD card and hit the hot key to run the script again, and sure enough it said Camera Sync Started followed by Camera Sync Complete... yet no SD card is mounted... so nothing truly completed.

Perhaps I should look into adding some more statements to it, so instead it'll try to sync, if it fails, it throws "Camera Sync Failed" in a notification instead. In the mean time I'm just keeping it simple and wondering if someone could explain why set -e is burning me in this case. Thanks for any assistance!

---

### Post by steeldriver on 2015-05-16
I'm not an rsync expert but my first thought would be to remove the set -e and examine the actual rsync exit code (using the $? shell variable) to try to figure out why it's non-zero

```

#!/bin/bash
# set -e

notify-send "Camera Sync Started"

rsync -a /media/jason/SDCARD/DCIM/ jason@192.168.1.20:/media/2g780da3-263d-493f-af11-cc945e3158ef/pictures/TO_BE_SORTED/
echo $?

notify-send "Camera Sync Complete"

```

You could even to a case...esac construct to report the various types of failure

---

### Post by corti-nico on 2015-05-16
> **steeldriver said:**
> I'm not an rsync expert but my first thought would be to remove the set -e and examine the actual rsync exit code (using the $? shell variable) to try to figure out why it's non-zero

```

#!/bin/bash
# set -e

notify-send "Camera Sync Started"

rsync -a /media/jason/SDCARD/DCIM/ jason@192.168.1.20:/media/2g780da3-263d-493f-af11-cc945e3158ef/pictures/TO_BE_SORTED/
echo $?

notify-send "Camera Sync Complete"

```

You could even to a case...esac construct to report the various types of failure

You can check on this page [http://wpkg.org/Rsync_exit_codes](http://wpkg.org/Rsync_exit_codes) the exit code to figure out what's wrong.
What about ssh auth? Are you using privatekeys or password?

---

### Post by steeldriver on 2015-05-16
FWIW the exit codes are listed in the rsync manpage

```

EXIT VALUES
       0      Success

       1      Syntax or usage error

       2      Protocol incompatibility

       3      Errors selecting input/output files, dirs

       4      Requested action not supported: an attempt was made  to  manipu&#8208;
              late  64-bit files on a platform that cannot support them; or an
              option was specified that is supported by the client and not  by
              the server.

       5      Error starting client-server protocol

       6      Daemon unable to append to log-file

       10     Error in socket I/O

       11     Error in file I/O

       12     Error in rsync protocol data stream

       13     Errors with program diagnostics

       14     Error in IPC code

       20     Received SIGUSR1 or SIGINT

       21     Some error returned by waitpid()

       22     Error allocating core memory buffers

       23     Partial transfer due to error

       24     Partial transfer due to vanished source files

       25     The --max-delete limit stopped deletions

       30     Timeout in data send/receive

       35     Timeout waiting for daemon connection

```

---

### Post by Roasted on 2015-05-16
It seems as if it's the -a that's getting to me, which includes a multitude of flags in rsync. It looks like retaining owner, group, and times is what fouls it up. Wonder why... anyway I have something to work with. If I just use rsync -r in the old script, it works fine and the Complete notification comes across without issue.

Due to the files syncing, yet not being able to reset the modification times/owner/group permissions, it transferred the files but fouled out after. Due to set -e, it never passed the 'Completed' notification since the nature of set -e is to fail the rest of the script if any lines fail.

---

### Post by Roasted on 2015-05-16
Unfortunately I closed all of my terminal windows so let me see if I can articulate this from memory...

Basically with OpenMediaVault (OMV) it sets ownership/group to root:users for all directories. All users are added to the users group. Default rwx permissions are 775. You can add users to write list, read lists, or even basic access lists. This appends these users to the smb.conf as appropriate users for read, write, etc. In essence, it passes basic samba flags in the smb.conf to control who has access.

So if we envision /media/UUID/pictures being root:users @ 775 permissions, and the user "jason" rsyncing info with the -a flag, it's going to try to retain modification times, ownership, group assignment, etc. It gets hung up on /media/UUID/pictures/TO_BE_SORTED/.

Notice the period at the end. Period as in this top line here:

drwsrwsr-x 31 root users  4096 Apr 30 21:01 .
drwxr-sr-x 14 root users  4096 Mar 16 23:27 ..

So when I rsync the data to the /media/UUID/pictures/TO_BE_SORTED directory, it tries to adjust the modification time to /media/UUID/pictures/TO_BE_SORTED/. (note the period), but cannot, because root owns it - not jason. Again, jason only has access from being a member of "users", and "users" being the group assigned to the directory.

Moral of the story, if you're rsyncing data you own to a location you own, rsync -a is fine. But in this case, the destination I don't technically own, so it acted up accordingly. Due to using set -e, it fails the rest of the script if an error is encountered. So you have camera sync started, then the rsync command, then camera sync complete. Due to rsync's design, it will transfer the data first, then append time modification stamps, ownership, group, permissions after. Since that part fails, the data succeeds the sync since it happens first, but set -e causes everything else to fail. The only thing beyond the rsync itself... is camera sync complete.

So, I guess we're good? I just may need to use rsync -r in this case, me thinks. Any opinions?

---

### Post by sudodus on 2015-05-17
One way to preserve permissions and ownership is to create a tarball. The tarball itself can have whatever permissions are possible for a regular user in the remote computer.

---

