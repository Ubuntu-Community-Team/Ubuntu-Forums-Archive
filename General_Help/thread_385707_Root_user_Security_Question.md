---
title: "Root user Security Question"
date: 2007-03-16
forum: General Help
---

### Post by mmilitia9 on 2007-03-16
This website says this:

*"Root Account Disabled by Default: This may not seem like a big deal but it is a huge deal when it comes to security. Ubuntu functions so that the user created during installation is part of the sudo users group and can do root user tasks once authenticated. This means that any Ubuntu computer effectively has a different root user name and since root is the most attacked account on a Linux box, the Ubuntu computer becomes very secure for not having this account enabled by default."*

What does that mean?  No root needed?   I thought by having a root user and 2 multiple users is the safest bet?  When I was on Mandrake they said the best thing to do for that distro was like... Surf the web with one of the usersnames and login to the root to do your admin work.  Am I wrong?  Can someone break down that paragraph for me?

Thanks,

Dominick

---

### Post by aysiu on 2007-03-16
Sure. I'll break it down for you.

To log in, you basically have two things--a username and a password.

To breach security, it helps a cracker to know your username and your password.

In most traditional Linux setups, there is a root user. The cracker knows straight away that there is a user named *root* (username known) and also that that username has root privileges and can do anything on the computer. So the only thing left is the root password.

In Ubuntu, there is no root user. There are only regular users. Those users could be any username. And any of those users could be administrators... or not. Just by knowing the name of the user (Jane, Bob, Ozymandias), you can't tell what privileges that user has. So you have to guess or figure out the username, and even after that and figuring out the password... you still may have compromised an account that can't do anything to the entire system.

To break it down visually:
**Ubuntu**
Username needs guessing
User privilege level needs guessing
Password needs guessing

**Other Linux Distros**
Username doesn't need guessing (username is *root*)
User privilege doesn't need guessing (root has full privileges)
Password needs guessing

Now, while that increases security *somewhat*, all it does is put some obstacles in the way. If one account gets compromised, that's **really** bad--root account or not, administrative account or not. Also, if you have easy-to-guess passwords like *temp* or *abc123*, then it won't matter how secure the "security model" is because the implementation sucks.

Read more here:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by dreadlord_chris on 2007-03-17
OK, I'm a little confused now....

I keep reading people with lots of bean counters or Staff listed under their names saying:
> In Ubuntu, there is no root user.

There **is** a _root_ on my system. It was there when I installed Edgy, and it's here under Feisty. It's just *locked*, or disabled in Ubuntu parlance.

The way I understand the default Ubuntu security model in regards to accounts is: 
1. Accounts with no password set are denied **multi-user mode** login - runlevels 2, 3 and 5 (& maybe 6 not sure, is root allowed to reboot the machine or just shut it down?) - I tried setting up a normal user w/ no password, I was unable to log into a graphical shell with it.
2. The root account, though locked, is allowed **Single User** - runlevel 1 login, because of a [patched]("https://help.ubuntu.com/community/RootSudo#head-a76e0b38808fca380fa209babb080d60ffe0ec8e") sulogin program in Ubuntu. This allows the locked root account to log into the Recovery mode console to fix a fubar'd system.
3. Users that are part of the admin group, through sudo, are granted a subset of the root's privileges - this is configured through the file **/etc/sudoers**. Reference [here]("http://www.gratisoft.us/sudo/intro.html"). Thus allowing a level of fine-grained control over who can do what in a system.

Please correct me if I'm wrong...

---

### Post by aysiu on 2007-03-17
You're not wrong.

But, as far as a new user who's trying to log in as root (either through the GUI or using the *su* command in the terminal) is concerned, there is effectively no root user. Every time you see someone say "there is no root user," it's usually in response to someone frustrated who is trying to log in as root.

Of course there *is* a root user--it's just not enabled for login (with the one exception of recovery mode) by default. Knowing that doesn't help new users understand how to **use** their systems, since *sudo* is a part of regular use, and recovery mode is only for recovery.

---

### Post by Irony on 2007-03-17
aysiu, one thing that puzzles me is that in System > Administration > Users and Groups there is a root account with a root password, which looks like it can be set independently of my and other users passwords.

If I change my password what happens to the root password - I've changed my password several times, does the root user password remain the same or does it change when I change my password. And if I change the root password then change my password does this then negate the root password change and make it the same as my password... its a bit confusing.

---

### Post by dreadlord_chris on 2007-03-17
> **aysiu said:**
> You're not wrong.

But, as far as a new user who's trying to log in as root (either through the GUI or using the *su* command in the terminal) is concerned, there is effectively no root user. Every time you see someone say "there is no root user," it's usually in response to someone frustrated who is trying to log in as root.

Of course there *is* a root user--it's just not enabled for login (with the one exception of recovery mode) by default. Knowing that doesn't help new users understand how to **use** their systems, since *sudo* is a part of regular use, and recovery mode is only for recovery.

Sorry, didn't mean to sound snippy. It's just that I was one of those new users who, like Irony, opened up the user manager, and discovered there is a root account - and when you open the properties for root the little check-box next to disabled isn't checked. This led to my own independent research - leading to what I posted earlier.

It just seems more confusing to promote the misconseption that there is no root account...

.02

---

### Post by dreadlord_chris on 2007-03-17
> **Irony said:**
> aysiu, one thing that puzzles me is that in System > Administration > Users and Groups there is a root account with a root password, which looks like it can be set independently of my and other users passwords.

If I change my password what happens to the root password - I've changed my password several times, does the root user password remain the same or does it change when I change my password. And if I change the root password then change my password does this then negate the root password change and make it the same as my password... its a bit confusing.

Manually setting a password for root will effectively enable the account for full login - bypassing Ubuntu's built-in security policy that this thread has been discussing - and is therefor **not recommended**

If you change your password - your password changes. It will have no effect on root or any other account.

To clear things up about sudo a little more: when you type sudo <command> and it asks for a password - it's expecting **your** password not root's. If you enter the correct password & your account is listed in /etc/sudoers, then <command> is run with administrative privileges.

They probalby explain it better here: [http://www.gratisoft.us/sudo/intro.html](http://www.gratisoft.us/sudo/intro.html)

---

### Post by aysiu on 2007-03-17
Well, in addition to activating root by creating a password for it, you would also have to change your login manager (GDM or KDM) settings to allow a graphical root login. You would have to do something else (edit the /etc/sudoers file?) to have administrative programs (Synaptic Package Manager, Users and Groups, etc.) to ask for the root password instead of the sudo one.

There are a lot of hoops you have to jump through to change Ubuntu from a *sudo* model to a root one. It's not worth the effort, especially since the *sudo* model is faster in most cases than logging in separately as root.

---

### Post by Irony on 2007-03-18
So is the root password that shows up in User Accounts the same as my original user password?

My user password is different to what it was before, but is the root user account password the same as my original user password.

In other words if I did have to log in to recovery what is my root password?

---

### Post by tribaal on 2007-03-18
root password on a default Ubuntu install is a very strong random choice.

To have a root shell you can just ytpe "sudo su", and you'll have a "root terminal". 

- trib'

---

### Post by Irony on 2007-03-18
Yes but what is my root user account password?

---

### Post by dreadlord_chris on 2007-03-18
> **Irony said:**
> So is the root password that shows up in User Accounts the same as my original user password?

My user password is different to what it was before, but is the root user account password the same as my original user password.

In other words if I did have to log in to recovery what is my root password?

As stated before - your root account & your normal user account are totally different. Changing the password (or anything else for that matter) on one will have no effect on the other.

As long as you haven't actually set a password for root - when you boot into recovery you go straight into root, no password necessary.

and remember, when you sudo - it expects the password for the account you are logged in to - not roots

---

### Post by aysiu on 2007-03-18
> **Irony said:**
> So is the root password that shows up in User Accounts the same as my original user password?

My user password is different to what it was before, but is the root user account password the same as my original user password.

In other words if I did have to log in to recovery what is my root password?
The root account password will only be the same as your original user password if you make it the same. That is, you change your user password to *blahblahblah* and then separately change your root password also to *blahblahblah*

Root is its own user with its own password and all privileges all the time. By default, in Ubuntu, it's password is unknowable. You can change the password to something knowable if you want.

Your user is its own user with its own password. If the user belongs to the *admin* group, it can temporarily assume administrative (or root) privileges with certain commands.

They are two separate users. 

In a default Ubuntu installation, you do not need to ever log in as root (except in recovery mode, and even that isn't a log in--you're basically just choosing a boot option). Your user can perform all the tasks you need to perform by temporarily assuming root privilege with the *sudo* or *gksudo* preface to commands. If you decide to make your root password the same as your user password, I **really** don't see the point in enabling the root account, since you're essentially replicating the *sudo* model (gain root privileges with a user password).

I'm not sure how else to explain it. Enabling a root login just complicates things in Ubuntu.

---

### Post by aysiu on 2007-03-18
> **Irony said:**
> Yes but what is my root user account password?
We don't know.

In a default Ubuntu installation, it's unknowable and completely irrelevant to functionality. You don't need it.

If you decide to change your root password to something **you** know, only you will know what you changed it to.

---

### Post by Irony on 2007-03-18
I assumed the root user account has a password because there are a bunch of asterisks in it under the users account.

I realise that one wouldn't normally use the root account (I never have). Having said that if I do sudo init 1 this takes me to a screen that says root@ubuntu, the same if I open the root terminal in system tools - I assume this isn't actually root?

---

### Post by dreadlord_chris on 2007-03-18
> **Irony said:**
> I assumed the root user account has a password because there are a bunch of asterisks in it under the users account.

I realise that one wouldn't normally use the root account (I never have). Having said that if I do sudo init 1 this takes me to a screen that says root@ubuntu, the same if I open the root terminal in system tools - I assume this isn't actually root?

Yup, it is actually root.

sudo init 1 puts you into single-user mode - basically the same as the recovery console. If there actually was a password set for root - you would be asked for it before being given a command prompt.

opening the root terminal from System Tools is equivalent entering **sudo -i** in a terminal - Now, if you've set a password for root, I'm really not sure what would happen. Since sudo expects
the password of the user issuing the command - but to log into root requires root's password...

hmmm... round & round....

all in all it's better to just leave root as default - locked w/out a password

---

