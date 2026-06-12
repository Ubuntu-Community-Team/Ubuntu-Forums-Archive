---
title: "Running Ubuntu as Limited User"
date: 2015-11-14
forum: General Help
---

### Post by Richard_Romick on 2015-11-14
I have heard quite a bit that, in Windows, I should be running as a limited user.  Should I do the same thing in Ubuntu?  For a while I have been running as a limited user, but having to su to another account, enter a password, then run a command with sudo and have to enter another password was too much of a hassle.

---

### Post by ian-weisser on 2015-11-14
I think your Windows security experience is hampering you in Ubuntu.
Most of your questions should be answered by [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by yancek on 2015-11-14
If typing a password is too much of a hassle for you, then do the rest of the computer world a favor and stay off the internet.

---

### Post by Richard_Romick on 2015-11-14
> **yancek said:**
> If typing a password is too much of a hassle for you, then do the rest of the computer world a favor and stay off the internet.

The hassle is having to enter the password twice.  While not a huge hurdle, it would be nice to remove this extra step performed often if it is not needed.

---

### Post by Richard_Romick on 2015-11-14
> **ian-weisser said:**
> I think your Windows security experience is hampering you in Ubuntu.
Most of your questions should be answered by [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

From that document: "Learn how to use file permissions and non-privileged users (which Ubuntu makes very easy)."

Wouldn't a non-privalaged user be one not in the admin group, and by extension someone without sudo privileges?

---

### Post by grahammechanical on 2015-11-14
I would say that it is standard in Ubuntu for users to work as a standard user or limited as you might call it.

When I or anyone else who may get access to my machine tries to do something that only an administrator can do, then all I need to do is enter my password just once to authorise the action. But notice, any other person accessing my computer would not know my password and would not be able to authorise the task = security with convenience = the usual way of working in Ubuntu.

If I wish to edit system configuration files I prefix the command to load the text editor with sudo and I am then required to authorise the action with my password. But I only do it once. In both cases we are only required to enter the password once and then  when the task is complete our authorisation expires and we are back as a  standard user. It is very risky to run a computer operating system as an administrator (or root as it is called in Linux). And it is not necessary in Ubuntu and not easy to do either.

I think that in trying to use Ubuntu according to the methods of Microsoft you have made things more complicated for yourself.

---

### Post by mc4man on 2015-11-15
> **Richard_Romick said:**
> From that document: "Learn how to use file permissions and non-privileged users (which Ubuntu makes very easy)."

Wouldn't a non-privalaged user be one not in the admin group, and by extension someone without sudo privileges?
Yeah, if that describes you then there is usually no good reason for *you * not to be in the admin group.
(Unless you think you need protection from yourself

---

### Post by Richard_Romick on 2015-11-15
> **grahammechanical said:**
> I would say that it is standard in Ubuntu for users to work as a standard user or limited as you might call it.

When I or anyone else who may get access to my machine tries to do something that only an administrator can do, then all I need to do is enter my password just once to authorise the action. But notice, any other person accessing my computer would not know my password and would not be able to authorise the task = security with convenience = the usual way of working in Ubuntu.

If I wish to edit system configuration files I prefix the command to load the text editor with sudo and I am then required to authorise the action with my password. But I only do it once. In both cases we are only required to enter the password once and then  when the task is complete our authorisation expires and we are back as a  standard user. It is very risky to run a computer operating system as an administrator (or root as it is called in Linux). And it is not necessary in Ubuntu and not easy to do either.

I think that in trying to use Ubuntu according to the methods of Microsoft you have made things more complicated for yourself.

Not to belabour the point, but I want to clarify the threat I am thinking of.  What you said makes perfect sense for someone at the system or a malicious attack trying to gain admin privileges.  What about a privilege escalation attack?  I have heard of such attacks on Linux though Flash vulnerabilities (I do restrict running Flash in my browser btw).  Would a privilege escalation attack be possible against a user with sudo privileges and not possible against someone who does not have sudo privileges?  Sorry if I don't get the nomenclature right.

---

### Post by ian-weisser on 2015-11-15
A privilege escalation attack is possible against both admin and non-admin users. The specific method of attack may work for one or the other...or both.

---

### Post by Richard_Romick on 2015-11-16
> **ian-weisser said:**
> A privilege escalation attack is possible against both admin and non-admin users. The specific method of attack may work for one or the other...or both.

Thanks, I learned something today.

Since it is recommended that Windows users not run as admin, but it seems that it doesn't matter in Linux, Sudo must be better security than UAC (which wouldn't surprise me at all)

---

### Post by ian-weisser on 2015-11-16
The mirror in Linux is to not run as Root, unless you are doing Root activities.
That's one reason why login to the Root account is disabled in Ubuntu.

Good security is often not about one tool being better or worse than another. It's about understanding any tool's limitations and using it properly.

---

