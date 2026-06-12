---
title: "Webdav authentication question (beginner)"
date: 2013-04-11
forum: General Help
---

### Post by karnalta on 2013-04-11
Hi all,

I am still quite new to Linux (2 weeks) and I am facing a right management problem that I can't solve by myself.

I have setup a Webdav server with SSL authentication to have a remote access to my /mnt/raid5/ storage.

My webdav is working correctly but only if I set www-data user as the owner of /mnt/raid5. If I set, let say "userxxx", owner of this raid I endup with a problem where I cannot see the directory anymore in webdav.

The problem is that, when www-data is the owner of the directory, a simple browser is able to download a file from it with "https://xxx.xxx.xxx.xxx/webdav/raid5/afile.xxx".

I am getting a little bit confused about the right management of webdav. I have created a user into the htpasswd file of Apache2 that is used to authenticate to webdav (it's working with a software like BitKinex) but why a simple browser let access to my file without asking any authentication ?? (because the htpasswd's user is member of www-data ?)

What I'd like to do is using the existing linux user to manage right on /mnt/raid5 even with Webdav, so I could tell "userxxx" member of the group "groupxxx" is the owner of it. And so, only him could authenticate to webdav and view/edit/delete his content.

Can someone light me up a little bit about that ?

Thank a lot.

---

### Post by karnalta on 2013-04-11
Bump.

No one can help me ? I though it was a simple newbie misunderstood..

---

### Post by karnalta on 2013-04-12
I have partially solved my issue.

Concerning the fact that all my files were accessible by a simple HTTPS request in a browser, it was due to my lack of attention about the conf file of webdav. I had just copy/paste it from a tutorial and I didn't noticed that they were a exception for the GET command in it.

I have commented it out like this and it's now impossible to access anything without authentication.

```

Alias /webdav /mnt
<Location /webdav>
   DAV On
   SSLRequireSSL
   Options None
   AuthType Basic
   AuthName WebDAV
   AuthUserFile /etc/apache2/conf.d/.htpasswd
   Require valid-user
#   <LimitExcept GET OPTIONS>
#       Order allow,deny
#       allow from all
#       Require valid-user
#   </LimitExcept>
</Location>

```

But I think I am still missing a basic right knowledge, here is my case :

- I have a group called "MyGroup" and the two users "www-data" and "myuser" are both members of this group.
- The /mnt/* directory is chmod on 770

If I chown -R /mnt with "www-data:MyGroup" user, Webdav has full access to it and "MyUser" as also access to it. That's sound logic for me.

But, if I chown -R /mnt with "MyUser:MyGroup", Webdav has no more access to it and "MyUser" still have. That's what I don't understand ... if "www-data" is member of "MyGroup" and that /mnt is chmod of 770, "www-data" should have access, no ?

---

