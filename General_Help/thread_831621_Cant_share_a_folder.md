---
title: "Cant share a folder"
date: 2008-06-17
forum: General Help
---

### Post by ians1 on 2008-06-17
I want to share a previously created folder and make it read/write via a Windows network.  I have installed Samba and the ubuntu box is visible via the network browser on the XP machine, it prompts for username/password which is fine as it accepts the login I use for ubuntu.

Now, when I click on the "Properties" for the newly created folder and select the "Share" tab and then tick the box "Share this folder" and also "Allow other people to write in this folder"  then click "Create share" the next window is saying:-

"Nautilus needs to add some permissions"

and when I click the "Add the permissions automatically" I get the following error displayed in the first (folder sharing) dialogue above:-

```
'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
```

Trouble is being an absolute beginner I dont know how to give myself permissions!

Anybody point me in the right direction?

ian:(

---

### Post by iaculallad on 2008-06-17
After installing you Samba Server, try to restart your system and try to share folders.

---

### Post by jetsam on 2008-06-19
If you're still having trouble and get the same error message even after a re-boot, double check that your user is in the sambashare group.  You can list all the groups you're in by typing 
```
id
```
from the command line.
If you aren't part of the sambashare group, you can put yourself in it by going to 
**System-->Administration-->Users and Groups**
Then hit the **unlock** button at the bottom, and enter your password.  Select your username and hit **properties**
Select the **User Privileges** tab, and check "Share Files With the Local Network," then hit OK.
You'll need to reboot or log off and back in again.  You should then be in the sambashare group, and hopefully can proceed to share away...

---

### Post by bodhi.zazen on 2008-06-19
> **iaculallad said:**
> After installing you Samba Server, try to restart your system and try to share folders.

You do not need to reboot (rebooting is soooo windows)

All that need be done is to log off and back on (tu update permissions).

Also, do not share your home directory, rather make a shared directory in $HOME

---

### Post by ians1 on 2008-06-20
I put myself in Users and I was already in Sambashare.

Now I can create shares.

Problem now is nobody can access them from Windows machines.

Get the message
> **Windows cannot access \\machine\share name**
Check the spelling of the name. Otherwise there might be a problem with your network. To try to identify and resolve network problems, click Diagnose.


Is this due to permissions? I clicked the "Guest access" box so I cant see why there is no access from Windows.

ian

---

### Post by ians1 on 2008-06-20
When I try to connect to the PDF printer on the ubuntu box from Windows it says "Access denied unable to connect" but I can open the Printers system folder.

Seems odd to me.

ian

---

### Post by jetsam on 2008-06-20
> Is this due to permissions?

Possibly, but it's a different permission issue than the one at the beginning of the thread.  

Can you post the results of 
```
ls -l [COLOR="Blue"]/path/to/share[/COLOR]
```
run in a terminal on the Ubuntu machine?  Replace [COLOR="Blue"]/path/to/share[/COLOR] with the path to your shared directory.

It looks like you have another thread mentioning an external drive.  Is the share on an external drive?  If so, how is it formatted (ntfs, vfat, ext3?)

An external drive can cause complications; you might want to see if you can share a simple test folder right on your desktop successfully.

---

### Post by bodhi.zazen on 2008-06-20
> **ians1 said:**
> I put myself in Users and I was already in Sambashare.

Now I can create shares.

Problem now is nobody can access them from Windows machines.

Get the message


Is this due to permissions? I clicked the "Guest access" box so I cant see why there is no access from Windows.

ian

Try connection by ip address rather the host name.

---

### Post by ians1 on 2008-06-21
> **jetsam said:**
> Possibly, but it's a different permission issue than the one at the beginning of the thread.  

Can you post the results of 
```
ls -l [COLOR="Blue"]/path/to/share[/COLOR]
```
run in a terminal on the Ubuntu machine?  Replace [COLOR="Blue"]/path/to/share[/COLOR] with the path to your shared directory.

It looks like you have another thread mentioning an external drive.  Is the share on an external drive?  If so, how is it formatted (ntfs, vfat, ext3?)

An external drive can cause complications; you might want to see if you can share a simple test folder right on your desktop successfully.

```
ians@ians-unix:~$ ls -1 /media/disk/D_arc
Docs

```

Its an IDE drive in the same box, there are 2 IDE drives both NTFS I think.

Not sure how I would access it via IP address, I using Windows Vista std network browser (explorer).

ian

---

### Post by ians1 on 2008-06-21
Just a thought, does Samba have its own set of permissions seperate from the unix account names?  It would be a bit like Windows file sharing were there are file/folder permissions as distinct from Share permissions which may or may not be the same as set.  Does Samba respond to std Windows CHAP type diallogues for user/password prompts?  If so I could make the user/pass on the Windows machine exactly the same then it must accept them, maybe?

ian

---

### Post by ians1 on 2008-06-21
> you might want to see if you can share a simple test folder right on your desktop successfully.

Just tried sharing /home and all I get is Access Denied when I look at the details of why Windows cant read the directory.

ian

---

### Post by ians1 on 2008-06-21
Begining to think it may be easier to setup FTP, it would achieve the same ends for my purposes.

ian

---

### Post by jetsam on 2008-06-21
> Just tried sharing /home and...
...Don't try to share /home or /home/[COLOR="Blue"]your_username[/COLOR] because of this:  [http://ubuntuforums.org/showpost.php?p=4831320&postcount=7]("http://ubuntuforums.org/showpost.php?p=4831320&postcount=7")

I'm pretty sure I'm starting to understand the trouble you're having.  The NTFS partition you are trying to share is being mounted in such a way that its Unix permissions are too restrictive for sharing, and it isn't possible for you to change permissions.  This is fixable, but before you get into it, it would be nice to know that simple sharing works on your system and can be accessed by the Windows machines.

So...
Right click on your desktop and create a folder.  Name it **testshare**.  Place a copy of some file in it, or create a new "hello world" document in it. Right click on the folder itself, and click properties.  Click the permissions tab and give your own group and (more importantly) others "Create and delete files" permissions next to "Folder Access," and "Read and write" permissions next to "File access."  Click "apply permissions to included files."  The "file access" permissions in that dialog will turn to a line after you do this.  That's OK. 

Then... click the sharing tab in the folder properties and check all that's checkable--  "Share this folder", "Allow other people to write to this folder," and "Guest access."  Hit the "Create Share" button and close the dialog box.  

You should then hopefully have a share that's accessible from the Windows machines.  If you don't and are getting the same error message, the problem may be more subtle, and you're probably right that you're best off looking at some other file sharing method-- either a winscp to ssh combination, or an ftp server (though an ftp server would require some configuration.)

---

### Post by ians1 on 2008-06-21
> **jetsam said:**
> ...Don't try to share /home or /home/[COLOR="Blue"]your_username[/COLOR] because of this:  [http://ubuntuforums.org/showpost.php?p=4831320&postcount=7]("http://ubuntuforums.org/showpost.php?p=4831320&postcount=7")

I'm pretty sure I'm starting to understand the trouble you're having.  The NTFS partition you are trying to share is being mounted in such a way that its Unix permissions are too restrictive for sharing, and it isn't possible for you to change permissions.  This is fixable, but before you get into it, it would be nice to know that simple sharing works on your system and can be accessed by the Windows machines.

So...
Right click on your desktop and create a folder.  Name it **testshare**.  Place a copy of some file in it, or create a new "hello world" document in it. Right click on the folder itself, and click properties.  Click the permissions tab and give your own group and (more importantly) others "Create and delete files" permissions next to "Folder Access," and "Read and write" permissions next to "File access."  Click "apply permissions to included files."  The "file access" permissions in that dialog will turn to a line after you do this.  That's OK. 

Then... click the sharing tab in the folder properties and check all that's checkable--  "Share this folder", "Allow other people to write to this folder," and "Guest access."  Hit the "Create Share" button and close the dialog box.  

You should then hopefully have a share that's accessible from the Windows machines.  If you don't and are getting the same error message, the problem may be more subtle, and you're probably right that you're best off looking at some other file sharing method-- either a winscp to ssh combination, or an ftp server (though an ftp server would require some configuration.)

I tried to share the folder and file i created, all was OK until the Share tab, Guest Access is greyed out.

I created the share anyway.

I can see the machine name in Windows but I can't open this to see anything in it, it just tells me Access Denied, not even a prompt for a user/password etc, just stonewalled.

I did however look what FTP server s/w there was an proftp seemed OK so I installed that, and it works straight out the box!  I can connect to port 21 on the ubuntu machine with Filezilla and read/write most of the folders there.

I would like to know why the Samba share thing does not work really as its better to have it browsable in windows explorer rather than saving locally and then FTPing.

Its to share Word/Excel pdf mp3 and jpg files really so it would be handy to be able to map a drive letter to the folder in the Windows machines so that save/open works easier from various apps.

ian

---

### Post by jerome1232 on 2008-06-21
I think you missed a step, you need to generate a user/pw for samba.
From the built in help system for Ubuntu:

6.3.1.&#8195;Accessing shared folders via Windows

If you would like to access a shared folder hosted on an Ubuntu computer by using computers running Windows, you may have to perform some additional steps:

   1. Press Applications &#9656; Accessories &#9656; Terminal to open a Terminal

      					
   2. Type sudo smbpasswd -a username, replacing &#8220;username&#8221; with your own username. 
Press Return to run the command.
You can find out what your username is by typing whoami into the Terminal and then pressing Return

      						

      					
   3. Enter your password when prompted with &#8220;[sudo] password for username:&#8221; and press Return again.

      					
   4. When prompted with &#8220;New SMB password:&#8221;, enter the password that you would like to use to access the shared folder and then press Return. You can leave the password blank if you like, which will allow anyone to access the shared folder.

      					
   5. When prompted with &#8220;Retype new SMB password:&#8221;, enter the password that you just entered and then press Return

      					
   6. You should now be able to connect to the shared folders on the Ubuntu computer

might want to check out the help feature built in to ubuntu has a decent basic how to for samba in it.

---

### Post by ians1 on 2008-06-21
Done that, blank password.  Entered OK.

Windows still saying Access Denied, no prompt for user/pass at all.

I can see the computer but it just keeps saying "Windows Cannot access \\IANS-UNIX   (thats the right name) and when you click Details it says an error code then Access Denied.

AM thinking remove and reinstall Samba.

ian

---

### Post by ians1 on 2008-06-21
On the way past removing and reinstalling Samba I noticed a Samba GUI component that I had not installed before.

The install went OK.

I configured the Samba user and selected myself as the unix username. It also asksfor a Windows user and password so I made these the same.

The only other thing I selected was Guest user account = nobody dont know if thats correct.

I created a folder and placed a dummy text file in it and set permissions as suggested above and then setup a share.

I am glad to say this works OK from this PC, not sure whats going to happen from another with another username.

I will let you know.

Thanks everyone for your help here.

ian

---

### Post by ians1 on 2008-06-21
This works from another PC on the same network, curiously without a password prompt although the usernames are different.

Is this because I set Guest Access user to  "nobody" ?

ian

---

### Post by jetsam on 2008-06-21
> On the way past removing and reinstalling Samba I noticed a Samba GUI component that I had not installed before...
> Is this because I set Guest Access user to "nobody" ?
I think so.  I'm pretty sure it wasn't working before because you couldn't allow guest access on the shares (the option was grayed out.)
An option in the smb.conf that might affect this is:
```
usershare allow guests = yes
```
I think that extra Samba GUI component on the second install set this value correctly, where it wasn't before.  Not 100% sure-- there's always a bit of filling in the blanks needed to understand things over the forums. 

When a Windows computer connects to Samba, it generally uses its own user name and password to try to authenticate to Samba.  Samba will allow a user that isn't in its database (as per jerome1232's suggestion) to have guest access if it's configured to do so.   I think the guest access wasn't working before but it is now after the reinstall.

Glad you got it working, though, and now you have an ftp server too...

Everything OK even sharing the folder from your NTFS partition now?

---

### Post by ians1 on 2008-06-21
Yes but I had to add a line to the smb.conf file

> usershare owner only = False


goes in the [global] section of that file

thanks again

ian:)

---

### Post by cariboo on 2008-06-21
There are two ways to do this make the share world readable or the better way create users for anyone who is going to access the share.

Jim

---

### Post by ians1 on 2008-06-22
I think thats the problem in a nutshell  for beginners like me, how do we know what users and groups to select? I put the user permissions in for me using the Samba gui but still cant access the share unless I create the shared folder myself otherwise it has root as owner and will not let me change anything.

ian

---

