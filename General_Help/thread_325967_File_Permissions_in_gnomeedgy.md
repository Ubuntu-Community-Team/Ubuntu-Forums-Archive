---
title: "File Permissions in gnome/edgy"
date: 2006-12-26
forum: General Help
---

### Post by andydread on 2006-12-26
Hi. I just upgraded a few computers to edgy from dapper
I noticed that with the new version of gnome I no longer have
control over file permissions.  Maybe I am going crazy but 
When I try to give file ownership to new groups that I have created
they do not show up in the nautilus permissions dialog.   Try it for 
yourself.  Go to usermanager create a new group the assign people
to the group.  Now go create a new file and attempt to assign group
ownership of the file by right-clicking on it and setting it to the group
you created in the file manager.   Notice it does not show up.  
Is there a way to show all groups in the file permissions dialog? 
Is this more dumbing down of gnome or am I missing something here. 
Gnome has been going in the wrong direction lately.  No more screensaver 
options.  now this.    I am beginning to HATE gnome.

---

### Post by pay on 2006-12-26
You can do it with the terminal. ```
sudo chmod -R 710 /path/to/file.doc
```would make it read. write and executable to the owner and executable to people in the group and people not in the group can't use it. ```
chown -R <username>:<groupname> file
```will change the owner and the group of that file. This goes into permisions with more depth [http://www.zzee.com/solutions/unix-permissions.shtml](http://www.zzee.com/solutions/unix-permissions.shtml)

---

### Post by andydread on 2006-12-26
Thank you for the unbelievably rapid response.  One of the things Ubuntu is what it is to me 
is because of the incredible community. just incredible.  Anyways. I already know how to drop to the cli and do all the chmod and chown commands from the slackware days however, I have new users from windows that I have migrated from windows to Edgy and I was in the middle of showing  them (in the GUI) how to change permissions by 
1 Create users in user manager
2 Create groups in user manager
in this case the accounting group
3 Assign users to accounting group in user manager
4 copy quickbooks files to the computer and right clicking on the file
and assigning group read and right permissions.  so only people in the 
accounting group can access the qbw file.  

This is a simple procedure on all basic GUIs and also in earlier versions of Gnome
even in Dapper.  Now It seems it has been disabled in the current version of Gnome
that comes with Edgy.   When I right click on the file to assign it to the accounting group
it does not show up.  not even the group users show up when u try to assign group 
permissions to a file.   I know I can do this in the cli but still having a hard time why 
this feature has been removed from Gnome if that is the case.  

Now it seams like a simple task such as group ownership of a file has to be done
at the command line.   Maybe in the future the only thing you can do in the GUI in 
Gnome is to open and close firefox.  All other features will be removed to protect 
the Innocent.   

I hope I am wrong and there is actually a way to assign group permissions
to file from within the GUI.

---

### Post by mcduck on 2006-12-27
Open Configuration Editor (Alt-F2 and run gconf-editor), then browse to apps/nautilus/preferences and enable 'show_advanced_permissions'.  That should do what you need :)

---

### Post by davecjr on 2007-01-03
I am very new to Linux and ran into this same problem.  I used gconf-editor but do not have the 'show_advanced_permissions' option listed when I get to apps/nautilus/preferences.  Does that make sense?

---

### Post by mcduck on 2007-01-03
If you are using Ubuntu 6.06 (Dapper) then that's normal.

---

