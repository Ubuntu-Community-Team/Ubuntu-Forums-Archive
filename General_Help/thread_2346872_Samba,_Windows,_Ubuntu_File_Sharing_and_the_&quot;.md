---
title: "Samba, Windows, Ubuntu File Sharing and the &quot;nobody&quot; snag"
date: 2016-12-19
forum: General Help
---

### Post by mgarrett682 on 2016-12-19
I’m a new Ubuntu user having problems with file sharing between Ubuntu and Windows systems. I’ve had a home network populated entirely with Windows systems for years. I am in the process of switching all of those systems except one to Ubuntu. So far installing Ubuntu and setting up individual computers has been simple but I’m running into a snag on setting up one as a file sharing machine.

On the machine intended for the file server I wiped the hard drive that had previously run Windows 10 and did a fresh install of Ubuntu 16.04 Desktop. Everything worked well. I then installed Pi-Hole for internet ad blocking. I next wiped a 2TB hard drive (it had previously had a Windows installation), installed it in the server machine and created a partition named “Data,” intending to use that drive for file sharing across the network, and formated it as ext4. 

The next step was to move about 600gb of data to that Data drive over the network. I found a tutorial for setting up samba to share files between Windows and Linux systems. I created a directory named “Media” on the Data partition to allow sharing of files across all the computers without need to log in or enter passwords, or so I thought. I created the Media directory and set the Permissions tab (using the “Files” gui) with create/delete  permissions for owner, group, and others along with read/write permissions for owner, group, and others. On the Local Network Share tab I checked the Share this folder box,entered a share name of Media, and checked the Allow others to create and delete files in this folder box as well as the Guest access box.Then I proceeded to copy about 600gb of files, directories and subdirectories to Media over the network from a Windows machine.

After copying the data I found that I could not edit or delete any of those files from the Ubuntu machine the files were now stored on. I could from the Windows machine over the network, but not the Ubuntu box. Looking at the files and folders that came from the Windows box I find that the properties of each to show owner and group as “nobody” and“nogroup” with the  permissions being read and write for owner/nobody and read only for group/nogroup and others.

That isn’t going to work. I want to be able to edit, rename, or delete the files from any computer on the network. I obviously did something wrong and I’m perfectly willing to start over from scratch.

So, can anyone explain to me how to set up a share on a Ubuntu machine that will allow access without logins to every Windows machine and Ubuntu machine on my network AND allow me to edit, delete, rename, move,etc. from any of those computers including the Ubuntu machine the files are stored on? Is that possible? 

Any help or suggestions are greatly appreciated!

---

### Post by SeijiSensei on 2016-12-19
It depends on whether you care about identifying the owners of the shared files.  If you want susie's files to be owned by her and joey's files to be owned by him, that's possible but a bit more complicated.  If you don't care about keeping track of ownerships, then Samba has a nice feature that makes life easier.

Create a Linux user with the adduser command that will own all the files.  Let's call it the "filemgr" user.  Next go to the top of the data share and use
```

sudo chown filemgr:filemgr -R .
sudo chmod 755 -R .

```
which will make the filemgr user and group own all the files.  Now in the share definition for these files in smb.conf add the directives
```

force user = filemgr
force group = filemgr

```
Now all the file transactions will happen at the OS level under the filemgr user and group regardless of the identity of the person logged into the share.  That will mean that susie can delete joey's files and vice versa, so if you don't trust the users, this isn't a good solution.  But if that's not an issue, then the force user/group method can be a simple and effective solution.

---

### Post by HermanAB on 2016-12-20
There is also the 'sticky' bit, that can be used on the parent directory.  

If you set the directory sticky bit with "chmod 1755 directoryname" and set the directory ownership with "chmod filemgr:filemgr directoryname", then a couple of things happen:
1. Files uploaded to the directory will have the owner of the user that uploaded it and the group of the directory eg: herman:filemgr
2. Users will not be able to delete each other's files - but they will be able to read and modify each other's files, if they are all members of the filemgr group.

---

### Post by HermanAB on 2016-12-20
Dup

---

### Post by Morbius1 on 2016-12-20
This all depends on how you use and maintain the Linux box.
> **mgarrett682 said:**
>  On the Local Network Share tab I checked the Share this folder box,entered a share name of Media, and checked the Allow others to create and delete files in this folder box as well as the Guest access box.
You created a Samba Usershare. [COLOR=#0000cd]**SeijiSensei**[/COLOR]'s suggestion will work:
> Now in the share definition for these files in smb.conf add the directives
force user = filemgr
force group = filemgr
[I][COLOR=#0000cd]Not sure why we are adding a new user instead of just using  mgarrett682's user name on that box ....
[/COLOR][/I]
But you will have to place those lines in the [global] section of /etc/samba/smb.conf since there are no share definitions in smb.conf. I would put them under the "workgroup = workgroup" line towards the top of the file so it's easy to see.

As long as you do everything as the user "filemgr" locally on that machine then both the local user and the remote samba client user will have read / write access to the shared folder. This would apply to any new files added by the samba client. You will have to change ownership from nobody to filemgr on the existing files locally.

If you have a local process that is not initiated by the local user filemgr that adds to that folder then things get a bit more complicated.

---

### Post by mgarrett682 on 2016-12-20
Thanks for the responses. I'll look into the various suggestions and see if I can sort it out. Your responses have me looking up a lot of info. Being new to linux has me doing a lot of head scratching right now.

---

