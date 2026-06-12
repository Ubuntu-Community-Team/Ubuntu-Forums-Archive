---
title: "I get a permission denied error when copying files"
date: 2016-09-06
forum: General Help
---

### Post by naomibrown on 2016-09-06
A little background. I have been working on a laptop and a desktop and now wish to copy the files I have from the laptop to the desktop to use just the desktop. I've copied the files onto an external hard drive and also onto the desktop. I have the same problem when copying from both places. Some of the files are copying correctly and some have the following error message. 

With just one of these files, when I try to copy the file (copy and paste) and click on "Replace file" the following error is reported: 

```
Error while copying &#8220;pcc minutes 10th February 2015.doc&#8221;.

There was an error copying the file into /home/nb/Documents/church stuff/PCC/2015-02-10.

Error opening file '/home/nb/Documents/church stuff/PCC/2015-02-10/pcc minutes 10th February 2015.doc': Permission denied
```

I can see a little padlock on that file, but not on others that will copy. However, when I look at their permissions they look the same to me. 

Owner: me Access: Read and Write

Group: nb Access: Read and Write

Others: Access: Read and Write 


How do I change the permissions on the files, and should I do this, if they are actually the same?  

Thanks,
Naomi

---

### Post by speartip on 2016-09-06
You haven't by any chance copied these files from a Linux Mint distro have you? The reason I ask, is that Mint uses the Nemo file manager & the issue you report is common when copying files/folders onto a FAT32 formatted stick or drive.

---

### Post by naomibrown on 2016-09-06
My laptop is running XFCE version 4.12 so yes (I think). 

I didn't realise that would be a problem. Do I need to copy in a particular way? I just copy and pasted like normal! 

Thanks,
Naomi

---

### Post by speartip on 2016-09-06
No thats not the issue. XFCE uses the thunar file manager not Nemo.
Is it only 1 file that's giving you the issue?

---

### Post by HereInOz on 2016-09-06
Have a go setting the permissions on the file on the USB drive to something else, then set them back to the permissions as you set out above.  This has worked on some occasions, and failed on others.  Worth a try.

Also, try copying the file as root, by opening a terminal,  then sudo nautilus to open nautilus as root, then copy the file.  Once you get it to your desktop, it may behave itself.

---

### Post by vasa1 on 2016-09-06
@naomi, please use code tags so that content copied from a terminal display nicely (with a fixed font). I've added code tags in your first post in this thread.

Also, while this may not be related to your current problem, try to avoid spaces in filenames. There's no telling when spaces in filenames may bite you. See the section titled "Making safe choices" over here: [Filenames: What's In A Name?]("http://pclosmag.com/html/Issues/201607/page03.html")

---

### Post by naomibrown on 2016-09-06
No, I've got about 13 files so far out of over 10,000 when I stopped it as I realised that there was a problem after about 15 minutes.

I've tried changing the permissions by right clicking on Properties and Permissions and changing them to read-only both for the whole drive and just the folder I'm interested in. When I do this they change back to what they were originally without any further input from me. Weird. Am I doing this wrong? 

When I try nautilus as sudo I get the following warning, even after I've closed all other windows:

```
"(nautilus:6110): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (nautilus:6110): CRITICAL **: Another desktop manager in use; desktop window won't be created
Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
"

```

I've successfully copied all of the files to my desktop using nautilus but when I try to merge and replace them with the others the same files are giving permission denied errors. 

Thanks,
Naomi

---

### Post by dragonfly41 on 2016-09-06
Try ... instead of sudo ...
```
gksu nautilus
```

---

### Post by Jimysbil on 2016-09-06
You could easily copy those files from a root terminal.
But it would be more usefull if you could restore permissions on this file for your user.
At first open a terminal and type:
```
sudo su
cd '/home/nb/Documents/church stuff/PCC/2015-02-10'
ls -la
```
You should be able to see something like:
```
(d)rwxrwx--- {username}     {group}          {date and hour} {file/folder name}
```
[COLOR="#FF0000"]* Copy-paste the results here.[/COLOR]
If you are not the owner of some file(s) you can use a command in this format:
```
chown {username}:{group} {file/folder}
```
[COLOR="#FF0000"]** In my opinion the most of the files inside this folder should have the right owner (probably your username twice for username and group).So you can see the username and the group you should apply to your folder.[/COLOR]
If you want to proceed with change ownership process type:
```
chown {your username}:{group} {the name of the file(s) it gave you permission denied error}
```

---

### Post by HermanAB on 2016-09-06
Howdy,

Note that most USB devices are formatted with FAT32, which does not store the user and group information.  Therefore, when copying data using one of these it usually proceeds smoothly - the system assumes that you know what you are doing and copies the data using the permissions of the logged in user.

However, if the USB device is formatted with ext3, ext4, NTFS, HFS etc, then the user and group data is preserved and it is then that you run into these weird issues.

---

### Post by naomibrown on 2016-09-06
I think the only problems I've had with files now I'm done have had brackets in their name or are just numbers.

As soon as I change the names of the files I'm fine! :)

Thanks for all of your help guys!!!

Naomi

---

