---
title: "apt/synaptic locked and broken"
date: 2007-02-22
forum: General Help
---

### Post by dmex on 2007-02-22
Hello                                        (OS 6.10)

My apt installation is not updating and is not allowing me to install anything, I get the exact same error as gig ([http://ubuntuforums.org/showthread.php?t=217744&page=2](http://ubuntuforums.org/showthread.php?t=217744&page=2)) I tryed to delete the files and change the permissions but everything I have tryed allways come up with a error?
Im not sure if autopackage might have something todo with it?
 when running synaptic i get

E: Lists directory /var/lib/apt/lists/partial is missing.
E: Unable to lock the download directory
E: Lists directory /var/lib/apt/lists/partial is missing.
E: Could not open lock file /var/lib/apt/lists/lock - open (20 Not a directory)
E: Unable to lock the list directory

If anyone has any thoughts on how to repair apt?
it would be a shame if I had to reinstall :<

Thanks
Steven

---

### Post by zanglang on 2007-02-22
Try 'sudo mkdir -p /var/lib/apt/lists/partial' first and then 'sudo aptitude update'. Does it still give an error?

---

### Post by dmex on 2007-02-23
Yeah theres stll some error there

 j@j-xs:~$ sudo rm /var/lib/apt/lists/partial
rm: cannot remove `/var/lib/apt/lists/partial': Not a directory

The permissions for lists and periodic are a bit weird though...

s--x---rw- 34 1935736866 2004075939 33619980 1971-01-26 05:05 lists
srw-r-s--x 34 3316580386    2278826 17694744 2026-01-23 21:11 periodic

chmod cant change the permssions it says operation not permitted
 any ideas on how to reset the permissions for the file or completely remove it?

---

### Post by zanglang on 2007-02-25
That looks pretty bad. Try:
> sudo rm -rf /var/lib/apt/lists
sudo mkdir -p /var/lib/apt/lists/partial
sudo chmod -R 755 /var/lib/apt/lists

---

### Post by sonoftheclayr on 2007-03-01
I have the same problem and last night when I did it I fixed apt but today the same thing happened and again I followed the above steps but to no avail. I still have the same problem.
Kubuntu 6.10

---

### Post by Porpoise on 2007-12-23
Your the man zanglang

 sudo mkdir -p /var/lib/apt/lists/partial

worked for me - I guess it re-created the file, which enabled the Upgrade to proceed. I'm now fully upgraded and functioning (AFAIK).

Cheers.

---

