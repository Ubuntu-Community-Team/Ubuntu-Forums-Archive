---
title: "Editing sudoers to allow priviliges without using sudo"
date: 2022-09-29
forum: General Help
---

### Post by raleigh3 on 2022-09-29
I want to run privileged commands with having to enter my password.

I used visudo and edited sudoers.

But I still have to enter my password?

```
# User privilege specification
root    ALL=(ALL:ALL) ALL

andy ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
andy ALL=(ALL) NOPASSWD: ALL


```

---

### Post by Tadaen_Sylvermane on 2022-09-29
The way config files seem to work is from the top down. It will parse the file then stop when a line matches a given circumstance. I'm not 100% but commenting out the first iteration of andy should make it work. Make sure you can undo this if it fails with a live boot or creating a backup user with sudo access before making the change.

---

### Post by grahammechanical on 2022-09-29
A dated community document states this:

> **By default, the root account password is locked in Ubuntu.** This means that you cannot login as root directly or use the su command to become the root user.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I think that situation still exists. If if it was possible to unlock the root account I think it would be against Forum policy for anyone to explain how to do it. 

Regards

---

### Post by #&amp;thj^% on 2022-09-29
> **grahammechanical said:**
> A dated community document states this:



[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I think that situation still exists. If if it was possible to unlock the root account I think it would be against Forum policy for anyone to explain how to do it. 

Regards
I'm not sure it's against Forum policy, we just shouldn't put the bullet in the gun to shoot our-self or others critically..  
But I still use it from time to time, ***knowing I have the power to Nuke my entire set-up***
Also I love the new Warning:
> March 14, 2019 PLEASE NOTE: This wiki article is being significanly rewritten as it contains a good deal of old, dated and possibly questionable material. Using caution and consulting with others on the Ubuntu Forums or Ask Ubuntu is highly recommended!

---

### Post by raleigh3 on 2022-09-29
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

```
I think that situation still exists. If if it was possible to unlock the root account I think it would be against Forum policy for anyone to explain how to do it.
```

Thanks for the article.

---

### Post by raleigh3 on 2022-09-29
When I run this, it opens it without asking for a password.

```
sudo synaptic-pkexec

```
Then I tried this.

```
sudo gparted
Unit -.mount does not exist, proceeding anyway.
======================
libparted : 3.2
======================
```

And it opened gparted without requiring a password.

Did my changes to sudoers suceed?

---

### Post by grahammechanical on 2022-09-29
Reading through that old community document I found this warning:

> **Please keep in mind, a substantial number of Ubuntu users are new to Linux.**  There is a learning curve associated with any OS and many new users try  to take shortcuts by enabling the root account, logging in as root, and  changing ownership of system files. 

Example: [Broken system via (ab)use of root by a new user]("http://ubuntuforums.org/showthread.php?t=1877557") 

Please  note: At the time of the post, this was the users' first post on the  Ubuntu forums. While some might call this a "learning experience",  learning by breaking your system is frustrating and can result in data  loss. 

When  giving advice on the Ubuntu Forums and IRC, please take the time to  teach "the basics" such as ownership, permissions, and how to use sudo /  gksu / kdesudo in such a way that new users do not break systems.

In the past I have installed distributions that offer both a User account and a Root account. I have logged in as Root to make some system changes and then fell into the trap of continuing to work as the root user. That is a very risky way of working. I am just a home user. Imagine an IT administrator doing that in a business environment. 

Regards

---

### Post by grahammechanical on 2022-09-29
> Did my changes to sudoers suceed?

I am not sure but please note this about pkxec.

> [pkexec]("https://manpages.ubuntu.com/manpages/focal/en/man1/pkexec.1.html") is a similar command to [sudo]("https://manpages.ubuntu.com/manpages/focal/en/man8/sudo.8.html"), which enables you to run a command as root. If you run pkexec  in a graphical session, it will pop up a dialog box, but if you run it  in a text-mode session such as SSH then it starts its own text-mode  authentication agent:

[https://github.blog/2021-06-10-privilege-escalation-polkit-root-on-linux-with-bug/](https://github.blog/2021-06-10-privilege-escalation-polkit-root-on-linux-with-bug/)

It is starting to get interesting. Is it not?

Edit: When pkxec/polkit was first introduced into Ubuntu I did a little amature investigation. If we go to /usr/share/polkit-1/actions we will see policy documents that are used by pkxec to trigger polkit to produce a request for authentication. These documents are html files and can be viewed in a web browser. They can also be edited to remove the need to request authentication. We can copy the style of these documents to force a request for authentication for any application we desire.

This is not the same as unlocking the Root account. It gives a user a little bit of control but should be used carefully.

Regards

---

### Post by HermanAB on 2022-09-30
Best is to get used to typing your password. On Windows systems you are  forever running virus scans.  On UNIX systems you are forever typing passwords.  Typing passwords is rather less troublesome.

---

