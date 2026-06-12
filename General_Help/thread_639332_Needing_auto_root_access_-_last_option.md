---
title: "Needing auto root access - last option"
date: 2007-12-13
forum: General Help
---

### Post by elix1r on 2007-12-13
Hi, I decided to install ubuntu 3 days ago and I must say wow linux has changed so much.
In the last 3 days I have managed fairly well by googling all my problems, but there is one problem I can not fix and It seems my only option is to login as root instead of my user account "jason"

My problems is that I want my ubuntu to run a socat command when it loads up, I've tried adding a script with my socat command into init.d and linking it to the rcS.d but that turned out to be a total failure. I've discovered that setting up my script to run in /System/Preference/Sessons is the best way.

I have set my script /home/jason/socatstart.sh to be an excutable already.

Upon restarting my PC, everything goes well, even the socat command runs file, "However" when I try to run an application that requires socat I get the following error message and my application is then disconnected from the internet. the error message I get is "#!/bin/bashE initgroups(nobody, 65534): Operation not permitted"

Upon further investigations I have discovered that socat isn't fully functional because my user account doesn't have root privileges. By using Terminal and running the command "sudo /home/jason/socatstart.sh" socat runs fine and all applications that depend on it work fine.

One thing to note is that I have tried to edit the /etc/passwd file and changed the value next to my username to 0. after editing the passwd file and rebooting I was presented with an error message and also an annoying popup message saying I am about to log into a privileged user and that it wasn't safe, and it hangs on loading up the desktop until I press ok or quit.

So now my only options is to auto login to root, because the script runs fine without any access denied problems. I would love to have more options but I'm really stuck, I am only a 3 day linux virgin so please help.

PS I've also tried visudo and added "jason ALL=NOPASSWD:/home/jason/socatstart.sh" but the script still won't work because it needs root access to run.

Finally, How do I make ubuntu-7.10-desktop-i386 automatically login to the root account? I know logging in as root is dangerous but I have no other way because socat won't work properly without me running it from root
I would also like to know how to make my script run with root privileges so that I don' have to login as root.

What I really need is a way to run my script as a root user, without me having to input my root password.

---

### Post by Lostincyberspace on 2007-12-13
You need to into Users and Groups and set your self to be in roots group. to make it auto login as root just go to login are and set the timed login or auto login then just type in root and put in the password,

---

### Post by elix1r on 2007-12-13
Ive checked my groups and I am in the root group, also when I goto loginwindow preference then security and under enable auto login, I type in root but it presents an error message saying "Autologin to root account is forbidden"

---

### Post by r-mo on 2007-12-13
To login as root, 
1) go to System->Administration->Login Window
2) On the security tab, tick the box for Allow Local System Administrator Login

I think the init.d route is really the way to go on this though.  You really shouldn't be logging as root, there must be another way.

---

### Post by elix1r on 2007-12-13
OK I ticked the "Allow local system administrator login" but still when I type in root under Enable automatic login, I get the same error message ""Autologin to root account is forbidden"

---

### Post by daengbo on 2007-12-13
Warning! This is DANGEROUS!!! (But less so than logging in as root...)
in a terminal, type:
sudo visudo

Find the following lines:
...
# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL
...

and change them to this:
...
# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL
...

Next, change your startup commad to begin with sudo. You should be in business.

I cannot stress how dangerous this is. You will be able to get root without a password. If anyone can pass a command through an application using a remote exploit, they own your box. You should really look into trying to use the system startup scripts.

p.s.
A final idea -- you could start your program with 
gksudo /home/jason/socatstart.sh
in sessions and you would have to input your password again when you login, but everything should work. That's a much better choice than giving yourself passwordless root.

---

