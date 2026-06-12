---
title: "Having Problem with Users and Groups.."
date: 2008-06-25
forum: General Help
---

### Post by simplyasir on 2008-06-25
I have been using ubuntu for the last 2 weeks..everything was working too good..i even made the different users..But as soon as i wanted to share a folder on the network it told me i dont have the permission,Concult the admin.when i went to the user and groups i made ma root from user to admin.And from there the prob started..
Now i dont have the Sympathic manager nor i can unlock the user and group again so that i can change the root back to user..i cant install anything now..whenever i try to unlock the users and groups it says unexpected error occured
Please help me with this Problem i dont want to Reinstall Ubuntu

Waiting for your kind reply

Thanks in Advance

---

### Post by CrusaderAD on 2008-06-25
Well to manually add a shared folder to the network, just edit the /etc/samba/smb.conf file like so from the command line:

sudo gedit /etc/samba/smb.conf

and add the shared lines to the bottom of the file like this:

[yourfolder]
path = /home/youruser/folder
available = yes
browsable = yes
public = yes
writable = yes

I'll look into your other problem, I had a similar issue. Will post again in a few.

---

### Post by CrusaderAD on 2008-06-25
su from command line doesn't work? you should be able to "switch user" from command line like so:

su username

---

### Post by simplyasir on 2008-06-25
Thx alot buddy i was waiting for sumone's reply on the topic
Thanks for ur effort and time
i will be waiting for the other reply of yours too

---

### Post by CrusaderAD on 2008-06-25
Looks like we cross posted. Were you able to use su from the command line? That should log you out of root.

---

### Post by CrusaderAD on 2008-06-25
I think I got a better understanding now... you can try logging into root at the command line with:

su root

if you have no password set for root, use:

sudo passwd root

and login again. To add new users to sudo, the easiest way is to use the usermod command. Run sudo usermod -G admin username . That's all there is to it. However, if the user is already a member of other groups, you'll want to add the -a option, like so: sudo usermod -a -G admin username (in this case root for username) and you should be able to change the groups from there.

---

### Post by bodhi.zazen on 2008-06-25
Every OS has a method to obtain root or administrator access, in Windows there is the administrative user(s), in some versions of *nix there is su or direct root logins. ***The "proper" way to obtain root access is to either***:


[LIST=1]
[*]sudo -i
[*]for graphical applicationa use gksu (kdesu on Kubuntu).
[*]Boot to recovery mode.
[/LIST]


[uwiki]RootSudo[/uwiki]

***Please do not post information on enabling the root account, especially to new users, without appropriate information.***

Appropriate information, IMO, includes at least (although I am sure other mods could add to the list):


[LIST=1]
[*]How to use sudo and gksu (kdesu on Kubuntu).
[*]Permissions, understanding and changing them.
[*]The risks of enabling the root account and circumventing Linux permissions, including security risks and risks (to new uses especially) of altering system (config) files (this happens to veterans too).
[*]How to re-lock the root account.
[/LIST]


To un-set a root password :

```
sudo passwd root -l
```There are times when it is indeed necessary to set a root password, but they are rare. Setting a root password, when necessary, is supported. If you are an experienced user, feel free to set a root password (experienced users do not need to ask how to set a root password).

While you are free to run your box the way you wish, but *enabling the root account is in general felt to be bad advice to new users and is discouraged on these forums*. If you wish to provide this kind of information, feel free to user one of the several off-site methods of documentation (personal blog, etc).

[New forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by bodhi.zazen on 2008-06-25
> **simplyasir said:**
> I have been using ubuntu for the last 2 weeks..everything was working too good..i even made the different users..But as soon as i wanted to share a folder on the network it told me i dont have the permission,Concult the admin.when i went to the user and groups i made ma root from user to admin.And from there the prob started..
Now i dont have the Sympathic manager nor i can unlock the user and group again so that i can change the root back to user..i cant install anything now..whenever i try to unlock the users and groups it says unexpected error occured
Please help me with this Problem i dont want to Reinstall Ubuntu

Waiting for your kind reply

Thanks in Advance

Sounds like your user is not in the admin group.

To list your groups, in the command line :

```
id
```

to "fix" sudo : [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by simplyasir on 2008-06-25
i really appreciate everything

But im sorry guys as a newbie i aint able to do anything.Itz kind of too confusing for me

i even tried the su command nothing happend
then i went to the rebooted n went to the Dos system
i choosed the ubuntu 8.04 something as it was in the sample pic

n when i tried to make the backup 
i wrote the command it said sumthing like file doesnt exists.


im sure itz not that hard.But can i have any other way.If im not able to solve the prob i just have to reinstall it :S..which i dont want.i might get the prob in future too so that why i wanted to know how to solve it out..

---

### Post by simplyasir on 2008-06-25
> **bodhi.zazen said:**
> Sounds like your user is not in the admin group.

To list your groups, in the command line :

```
id
```

to "fix" sudo : [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)


this is what it showed to me

---

### Post by bodhi.zazen on 2008-06-25
You need to boot to recovery mode and add your user to the admin group.

The psychocats link I gave you will walk you through it :)

---

