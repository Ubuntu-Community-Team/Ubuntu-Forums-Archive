---
title: "Figuring out personal Sudo terminal password"
date: 2019-10-28
forum: General Help
---

### Post by nocruoro on 2019-10-28
The more and more i decide to customize Ubuntu 18.04.3 LTS, more references to needing the **Terminal** crop up. However in my case it does not respond to a username password like i would have thought.

How do i carefully figure out my Sudo Password when prompted for it based on a USB install which provides no documentation for setting this up?

---

### Post by wildmanne39 on 2019-10-28
What exactly happens when you type your password? the terminal does not show your password as it is typed for security reasons so after you type it just hit enter, many commands show no output as long as they complete successfully, the password you use is the user password you created when you installed Ubuntu.

---

### Post by nocruoro on 2019-10-28
Says sorry try again after attemting a installation command for attempting to enable Gnome for addons. When trying to install gnome so i can add things like dash-to-panel which requires it.

Im the only user on this conputer so it have full access right? no other admin is registered to it.

---

### Post by TheFu on 2019-10-28
There isn't anything called a "sudo password". There is just the password used to login for each account. 

If an account is setup in the sudoers file to have the ability to escalate/change userids, then the password used is the same password that is used for that userid to login.

---

### Post by crip720 on 2019-10-28
When installing Ubuntu it asks you to make a password.  This is the password you need.  It will not show in terminal, so you also need to make sure 'caps lock' is not on by mistake.  You are only a user, not admin of computer even if you are the only one.  You need the password to make you admin for a limited time.  If you don't completely remember password, let these nice folks know and they can help you to replace it.

---

### Post by nocruoro on 2019-10-29
I am calm and remember the password but why do i just get "sorry try again" ? one time it even froze on me me after typing correctly and getting the error

had to pull the plug and laptop battery

---

### Post by TheFu on 2019-10-29
The only times I've seen this sort of issue was when I'd edited the sudoers file and broke it 
or
if snap or flatpak package management was involved and it didn't remember credentials for any time.  

I haven't researched a solution for the 2nd problem.  About once every 2 yrs I'll screw up my sudoers config and need to hack into my system to correct it.  Most recently that happened last weekend. ;)  Some day I'll learn a method that doesn't let me break it. Someday.

---

### Post by nocruoro on 2019-10-29
> **TheFu said:**
> The only times I've seen this sort of issue was when I'd edited the sudoers file and broke it 
or
if snap or flatpak package management was involved and it didn't remember credentials for any time.  

I haven't researched a solution for the 2nd problem.  About once every 2 yrs I'll screw up my sudoers config and need to hack into my system to correct it.  Most recently that happened last weekend. ;)  Some day I'll learn a method that doesn't let me break it. Someday.

Haven't tampered with anything yet. I've barely done much since friday 25 ocotber this month after installing it.

---

### Post by nocruoro on 2019-10-29
> **nocruoro said:**
> Haven't tampered with anything yet. I've barely done much since friday 25 ocotber this month after installing it.

> **TheFu said:**
> The only times I've seen this sort of issue was when I'd edited the sudoers file and broke it 
or
if snap or flatpak package management was involved and it didn't remember credentials for any time.  

I haven't researched a solution for the 2nd problem.  About once every 2 yrs I'll screw up my sudoers config and need to hack into my system to correct it.  Most recently that happened last weekend. ;)  Some day I'll learn a method that doesn't let me break it. Someday.

Managed to find it. Google really has a poor documentation on finding websites that are letting people know if an extension is available under a different name in that [COLOR=#a52a2a]**Ubuntu Software store**[/COLOR].

I guess i wont be needing that terminal assisstance after all.

---

