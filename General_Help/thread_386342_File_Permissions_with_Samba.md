---
title: "File Permissions with Samba"
date: 2007-03-16
forum: General Help
---

### Post by Kickboy on 2007-03-16
This has been bugging me for a while. I've mostly just ignored the issue, but I've realized it is a major security concern and so should be addressed.

Here's my problem:

I have a development server on my home network that runs Ubuntu, and I use Windows as my main development environment. I use samba to work on my web projects over the network, which is all fine and good for the most part. The issue comes in with file permissions. These files not only have to be accessible via the network, but also via HTTP and FTP (other people work on some of these projects). Since my home network is pretty secure, and I hate having to type a password in every 10 minutes to edit my files, I have samba set up as 'shared', so anyone on the network has access to the files. I'm really not too worried about this concept in general. However, what I am concerned about is the fact that every file has to have FULL guest permissions (757 or 777) in order for me to edit it via Samba. I find this to be less than ideal for any kind of web server. I have attempted to find a way for Samba to run as a different user over the network so I could just set permissions on all web files to 752, which would be the most ideal. My attempts at finding a way to do this have failed. Samba refuses to let me run as a different user. This is quite frustrating.

Another annoyance: For some reason I can't save the file over the network if I don't have execute permissions. This seems really mind boggling to me. If I have read a write permissions, I should be able to save a file. I'm not sure if this is a Samba or a Windows issue, but it can be frustrating.

If anyone has any kind of a solution for me, I'd love to hear it.

Thanks,
- Kickboy

---

### Post by dannyboy79 on 2007-03-16
i believe you can use the force user, force group, force create mode  options for that share in your smb.conf

**force group (S)**

    This specifies a UNIX group name that will be assigned as the default primary group for all users connecting to this service. This is useful for sharing files by ensuring that all access to files on service will use the named group for their permissions checking. Thus, by assigning permissions for this group to the files and directories within this service the Samba administrator can restrict or allow sharing of these files.

    In Samba 2.0.5 and above this parameter has extended functionality in the following way. If the group name listed here has a '+' character prepended to it then the current user accessing the share only has the primary group default assigned to this group if they are already assigned as a member of that group. This allows an administrator to decide that only users who are already in a particular group will create files with group ownership set to that group. This gives a finer granularity of ownership assignment. For example, the setting force group = +sys means that only users who are already in group sys will have their default primary group assigned to sys when accessing this Samba share. All other users will retain their ordinary primary group.

    If the force user parameter is also set the group specified in force group will override the primary group set in force user.

    Default: force group =

    Example: force group = agroup 

**force user (S)**

    This specifies a UNIX user name that will be assigned as the default user for all users connecting to this service. This is useful for sharing files. You should also use it carefully as using it incorrectly can cause security problems.

    This user name only gets used once a connection is established. Thus clients still need to connect as a valid user and supply a valid password. Once connected, all file operations will be performed as the "forced user", no matter what username the client connected as. This can be very useful.

    In Samba 2.0.5 and above this parameter also causes the primary group of the forced user to be used as the primary group for all file activity. Prior to 2.0.5 the primary group was left as the primary group of the connecting user (this was a bug).

    Default: force user =

    Example: force user = auser 

**force create mode (S)**

    This parameter specifies a set of UNIX mode bit permissions that will always be set on a file created by Samba. This is done by bitwise 'OR'ing these bits onto the mode bits of a file that is being created or having its permissions changed. The default for this parameter is (in octal) 000. The modes in this parameter are bitwise 'OR'ed onto the file mode after the mask set in the create mask parameter is applied.

    The example below would force all created files to have read and execute permissions set for 'group' and 'other' as well as the read/write/execute bits set for the 'user'.

    Default: force create mode = 000

    Example: force create mode = 0755 

**force directory mode (S)**

    This parameter specifies a set of UNIX mode bit permissions that will always be set on a directory created by Samba. This is done by bitwise 'OR'ing these bits onto the mode bits of a directory that is being created. The default for this parameter is (in octal) 0000 which will not add any extra permission bits to a created directory. This operation is done after the mode mask in the parameter directory mask is applied.

    The example below would force all created directories to have read and execute permissions set for 'group' and 'other' as well as the read/write/execute bits set for the 'user'.

    Default: force directory mode = 000

    Example: force directory mode = 0755 

heres a link to the man page for easier reading than in the man of linux

[http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

---

### Post by Kickboy on 2007-03-16
Thanks, dannyboy79. That's exactly what I needed. Everything is working perfectly now.

Curious why that didn't show up in any of my google searches. I searched for a while trying to find a solution.

Oh well. Thanks again! :)

---

### Post by dannyboy79 on 2007-03-16
glad I could help. chalk up another happy customer!

---

