---
title: "Maintain desktop theme across various users"
date: 2014-04-15
forum: General Help
---

### Post by Jacob_Tennant on 2014-04-15
I have a test lab of computers that are setup so the desktop theme looks almost like Windows 7 so as to not to scare them as they did when they saw the linux desktop...

These computers are going to be connected to a Windows 2012R2 Active Directory server for user authentication. Tested & Working

When I sign in as a local administrator (only local user on base system used to create Clonezilla image) I get the Windows 7 theme that we setup. When a AD authenticated user logs in they get the default linux desktop theme.

[B]Where/How would I setup the Windows 7 theme data so that ALL users that sign in to these computers thru AD authentication get the Windows 7 themed desktop?


[/B]&#8203;Thank you

---

### Post by jbaerboc on 2014-04-17
I'm guessing they each have some sort of /home folder somewhere. Typically a user's individual theme is stored on their own /home/.themes directory folder. Now that's with a single user so don't know how that changes when using active directory etc...

My guess is you'd need to copy/paste that theme into every /user/.theme folder and then make it the active theme for every user. Don't know if there's a mass command via terminal or not but that's my bet. Good luck ;-)

---

### Post by Derek Karpinski on 2014-04-19
Use /etc/skel

---

### Post by bab1 on 2014-04-19
> **Derek Karpinski said:**
> Use /etc/skel
+ ! for this.  Be sure to use the Debian method of adding users or the /etc/skel files will not be used.

---

### Post by Jacob_Tennant on 2014-04-23
I am not adding local users to the computers, these users will only login through Active Directory. They will not have a local computer user account but will be given a desktop following the specifications of the default user.

---

