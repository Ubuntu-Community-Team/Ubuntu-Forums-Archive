---
title: "Can someone clarify GUI file/folder copying vs cli? Gui does not allow this at times?"
date: 2016-01-02
forum: General Help
---

### Post by Elishasmantle on 2016-01-02
Hello,

I'm confused at the copying via gui and copying via cli.

It seems inconsistent to me.
Sometimes I can do a copy / paste using gui, other times the paste option is not available on the folder I go to?
are there some type of permissions issues, or because where I am copying it deems it a critical folder?
I'm confused at the apparent rules and how linux works.

Thank You,

Elishasmantle

---

### Post by matt_symes on 2016-01-02
Hi

You should only be able to write to your home folder and sub folders by default.

You need elevated privileges to write anywhere else unless you change the folders permissions.

Kind regards

---

### Post by oldos2er on 2016-01-02
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by grahammechanical on 2016-01-02
Imagine the situation where you allow other people to use the machine. You may set them up with their own account complete with a login password. You would not want them to mess with system configuration files and break the OS. Would you? Ubuntu stops that from happening.

When we install Ubuntu we set a password. We then become both a standard user and an administrator. From the moment we log in we work as standard user and we are not allowed to edit system files or even paste into system folders. To do that we need to be working as the administrator.

Have you seen posts on this forum where people suggest running certain commands that have the word "sudo" at the beginning of the command? The word "sudo" prompts the OS to insist that we enter our user password. Then we become Administrator but our power as Administrator is time limited. Then we revert back to being a standard user once again.

So, even if you let someone use your computer without their having their own account they cannot mess with the OS unless you have been careless with your user password.

Oh, it is possible to run the file manager and a text editor as administrator. But we would need to load the utility from the command line and prefix the command with "sudo."

Regards.

---

### Post by Elishasmantle on 2016-01-02
Hello,

Thanks for the info and the links. I'll read up on the file permissions. Sorry, still real new. 20 year Windows user here. 
I think I am going to start using help.ubuntu.com a lot more. They seem to have good, clear accurate and non-confusing documentation. I find many other types of linux/unix docs confusing. KUDOS!! To UBUNTU for their good documentation. I set-up a Samaba share off one of their documents without a hitch. I was very happy about that.

I'll mark my post resolved.

---

### Post by coldraven on 2016-01-03
Look in /home and you will see your home folder. If you create another user called Alice then Alice's home folder will also appear there. When Alice is logged in she will not be able to read or write to files in your home folder (with the exception of the folder Public) or any system folder. 
If you wanted Alice to share some files you could create a folder, say /home/elisha/MyProject and give Alice read/write permissions. Then as administrator create a link to MyProject in Alice's home folder. To Alice it will appear that that MyProject exists in her home folder.
Also remember that hidden config files and folders are in your home folder. A hidden file/folder name has a period (.) in front of it. To see them in nautilus either press Ctrl+H or View>Show hidden files.

---

### Post by Elishasmantle on 2016-01-06
Thank you all for your replies. I'll consider this issue resolved.

elishasmantle

---

