---
title: "Understanding Users/Groups and Permissions"
date: 2014-03-04
forum: General Help
---

### Post by NebulaM57 on 2014-03-04
Hello,

  I am not really sure how to ask my question so I'll explain what I'm trying to do.
  I am wanting to make a personal "cloud" for viewing PDF's and other documents remotely via a browser.

  I have an physical Ubuntu 12.04 Desktop running as a file server.  There are 5 individual drives, each configured a volume.  Documents are on VOL4.
  I also have an Ubuntu 12.04 VM Desktop.  It has Apache 2 installed.  From this VM, I added an entry inside fstab that points to the documents folder on the remote VOL4.
  So from the VM, I am able to see my files in the documents folder on the remote VOL4.  Also, Apache is serving the documents as desired.

  Problem:  As it currently runs, everyone has access to these documents.

  Desire: I want to be able to give access to a few people with username/password security.  Or, give a group rights to the folder and make users as part of the group.

  Help: In windows or novell, I understand how to give a folder group rights and make users part of a group.  But I am rather confused with this process in linux.  I was hoping I could get a "simple" step by step for a similar situation that would help me understand the concepts of users/groups and rights in linux.  I have seen pages on ACL's.  That sounded like what I wanted.  But I've had trouble adding 'acl' to the fstab line.  Remounting the drives return an error.  Another issue is knowing if I should be configuring this via linux or within apache itself.  I'm pretty comfortable getting around in linux, but I just have trouble getting my head around the users/permissions stuff.

  Thanks for any help you can provide.

Doug

---

### Post by Lars Noodén on 2014-03-04
How are your users to access the files, via Apache or via the file system?  If via the file system, it is EXT3 or EXT4, right?

---

### Post by NebulaM57 on 2014-03-04
Yes, the file system is EXT4 I believe.  Access to the files is thru Apache.

  My desire was to not have to download the document before viewing it.  I was hoping to find something that would let me "stream" the document.  Then there would be no cleanup of old files to worry about.  It would be nice to be prompted for user/pass then straight to file directory.  I know this is not the only way to do this.  So if you have a suggestion for a better way, I'd like to know.  I was originally thinking of a free document management system.  But I don't know enough about them to know what to look for.  

  In the end, I was just wanting a simple little system for about 10 people.

Doug

---

### Post by Lars Noodén on 2014-03-04
Ok, if access is via Apache, then that's where you have to do the configuration.  It helps if you have HTTPS set up first so that the passwords are not send unencrypted.  

   [http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html)

Generally the user+password database used by Apache is separate from the system accounts.  There are a lot of tutorials on how to set a password on a web directory, but ignore references to .htaccess because it is not needed because you already have access to the main configuration file.  

The way HTTP/HTTPS works is that the web browser downloads the whole file and saves a copy locally and then displays that.

---

### Post by Elfy on 2014-03-04
*Thread moved to **General Help**.*

---

### Post by amish_otaku on 2014-03-05
You might also look at using owncloud on your "server" as I think it can do username/password access permissions. Plus it has quite a few builtin features that might be right up your alley.

---

### Post by NebulaM57 on 2014-03-07
YYpzf4N,

  Hey, I took you up on the ownCloud suggestion.  So far so good.  Thanks for the info!

---

### Post by amish_otaku on 2014-03-12
NP man... sounded like it might be just the fit.

---

