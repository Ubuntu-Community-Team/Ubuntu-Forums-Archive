---
title: "adduser question (i think"
date: 2008-04-21
forum: General Help
---

### Post by bcross64 on 2008-04-21
Here's what I have:
Ubuntu 8.04 with Likewise installed and configured to attach to my domain.
When a domain user logs on, they have no rights. I really don't want to sit around adding 100+ users to the correct groups. Is there a way this could be automated? a log-in script that adds the domain user that just logged in to the correct groups? Or somehow populate the groups with all the AD users? Thanks in advance for your help. As sort of a related topic, the domain users that have logged in can't be added to groups through the gui (System > Administration > Users and Groups). Anyone else find this weird/obnoxious?

---

### Post by p_quarles on 2008-04-21
Edit the adduser configuration file:
```
sudo nano /etc/adduser.conf
```
Now, uncomment the following line:
```
#EXTRA_GROUPS="dialout cdrom floppy audio src video lp src users"
```
Newly created users will now be added to the groups listed above automatically. Other new user defaults (such as shell environment) can also be set by editing this file.

---

### Post by bcross64 on 2008-04-21
That's pretty simple. Thanks. Is there a guide or documentation or something for these kinds of weird specific questions for clueless people like me?

---

### Post by p_quarles on 2008-04-21
Well, there's no central one that I'm aware of. What I did (I didn't know the answer to your question before looking it up) was to look at the adduser man page, which pointed me to the adduser.conf file. Looking through that, I saw that there was a setting for what you wanted to do.

---

### Post by bcross64 on 2008-04-21
> **p_quarles said:**
> Edit the adduser configuration file:
```
sudo nano /etc/adduser.conf
```Now, uncomment the following line:
```
#EXTRA_GROUPS="dialout cdrom floppy audio src video lp src users"
```Newly created users will now be added to the groups listed above automatically. Other new user defaults (such as shell environment) can also be set by editing this file.

After thinking/testing it out, this will only work if the domain user has sudo rights (which they don't).

    I've been poking around in the Likewise Open mailing lists and come up with this. To add the domain users to the sudoers list you add AD\\USERNAME ALL=(ALL) ALL under user privilege specification ([[COLOR="Blue"]reference[/COLOR]]("http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-February/000116.html")).

    My question to this comment is can I add a wildcard in place of USERNAME to allow all domain users to have sudo rights? Also, is the AD a server name or is it supposed to be AD?

   The other thing I found (for the sake of logging this whole adventure on this forum) is how to add domain users as Linux users ([[COLOR="Blue"]reference[/COLOR]]("http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-March/000161.html")).

And since I can map domain users to Linux users (supposedly, I'll try tomorrow at work), is there a way to automatically put users in a group and/or give them sudo rights?

---

### Post by trippinnik on 2008-04-22
This is the first I've heard of Likewise, but it looks interesting.  I've seen a few other projects to connect linux to AD too.  Making the users have sudo rights would be a really bad idea though.  I mean the point of AD is to have locked down accounts.

---

### Post by simon_w on 2008-04-30
Hi folks,

> **bcross64 said:**
> 
   The other thing I found (for the sake of logging this whole adventure on this forum) is how to add domain users as Linux users ([[COLOR="Blue"]reference[/COLOR]]("http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-March/000161.html")).

And since I can map domain users to Linux users (supposedly, I'll try tomorrow at work), is there a way to automatically put users in a group and/or give them sudo rights?

Have you (or anyone else) got this to work successfully?  From the archived mailing-list discussion referenced above:

> > I'm looking for mapping AD user --> Linux user so users don't 
> have to type in domain\username, but rather just a simple
> user name, and also, I want to add certain users to the
> sudoers list.

Add these two lines to /etc/samba/lwiauthd.conf:

	winbind nss info = lwopen
	lwopen:name_map = /etc/samba/lwopen_map.txt

And create the map file to be

  simple name = DOMAIN\name

This will work for users and groups.

but, so far as I can tell, this is having no effect at all on my (Hardy) system.

I simply want my main user on my Ubuntu workstation to authenticate as my AD Domain user, or at least to allow my Domain user to logon locally to my laptop and have sudo rights, etc.

If anyone has any experience, suggestions or solutions, please share them here!

Thanks!

Simon

---

### Post by bcross64 on 2008-04-30
Sorry about not reporting back. Domain users are stored in the DOMAIN\domain^users group. Therefore, to give all domain users sudo rights all you have to do is edit the sudoers file (/etc/sudoers) and copy the line for the root user group to give that group sudo rights. I think it should look like this
```
%DOMAIN\domain^users ALL = (ALL) ALL
```
Replace DOMAIN with your domain. Unfortunately, you can't add domain users to groups automatically or manage them through users and groups. you have to edit the group file directly
```
sudo gedit /etc/group
```
Add your domain user(s) to whichever group(s) you want. There may be a wildcard for this so that you could add all domain users at once, but I don't know it. If someone reading this knows which wildcard to use in the group file, let me know. All this work being preceded by installing Likewise. Likewise is what adds your ubuntu machine to the domain. If you or your users don't need sudo or any rights, just add the computer to the domain with likewise and go on.

What the guy in the likewise mail post is talking about is making it so that your users won't have to type in DOMAIN\USERNAME to login. Just USERNAME. The only thing is you would have to put every user in that file. We have 100+ users, so that's not an option for me.

Hope all that helped.

---

