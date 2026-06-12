---
title: "VirualBox won't work with Photoshop CS2 in W2K"
date: 2007-04-07
forum: General Help
---

### Post by regomodo on 2007-04-07
Well, actually it does but when combine with the Virtualbox Shared Folders i receive this error
[I]
Windows

An error occurred while reconnecting F: to \\vboxsvr\SDA2

VirtualBox Shared Folders : The local device name is already in use.

This connection has not been restored[/I]

I have no idea what that means but i am able to use the Vbox folder for other things. The box will not go away until i restart the Guest OS.

Is this a bug or is it something i did wrong?

[I]
PS 

I used the following thread to setup the folder

[http://ubuntuforums.org/showthread.php?t=400835](http://ubuntuforums.org/showthread.php?t=400835)[/I]

---

### Post by Boni2k on 2007-04-07
A word from VBox developers:
"Shared folder sucks hairy nuts"

But anyway your problem and what causes it is in the Error Message. I don't know what you are trying to do, anyway :-)
You might want to setup a nice Samba Server instead.

---

### Post by regomodo on 2007-04-07
Well, i kinda sorted it.

I installed Windows XP Pro. Adobe Bridge and Photoshop CS2 can access the shared drive. 

Unfortunatley Virtualbox doesn't seem to allow RAW .nef files. God knows why, i installed it as i normally would.

I've opened up a new can of worms

[B]EDIT : Photoshop CS2 will work in Virtualbox, it just won't work with the VBox drive setup as explained above.
Spose i'll have to figure out how to do a Samba file server. I've tried 3 times before but it never works for me[/B]

---

### Post by Boni2k on 2007-04-08
[http://www.ubuntuusers.de/paste/9018/](http://www.ubuntuusers.de/paste/9018/)
This is my config file, it works perfectly for the configured folders with Password prompt.
You must edit host allow in [global] to fit in your network.

---

### Post by regomodo on 2007-04-08
Am i supposed to copy that into smb.conf ?

Does that mean all my partitions are shared?

I've also tried sharing using the Ubuntu shared folders. It appears in the Virtualbox Guest XP but i need to enter a username password.

I tried my Ubuntu name and pass but that didn't work

---

### Post by Boni2k on 2007-04-08
Yes, it's my smb.conf
It doesn't mean that, it only shared the folder that I configured. You might want to edit the paths to fit your PC.

---

### Post by regomodo on 2007-04-08
do you mean my IP or the subnet address?

---

### Post by Boni2k on 2007-04-08
No, I mean like in [windowsxp] you may edit the path to the folder to what you want to use.
After that do "sudo /etc/init.d/samba restart" and take a look in your VirtualBox if it's working

---

### Post by regomodo on 2007-04-08
sorry. i was referring to

"You must edit host allow in [global] to fit in your network."

---

### Post by Boni2k on 2007-04-10
I think you can leave out the numbers. It will then allow to access your Samba Server from every computer in your network

---

### Post by regomodo on 2007-04-29
cheers for the help.
 
In the end all i needed was to create samba passwords for users. I knew how to setup the shared folders, just was always asked for a password

---

