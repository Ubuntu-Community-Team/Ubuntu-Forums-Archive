---
title: "Acessing Ubuntu from Windows"
date: 2007-11-20
forum: General Help
---

### Post by Windows_RiscOS_&amp;_Linux on 2007-11-20
Hi, I'm not sure if this question has been raised before, but I'm very new to Linux.

I have Ubuntu 7.04 configured for DHCP, and it is able to access my Windows PC over the network - No Problems there.
Windows is (after a bit of tweeking on Ubuntu) able to see the Ubuntu system, but when I try to access it, Windows throws up its usuall permissions window. If I were accessing another Windows machine on the network, I'd type in Guest, and leave the password blank. However, this does not work when accessing Ubuntu, nor does my Ubuntu login name and password.
Has anyone experienced this, and can someone offer any advice? I do have a folder shared on Ubuntu by the way.

---

### Post by wolfger on 2007-11-20
Can you be a bit more explicit what you mean by "access it"? If you are trying to read/write the hard drive directly, you quite possibly have a filesystem problem (Windows, by default, can't read EXT2/3/4, or any of the other typical Linux filesystem types). I know there are a few ext2/3 drivers out there for Windows. I used one in the past, and it worked okay.

---

### Post by Windows_RiscOS_&amp;_Linux on 2007-11-20
I can't even get that far. It's a network user and password popup for logging onto other computers over the network. For some reason, windows can't log on to the Ubuntu system. I've tried putting in my Ubuntu login and password, as well as trying Guest, but Windows rejects it as incorrect user or password.

---

### Post by wolfger on 2007-11-20
I guess I've been away from Windows too long, because I can't picture what you're talking about. Which Windows OS are you using? 2000? XP? Vista? If you're on XP, I can try to duplicate this when I get home.

---

### Post by jshurst on 2007-11-20
Do you have any folders setup for sharing?  You might want to look into Samba sharing...

You're not talking about remote access are you?  If so then I would look into an NX client ([www.nomachine.com](www.nomachine.com))

J

---

### Post by Nem1976 on 2007-11-20
I'm assuming he's talking about accessing his Nix shares from his windows box.  From my understanding even though you have shared out a folder you still need to modify your Samba  and create specific username and password for access.,   I need to do the same thing I just havn't gotten around to doing it yet.

I will do some quick looking to see if I can get it working then will post back here.

---

### Post by dfreer on 2007-11-20
Yep, basically samba has it's own user list and passwords. It is separate from the existing accounts on your computer, so you wouldn't normally use the same username/password that you login into linux with, unless of course you set the samba username/password to be exactly the same.
Anyways, If you wish to be able to have anonymous access (so that you don't have to enter a username/password), you can try following this guide:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29)
There are several other guides relating to setting up samba shares on that site, including using authentication, so you can choose the best one for what you need.

---

### Post by Nem1976 on 2007-11-20
Ok Well I got it working the way I like it.

Here is what I did.

sudo gedit /etc/samba/smb.conf

do a find and look for browseable 

it should look like this.
;   browseable = no

I removed the ; and changed it to yes

also right below that you will  find    
 ;  writable = no
do the same as above remove the ; and change to yes.

now save and close the file.

Now restart samba by typing 

sudo /etc/init.d/samba reload

Now type 

sudo smbpasswd -a your_username
it will ask you for what password you want I set mine to the same as my nix login.

And now from my WinXP box under in the login screen you get use that username and password you created.

 Now this might not be the best practice and any suggestions anyone else can give that would be great.

---

### Post by Windows_RiscOS_&amp;_Linux on 2007-11-20
Thanks, Nem1976, I'll give that a try later and let you know if it worked.

---

### Post by jonandrews on 2007-11-22
Yep, that's all very familiar to me.
I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.

---

