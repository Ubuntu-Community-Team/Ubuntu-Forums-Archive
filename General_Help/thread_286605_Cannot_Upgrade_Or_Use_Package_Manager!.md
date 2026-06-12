---
title: "Cannot Upgrade Or Use Package Manager!"
date: 2006-10-28
forum: General Help
---

### Post by Vert on 2006-10-28
I'm running Edgy 6.10 and everything has been fine.  Then today, I come home and try to update and it says it's unable to.  It says, "E: The package swiftfox needs to be reinstalled, but I can't find an archive for it."  Upon further playing of commands it says, 

# sudo aptitude purge swiftfox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  swiftfox{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 24.3MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing swiftfox (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 swiftfox
Aborted (core dumped)

Because of this, Ubuntu will no longer find it's repositories.  When I go to update-manager it crashes when it is reading the repositories and when I go into synaptic no packages show up (not even the ones installed on my system) and it gives me a pop up with this error 

E: The package swiftfox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Any help at all would be much, MUCH appreciated.  I'm going crazy here... I need my updates and I can't install or remove any packages! ](*,)   Thank you to the Ubuntu Community at large in advance for any help or advice.

---

### Post by ~LoKe on 2006-10-28
How about something as simple as...
```
sudo dpkg-reconfigure swiftfox
```
or...
```
sudo dpkg -r swiftfox
```

---

### Post by Vert on 2006-10-28
I tried what you said and after the first time I tried these commands I ran the swiftfox installer, only to get the same messages.

# dpkg-reconfigure swiftfox
/usr/sbin/dpkg-reconfigure: swiftfox is broken or not fully installed

# dpkg -r swiftfox
dpkg: error processing swiftfox (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 swiftfox

---

### Post by Stirling on 2006-10-28
Try downloading the deb file and reinstalling it.

[http://getswiftfox.com/debian.htm]("http://getswiftfox.com/debian.htm")

---

### Post by Vert on 2006-10-28
When I try to use the Gdebi package installer it will pop up this menu [http://aycu08.webshots.com/image/7607/2003771248734427848_rs.jpg](http://aycu08.webshots.com/image/7607/2003771248734427848_rs.jpg) and will not let me continue the installation.

[Edit: The picture is broken for some reason... but it says, 
"Could not open 'swiftfox_2.0-1_athlon-xp.deb'  The package might be corrupted or you are not allowed to open the file.  Check permissions of the file."  (I'm the owner of the file and I have full access to it)]

---

### Post by Vert on 2006-10-29
I've tried everything I can think of and yet I still cannot upgrade, update, or install any debian packages.  Please any help at all would be appreciated.  I'd rather not have to format/reinstall ubuntu and lose all my data.

---

### Post by ~LoKe on 2006-10-29
Trying deleting the cached .deb file for swiftfox.

---

