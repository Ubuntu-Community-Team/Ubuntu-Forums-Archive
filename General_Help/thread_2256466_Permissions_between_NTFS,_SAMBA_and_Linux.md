---
title: "Permissions between NTFS, SAMBA and Linux"
date: 2014-12-12
forum: General Help
---

### Post by aaron50 on 2014-12-12
Hello All,

I have a question, more as a way to gain a little more knowledge than anything. I am pretty new to Ubuntu, i am running Ubuntu 14.04 cli headless. I have successfully auto mounted my external hard drive in fstab, i am using ntfs-3g (not sure why, rather than another option, it just worked for me). On my external hard drive I want to have a public folder for movies etc, and a private folder for all my private materials. since I don't believe I can mount the two separately since it is on one hard drive, here is my fstab statement:
```
/dev/sdb1 /ExternalMedia ntfs-3g defaults,umask=077,uid=1000,gid=1000 0 0
```

you can see that i am making the whole drive only accessible to me(077), user 1000.

I have set up my samba config file as follows
```
[Public]        comment = Public File Server
        path = /ExternalMedia/Media
        browsable = yes
        writable = yes
        guest ok = yes
        read only = no
        create mask = 0755


[Private]
        comment = Private File Server
        path = /ExternalMedia/Private
        browsable = yes
        writable = yes
        guest ok = no
        read only = no
        create mask = 0700



```

My question is, which privileges are the deciding factors. For example if i change my fstab to 000, and keep my private in smb.conf to say guest ok = no, it still lets me connect from any computer without a password. It appears that the fstab does everything. I am asking this because when I connected in the current configuration with a macbook and pointed the mac to only the public computer, the user was still able to go up a folder and then go into the private folder. I want these two to have completely seperate identities, for obvious reasons. I know that with ntfs i cannot use chmod or anything like that, but can someone explain in laments terms which of the two (fstab or smb.conf) files actually controls my samba share.

Thanks for any help you can provide.

---

### Post by bab1 on 2014-12-13
> **aaron50 said:**
> Hello All,

I have a question, more as a way to gain a little more knowledge than anything. I am pretty new to Ubuntu, i am running Ubuntu 14.04 cli headless. I have successfully auto mounted my external hard drive in fstab, i am using ntfs-3g (not sure why, rather than another option, it just worked for me). On my external hard drive I want to have a public folder for movies etc, and a private folder for all my private materials. since I don't believe I can mount the two separately since it is on one hard drive, here is my fstab statement:
```
/dev/sdb1 /ExternalMedia ntfs-3g defaults,umask=077,uid=1000,gid=1000 0 0
```

you can see that i am making the whole drive only accessible to me(077), user 1000.

I have set up my samba config file as follows
```
[Public]        comment = Public File Server
        path = /ExternalMedia/Media
        browsable = yes
        writable = yes
        guest ok = yes
        read only = no
        create mask = 0755


[Private]
        comment = Private File Server
        path = /ExternalMedia/Private
        browsable = yes
        writable = yes
        guest ok = no
        read only = no
        create mask = 0700



```

My question is, which privileges are the deciding factors. For example if i change my fstab to 000, and keep my private in smb.conf to say guest ok = no, it still lets me connect from any computer without a password. It appears that the fstab does everything. I am asking this because when I connected in the current configuration with a macbook and pointed the mac to only the public computer, the user was still able to go up a folder and then go into the private folder. I want these two to have completely seperate identities, for obvious reasons. I know that with ntfs i cannot use chmod or anything like that, but can someone explain in laments terms which of the two (fstab or smb.conf) files actually controls my samba share.

Thanks for any help you can provide.
There are multiple aspects to answer your question.  Access to the Samba resource (*the share*) is via the Samba configuration.  Samba permissions for objects **created subsequently ** (files and directories) are also set in the share configuration via the smb.conf file.  Access to the existing Linux file system objects are controlled by the Linux OS file system type drivers.  Since you can't alter the permissions scheme after mounting with NTFS you might need to rethink having only one partition on the hard drive or maybe reformatting the partition to ext4 so you can control user access to the directory.  

Bottom line.  Samba controls authentication (who are you?) and Linux controls access to the shared directory (you have permission).  Samba can set the ownership and permissions on files and directories **created subsequently** if Linux permissions on the parent directory allow it.

---

### Post by Morbius1 on 2014-12-13
> I am asking this because when I connected in the current configuration with a macbook and pointed the mac to only the public computer, the user was still able to go up a folder and then go into the private folder.
By "in the current configuration" do you mean this:
> /dev/sdb1 /ExternalMedia ntfs-3g defaults,umask=077,uid=1000,gid=1000 0 0
Finder ( or even "Connect to Server" ) asks you how you want to connect to the server - not the share - the server. Because of how you mounted the ntfs partition the only way ( unless you have a "force user" somewhere ) you are going to access the Public share is by passing credentials to the server since the only user able to access the shared public folder at the Linux permissions level is by the user represented by "uid=1000". At that point Finder remembers that state and any private shares accessible by any credentialed user will also be accessible.

If you then set umask to 000, disconnect from the server, and then reconnect as guest only the public share should be accessible but the Private share will not.

---

### Post by aaron50 on 2014-12-13
bab,

If i gather everything your saying correctly, since i am using NTFS, linux is controlling everything for me. Samba is just opening a pipeline and checking that the users match. All of the permission levels are being run through the linux system. Thank you very much for your detailed response. Do you happen to know how difficult it is to change over to ext4, i only have this one hard drive with everything on it, so no way to really back up my files at this point, this is a test server for when i build my real one. This may be a stupid question, but is it as easy as just changing my fstab statement to ext4 instead of NTFS-3g? If that is not possible then it appears as though i may have to partition my drive, not sure how to do this, but i will do some research.

Morbius,
Thank you as well for your response. I am not sure i fully understand your work around though. when i go and set the umask to 000, wont everything be accessible through guest? If both of the directories are connected by the one fstab statement, how will one be visible and one not? I am willing to try this though, i will try this out tonight when i have some time. Thank you both again for your posts.

---

### Post by Morbius1 on 2014-12-13
> Morbius,
Thank you as well for your response. I am not sure i fully understand  your work around though. when i go and set the umask to 000, wont  everything be accessible through guest? If both of the directories are  connected by the one fstab statement, how will one be visible and one  not? I am willing to try this though, i will try this out tonight when i  have some time. Thank you both again for your posts.
Think of the Samba share as a gatekeeper. It determines what the remote user may do. 

Your Public share allows everyone to read and write to the share. That share defines a specific path to a subfolder of the mounted partition. That user doesn't have access to anything other than that shared subfolder. But Linux permissions are the ultimate authority of what any user can do. In your original case only one user can access anything in that mounted partition and that is the user 1000. So although Samba allows anyone to access the share Linux allows only user 1000.

Linux permissions should be set so that it's permissions match or are greater than the permissions allowed by samba. So If I set the ntfs partition to be umask=000 allowing everyone access but then create a Private share say like this:
> [Private]
        comment = Private File Server
        path = /ExternalMedia/Private
        browsable = yes
        writable = yes
        guest ok = no
        [COLOR=#0000cd]**valid users = morbius**[/COLOR]
        read only = no
        create mask = 0700
Only one user will be allowed to access the Private share and in this case it's morbius despite the fact that the underlying Linux permissions on that folder will allow everyone.

---

### Post by bab1 on 2014-12-13
> **aaron50 said:**
> bab,

If i gather everything your saying correctly, since i am using NTFS, linux is controlling everything for me. Samba is just opening a pipeline and checking that the users match. All of the permission levels are being run through the linux system.


This is also true of ext4 file system.  Ext4 has been the default file system for Linux and is much more flexible with ownership and permissions.  Including the ability to reset the ownership and permissions later on after mount time.> 

 Thank you very much for your detailed response. Do you happen to know how difficult it is to change over to ext4, i only have this one hard drive with everything on it, so no way to really back up my files at this point, this is a test server for when i build my real one. This may be a stupid question, but is it as easy as just changing my fstab statement to ext4 instead of NTFS-3g? If that is not possible then it appears as though i may have to partition my drive, not sure how to do this, but i will do some research.

If you want to reformat the partition or repartition the drive and reformat you will have to store the data elsewhere.  You should always have an off line backup of your data anyway.

---

### Post by aaron50 on 2014-12-13
Morbius, 
That makes more sense, i will try what you are suggesting and see how it works out for me. I will report back how it goes.

Bab,
Thank you for the information. When I set up my "true" server, i will consider changing to ext4, since that seems to be the more conventional route. I figured you would say i need a backup, I myself am scared of having it all on only one drive, and have been meaning to back it all up. Thanks again for all of the useful information.

---

### Post by Morbius1 on 2014-12-14
> **aaron50 said:**
> Morbius, 
That makes more sense, i will try what you are suggesting and see how it works out for me. I will report back how it goes.
Just to be clear all of my posts were really a response to two items in your original post and it was narrowly focused more on the OSX part:
> For example if i change my fstab to 000, and keep my private in smb.conf to say guest ok = no, it still lets me connect from any computer without a password.
This is not possible unless:
(1) The client is Windows, the Windows user name matches a Linux user name, and you have added that user to the samba password database. This is because Windows automatically sends the user name with the request to view the shares of the server. Given all these conditions the Windows user is no longer a guest.
(2) The client is OSX, and when prompted for how you want to access the server you indicate a user name that matches a Linux user and have also added that user to the samba password database. In this case the OSX client is acting just like a Windows client.
(3) The client is Linux , you force credentials in how you are mounting the shares, and that user name and password are also part of the samba password database.
> I am asking this because when I connected in the current configuration with a macbook and pointed the mac to only the public computer, the user was still able to go up a folder and then go into the private folder.
The exact way you described this in that statement is also not possible. 
*** The client can't go "up a folder" to access other folders outside the shares defined by samba - unless you have symbolic links and have modified samba allowing the client to follow them.

In my mind the only way you could have access to the Public and the Private shares from OSX without doing some adjustments to smb.conf is if you are accessing the share as I described in (2) above.

[COLOR=#0000cd]*BTW, I have reproduced your share definitions on a test Ubuntu 14.04 server along with pointing them to an NTFS partition mounted as you have done ( with umask=000 ) just to make sure that OSX-Yosemite hasn't added some magic that allows it to do something different from earlier versions. *[/COLOR]

---

### Post by aaron50 on 2014-12-14
> **Morbius1 said:**
> Just to be clear all of my posts were really a response to two items in your original post and it was narrowly focused more on the OSX part:

This is not possible unless:
(1) The client is Windows, the Windows user name matches a Linux user name, and you have added that user to the samba password database. This is because Windows automatically sends the user name with the request to view the shares of the server. At that point the Windows user is no longer a guest.
(2) The client is OSX, and when prompted for how you want to access the server you indicate a user name that matches a Linux user and have also added that user to the samba password database. In this case the OSX client is acting just like a Windows client.


(2) appears to be what is happening. on the OSX. The only user on the linux server is amotto11 which is uid=1000. I guess i explained going up a folder incorrectly. This is exactly what happened:
[LIST]
[*]Opened Finder and chose to connect to server
[*]server name smb://LaptopMediaServer/
[*]username: amotto11
[*]password: *************
[*]chose to only mount the public share
[*]At this point i am in the public share. I close finder, open it back up and the server shows as LaptopMediaServer, once i click on that it shows Private and Public folders, it did not just go into the public folder.
[/LIST]

I am going to try your workaround now and i will let you know how it goes. Do you suggest i create a "guest" username and password so that they can only access certain folders, or in my configuration only adding user=amotto11 to my smb.conf file in private should be good enough?

---

### Post by aaron50 on 2014-12-14
> **Morbius1 said:**
> 
Linux permissions should be set so that it's permissions match or are greater than the permissions allowed by samba. So If I set the ntfs partition to be umask=000 allowing everyone access but then create a Private share say like this:

[COLOR=#000000]*[Private]*[/COLOR]
[COLOR=#000000]*comment = Private File Server*[/COLOR]
[COLOR=#000000]*path = /ExternalMedia/Private*[/COLOR]
[COLOR=#000000]*browsable = yes*[/COLOR]
[COLOR=#000000]*writable = yes*[/COLOR]
[COLOR=#000000]*guest ok = no*[/COLOR]
[COLOR=#0000cd]***valid users = morbius***[/COLOR]
[COLOR=#000000]*read only = no*[/COLOR]
[COLOR=#000000]*create mask = 0700*[/COLOR]

Only one user will be allowed to access the Private share and in this case it's morbius despite the fact that the underlying Linux permissions on that folder will allow everyone.

I did that and it does not appear to be working. Here are my steps that i went through, maybe i did something wrong, correct me where i screwed up.
[LIST]
[*]new fstab statement: /dev/sdb1 /ExternalMedia ntfs-3g defaults,umask=000,uid=1000,gid=1000 0 0
[*]new smb.conf config for both public and private
[/LIST]
[Public]
        comment = Public File Server
        path = /ExternalMedia/Media
        browsable = yes
        writable = yes
        guest ok = yes
        read only = no
        create mask = 0755


[Private]
        comment = Private File Server
        path = /ExternalMedia/Private
        browsable = yes
        writable = yes
        guest ok = no
        valid users = amotto11
        read only = no
        create mask = 0700

[LIST]
[*]Restarted the server
[*]Logged into my laptop as my wife, so that the username is not amotto11.
[*]opened file explorer, mapped network drive. Entered \\LaptopMediaServer\Private
[*]Entered no password or username, did not check the reconnect at login or connect using different credentials boxes
[*]clicked finish and I was in.
[/LIST]
It appears as though it just allowed a guest, what did i do wrong. Once I get it working on this computer, i will try the mac, i am guessing both should work similar

---

### Post by Morbius1 on 2014-12-14
> **aaron50 said:**
> (2) appears to be what is happening. on the OSX. The only user on the linux server is amotto11 which is uid=1000. I guess i explained going up a folder incorrectly. This is exactly what happened:
[LIST]
[*]Opened Finder and chose to connect to server 
[*]server name smb://LaptopMediaServer/ 
[*]username: amotto11 
[*]password: ************* 
[*]chose to only mount the public share 
[*]At this point i am in the public share. I close finder, open it back up and the server shows as LaptopMediaServer, once i click on that it shows Private and Public folders, it did not just go into the public folder. 
[/LIST]

I am going to try your workaround now and i will let you know how it goes. Do you suggest i create a "guest" username and password so that they can only access certain folders, or in my configuration only adding user=amotto11 to my smb.conf file in private should be good enough?
I wish you'd stop calling it a workaround ;)

This issue with OSX is that it's an all or nothing thing. 

When you use "Connect to server" and access the public share specify " Connect as: Guest" not amotto11. Then you will only have access to the Public share. Finder will show you a lovely icon for the Private share but you won't be able to do anything with it. 

If you want to restrict access for your other users to the private share then ask them to only access as Guest, or don't add them to the samba password database, or specify only one user like yourself using "valid users = amotto11" so that even if they had a samba password they still couldn&#8217;t gain access to the private share.

---

### Post by Morbius1 on 2014-12-14
Didn't see your edit before my last post.

On the server run this command:
```
sudo smbpasswd -a amotto11
```
It will first ask you for sudo's password then it will ask you for the SMB password. For this experiment just make it temp. Literally.

Then on the Windows machine "un-map" the drive and try accessing it again. Windows remembers how it successfully mounted the share the last time it connected and you probably used amotto to do that the way you were originally set up.

[COLOR=#0000cd]**EDIT**[/COLOR]: In case that wasn't clear the presumption is that your wife doesn't know the new password for amotto11 is now "temp". She should have access to the Public share but not the Private share.

---

### Post by aaron50 on 2014-12-14
I tried what you are explaining, i changed the password to temp, rebooted the server. Then went onto this computer, logged in as my wife, instead of amotto11. I was able to access both the private and public accounts without a password. I must be doing something wrong...

---

### Post by Morbius1 on 2014-12-14
** If you currently have any of these share mapped in windows remove the map.

** Go to the server and remove yourself from the samba database:
```
sudo smbpasswd -x amotto11
```

** Then access the server from Windows again. Still get access to both shares?

If you can then go back to the server and run this command and post it's output:
```
 testparm -s
```
And just in case run this command and post it's output if there is any:
```
net usershare info --long
```

---

### Post by aaron50 on 2014-12-14
okay, were getting somewhere.

I did exactly as you said.
1.) removed amotto11 from samba database
2.) rebooted samba

I was able to log onto the public with no user or password, but the private required a user and password. tried a couple of usernames and passwords i have used in the past to make absolute certain i could not get on and i was not able to. Now how to I go about adding amotto11 back on? hah

Edit: The exact same thing happened on the mac by the way. I only was able to get to the public folder, even though i could see the private folder exists i could not get access to it as guest

---

### Post by Morbius1 on 2014-12-14
Did you do the other part? Removing the map in Windows? The map will contain instructions you want to clear before we add amotto11 back to samba.

---

### Post by aaron50 on 2014-12-14
yes i removed all mapping before i worked with samba. i can undo the mapping again when i add a user back, since i was testing with no user

here is the output to testparm -s

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Public]"
Processing section "[Private]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:                                                                                        * %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb


[Public]
        comment = Public File Server
        path = /ExternalMedia/Media
        read only = No
        create mask = 0755
        guest ok = Yes


[Private]
        comment = Private File Server
        path = /ExternalMedia/Private
        valid users = amotto11
        read only = No
        create mask = 0700

```

here is net usershare info --log

```
Invalid option --log: unknown option
Usage:  Use 'net help rpc' to get more extensive information about 'net rpc' commands.
  Use 'net help rap' to get more extensive information about 'net rap' commands.
  Use 'net help ads' to get more extensive information about 'net ads' commands.
  Use 'net help file' to get more information about 'net file' commands.
  Use 'net help share' to get more information about 'net share' commands.
  Use 'net help session' to get more information about 'net session' commands.
  Use 'net help server' to get more information about 'net server' commands.
  Use 'net help domain' to get more information about 'net domain' commands.
  Use 'net help printq' to get more information about 'net printq' commands.
  Use 'net help user' to get more information about 'net user' commands.
  Use 'net help group' to get more information about 'net group' commands.
  Use 'net help groupmap' to get more information about 'net groupmap' commands.
  Use 'net help sam' to get more information about 'net sam' commands.
  Use 'net help validate' to get more information about 'net validate' commands.
  Use 'net help groupmember' to get more information about 'net groupmember' commands.
  Use 'net help admin' to get more information about 'net admin' commands.
  Use 'net help service' to get more information about 'net service' commands.
  Use 'net help password' to get more information about 'net password' commands.
  Use 'net help changetrustpw' to get more information about 'net changetrustpw'.
  net [options] changesecretpw
    Change the ADS domain member machine account password in secrets.tdb.
    Do NOT use this function unless you know what it does.
    Requires the -f flag to work.
  net -U user[%%password] [-W domain] setauthuser
    Set the auth user, password (and optionally domain
    Will prompt for password if not given.
  net setauthuser delete
    Delete the existing auth user settings.
  net getauthuser
    Get the current winbind auth user settings.
  Use 'net help time' to get more information about 'net time' commands.
  Use 'net help lookup' to get more information about 'net lookup' commands.
  Use 'net help g_lock' to get more information about 'net g_lock' commands.
  Use 'net help join' to get more information about 'net join'.
  Use 'net help dom' to get more information about 'net dom' commands.
  Use 'net help cache' to get more information about 'net cache' commands.
  net getlocalsid
  net setlocalsid S-1-5-21-x-y-z
  net setdomainsid S-1-5-21-x-y-z
  net getdomainsid
  net maxrid
  Use 'net help idmap to get more information about 'net idmap' commands.
  Use 'net help status' to get more information about 'net status' commands.
  Use 'net help usershare to get more information about 'net usershare' commands.
  Use 'net help usersidlist' to get more information about 'net usersidlist'.
  Use 'net help conf' to get more information about 'net conf' commands.
  Use 'net help registry' to get more information about 'net registry' commands.
  Use 'net help eventlog' to get more information about 'net eventlog' commands.
  Use 'net help printing' to get more information about 'net printing' commands.
  Use 'net help serverid' to get more information about 'net serverid' commands.
  Use 'net help help' to list usage information for 'net' commands.



```

---

### Post by Morbius1 on 2014-12-14
To add amotto11 back run:
```
sudo smbpasswd -a amotto11
```

There's no need to reboot anything or restart samba.

---

### Post by aaron50 on 2014-12-14
Okay, that worked somewhat it appears.

here were my test scenarios in this order:
1.) testing this computer under username amotto11 - i was able to get into public and private without the use of a username or password, I'm okay with that since i am the owner, but would still like it to require a password, but that may force me to just use a different samba username or something
2.) testing this computer under username snr05 (my wife's account) - I was able to get into public and private without the use of a username or password. I am somewhat okay with that, I want my wife to be able to get in, but i would like to require a password when mapping. My only theory here is that somehow my two accounts are linked or something and it is allowing me to map from my wifes account via amotto11, or the computer remembers the map from user to user.
3.) testing on a seperate windows machine - worked perfectly. I was able to get into the public without a username or password, but was not able to get into private without one.
4.) testing the mac computer - worked perfectly. I was able to get into public without a username or password, but was not able to get into private without one.

Do you know why my windows computer seems to be linking the two accounts under amotto11, maybe because i mapped the drive under that account first(it is the admin account on the machine i believe), it allowed every other user to map to the drive?

---

### Post by aaron50 on 2014-12-14
One more question. I logged in to the private on the mac(without checking to remember the password), then disconnected the drive, then reconnected and this time it connected without a username and password. Is there a way to make the computer require a password each and every time a drive is disconnected, or does the computer always remember the credentials? I haven't tried this on the other windows machine, because it is not mine and i do not want to have to go through this whole process again of deleting the user, but i am guessing it will act the same way

---

### Post by Morbius1 on 2014-12-14
> 1.) testing this computer under username amotto11 - i was able to get  into public and private without the use of a username or password, I'm  okay with that since i am the owner, but would still like it to require a  password, but that may force me to just use a different samba username  or something
There is no easy answer for this and here's why:

** If your Windows user name and password matches the Linux user name and password WIndows actually sends those credentials by itself without your intervention automatically and access is granted.
** Even if you set this up with a different user name and password one successful access attempt will be remembered by Windows in perpetuity and you still won't be prompted for credentials again.
>  2.) testing this computer under username snr05 (my wife's account) - I  was able to get into public and private without the use of a username or  password. I am somewhat okay with that, I want my wife to be able to get in, but i would like to require a password when mapping.
Nope. It's still broke. Maybe you didn't remove the map on this account.

And if you also want your wife to gain access to the share then add her name to the "valid users" list in the share:
> [Private]
        comment = Private File Server
        path = /ExternalMedia/Private
        browsable = yes
        writable = yes
        guest ok = no
        [COLOR=#0000cd]**valid users = amotto11, snr05**[/COLOR]
        read only = no
        create mask = 0700

As far as the mac is concerned it will remember credentials to the server untill every share is unmounted and Finder is restarted.

[COLOR=#0000cd]**EDIT**[/COLOR]: You know, why not create another user on the server. Call him ... say ... samotto11 for server amotto11. Remove the original amotto11 from samba ( sudo smbpasswd -x amotto11 ) then add the new samotto11 to samba and start fresh. It won't fix (1) after the first login but it should fix (2) so that it act's more like (3) and (4). You'd have to fix the valid users to add this new samotto11 user.

---

### Post by aaron50 on 2014-12-14
that is a good idea, i will do that. Thank you for all of your help!

---

