---
title: "tar command ran out of memory"
date: 2007-12-08
forum: General Help
---

### Post by artooro on 2007-12-08
Hi folks,

Just a quick question here, When I try to create an archive file from a 4.1GB folder I get an error message like so:
```
fatal: Out of memory? mmap failed: Cannot allocate memory
```

My question just happens to be is there any way I can circumvent that? The machine has 512MB of RAM and I don't really want to install more not to mention 5GB.

The thing is eventually I need to use this function for archiving folders consisting of 160GB which would certainly pose a problem in this situation. Luckily that box has more RAM but still.

The only thing I've thought of so far is having tar output to STDIN and pipe it to a file. Haven't tried it yet though.

Appreciate your tips!

---

### Post by tgalati4 on 2007-12-08
Post the output of:

>df -h

How large is your swap file?

---

### Post by artooro on 2007-12-08
OK the output of df -h is:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             128G   17G  105G  14% /
varrun                252M  256K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   84K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   35M  218M  14% /lib/modules/2.6.22-14-386/volatile
```

and I have 1.3 GB of swap with 130MB being used. And I watched the memory statistics as the script was running and it didn't come near the restrictions. Doesn't seem the lack of physical memory is the issue here.

Just for interest sake, the script I'm using is this here:
```
#!/bin/bash

############# CONFIGURATION #####################
backup_location="/home/lgc/backup/vmware/"
path_to_vmx="/var/lib/vmware/Virtual Machines/Windows XP Home Edition/Windows XP Home Edition.vmx"
path_to_vm="/var/lib/vmware/Virtual Machines/Windows XP Home Edition/"
#################################################

# Shutdown running VM
/usr/bin/vmrun stop "$path_to_vmx"

# Tar and feather the VM
tar -vcf $backup_location/vmware_backup.tar "$path_to_vm"

# Commit this revision to GIT VC
cd $backup_location
git add vmware_backup.tar
git commit -m "Automatic backup"

# Start VM
/usr/bin/vmrun start "$path_to_vmx"

```

---

### Post by tgalati4 on 2007-12-08
You are trying to run this tar operation from a virtual machine?

There may be limits in the virtual machine parameters that keep it from clobbering the host.  You may have found one of them.

---

### Post by dagnabit dang doohickey on 2007-12-08
Isolate your problem by commenting out the vmrun "stop" and "start" lines in the bash script. Shut down the virtual machine if it's running. Now, run the script to see if tar still returns an error.

---

### Post by dagnabit dang doohickey on 2007-12-08
There are two slashes next to each other in the path to your tar file in the tar command.

---

### Post by artooro on 2007-12-08
OK, once I commented out the git lines:
```
# Commit this revision to GIT VC
cd $backup_location
git add vmware_backup.tar
git commit -m "Automatic backup"
```

I stopped getting the error. Now, what to do about that?

Basically what I'm trying to do is write a system to automatically backup a virtual server for a client to an external hard drive. I thought it would be really nice to have versions of the backup and so decided to try git.

Is there something I'm missing? If I run the commands individually without the script, it works great. Seems there's an issue here that I don't understand.

Thanks for your help folks!

---

### Post by artooro on 2007-12-08
OOH wait a minute, it seems now when I actually run "git add vmware_backup.tar" I actually get the error there:
fatal: Out of memory? mmap failed: Cannot allocate memory

OK, at least we're getting somewhere. I guess the subject of this post is rather decieving by now.

---

### Post by dagnabit dang doohickey on 2007-12-08
This [link]("http://josefsipek.net/blahg/?p=219") has info on the problem of using git with large files.

---

### Post by artooro on 2007-12-08
Raw pain that it is. Probably won't see me using git again.

Looking into versioned file systems using FUSE now.

Thanks for the help.

---

