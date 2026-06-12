---
title: "Default mount permissions for launcher volume mounts"
date: 2014-03-09
forum: General Help
---

### Post by guice on 2014-03-09
I've running a dual boot system. Ubuntu has automatically recognized, and created launcher shortcuts for each Windows volume.

However, I have a problem when using them: the permissions are poor for my needs. How do I modify the default mounting permissions? The case being, I'm running a local Apache instance that I want to access these files. With default user www-data:www-data against my default mount user:user, mask 0077, it doesn't play well. I need one of a couple options: enable umask of 0027 (allowing me to add www-data to my user group), or 0022. And, preferably, a way to modify group on selected directories.

How do I achieve this? I've already checked /etc/fstab and noticed they were indeed not in there. Ideally, I do need one particular mount to be there (auto-mounted on boot): my Data drive.

Thanks

---

### Post by tfrue on 2014-03-11
You *have* to mount with "root" privileges. I've seen the program *pmount*, but I don't advise using it as it can cause a tremendous amounts of damage. You also have to manually add the mount options to /etc/fstab so they can be auto-mounted at boot since a script will run that will mount everything listed in /etc/fstab at boot. 

I don't quite understand what you are trying to get at with the permissions, the only thing I can advise from what I understand is that you will set the permissions on the directories you plan to mount the Windows volumes. Which you would do after you mounted the volumes because it would be pointless to set the permissions then mount as they would be over-ridden when the volume mounts.

I would also over look your permissions you are trying to apply, here is what you are doing: 

0077 / 0027.

That means you are trying to give the owner no privileges on both, the group either full (for the first) / 2 isn't even an option (For the second), and full control for the Computers(Users) on both.

Remember, the Read/Write/Execute bits are set up as 4/2/1. So 0754 is 0(Sticky bits)/ 7(RWX for Owner) / 5(RX for Groups) / 4(R for Computers)

I suggest that you only put Write and Execute permissions on the files that need those permissions, we don't want to be too giving with other people handling data on our servers.

Good luck,
Chris

---

### Post by guice on 2014-03-11
I think you misunderstood some of my question: the **umask** is 0077 currently. Which is equiv to 0700 for directories and 0600 for files. I need the umask updated to allow group or other permissions. 

I'm wanting to know of there's a way to modify the default created mount short-cuts created by Ubuntu in the Unity side-bar, so that it uses a umask of 0007 or 0022.

However, manually adding it to fstab will allow me to manually set user, group, and default umask accordingly.

---

### Post by Morbius1 on 2014-03-11
> I need one of a couple options: enable umask of 0027 (allowing me to add  www-data to my user group), or 0022. And, preferably, a way to modify  group on selected directories.
Since your Windows partitions are in a dual boot environment add mounting to /etc/fstab so they mount automatically when booted.

Here's an example with say your "D Drive""

Create a mount point:
```
sudo mkdir /WinD
```
Find the UUID number ( a unique identifier of that partition ) by running the following command:
```
sudo blkid -c /dev/null
```
Then enter the following line - with the correct UUID - at the end of /etc/fstab:
```
UUID=DA9056C19056A3B3 /WinD ntfs defaults,nls=utf8,umask=027,uid=1000,gid=1000,windows_names 0 0
```
Unmount the partition if it's currently mounted.

 Then remount it with this command:
```
sudo mount -a
```
If there are no errors your WinD partition should have you as owner and group with permissions of 750.

NTFS mounts in linux are virtual in that what linux sees is a "view" created by the fstab statement to give it the appearance that it has Linux permissions when in fact it does not. They are also immutable in that you can't make a sub-directory have permissions different from the parent.

[I]Note: That last sentence is not entirely true. You can set set sub-folders to different permissions but you have to use something like bindfs to do it.

[COLOR=#0000cd]Another note[/COLOR]: If you want to remove the execute bit on files you can break apart umask into it's component parts: dmask for directories and fmask for files so the line in fstab would change to something like this:
```
 UUID=DA9056C19056A3B3 /WinD ntfs defaults,nls=utf8,dmask=027,fmask=137,uid=1000,gid=1000,windows_names 0 0
```
Then folders will be 750 and files will be 640.
[/I]

---

### Post by guice on 2014-03-11
Awesome! That's what I was looking for. I was trying to find the UUID a few times over the weekend, with little success. I justed blkid. I'll try the -c switch. This is great info! I'll try it tonight, and let you know the outcome. Thanks!

---

