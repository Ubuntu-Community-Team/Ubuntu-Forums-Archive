---
title: "Permissions issue"
date: 2008-01-11
forum: General Help
---

### Post by Unknownz on 2008-01-11
Hello,

I have searched in the forums and the similar threads suggested don't help. The thing is I am quite annoyed by the fact that I can't even edit files inside the file system, even though I am an administrator, it gives me the error:

Could not save the file blah blah blah
You do not have the perYou do not have the permissions necessary to save the file.missions necessary to save the file.

I have to use the terminal, and sudo gedit writethefullpathtoanobscurefileineedchangingthenthenameofthefile, which then let's me save, but the path is long, and I much prefer simply opening it in my UI.

Also, I hate having to sudo everything while I work, it's like Vista asking to confirm or cancel my every move. But in Vista I figured out how to disable it, but I'm still stuck in Ubuntu.

I don't want to login as root, but I want my current user to have total root access, so as to not be bothered sudoing or entering the password every time I want to do something. I tried system -> users and groups, but nothing hapened.

Sorry if my post seems like a rant or something, it's not, I like explaining in details, to make it clear :)

---

### Post by reckless2k2 on 2008-01-11
[http://sial.org/howto/sudo/](http://sial.org/howto/sudo/)

that link shows you how to edit the sudoers file to make your user and the admin user/group require no passwords when using sudo. you will still have to use sudo though but you just won't be prompted for a password. 

that being said, it is not recommended and creates security issues. if you're coming from windows and don't understand permission or the impact of them then it can be confusing or even "bothersome" getting adjusted. 

to completely circumvent the situation you could run as root and then you won't have a problem. again, that is a security issue that is well documented. 

understanding permissions does take some patience and time depending on what you are trying to do especially coming from a windows world. mac users tend to understand all of this much better because mac is built on unix and have similar responses to editing certain files or installing software. 

it really just requires a change in thinking. ubuntu or even linux for that matter is not a "windows" alternative. it is an operating system unto itself.

---

### Post by schaumkeks on 2008-01-11
> **Unknownz said:**
> I have searched in the forums and the similar threads suggested don't help. The thing is I am quite annoyed by the fact that I can't even edit files inside the file system, even though I am an administrator, it gives me the error:

Could not save the file blah blah blah
You do not have the perYou do not have the permissions necessary to save the file.missions necessary to save the file.


What do you mean with "files in the filesystem"? Nearly all files that are not located in the /home directory should only be writable by root or other system-users, but those shouldn't be changed for everyday work. Do you have an example?

Bye, Sven

---

### Post by oldos2er on 2008-01-11
"I have to use the terminal, and sudo gedit writethefullpathtoanobscurefileineedchangingthenth enameofthefile, which then let's me save, but the path is long, and I much prefer simply opening it in my UI."

 So type in "gksudo gedit" and open the file from gedit's menu. Or, install nautilus-gksu, then simply right-click on the file you want to edit and choose 'Open as Administrator.'

---

### Post by kr152ta on 2008-01-11
Where are these files located? Maybe the carrying block device is not mounted properly. Check fstab.

---

### Post by chrisccoulson on 2008-01-11
> **Unknownz said:**
> I have to use the terminal, and sudo gedit writethefullpathtoanobscurefileineedchangingthenthenameofthefile, which then let's me save, but the path is long, and I much prefer simply opening it in my UI.


As a tip, when typing long path names in the terminal, use the TAB key to autocomplete.

> **Unknownz said:**
> Also, I hate having to sudo everything while I work, it's like Vista asking to confirm or cancel my every move. But in Vista I figured out how to disable it, but I'm still stuck in Ubuntu.

First of all, you shouldn't have to be 'sudo'ing everything' as you work. The only times I have to use sudo, is if I'm making changes to the system, which I don't do when I work.

> **Unknownz said:**
> I don't want to login as root, but I want my current user to have total root access, so as to not be bothered sudoing or entering the password every time I want to do something. I tried system -> users and groups, but nothing hapened.

You may as well just log in as root then, which is strongly discouraged.

Also, I strongly discourage messing about with permissions in any of the system folders, unless you really know what you're doing. If you search the forums, you'll find posts by other users who have borked their systems doing this. As an example, another user recently did a recursive chown on /usr, which screwed up the permissions to the sudo binary and broke sudo completely. ****DON'T DO IT!!****

For your information, you can disable the password prompt with sudo - again, highly unrecommended. You can do:
```
sudo visudo
```
Then change the line that looks like this:
```
%admin  ALL=(ALL) ALL
```
to this:
```
%admin  ALL=NOPASSWD: ALL
```

You've been warned though. I wouldn't recommend anybody did this, and **I take no responsibility for you breaking your system**

---

