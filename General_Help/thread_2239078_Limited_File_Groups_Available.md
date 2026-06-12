---
title: "Limited File Groups Available"
date: 2014-08-11
forum: General Help
---

### Post by Binarydreams on 2014-08-11
Hello, I just installed Ubuntu Server and installed the GUI and Samba.  I also created a number of user groups so that I could segregate shared folders on our network by user groups.  I only have a small number of user groups available from the drop down menu under the right click file properties dialogue.  None of the user groups I have created are there and there is no obvious way to add them to the drop down selector either...  Any help would be appreciated.  Creating the groups and assigning the users to them was a piece of cake.  Assigning the users to the file shares is another story...  I would rather do everything through the GUI if there's a way but I'm not a total noob to the command line either.  As I get older, I choose to tinker less and less and prefer GUI tools if available.

Thank you in advance.

---

### Post by bab1 on 2014-08-11
I don't use a GUI at all on any of my Ubuntu server installs.  I create shares in the /etc/samba/smb.conf file.  The permissions for the underlying directory that is being shared can be easily set.  In addition you will need to use the sgid bit to provide user group inheritance in the shares file system.  All of this is best set using a text editor and the CLI

Not all GUI interfaces have the same options.  What GUI did you install?  For the most part GUI created Samba shares are always located in someones home directory.  Is this what you want to do?

Give use an example of a share and the user group that will be using it.

---

### Post by Binarydreams on 2014-08-12
I installed the standard Gnome desktop using apt-get install ubuntu-desktop after installing server.  I don't mind the shared folders being in the admin user home directory.  

Some examples of the shares I created are "Technician," "Office," "Scan," Manager," etc.  I want our technicians and above to have access to the technician folder, whereas the office staff should only have access to the office documents.  In all, I need 3 levels of permission based on groups.  I have so far used two permission levels to give two levels of access.  I created additional user groups but they are not appearing under the "groups" dropdown in the folder properties.  That seems to be the only challenge in getting things to work how I want.  I want my new usergroups to appear in the file properties dropdown so I can assign my custom groups to the file share.

---

### Post by bab1 on 2014-08-12
> **Binarydreams said:**
> I installed the standard Gnome desktop using apt-get install ubuntu-desktop after installing server.  I don't mind the shared folders being in the admin user home directory.  

Some examples of the shares I created are "Technician," "Office," "Scan," Manager," etc. 

I want our technicians and above to have access to the technician folder, whereas the office staff should only have access to the office documents.

These shares should each have there own branch in your home directory file system.  Maybe something like```

/home/<user>/samba/Technician
/home/<user>/samba/Office
/home/<user>/samba/Scan
/home/<user>/samba/Manager

```
>  
In all, I need 3 levels of permission based on groups.  I have so far used two permission levels to give two levels of access.  

Do you really mean *levels * as one above another?  Did you use ACL's t accomplish this.  Or, do you mean that you have 2 distinct shares, each managed by its own usergroup?  
> 
I created additional user groups but they are not appearing under the "groups" dropdown in the folder properties.  That seems to be the only challenge in getting things to work how I want.  I want my new usergroups to appear in the file properties dropdown so I can assign my custom groups to the file share.
You may not be able to do that at all.  The devs at GNOME or the packager that compiled the source code control what is displayed in the drop down list.  I would have no idea as to what their parameters are.  It could be as simple as what the gid # is.  A gid # below 500 is usually for a system user in a Debian system.

---

### Post by Binarydreams on 2014-08-12
Yes, I have several distinct shares, each managed by the usergroup.

I will look at the gid #'s.  That definitely makes sense.  Maybe if I change the gid's of my new groups to lower numbers they will bump off the others above them.

---

### Post by bab1 on 2014-08-12
> **Binarydreams said:**
> Yes, I have several distinct shares, each managed by the usergroup.

I will look at the gid #'s.  That definitely makes sense.  Maybe if I change the gid's of my new groups to lower numbers they will bump off the others above them.

I'm not saying that the ordinal position matters at all.  What I am saying is:  If gid < 500 then include.  Another way could be: if > 500 ignore.

On the other hand that criteria does not have to be used at all.

---

