---
title: "Local network sharing config issue"
date: 2021-02-08
forum: General Help
---

### Post by Lee_Nowell on 2021-02-08
Hi All,

I have a few directories on a Ubuntu machine that I would like to share with both Windows and Ubuntu PCs.  I am building this for a friend and adding new shares needs to be simple.  I have managed to share the directories by using the "Local network share" option in "files" with both "allow others to create and delete files" and "guest access" enabled. I am able to see it in Windows and create files but it seems that files created from my test windows machine defaults to a  file permissions of 744 and owned by nobody:nobody. 

Anyone know how to configure this to default to r/w everyone instead?  If it is from a Windows machine then I guess x is not particularly relevant but for the Ubuntu machines then the file permissions would need to be determined by the client end user.

I thought this would be in /etc/samba/smb.conf but everything I found only suggests I have to do this individually for each shared directory.  This gives me 2 issues
1. The shared folders are not in the smb.conf file so couldn't do it there
2. Editing smb.conf isn't user friendly for the person I am building this for so was hoping there is a global config for setting the file permissions for new files?

If these shares are samba shares, how come they don't appear in smb.conf?  Where is the config stored?

Thanks in advance for your help

Lee.

---

### Post by Morbius1 on 2021-02-08
Local Network Share creates Samba Usershares. They are not defined in smb.conf. They are defined in /var/lib/samba/usershares. You can see how all of these shares are defined with this command:
```
net usershare info --long
```
They are generally not edited like you would in Samba Classic Shares - the ones in smb.conf.

One way around the nobody:nobody issue is to edit /etc/samba/smb.conf ( Usershares are still controlled on a macro level in smb.conf ) and right below the **workgroup = WORKGROUP** line add this one:
```
force user = XXXXX
```
Then restart smbd.

Where XXXXX is the Linux user name on the server. When the guest user accesses the share his identity - at least for the samba shares - will be converted from nobody to XXXXX.

---

### Post by Lee_Nowell on 2021-02-09
Thanks very much @Morbius1.  Is that the only way around the file permission aspect of my issue i.e. force all to come in as a certain user so that all files are owned by that user (say sambauser) and therefore 744 is makes them r/w for all samba users?  I think this would work for my situation except that the user logged on to the server would not be able to edit the files?

---

### Post by Morbius1 on 2021-02-10
> I think this would work for my situation except that the user logged on to the server would not be able to edit the files?                 

Let's say I log into my Ubuntu server - locally - as user = morbius. I create a usershare of my Public folder. I edit smb.conf and set the following directive:
```
 force user = morbius
```

When the Windows, Mac, other Linux guest users connects to my share they will become morbius. Any new file he adds will save with owner = morbius. The local logged in user and all of the networked users will be as morbius.

They are not connecting as mobius. They are connecting as a guest. They are being converted internally to morbius. Even if you set up a share that requires credentials to access and say ... user=agnes connects to the share. Agness will become morbius internally to samba.

There are far more complex ways to achieve the same relative result but it violates your original use case:
> I am building this for a friend and adding new shares needs to be simple.
With the force user in place in the [global] section of smb,conf all new samba shared created from the file manager will operate in the same way without adjusting smb.conf or adjusting Linux permissions on the folder being shared.

---

### Post by Lee_Nowell on 2021-02-10
Thanks very much for your reply.  Sorry I should have said, I have multiple users on the server so was hoping to get the files r/w for all of them.

---

### Post by Morbius1 on 2021-02-10
Okey Doke,

Let's say I have a folder at /mnt/Shared

[1] Change the group of the folder to say ... plugdev ( group already exists ):
```
sudo chown :plugdev /mnt/Shared
```

[2] Set the group inheritance for all files and folders:
```
sudo chmod 2775 /mnt/Shared
```

[3] Create a Classic samba share definition in smb.conf for that folder - not a usershare:
```
[Shared]
path = /mnt/Shared
browseable = yes
guest ok = yes
force group = plugdev
writeable = yes
create mask = 0664
force directory mode = 2775
```

[4] Restart smbd

[5] All local users will need to be members of the plugdev group

[COLOR=#ff0000]**EDIT**[/COLOR]: I should have stated that the default umask for your system needs to be 0002 for this to work.

Your only alternative to this is to place all shared folders on an NTFS partition so that the permissions can be predefined and immutable or use something like bindfs to make a Linux filesystem act like an NTFS partition in that regard.

---

### Post by Lee_Nowell on 2021-02-10
Ah... I don't suppose "create mask" and "force directory mode" can be used as global for all shares - e.g. if I put them immediately under the workgroup=WORKGROUP line?  If so, what would they need to be to make them r/w for all users?  The trouble with the above is that they would need to add a section like your "Shared" example themselves if they want to share a different directory?

thanks  

Lee.

---

### Post by Morbius1 on 2021-02-11
That depends entirely on the full extent of your use case.

The process described in panel #6 will make it so every user on the network and every local user on the server has write and edit access on every new file added to the shared folder.

You can set create mask / force directory mode to 0666 / 0777 globally I suppose and every file added to the share across the network will be able to be edited by all users everywhere. However if userA adds a file locally to the shared folder it will save with owner = userA:userA and permissions of 664. UserB on the server itself will have read access to the file but cannot edit that file.

---

### Post by Lee_Nowell on 2021-02-13
Thanks Morbius1.  I have now implemented your suggestion in box #6 but put the group and perm/ mask in the global section instead hoping that then if they add another share in files it will work ok.  You mentioned that the default umask needs to be 0002.  Where do I set this?  The only issue I have now is if someone locally on the server creates a file it defaults to the users group rather than my new samba group (perms 664).  Is this because I haven't set the default umask?

Thanks again you have been **really** helpful

---

### Post by Morbius1 on 2021-02-13
>   I have now implemented your suggestion in box #6 but put the group and  perm/ mask in the global section instead hoping that then if they add  another share in files it will work ok
Nope. For every usershare you create in Files you will also need to do this:
```
sudo chown :plugdev /folder-being-shared
sudo chmod 2775 /folder-being-shared


```
> The only issue I have now is if someone locally on the server creates a  file it defaults to the users group rather than my new samba group  (perms 664).  Is this because I haven't set the default umask?
Nope. It's what I said:
> However if userA adds a file locally to the shared folder it will save  with owner = userA:userA and permissions of 664. UserB on the server  itself will have read access to the file but cannot edit that file.         
Your umask is already set correctly or else the saved file would not be 664. That is why you need to do the chown / chmod on every folder shared. Then the saved file will still save as 664 but the group would be - in my example - plugdev. Just remember that all users will have to be added to that group.

---

### Post by Morbius1 on 2021-02-13
Are all these local server users creating shares from their individual home folders? 

Is there any way you can confine them to create a subfolder then share that subfolder within one centralized parent folder?

---

### Post by Lee_Nowell on 2021-02-13
Great thanks for all your help.  I have worked around it but internally  mounting the shares on the server via samba and then linking the home  directories to that point instead.  So as long as they don't access the  disk mount directly we should be ok?

---

### Post by Morbius1 on 2021-02-13
Not sure I understand that but ...........

I was going to suggest something a bit out of the box.

---

### Post by Lee_Nowell on 2021-02-14
So I have the local disk mounted as /media/data.  I have then created samba shares for each shared directory in /media/shares and then symbolic links from each users home drive to the /media/shares directories.

e.g.   /home/lee/Documents --- (sym link) ---- > /media/shares/Documents ---- (samba mount) ----> /media/data/Documents.

The idea being that as long as they don't put anything directly in /media/data/Documents everything locally on the server will also be stored via samba and therefore should not have any perm issues.

I have just discovered an issue though.  When I reboot the server, it doesn't auto mount the samba shares and I have to run mount -a to fix it.  Any ideas?

Also... if you have an "out of the box" alternative, happy to try that instead.

Thanks
Lee.

---

### Post by Morbius1 on 2021-02-14
I'm not sure I understood that either ....... So you are creating a cifs mount on the client of the same server that has the shares? Um ... I guess that would work. It's may be more out of the box than mine.

As far as not automounting at boot .... yep cifs will do that ... fstab is being executed before the network stack is fully operational so it fails. One way around this is to use x-systemd.automount but you will have to change the mount point of the cifs mount from under /media to somewhere else.

If you post one of your cifs mount expressions I may be able to assist.

My "out of the box" may not fit your use case but here it is:

[COLOR=#ff0000][I]**NOTE**: BINDFS allows you to mount an object someplace else with a "view" defining permissions that are different from the original and are immutable. Sorta kinda the way Linux mounts an NTFS partition with a "view" showing Linux ownership and permissions when in fact in has none.
[/I][/COLOR]
[1] Create a "hidden" folder at say /.MasterShare
```
sudo mkdir /.MasterShare
```
[2] Create a non-hidden folder at /MasterShare
```
sudo mkdir /MasterShare
```
[I][COLOR=#ff0000]The permissions of those folders don't matter. Bindfs will change them in its "view"[/COLOR]
[/I]
[3] Install bindfs:
```
sudo apt install bindfs
```
[4] Edit /etc/fstab and have /.MasterShare mount to /MasterShare using bindfs and define the needed permissions:
```
/.MasterShare /MasterShare fuse.bindfs perms=0666:+X,x-gvfs-hide,nonempty    0    0
```
[5] Make systemd happy:
```
sudo systemctl daemon-reload
```
[6] Then issue the following to do the mounting:
```
sudo mount -a
```
[7] The only change you need to make to smb.conf from the default setup is to add just one line under workgroup = workgroup line to eliminate having samba set the execute bit on saved files:
```
map archive = no
```
[8] Then restart smbd
```
sudo service smbd restart
```

So the user would then create a subfolder under /MasterShare and use Files to share that subfolder.

Any file added locally or across the network to that subfolder / share will save with all manner of user and group but every file will be 666 and every folder will be 777.

---

### Post by Lee_Nowell on 2021-02-14
Thanks Morbius1 much appreciated.  Yes you are correct, I am creating a cifs mount on the same server that has the shares.  The cifs line in fstab is

> 
//server/Documents  /media/share/Documents  cifs  guest,uid=user,gid=group,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0


To be honest, I am not familiar with bindfs so if I could get this working I would prefer it as at least I understand it :)

---

### Post by Morbius1 on 2021-02-14
>                                                          //server/Documents  /media/share/Documents  cifs   guest,uid=user,gid=group,iocharset=utf8,file_mode=   0777,dir_mode=0777,noperm 0 0                      

     
 

Regrettably you will have to change that mount point to be something like /mnt/share/Documents. automounters and things under /media and $HOME don't play well together.

Then you need to add two more options to the statement: noauto,x-systemd.automount
```
//server/Documents  /mnt/share/Documents  cifs   guest,uid=user,gid=group,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm,noauto,x-systemd.automount 0 0
```
Then you have to do the systemd 2-step:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```
This works by mounting on request. It will not automatically mount at boot. But anything will initiate the mount: any user by accessing the mount point in the file manager, through the terminal, by any application ... It's pretty seamless.

---

### Post by Lee_Nowell on 2021-02-14
you star!!! Thanks it works a treat.   On the other PC I mount the remote directories in /media and then each user I have symbolic links from their home directories to each of the shared directories.  Trouble is that if the mounts were ok and the server goes down, an 'ls' in their home directory hangs.  Would adding the extra options to mount on demand help this too?

---

### Post by Morbius1 on 2021-02-14
The "noauto,x-systemd.automount" will fix the fstab is executed before the network is up problem but it doesn't fix your new issue. Once it is mounted it stays mounted. If your server goes away it can't repair itself.

There is another systemd fstab option which some folks use for your new issue: 
```
x-systemd.idle-timeout=30
```
When you are done accessing the server systemd starts a clock and if you haven't used the share in 30 seconds ( you can set this to whatever makes sense ) it auto-unmounts. Setting that time interval takes some experimentation. You are making a bet that the server will not go down when you are actively accessing it.


Don't forget the systemd commands:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```

---

### Post by Lee_Nowell on 2021-02-14
great thanks.  Is it just 'ls' that will fail or will any file access hang?  I am building this system for someone else but I don't recall this hanging being an issue on my system (nfs rather than cifs) but there again the server is always on so maybe never really got into this situation to notice :)

---

