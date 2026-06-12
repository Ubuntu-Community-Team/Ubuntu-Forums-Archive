---
title: "Help. All administrative rights are gone"
date: 2007-01-02
forum: General Help
---

### Post by Karl Norway on 2007-01-02
Hi 

I got Ubuntu DD (6.06) and currently no access to root.

When I try to open (ie) Update Manager nothing happends.
This goes fore all of the admin tools.
Also I cant get root terminal to work, and sudo command dosent work either

What can I do?

---

### Post by aliyanage on 2007-01-02
Hi,

what happens when you open up shell and type:

```
sudo -s
```

if prompted type in password...

aliyanage

---

### Post by jblebrun on 2007-01-02
> **Karl Norway said:**
> Hi 

I got Ubuntu DD (6.06) and currently no access to root.

When I try to open (ie) Update Manager nothing happends.
This goes fore all of the admin tools.
Also I cant get root terminal to work, and sudo command dosent work either

What can I do?

It sounds like something might have happened to your /etc/sudoers file. 

Can you tell us exactly what the output is when you try a command like "sudo su" at the command line? (This command would normally give you root access). 

If nothing seems to work, try rebooting into single-user mode (it should be an option in the boot manager). Change the password for root, and the reboot back into the regular multi-user mode, and try to fix what went wrong.

---

### Post by anaconda on 2007-01-02
Boot to recovery mode, and you will have root rights so that you can either make a new user or add your currrent user back to sudoers -file. (to regive you sudo rights..)


One way to give your user sudo powers: 
adduser your_username admin

---

### Post by Karl Norway on 2007-01-02
On both i get the reply

sudo: must be setuid root.

jbleburn: I dont think i got a single-user login but i will check

---

### Post by anaconda on 2007-01-02
> **Karl Norway said:**
> 
jbleburn: I dont think i got a single-user login but i will check

Single-user login is the same as recovery mode, and if you dont have it in your grub-menu, you can edit your normal boot option by pressing 'e' when you are in the menu, and add single to the end of the second line.
And then just press 'b' to boot to recovery mode.

(Dont worry! Any changes you make to your grub menu are gone when you boot the next time. To permanently change your grub menu you would have to edit your /boot/grub/menu.lst  -file)

---

### Post by Karl Norway on 2007-01-02
Ok I have now made three more users and noone of my now four users have root rights 

Help!

---

### Post by jblebrun on 2007-01-02
> **Karl Norway said:**
> Ok I have now made three more users and noone of my now four users have root rights 

Help!

Did you check your /etc/sudoers file? Did you try rebooting in recovery mode to enable a root password? 

Once you enable a root password, you can get a root terminal by typing:

su

and then enteringing the root password when prompted.

---

### Post by aliyanage on 2007-01-02
I guess the sudo must be setuid root to do its work.
enter this in command line:

```
chmod 4111 /usr/local/bin/sudo
```

let me know what you get and probably do a restart...

---

### Post by anaconda on 2007-01-02
> **Karl Norway said:**
> Ok I have now made three more users and noone of my now four users have root rights 

Help!

did you try 
```
adduser your_username admin
```
?
```
adduser username
```
creates new user named username
and
```
adduser username admin
```
adds user username to admin group, ie gives existing user sudo povers.

---

### Post by Karl Norway on 2007-01-02
> **anaconda said:**
> did you try 
```
adduser your_username admin
```
?
```
adduser username
```
creates new user named username
and
```
adduser username admin
```
adds user username to admin group, ie gives existing user sudo povers.

Yes i did try that but with no luck..

As far as i can see here (my comp) i got root when i booted in recovery mode. Cos i got to add users. 
But when im back in GUI I dont have root rights any more. (this sucks). I dont want to reinstall cos i had trouble with my wifi card (IPW 2200) and added something in a start up file. (I dont remember wich or what :( )
:confused: what to do

---

### Post by Karl Norway on 2007-01-02
Aliyanage;

the reply i get are:
 chmod: cannot access ' /user/local/bin/sudo ': no suchs file or directory

---

### Post by NGEvo on 2007-01-02
IF your in ROOT in Console, run "startx" that should get you somewhere, hopefully... but it might be different now, and BTW, thats VERY BAD... the Sudo directory MUST be there! It's necessary for >ahem< ADMINISTRATIVE RIGHTS.

Hmm, thats wierd, so this... when in root... (EDIT : READ LOWER!)

cd / (or \ if that doesn't work)

then

cd (oh crud,  I just remembered something)

isn't that supposed to be "usr" not "user"!?!?!?!?

try what Aliyanage said, again, with "usr" instead...

if not, say, and I will carry on saying what I was going to say.. lol

---

### Post by aliyanage on 2007-01-02
yes sorry, that was a mistake of mine

it's usr and NOT user

---

### Post by Karl Norway on 2007-01-02
I still get the same reply And its my bad cos i cant read properly (hihi)

---

### Post by jblebrun on 2007-01-02
> **Karl Norway said:**
> I still get the same reply And its my bad cos i cant read properly (hihi)

Karl, try this:

1. reboot into recovery mode
2. at the recovery mode prompt, type ** passwd root **
3. Set a root password (you could make it the same as your user password if you want)
4. Reboot into normal multi-user mode
5. Open up a terminal and just type ** su **
6. Enter the root password you created when prompted.

This won't fix your sudo problem, but it should at least give you a way to get root in multi-user mode so you don't have to keep rebooting to single-user (recovery) mode.

---

### Post by Karl Norway on 2007-01-03
> **jblebrun said:**
> Karl, try this:

1. reboot into recovery mode
2. at the recovery mode prompt, type ** passwd root **
3. Set a root password (you could make it the same as your user password if you want)
4. Reboot into normal multi-user mode
5. Open up a terminal and just type ** su **
6. Enter the root password you created when prompted.

This won't fix your sudo problem, but it should at least give you a way to get root in multi-user mode so you don't have to keep rebooting to single-user (recovery) mode.

This dosent help with updates....

---

### Post by Karl Norway on 2007-01-03
I have found the easiest fix ever :D :KS 

I've installed Edgy :KS

---

