---
title: "ssh keypair for developers"
date: 2013-11-04
forum: General Help
---

### Post by gopukrishnan on 2013-11-04
[TABLE]
[TR]
[TD="class: votecell"]      

              [/TD]
              [TD="class: postcell"]                I have a linux web server in which I have multiple web sites.  I have 5 website programmers now doing the coding for all the sites.  How can I provide a key-based authentication for the programmers in such  a way that they have access only to /home folder ? They should be able  to access only all the files inside /home and able to modify it. 

      

[/TD]
[/TR]
[/TABLE]

---

### Post by Lars Noodén on 2013-11-04
I'm guessing you mean using SFTP and not wanting to provide shell access.  

You'd do that with [ChrootDirectory](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html) and ForceCommand with [internal-sftp](http://manpages.ubuntu.com/manpages/raring/en/man8/sftp-server.8.html).  The following block applies to users in the group "sftp-only"

```

Subsystem sftp internal-sftp

Match Group sftp-only
        ChrootDirectory /home
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp -d %u

```

As you read in the man page, the chroot directory has to be owned by root and  not writable by others.  /home meets that requirement already.  The -d option then specifies the user's home to start in.  Using this method they can still see the other home directories but have to go out of their way to navigate to them.  

Is that what you were trying to get?

---

### Post by gopukrishnan on 2013-11-04
Hello Lars,

Unfortunately I was not looking for chroot. I wanted to create a user he is able to ssh into the server. I will elaborate my requirement: I have a cPanel server in which all the sites comes under /home directory as /home/site1 and /home/site2 etc. I want my programmer to access the /home so that he would be able to access all sites without having separate passwords for each and every site. I planned to create a user with his home directory /home/test_user and creating a softlink of the /home directory under his home directory /home/test_user. Since each site is having its own permission, I cant give full permission for the test_user for all the directories in /home. This is something like a root user having only access to /home and the changes he made should keep the current user permissions for the files and folders. I am really stuck.

Thanks,
Gopu

---

### Post by Lars Noodén on 2013-11-04
I'm still not quite sure about the requirements but take a guess.  

What about setting the account's home directory to /home and then letting the developers "cd" to the various site's subdirectories?  Write access would be granted by using group permissions, but just to the specific directories needed, not to all.  If you do that, you don't need to keep the authorized_keys file in the home directory, you can designate an alternate location in [sshd_config](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html) using "AuthorizedKeysFile".  So you could do something like this.

```

AuthorizedKeysFile .ssh/authorized_keys  /etc/ssh/keys/%u/authorized_keys

```

Where it looks in the home directory first but then in an alternate directory second.

---

### Post by gopukrishnan on 2013-11-06
Inside the /home directory, each site is having its own ownership. For example, /home/site1 should have ownership user1:user1 and /home/site2 should have user2:user2 and so on. If I create a user 'developer' with home directory as /home, would he be able to access and modify the site files inside /home/site1 and /home/site2 which is having different ownership. Its not practical to add the user 'developer' to all the groups user1,user2 etc. Any thoughts on this ?

---

### Post by Lars Noodén on 2013-11-06
Groups are the only way to do that, unless your sites' directories are also owned by the user 'developer'.  You could chown the directories, which would also limit you to one developer per site, but that is as much work or more than adding the developer to all the right groups.

---

### Post by gopukrishnan on 2013-11-06
Hi Lars,

I have succeed half of the task using setfacl but but the websites got 500 internal server error.:(

---

