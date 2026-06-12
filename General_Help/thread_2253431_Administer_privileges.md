---
title: "Administer privileges"
date: 2014-11-19
forum: General Help
---

### Post by zundap2 on 2014-11-19
Hi, i have just downloaded COMODO antivirus for ubuntu, it installed no problem but i then ran the Dianostic option to see if every thing was ok, but when I did I got the following error message.

The kernel module ( [COLOR=#ff0000]&#8220;redirts.ko&#8221; [/COLOR]) appropriate for your current kernel version does not exist, please run ( [COLOR=#0000ff]/opt/COMODO/post_setup.sh[/COLOR] ) to install it. Then run  /etc/init.d/cmdavdcommand to restart cmdavd service


I then launched Terminal, typed in 
( /[COLOR=#0000ff]opt/COMODO/post_setup.sh[/COLOR] ) and entered it with the enter button. I then got another error message 
( [COLOR=#ff0000]Please run this script with administrator privileges[/COLOR] ) 

Could anyone tell me how i run with administrator privilege?  I am the only person that uses the computer so I don&#8217;t have an administrator.  

Thanks in advance for any replies.

---

### Post by lisati on 2014-11-19
The default for a standard Ubuntu installation is that the user created during installation is the administrator. The way the Ubuntu security model works, it is *sometimes* necessary to temporarily elevate privileges to the equivalent of the "root" user in other *nix-based systems to be able to perform administrative tasks. This is done with [sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by BBQdave on 2014-11-20
> **zundap2 said:**
> Hi, i have just downloaded COMODO antivirus for ubuntu...

Installing COMODO seems redundant to your security. I would recommend checking out Ubuntu's default secure settings, that is to say:

[LIST]
[*]the use of secure repos
[*]Ubuntu does not accept port traffic by default (basic firewall)
[*]use of SUDO command for root function
[*]and of course - use a strong password for your account
[/LIST]

Personally, I have used Linux for 15 years, and Mac osX (off and on over 10 years) - never installed virus program, never had problems :)

---

### Post by zundap2 on 2014-11-22
> **lisati said:**
> The default for a standard Ubuntu installation is that the user created during installation is the administrator. The way the Ubuntu security model works, it is *sometimes* necessary to temporarily elevate privileges to the equivalent of the "root" user in other *nix-based systems to be able to perform administrative tasks. This is done with [sudo]("https://help.ubuntu.com/community/RootSudo").

That's as i understand lisati and but it does not work in this situation,  What exactly is sudo? I don't understand. that word

---

### Post by lisati on 2014-11-22
> **zundap2 said:**
> That's as i understand lisati and but it does not work in this situation,  What exactly is sudo? I don't understand. that word

You'll notice that in my previous post the word "sudo" is a different colour. That means you can click on it to be shown the relevent information at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by QIII on 2014-11-22
"sudo" is often given as "super user do", which isn't entirely correct.

The "su" part is "substitute user".  "do" means what it seems: execute a command.

In reality, what it means is "execute a command as another user"

You can read about it by executing the following in the terminal

```
man sudo
```

The reason that "sudo" acts to give you (near) root privileges (in the short term) is that without a user being specified, root is assumed.  However, the next thing that happens is that a password is requested.  That password has to match the current user and the password contained in the sudoers policy.  For the rest of that terminal session, the near root privileges are maintained, but "sudo" has to be typed before each command requiring elevated privileges.

With some distributions, one might use

```
su -
```

as a general rule.

Following that with the correct password for the root user then allows the user to execute commands with (real) root privileges.

What that means is "substitute user" and the dash, which would normally be followed by a user, is left open indicating that no user is specified.  That is, assume root.

Long winded explanation distilled:  sudo allows you to temporarily elevate your privileges to (near) root.


Edit:  Meh.  A bit more.

"su -" works in Ubuntu as well, but you will generally see "sudo" given as the recommendation.  The reason for this is that if one elevates his privileges, messes around a bit and forgets he's root, he might do something unwanted and bork his system.

"sudo" is used for each command, as in:

```
sudo do this
sudo do that
sudo do the other

```

Some prefer to use "su -" or "sudo -i"  (i = simulate initial login, which means that the shell attempts to use the users profile and change to the user's /home).   Both of these will avoid the necessity for retyping "sudo" over and over.  My primary misgiving with either of those, as I said, it that you might forget and do something you don't want.  Having to type "sudo" reminds you that you are doing something that might be important...

---

### Post by zundap2 on 2014-11-22
> **lisati said:**
> The default for a standard Ubuntu installation is that the user created during installation is the administrator. The way the Ubuntu security model works, it is *sometimes* necessary to temporarily elevate privileges to the equivalent of the "root" user in other *nix-based systems to be able to perform administrative tasks. This is done with [sudo]("https://help.ubuntu.com/community/RootSudo").

Thanks lisati, that's as i see it also, but my password does not work in this situation, Any other ideas would be very welcome.

---

### Post by lisati on 2014-11-22
When you use something like:
```
sudo do this
```
it will ask for your password. When you type your password, it won't show on the screen. This is normal: just type your password as usual.

---

### Post by zundap2 on 2014-11-22
> **BBQdave said:**
> Installing COMODO seems redundant to your security. I would recommend checking out Ubuntu's default secure settings, that is to say:

[LIST]
[*]the use of secure repos 
[*]Ubuntu does not accept port traffic by default (basic firewall) 
[*]use of SUDO command for root function 
[*]and of course - use a strong password for your account 
[/LIST]

Personally, I have used Linux for 15 years, and Mac osX (off and on over 10 years) - never installed virus program, never had problems :)

Thanks BBQdave; the problem i was having was that every time i placed the curser over something and tried to click on it, it would shoot away from the curser, in effect i could not select anything, so i assumed it was a virus. I have since wiped the hardrive and reinstalled ubuntu 4 times, After wiping the hard drive and reinstalling 3 times with no change to the problem i decided to give just one more shot and on the 4th time for some reason the problem was no longer there. This makes absolutely no sense to me at all. However i will study the areas you indicated, hopefully that may reveal the cause of the problem. Thanks.

---

### Post by zundap2 on 2014-11-23
> **QIII said:**
> "sudo" is often given as "super user do", which isn't entirely correct.

The "su" part is "substitute user".  "do" means what it seems: execute a command.

In reality, what it means is "execute a command as another user"

You can read about it by executing the following in the terminal

```
man sudo
```

The reason that "sudo" acts to give you (near) root privileges (in the short term) is that without a user being specified, root is assumed.  However, the next thing that happens is that a password is requested.  That password has to match the current user and the password contained in the sudoers policy.  For the rest of that terminal session, the near root privileges are maintained, but "sudo" has to be typed before each command requiring elevated privileges.

With some distributions, one might use

```
su -
```

as a general rule.

Following that with the correct password for the root user then allows the user to execute commands with (real) root privileges.

What that means is "substitute user" and the dash, which would normally be followed by a user, is left open indicating that no user is specified.  That is, assume root.

Long winded explanation distilled:  sudo allows you to temporarily elevate your privileges to (near) root.


Edit:  Meh.  A bit more.

"su -" works in Ubuntu as well, but you will generally see "sudo" given as the recommendation.  The reason for this is that if one elevates his privileges, messes around a bit and forgets he's root, he might do something unwanted and bork his system.

"sudo" is used for each command, as in:

```
sudo do this
sudo do that
sudo do the other

```

Some prefer to use "su -" or "sudo -i"  (i = simulate initial login, which means that the shell attempts to use the users profile and change to the user's /home).   Both of these will avoid the necessity for retyping "sudo" over and over.  My primary misgiving with either of those, as I said, it that you might forget and do something you don't want.  Having to type "sudo" reminds you that you are doing something that might be important...


Thanks for a very detailed response QIII; Thanks to all three of you guys, i now have a much clearer idea of how things work, i will now try to put in to practice the things you have suggested. Thanks again.

---

