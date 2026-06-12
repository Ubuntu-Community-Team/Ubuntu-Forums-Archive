---
title: "Home Folder Permissions Workaround?"
date: 2007-09-01
forum: General Help
---

### Post by mikaelsnavy on 2007-09-01
Hello,
I have seen a lot of the  .dmrc and home folder permission threads, but I could not find what I was looking for. I am attempting to setup a linux lab at a local school and I am running in to a problem. I am trying to either have the user's home folder be pulled from the network or use pam_mount to mount the network drive. In the network, I mount with CIFS for the file system. Not only the user has access to their home folder, but all the domain admins can access the user's home folders. Every time I try to login, I get .dmrc errors. I was wondering if there is any way to bypass this error and just login anyways?
Thanks,
Mikael

---

### Post by mikaelsnavy on 2007-09-01
+bump+, I have to go to work in a couple hours hopefully with a fix!

---

### Post by merlinus on 2007-09-01
The error messages should not prevent you from logging in.

Ubuntu wants /home/user to be write-read for user and read-only for others.

-merlin

---

### Post by mikaelsnavy on 2007-09-01
They do prevent me from logging in. I think the problem is that the usershares is on a ntfs drive.

---

### Post by Matakoo on 2007-09-01
> **mikaelsnavy said:**
> They do prevent me from logging in. I think the problem is that the usershares is on a ntfs drive.

I would not be surprised. I assume the ntfs-drive is attached to a windows-server? As you undoubtedly know, the security context is different in the windows world. Standard unix-like file permission flags do not apply. You can try this:

1. Change the file permissions on the server. Either on just the offending file or the entire home-directory. A quick way of checking if it is a file permission problem is to, on the windows machine, remove all existing permissions and replace them with "Everyone full control" (change owner too if necessary). Properties. Security tab. Advanced button. Remove the top-tick ("Inherit from parent..."). Tick the second option ("Replace permission...). Remove all entires in the top-box (except the SYSTEM account, and the backup account if you have one). Make sure the everyone user has full permission. Click the apply button. NOTE: This is a temporary measure only and only meant as a way to make sure if it is a file permission problem or not. 

2. You may also want to check the sharing tab. The user in question need to have access to his/her files across the network. Default is that the user has change and read rights, and should be sufficient.

Try to login again. If it works now, it was a permission problem.

If it still doesn't work, see if there's a correct mapping between linux user and windows user. That's a very common pitfall in getting samba to work correctly. This depends a bit on how you've set up samba (for example, if samba gets the login credentials from a windows domain controller or not).

If the above is not an option, look into how you mount the shared drive. 
dmask=0777, and fmask=0777 is one way of making sure the user has full control from a linux machine. A mask of 0644 should do though.

And it is normal for domain admins to have full control of the folder. Or rather, I should say it's the default. It's easily changed if you have administrative privileges on the server though. What I outlined in step 1 above would have removed their access (the Administrators group contain the domain administrators), although they can easily change that back if they deem it necessary for whatever reason.

Hope this is of some help, or points you in the right direction at least!

---

### Post by Matakoo on 2007-09-01
> **mikaelsnavy said:**
> They do prevent me from logging in. I think the problem is that the usershares is on a ntfs drive.

Oh, and I forgot to mention...windows file security can be complex.

Let's say your user is a member of two groups. X and Y for example.
The user has full access.
Group X has change rights.
Group Y has read-access.

The effective permission will, in this case, be read-access only. The most-restrictive case takes precedence. Let's just hope there are no nested groups, or it can quickly become a nightmare in finding out why a user do not have access to a file or directory he or she ought to have access to. In an organization where users have the right to change security flags (of files they have the appropiate rights to in the first place naturally), it is not uncommon for users to accidentally lock themselves out from accessing their own files.

---

### Post by mikaelsnavy on 2007-09-01
Thank you so much for the reply (probably the most thorough I have ever got)! Aftrer what I tried out what you told me to do, I think that my problem is a combonation. I changed the permissions just like you said on the windows box and that changed the error to:
```

Your home directory is listed as:
"/home/D9LTSP/thinclient"
but it does not appear to exist. Do you want to login with the / (root) directory as your home directory?"

```
If I hit no, it brings  up the login screen again. If I hit yes, I get the same .dmrc error. 

I think what the problem is not with the permissions that I mount with but how I mount (I tried to change the mounting permissions, same thing). I figured out how to use pam_mount to auto mount network shares at login but the share I need to mount is at "//2k3/Home/thinclient" which will not mount (because it is not a share?). I have thought of trying to mount "//2k3/home" to "/network" and then trying to use pam_mount to mount the user folder inside the network folder or doing a symbolic link of the users home folder in the network folder. Any ideas on any of this?
Thanks,
Mikael

---

### Post by Matakoo on 2007-09-01
> **mikaelsnavy said:**
> Thank you so much for the reply (probably the most thorough I have ever got)! Aftrer what I tried out what you told me to do, I think that my problem is a combonation. I changed the permissions just like you said on the windows box and that changed the error to:
```

Your home directory is listed as:
"/home/D9LTSP/thinclient"
but it does not appear to exist. Do you want to login with the / (root) directory as your home directory?"

```If I hit no, it brings  up the login screen again. If I hit yes, I get the same .dmrc error. 

I think what the problem is not with the permissions that I mount with but how I mount (I tried to change the mounting permissions, same thing). I figured out how to use pam_mount to auto mount network shares at login but the share I need to mount is at "//2k3/Home/thinclient" which will not mount (because it is not a share?). I have thought of trying to mount "//2k3/home" to "/network" and then trying to use pam_mount to mount the user folder inside the network folder or doing a symbolic link of the users home folder in the network folder. Any ideas on any of this?
Thanks,
Mikael

Several actually.

1. Check the slashes. SMB usually wants backslashes. That is, your example should be \\2k3\Home\thinclient, not //2k3/Home/thinclient. It isn't necessarily a problem. My version of samba accepts both, but I have run into that problem in the past.

2. The thinclient directory is not shared, or not using that name. Check if it is shared using that name (especially if there is a $ at the end of the sharename, either on the thinclient directory or the home directory). Rightclick on the direcory, click on properties, and the sharing tab to make sure. It is sufficient to have, to use your example, \\2k3\home shared. Then you can mount it as \\2k3\home\thinclient  as the path.

3. There is a name resolution problem. Replace the 2k3 with the IP-adress to check if that's the problem.

4. Capitalization. For Linux, a directory named Home is different to one named home. Windows do not make that distinction. For windows, it is the same directory. For Linux, it is not. You wrote Home as both Home and home, which is why I thought it might be worthwhile to bring it up.

Another thing to consider:

According to your latest post,

"/home/D9LTSP/thinclient"

is the home directory.

That is, before your user tries to login login /home must be mounted. It is also the only directory that need to be shared on the windows server.

I would suggest making sure /home is mounted like this:
(if not installed, use sudo apt-get install smbfs)

```
mount -t smbfs //2k3/home /home -o uid=0,gid=0,defaults,username=root,password=password,dmask=0777,fmask=0777

```Now, that is re-mounting /home explicitly. You probably want to change that so it is refered to in /etc/fstab instead.

That should mount /home as root while keeping the home-directory on the 2k3 server before the login prompt shows up. 

Now all you should need to make sure of is that there is a user named D9LTSP on both systems (or on the domain controller), and:

1. There is a directory called D9LTSP under home on the windows server
2. There is a directory called thinclient under that D9LTSP directory. I.e. d:\home\D9LTSP\thinclient should exist if the shared directory home is located in the root of the d: drive.
3. The user in question has full access permissions to the D9LTSP directory as well as its sub-directories.

---

### Post by mikaelsnavy on 2007-09-01
Thanks again for a great response! I have this machine joined to a 2k3 domain and all the users on the domain have their home folders at /home/D9LTSP (D9LTSP is the short name for the domain).  Do you think that I should just pile all the accounts into /home? I left work just after you posted the reply, so I will try it again next time I am there (hopefully tomorrow or monday) and post the results. 
Thanks for all the help,
Mikael

---

### Post by Matakoo on 2007-09-02
> **mikaelsnavy said:**
> Thanks again for a great response! I have this machine joined to a 2k3 domain and all the users on the domain have their home folders at /home/D9LTSP (D9LTSP is the short name for the domain).  Do you think that I should just pile all the accounts into /home? I left work just after you posted the reply, so I will try it again next time I am there (hopefully tomorrow or monday) and post the results. 
Thanks for all the help,
Mikael

I would, or doing so for a test user to begin with at least. Linux does expect to find its users home-directory in /home.

Considering what you want to accomplish, I would do this:

1. Have /home shared, as you have. Have the user-folders straight in that folder (no need to have the user specific folders shared).
2. Make sure Linux and Windows agree on usernames and passwords. Make sure the user has the appropriate rights on his/her homefolder.
3. Install smbfs on the Linux-clients
4. Make sure that the home-directory is, on the windows side, configured to point to /home/username, either in AD or the old-fashinoned Usermanager depending on which is in use in your network.
5. Change /etc/fstab so the /home mountpoint is mounted across the network to your 2k3-server.

When step 5 has been accomplished, as far as Linux is concerned the user has a local homefolder. It just happens to be redirected to the windows server.

---

