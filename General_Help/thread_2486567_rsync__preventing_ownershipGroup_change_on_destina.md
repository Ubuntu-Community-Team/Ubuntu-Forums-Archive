---
title: "rsync  preventing ownership/Group change on destination Home"
date: 2023-05-04
forum: General Help
---

### Post by giobaxx on 2023-05-04
i have to rsync the home folder for user to new workstation and i have sudo privilege. how can i rsync their home profile without changing the original user and group ownership?  Is the command below correct?

> sudo rsync -auvz -o -g  /home/user1/       admin@newcomputer:/home/user1/

Thanks in advance

A.

---

### Post by #&amp;thj^% on 2023-05-04
Well the -o and -g options are required. Excluding them will fail to update their respective attribute, but produce no error.
I use:
```

rsync -og --chown=<user>:<user> [src] [dest]
```
Change the user to the right name, and src, dest to the proper paths.
Man Page:
```
-o, --owner
    This option causes rsync to set the owner of the destination file to be 
    the same as  the source file, but only if the receiving rsync is being run 
    as the super-user (see also the --super and --fake-super options). Without 
    this option, the owner of new and/or transferred files are set to the invoking 
    user on the receiving side...

-g, --group
    This option causes rsync to set the group of the destination file to be the same as 
    the source file. If the receiving program is not running as the super-user (or if
    --no-super was specified), only groups that the invoking user on the receiving side
    is a member of will be preserved. Without this option, the group is set to the default
    group of the invoking user on the receiving side...
```
Hope this helps.

---

### Post by giobaxx on 2023-05-04
Tanks for your reply, i made some step forward but it seems the problems is using running rsync with sudo. On the remote system i don't have permission denied copying the profile:


> rsync: failed to set times on "/home/user1/ ": Operation not permitted (1)
./
.ICEauthority
.bash_history
.bash_logout
.bashrc
.profile
examples.desktop
pippo.txt
rsync: recv_generator: mkdir "/home/user1/backup/.config" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/home/user1/backup/.gnupg" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/home/user1/backup/.local" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/home/user1/backup/Desktop" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***






There is a way to run it?  Admin and user1 are account in both machine but while admin have sudo privilege, user1 does not have.

---

### Post by aljames2 on 2023-05-04
For remote situations requiring sudo on the remote end, I do similar to this:

```

sudo rsync -avz -e "ssh" --rsync-path="sudo rsync" desk-box:/source/ /target/ —dry-run

```

-a is archive and is the same as:  -rlptgoD

The —dry-run will let you view what the outcome will be before making it official.  If you have a successful dry run, then you can simply remove the dry run on the tail end of the command to complete the command.

The “desk-box” in my case is defined in an SSH config file, containing the host info and user name that will be performing the task on the remote end.  Of course, that user needs to exist on the remote end and have elevated privileges.

---

### Post by #&amp;thj^% on 2023-05-04
> **aljames2 said:**
> For remote situations requiring sudo on the remote end, I do similar to this:

```

sudo rsync -avz -e "ssh" --rsync-path="sudo rsync" desk-box:/source/ /target/ —dry-run

```

-a is archive and is the same as:  -rlptgoD

The —dry-run will let you view what the outcome will be before making it official.  If you have a successful dry run, then you can simply remove the dry run on the tail end of the command to complete the command.

The “desk-box” in my case is defined in an SSH config file, containing the host info and user name that will be performing the task on the remote end.  Of course, that user needs to exist on the remote end and have elevated privileges.
+1

---

