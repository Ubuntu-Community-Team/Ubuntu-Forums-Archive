---
title: "Root log in"
date: 2007-08-02
forum: General Help
---

### Post by doctorbrowder on 2007-08-02
Question about logging in as "root". I don't remember having set a password for logging in as root. I have my regular log in ("password1", let's say), but I don't think I ever set a log in for the root. When I try to go to the terminal and log in as root at the 'su' prompt, it says "log in failure" when I use the "password1" as the log in password.

So, how do I find out my root log in password if I never set one?

---

### Post by Sunforge on 2007-08-02
As far as I know Ubuntu doens't have the root password set. The preference is to use the "sudo" command to execute commands as root. When you execute the sudo command you have a five minute grace period (I think) where you are a root user.

If you need to log in as root you have to open a command prompt and type:

sudo passwd root

You can then type in the password you want. It's best to have a separate password for root.

If you want to install or run something as root using your normal account remember that you can type "sudo" and then the command you wish to run as root, for example:

sudo gedit /etc/X11/xorg.conf

This command would open xorg.conf in gedit so that you can mess with your screen settings.

If you create a password for root and log in as root, your Gnome/KDE/whatever session will have root windows and displays which look different to a normal users display. I've never bothered to find out why.

Since this is the Ubuntu forum, I'm sure you'll get buried under replies and corrections in due course :-P

---

### Post by Steve1961 on 2007-08-02
In Ubuntu there isn't a root user password by default as sudo is used for admin tasks.  If you really want to set a root password just type sudo passwd root

---

### Post by sdowney717 on 2007-08-02
you can create a gui root login.

system admin users and groups to setup root user 

then 

system admin login window, click security tab to allow root login

---

### Post by Seisen on 2007-08-02
I wouldn't recommend using root unless absolutely necessary. The first thing a cracker does is scan for the root user because they know with that user they have full control of your computer if they can get your password. Sudo basically does everything that the root user can do without having to worry.

---

### Post by sdowney717 on 2007-08-02
yes well just how are they going to get the root password?

I thought the problem was if you are logged in as root, you could inadvertantly destroy your filesystem.

Can a hacker, if he does not have the root password and you are logged in as root do anything at all remotely to your system?

---

### Post by aysiu on 2007-08-02
Read these links:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by sdowney717 on 2007-08-03
it interesting to note that the ubuntu docs link does not mention that you can create a root login to the gui desktop  and very easy to do as well.

Also, I came over from fedora in which a root login to the gui desktop is automatically available.
How many distros dont configure a root login automatically?

If you want to simply use the gui to edit root files without opening a terminal and typing sudo gedit etc...., or ever try to copy these files from one place to another without the gui file manager is a pain.

---

### Post by aysiu on 2007-08-03
Well, you don't have to constantly type ```
gksudo nautilus
``` Just make a launcher for it and you can click on that icon every time you want to edit as root through the GUI. Not as much of a pain as logging into a separate account every time you want to make a change.

---

