---
title: "Samba server on Ubuntu..."
date: 2014-06-21
forum: General Help
---

### Post by wolfgentleman on 2014-06-21
What I want:
[LIST]
[*]The samba server accessible anywhere on my network.
[*]For the login to be based on the unix logins, if my username is user1 and the password is 123 to login to Ubuntu then I want to login with those through a samba client
[*]If I login with user1 and their home folder is /home/user1 then I want the samba server to show /home/user1 for the "shared directory"
[/LIST]
What I don't want:
[LIST]
[*]Printer server
[*]External access
[/LIST]

I was trying to find a howto but all I found was a [wiki page]("https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html") that didn't help. I'm sure there's one somewhere, but I couldn't find it. My Google fu is not at mastery level yet :-P
Anyway, I'm sorry if this is the wrong place or if it's a dupe.

---

### Post by capscrew on 2014-06-21
> **wolfgentleman said:**
> What I want:

The samba server accessible anywhere on my network.

You need to define what your network is.  Is it a simple single segment LAN or do you have multiple subnets or is there a WAN aspect to the network that you want to include?
> 
For the login to be based on the unix logins, if my username is user1 and the password is 123 to login to Ubuntu then I want to login with those through a samba client

This is how Samba works by default.  You need to have a system account (Linux) and a Samba account (smbpasswd).  The names should be matched and consistent through out the the network.  Your username and password should be the same on all hosts (the server and all clients)
> 
If I login with user1 and their home folder is /home/user1 then I want the samba server to show /home/user1 for the "shared directory"

Define *"shared directory"*.  A shared directory is not always the same as a Samba share.  Shares can be private (the user only has access) or public (multiple users have access).  If you want to set up a share that is private to the user only you can use a special share named [homes].  This share dynamically allows access to a private to the user share with the SMB resource name of *//server/user_name*.
> 

What I don't want:
Printer server

I agree.  There are much easier ways to provide networked printing.
> 
External access

External to what?  Samba is considered as remote access.
> 

I was trying to find a howto but all I found was a [wiki page]("https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html") that didn't help. I'm sure there's one somewhere, but I couldn't find it. My Google fu is not at mastery level yet :-P
Anyway, I'm sorry if this is the wrong place or if it's a dupe.
There is no one place to provide you with a howto for all of the various ways to configure Samba.  For a simple howto I recommend [this]("http://www.jonathanmoeller.com/screed/?p=4169").  

However, if you are going to have public shares then you want to place the data (and therefore the shares) in a directory below /srv.  This is the traditional spot for shared data.  

With shares with multiple users you will need to set up a common group and group inheritance.  I use the user group *users* (gid = 100) for this.

More info on what you want to do would be helpful.  I'm sure we can help you set up whatever you need.

---

### Post by wolfgentleman on 2014-06-21
> **capscrew said:**
> You need to define what your network is.  Is it a simple single segment LAN or do you have multiple subnets or is there a WAN aspect to the network that you want to include?
192.168.1.*

> **capscrew said:**
> This is how Samba works by default.  You need to have a system account (Linux) and a Samba account (smbpasswd).  The names should be matched and consistent through out the the network.  Your username and password should be the same on all hosts (the server and all clients)
It doesn't seem that way... I don't think anyway. When I try to login with my system account info and it says it can't connect.

> **capscrew said:**
> Define *"shared directory"*.  A shared directory is not always the same as a Samba share.  Shares can be private (the user only has access) or public (multiple users have access).  If you want to set up a share that is private to the user only you can use a special share named [homes].  This share dynamically allows access to a private to the user share with the SMB resource name of *//server/user_name*.
On Windows:
*Open network shares, I think it's something like Network & Places
*Click NetBIOS name
*Login with credentials (such as user1:pass1)
*Shows files in "shared directory" or multiple "shared directories", in this case it should show the contents of user1's home folder

In Dolphin:
*Click Network under Places
*Click Samba Shares
*Click your workspace name/domain
*Click NetBIOS name
*Login with credentials like above
*Shows files like above

In ES File Explorer:
*Open LAN window
*Scan for or add new server(s)
*Click or use the IP Address of the Samba server
*Login with credentials like above
*Shows files like above

and so on...


Does that clarify what I am meaning? Sorry for the confusion, I'm not the best "explainer"...

---

### Post by capscrew on 2014-06-21
> **wolfgentleman said:**
> 192.168.1.*

A single simple network then.
> 
When I try to login with my system account info and it says it can't connect.

This may not be due to authentication.  Not connecting happens before you are authenticated.  From the command line you can debug this.  Post the output of this command```
smbtree -d2
```
> 


On Windows:
*Open network shares, I think it's something like Network & Places
*Click NetBIOS name
*Login with credentials (such as user1:pass1)
*Shows files in "shared directory" or multiple "shared directories", in this case it should show the contents of user1's home folder

...and so on...
Does that clarify what I am meaning? Sorry for the confusion, I'm not the best "explainer"...
No it doesn't.  What I'm talking about is how many users will access a Samba share.  

[LIST]
[*]Are you going to have a file share that more than one user is going to access (shared access)? 
[*]Are you going to have a file share that only the individual user is going to access (private access)?
[*]Are you going to have a file share that is open to all users on the network (public share)?
[/LIST]
All of this is can be available at the same time.  You can have private file shares for home directories and share directories for groups of users and shares that are completely open for all users.

Lets just start with your account.  Have you created both  a Ubuntu user and a Samba user account on the server?  Have you a similar account on the client machine?   We can see what happens when you use the command *smbtree -d2*.  Please post the output using the CODE BLOCKS option in the advanced editor.  It is the [SIZE=3]#[/SIZE] icon at the top.  This formats the text as fixed spacing.  It makes it much easier to read.

---

