---
title: "trying to change owner with chown"
date: 2023-08-10
forum: General Help
---

### Post by jgw on 2023-08-10
I have been trying to change the owner of a folder.  I have tried:

sudo chown -R owner_name /mnt/3tb/TV
sudo chown -R owner_name:my_name /mnt/3tb/TV
sudo chown owner_name /mnt/3tb/TV
sudo chown owner_name:my_name /mnt/3tb/TV

I am sending you two pictures.  One of permissions as normal user and the other as super user.  The super user one show what I am trying to do and the other with no owner at all.  I have no idea which one is right and which one is wrong.

Thoughts?

---

### Post by Holger_Gehrke on 2023-08-10
Would this folder happen to be the mount point of a file system ? And is it a file system that can store Unix style permissions ? If it is NTFS or (Ex)Fat, then you can't have permissions and owners stored on that file system. You'll have to change the way you mount it to include a (simulated) owner with the mount option uid=<numeric user id as output by the command 'id'> or as an alternative for NTFS you can create a usermapping file that maps Linux users to NTFS SIDs and pass that file as a parameter to the mount option 'usermapping='. Read 'man mount' and 'man ntfs-3g' for the details.

Holger

---

### Post by jgw on 2023-08-10
Thank you for the reply...

I think you are asking if the file is mounted.  Its address is /mnt/3tb/TV.  Its a file that holds a list of other things.  I ran getfacl on it:
greg@greg2:~$ getfacl /mnt/3tb/TV
getfacl: Removing leading '/' from absolute path names
# file: mnt/3tb/TV
# owner: sonarr
# group: greg
user::rwx
group::rwx
other::r-x
(I ran this from several addresses and got the same result - when I am super user the owner is also there)

If this is true then something is very strange.  It still shows, when just clicking on the file, that it has no owner!  Again, the address of the file is /mnt/3tb/TV.  then I did this: 
greg@greg2:~$ ls -d -l /mnt/3tb/TV
drwxrwxr-x 164 sonarr greg 12288 Aug 10 16:15 /mnt/3tb/TV

Sonarr is still the owner.  However, when I just goto the file.  Click on properties there is no owner.  
/mnt/ is owned by me and group is root,  /3tb/ owned by me and so is group (have no idea if this matters)

I just don't understand how this can be or why.  I have never had a file that has no owner, for instance.  But it only has no owner in specific circumstances.  

Thoughts?

---

