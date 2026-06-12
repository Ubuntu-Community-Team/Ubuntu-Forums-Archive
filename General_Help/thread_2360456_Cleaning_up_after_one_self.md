---
title: "Cleaning up after one self"
date: 2017-05-04
forum: General Help
---

### Post by raleigh3 on 2017-05-04
I have a cleanup script.

When I recently ran it, I got this.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.4.0-71 linux-headers-4.4.0-71-generic linux-headers-4.4.0-72
  linux-headers-4.4.0-72-generic linux-image-4.4.0-71-generic
  linux-image-4.4.0-72-generic linux-image-extra-4.4.0-71-generic
  linux-image-extra-4.4.0-72-generic
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 594 MB disk space will be freed.
Do you want to continue? [Y/n] 
```

1/2 Gig is no small potatoes.

Where is all this coming from ?

Doesn't uninstalls etc clean up after themselves ?

How would I verify the before and after amount of disk space being used ?

---

### Post by vasa1 on 2017-05-05
> **raleigh3 said:**
> I have a cleanup script.
...
What are the contents of the script?

If you haven't messed up things, some time after a new kernel is installed you should see something like```
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic
  linux-image-4.4.0-72-generic linux-image-extra-4.4.0-72-generic
Use 'sudo apt autoremove' to remove them.

```Each kernel removal frees up about 279 MB.

```
The following packages will be REMOVED:
  linux-headers-4.4.0-72* linux-headers-4.4.0-72-generic* linux-image-4.4.0-72-generic* linux-image-extra-4.4.0-72-generic*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 297 MB disk space will be freed.
Do you want to continue? [Y/n] 

```

Normally, the latest and the previous kernel are retained.

---

### Post by mastablasta on 2017-05-05
> **raleigh3 said:**
> 
Where is all this coming from ?

Doesn't uninstalls etc clean up after themselves ?


These are old kernels. if an update goes wrong (they occasionally do) or when a new kernel comes with a bug that affects your specific hardware setup, you will be thankfull to have a kernel you can fall back to.

with 0.5TB or 1TB drives this really is a non issue. kernels would take up much less than 1% of the hard drive.

[/QUOTE]
How would I verify the before and after amount of disk space being used ?[/QUOTE]

in terminal try:
```
df -h
```

before and after.
if you want to see disk usage then use du command. for example:

```
du -h
```

try
```
man df
man du 
```

for additional information on commands and their switches.

---

