---
title: "Startup program problem, 70% Sudoers, 30% Firestarter"
date: 2005-08-23
forum: General Help
---

### Post by essexman on 2005-08-23
I would like to get Firestarter to auto load at Start for the admin user (me).

Forgive me if my story seems long winded. I have read the FAQs, man files, and Forums (everything picked up on Fire/Sudoers and Sudoers/nopassword).  I have searched google and the Sudo and firestarter websites.

I have used Linux for 3 years, and I have two machines running Ubuntu 5.04, 1 desktop and 1 Laptop, both with myself and my girlfriend as users, with me as admin.

I have edited my Sudoer file using : ```
export EDITOR=gedit && sudo visudo
```

with the following code:

```
user1	ALL= NOPASSWD: /usr/sbin/firestarter
```
```
user2	ALL= NOPASSWD: /usr/sbin/firestarter
```

I have added: sudo firestarter –start-hidden to my Start-up programs in System=>Preferences=>Sessions

In my girlfriends user environment, Firestarter starts, and the Icon appears.  There is a pop-up warning that “you must have root privileges”, but this can be clicked and closed without a problem.  It would be nice if this could be fixed, but it is not a problem because she can boot into a confident & secure environment.

I cannot start Fire start from boot or login.  The Icon does not appear and : ps aux | grep firestarter shows that Firestarter is not running.  I have tried changing the order of Startup using values between 19-80. This works fine on the first log-in or reboot, but wont repeat and the problem comes straight back. I've also tried using gksudo and removing –start-hidden, many things work once, but i think this is within the default sudo timer.

I have checked man:sudoers and man:sudo and can't find anything, though I am sure that this has something to do with me being the admin user with the sudo password.  Both machines are on auto login, the desktop for me and the laptop for my girlfriend. I am starting Firestarter from the Icon on my toolbar; this runs: ```
gksudo /usr/sbin/firestarter
``` and then asks for my password!

I'm fairly certain that there is a problem with my understanding of sudo, as sudo is very new to me.

I realise that Iptables is built into the kernel and my set up should still be safe, I would like to be visually assured and Firestarter seems to work well for doing that.  I also realise that these are well covered items already. Sudoers brings up 250 threads and Firestarter brings up 500(including this forum), but the answers  have seen are standard stuff that appears in the ubuntu guide. 

I have spent nearly a month on this and I don't think I will find the answer with out the help of an expert ](*,) .  I hope you can help.

Thanks for you consideration

Essexman

---

### Post by arnieboy on 2005-08-23
the solution is pretty simple. to system-->preferences-->sessions remove the firestarter entry that u have put in and replace it with:
```
gksudo usr/sbin/firestarter
``` (order may be anything 50 for example)
the difference between gksudo and sudo is that gksudo gives a GTK frontend to sudo. thats all.
if u have added:
```
user_name ALL=NOPASSWD:/usr/sbin/firestarter
```
where user_name is the name of your user account to your /etc/sudoers file all should be well,
the --start-hidden option hides ur icon but firestarter will run in the background.
hope this helps.

---

### Post by essexman on 2005-08-24
[QUOTE=arnieboy]the solution is pretty simple. to system-->preferences-->sessions remove the firestarter entry that u have put in and replace it with:
```
gksudo usr/sbin/firestarter
``` (order may be anything 50 for example)
the difference between gksudo and sudo is that gksudo gives a GTK frontend to sudo. thats all.
if u have added:
```
user_name ALL=NOPASSWD:/usr/sbin/firestarter
```
where user_name is the name of your user account to your /etc/sudoers file all should be well,
the --start-hidden option hides ur icon but firestarter will run in the background.
hope this helps.[/QUOTE]
Arniboy - Thanks for the reply.

I couldn't add everything in my original post, but gksudo doesn't work for me at all.  It wont load at startup as it still requires a password.  As you say, it it just the gtk versio of sudo. I think it is only for icons and such like.

I would like to try the :```
user_name ALL=NOPASSWD:/usr/sbin/firestarter
```
without spaces, as you have suggested.  Before i do i want to double check, as this goes against the advice on Firestarter FAQ, Ubuntu guide, and numerous forum posts.

The main thing is, why should the same code work for one user on my system and not another?

---

### Post by arnieboy on 2005-08-24
[QUOTE=essexman]Arniboy - Thanks for the reply.

I couldn't add everything in my original post, but gksudo doesn't work for me at all.  It wont load at startup as it still requires a password.  As you say, it it just the gtk versio of sudo. I think it is only for icons and such like.

I would like to try the :```
user_name ALL=NOPASSWD:/usr/sbin/firestarter
```
without spaces, as you have suggested.  Before i do i want to double check, as this goes against the advice on Firestarter FAQ, Ubuntu guide, and numerous forum posts.

The main thing is, why should the same code work for one user on my system and not another?[/QUOTE]
post ur /etc/sudoers file here. I will explain to u how it works.

---

### Post by essexman on 2005-08-25
[QUOTE=arnieboy]post ur /etc/sudoers file here. I will explain to u how it works.[/QUOTE]
 Arnieboy

Thanks for the reply but I found the answer yesterday evening.

Success!

I'm very pleased, i hope you don't think I have wasted you time as I have literally been two months on this; quite embarrassing.

I found the answer here: [http://www.sudo.ws/pipermail/sudo-users/2004-December/002317.html](http://www.sudo.ws/pipermail/sudo-users/2004-December/002317.html) 

Just is case anyone else finds this I'll describe what I found.

My old sudoers was this: 
```
Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

user1	ALL= NOPASSWD: /usr/sbin/firestarter
user2	ALL= NOPASSWD: /usr/sbin/firestarter

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

#Cut and paste from: User privilege specification


```
As the link explains - it is what you say last that counts.  Setting the admin group to ALL reset user1 to require a password because user1 has admin privilages.

user2 had no admin privilages and was unafected by the reset of %admin.

All that was required was a cut and paste to reorder the NOPASWD settings, which are now at the end of the file.

My new sudoers is this: 
```
Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

#Cut and paste from: User privilege specification

user1	ALL= NOPASSWD: /usr/sbin/firestarter
user2	ALL= NOPASSWD: /usr/sbin/firestarter
```

And firestarter loads on boot.

And I'm off to set it up on the laptop as well.

Hope this works for others

Cheers

essexman

---

### Post by goonmaster on 2007-06-04
Despite how long ago this thread was made i have a proper fully working solution
the current one no longer works!

found here:
[http://www.howtoadvice.com/AutoFirestarter/](http://www.howtoadvice.com/AutoFirestarter/)


> 
[SIZE="2"]Step 1[/SIZE]
In terminal type:
**export EDITOR=gedit && sudo visudo**
That will open /etc/sudoers

[SIZE="2"]Step 2[/SIZE]
In   /etc/sudoers   replace the line "defaults" from:
**Defaults !lecture,tty_tickets,!fqdn**
to
**Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME"**

[SIZE="2"]Step 3[/SIZE]
add this line at the *very end* of the   /etc/sudoers :
**username ALL= NOPASSWD: /usr/sbin/firestarter**
make sure to replace **username** with your username!
Then save and exit Gedit.

[SIZE="2"]Step 4[/SIZE]
Navigate to:
System > Preferences > Sessions >new startup program
Give it a name like "Firewall" or "Firestarter"
then use this command:
**sudo /usr/sbin/firestarter --start-hidden**


Thats it!
this post was started in 2005 and the error is still there.
no offence meant to essexman but his fix didnt work for _me_
(currently using **Ubuntu Feisty 7.04**   and  **Linux 2.6.20-16Generic(i686)**      June 5 2007)
hope this fix helps somebody like me who has been looking for a while!

From Goonmaster
:D:D:D:D:D:D:D:D
FIXED!!

---

### Post by fromgi on 2007-06-06
Thank you for the very accurate and detailed instructions!  It works perfectly!

---

### Post by dave3281 on 2008-01-17
Fix works with Gusty Also thanks to all who posted

---

