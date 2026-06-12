---
title: "File Permissions and Share"
date: 2008-06-25
forum: General Help
---

### Post by Rival9999999999 on 2008-06-25
I installed ampache on my server with success. I have created a catalog in apache for my music stored in the Home/music directory. When I download a new song on my main computer I ftp to the server and drop it in the correct folder. The only issue I have is that the files do not inherit permissions from its parent folder which gives me access denied errors. Is there a folder by default on the server that has read write and delete permissions? Is there a way to have files that I move to the server to automatically pick up the proper permissions? Any help would be great!

-JB

---

### Post by bodhi.zazen on 2008-06-25
Not sure if this helps, you are probably best off ssh into the server and changing the permissions.

[http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_11_1077830297](http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_11_1077830297)

[http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)

---

### Post by dexter.deepak on 2008-06-25
the "new" files created by the server are given the file permissions that are specific to the server as an "user"
i think you have to change the umask value of that "ampache user" in order to get the right permissions....sorry i cant tell you much about how to use umask...but that it can be used to set the "default permissions on the newly created files" (the default is 022 defined in the /etc/profile)

---

