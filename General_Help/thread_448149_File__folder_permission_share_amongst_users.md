---
title: "File / folder permission share amongst users"
date: 2007-05-18
forum: General Help
---

### Post by jius on 2007-05-18
I have set up a second hard drive with auto mount and full privileges across all users. took a while, but seems to be working. Users can now put folders, files create, delete, etc on that drive.

However if one user places a folder or file into that drive folder to share with other uses, any user that tries access their folder/file finds that they have denied access. Any ideas how it can be set up so that anything in this new second drive can be shared across everyone without any problems, with full read,write, edit access?

version using is Feisty Fawn (if that makes any difference) 

You help would be appreciated as i'm a linux newbie!

---

### Post by rmemm on 2007-05-18
Some basics -- when a file is saved the permission set on the file are set based on the "umask" settings on your system.  The umask is basically a bit pattern that defines default file permissions.  Users umasks are usually set to 007, 027 or 077 or something like that.  The digits are (user)(group)(other/world) access permissions.  007 is rw for user and group no access for others.  027 is rw access for user, ro access for group, and no access for world.

Now to the share question -- one could have writable files by using umask of 000 meaning all files the user creates are readable/write by anyone -- but this is not generally advisable.  A better way is to use groups and create a special group for share access, then set umasks to 007 so that by default file creation gives group rw access,  Then to enforce files saved on the share to be in the gorup of the share -- set the sgid bit on the share folder.

So that users home directories are private -- generally you use a separate group scheme in this case for users -- meaning each user should have his own primary group -- and as mentioned above also be member of the group used for the share.

Does that make any sense?

Rob

---

### Post by jius on 2007-05-19
Yeah Rob what you are saying seems to make sense. I create myself as main (administrator) under usual Ubuntu installation questions, then other users with their own accounts. Guess that means looking at it they are in themselves their own group. So all I need to do now is add myself and all users to a group and then give us all rw privileges? 

May sound like a daft question - but it is safe to place me (as main admin) within a separate group as mentioned above without messing up with anything or causing security issues? 

Thanks

---

### Post by rmemm on 2007-05-22
Generally on Ubuntu the "root" user (by that I mean the user named root) is not the one your logged in as -- so I assume you asking about a normal user account -- though one that has admin privs?

For normal accounts (with special admin permissions or not), I don't think their primary user or group matters beyond of course the natural effect of that -- when a user creates a files it's given his user and group usually.  The other thing I would say -- on my system -- users appear to be in separate groups anyway -- so I suspect your already setup like this as most distributions do this (though some do not -- for example linspire I think does not use the separate group for each user setup).  You see the priamry group (ubuntu calls this the user's "main group" by going to "System>Administration>User's and Groups>(select a user)>(hit properties)>advanced.  See the main group there.  I would NOT change this unless it seems like you must -- because it's probably already a separate group -- and even if it isn't you still don't need to change it unless you want to for some reason.

You just need to go into the User's and Groups tool and create a totally new group and make whoever a member of that group (basically as an axiliary group -- not as their main group).  You do that in the groups tab of the User's and Groups tool.

Then create your shared folder and edit its properties and assign it to whatever user -- probably either root or yourself and set it's group to the name of the group your using to share.  You'll also need to adjust permissions too.  Typically you'd make this folder rwx to user and group and no access to other.  Then you'd set the "special" permission of sgid on the folder .  You don't have to do the sgid thing but it forces the group of a file created in the folder to be the shared group rather than the creators group -- which is probably what you want.  You can see this in the permissions tab of the folder properties.  

That's the basic setup.  To finish the setup you now need to verify that all the users using this shared folder have a umask that will create files that have the appropriate permissions so you can read, write, or execute them -- whatever you want to do.  This "default" file creatioin permission is controled by the umask setting. It may be what you want or may not -- I've changed mine so I don't know what the normal setting is.  To check, open up a shell window and type the command "umask" to see it.  Mine is set to 0027 which means that when I create files by default other has no access, user (me) has rw and possibly x access, and group has only read and possibly x access.  For what you want umasks of either 0007 or 0027 is probably what you want.  First is group rw latter is group ro.  If you need to change this defualt you can put the umask command in the .bashrc file for each user or in the system wide file (maybe /etc/bash.bashrc -- but I can't remember).  I for example use "umask 027" in my .bashrc.  

As an asside for umasks -- the full mask shown when you type umask is 4 digits on my system (though I've seen this display vary quite a lot between distributions and systems and shells) -- the first diget is the "special bits" followed by user, group, other.  I think you'll find that when setting 0027,027,27 gives the same umask -- meaning it's only the octal number that's important here -- but you can play with this and check.

Does that help?

Rob

---

### Post by rmemm on 2007-05-22
You asked a question about security.  Adding an axilary group to your user account as far as I know does not effect security unless you create files that have this group ownership.  Normally files are created owned by the user and primary group of the user that created them.  

There are situations where security can be compromised.  For example:

*  As with all sharing the simple act of sharing opens up avenues for attack. For example if you run a program someone else writes -- or open up a spread sheet with a macro in it and run it from the share -- you trusting other users.  Even opening a file from someone else is an act of trust at some level because people find bugs in programs that can be expoited in non-standard ways.  
*  Along with the above -- if your concerned about the security of the share and the reliability of the users that access the share -- neither "." nor any directory on the share should be in the PATH -- nor in any other of the many search paths that can be defined.
*  I seem to remember that at least from the shell it's possible to temporaly change the group that's used during default creation though I never do this.
*  Being a member of course you can now change the group ownership of a file to be owned by the group -- such as in the properties>permission dialog or with the chown, chgrp etc shell commands.
*  If create files in directories that have sgid or suid permissions set than the file will automatically change ownership -- user, group, or both depending on the setting and this of course effect access -- typically in a positvie way -- but not always of course.
*  If you change your umask -- it does effect default permissions of all files you create -- so you need to decide if this is OK.  Most notably you need to know especially who else is in your primary group for example as it's likely to change default access to your personal files if others are part of your primary group (meaning if your not using the separate group approach on your system).
*  Files you create should not have the suid or sgid bits set especially if they are executable (this is for files not folders).  If an executable file has the suid or sgid bit set it will be execututed with the permissions of the owner of the file not that of the user.  Meaning as the file user id if suid is set or the file group id if sgid is set.

So the short answer -- I don't think there's any general security issue with this -- but of course there are always ways to compromise security if you try -- and I can't guarnatee this is a full list -- but it's all I could think of at the moment.

Rob

---

