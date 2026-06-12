---
title: "Checking integraty of book - Root and sudoers question"
date: 2019-05-02
forum: General Help
---

### Post by wavestar on 2019-05-02
Hello, I'm actually a Debian user, but my A+ book uses ubuntu in their example, and I wanted to verify the accuracy of their statements. I've found many errors in these Sybex books.



[COLOR=#696969]_**Firstly**_[/COLOR]
The book says, "[COLOR=#ff0000]*In some distos, such as Ubuntu, you must use the sudo command because you don't get to set up a root user when you install.*" The book then goes onto say, "*If you are listed as an authorized user in the sudoers file, sudo executes the command.*[/COLOR]"
The problem I have with this is, you need to be root to add a user to the sudoers file to give sudo it's power. Is this not so? I'm not new to adding users to the sudoers file, but how can a standard user add someone if there is no root account on the system?



[COLOR=#696969]_**The second question**_[/COLOR] is, the book says, "[COLOR=#ff0000]*if you enter **su** without any arguments, it starts a new shell, but if you enter **su -** (with the hyphen), before your command you _stay_ in the same shell.*[/COLOR]" Is this true?


[COLOR=#696969]_**Lastly**_[/COLOR] they are saying that, "[COLOR=#ff0000]*when you run sudo, you're running as another user, usually root*[/COLOR]." But I would say, sudo is more of an elevated power user, It's NOT as powerful as root unless the root user gives a sudo user full power.



Thank you.

---

### Post by sisco311 on 2019-05-03
> **wavestar said:**
> Hello, I'm actually a Debian user, but my A+ book uses ubuntu in their example, and I wanted to verify the accuracy of their statements. I've found many errors in these Sybex books.



[COLOR=#696969]_**Firstly**_[/COLOR]
The book says, "[COLOR=#ff0000]*In some distos, such as Ubuntu, you must use the sudo command because you don't get to set up a root user when you install.*" The book then goes onto say, "*If you are listed as an authorized user in the sudoers file, sudo executes the command.*[/COLOR]"
The problem I have with this is, you need to be root to add a user to the sudoers file to give sudo it's power. Is this not so? I'm not new to adding users to the sudoers file, but how can a standard user add someone if there is no root account on the system?


I see why this statement is  a little bit misleading. What the author wants to say is that during installation you are not prompted to set up a root password. The root account is ("created" and) configured in a very similar way like in any other major distros. The difference is that the root account password is locked. 

If you check out the /etc/shadow file you will see an exclamation mark (!) in the place of the encrypted password. This is a very common way to lock a user's **password**. 

This simply means that you can't use a password to authenticate as root. The account is not disabled!

From man passwd:
```

       -l, --lock
           Lock the password of the named account. This option disables a
           password by changing it to a value which matches no possible
           encrypted value (it adds a '!' at the beginning of the password).

           Note that this does not disable the account. The user may still be
           able to login using another authentication token (e.g. an SSH key).
           To disable the account, administrators should use usermod
           --expiredate 1 (this set the account's expire date to Jan 2, 1970).

           Users with a locked password are not allowed to change their
           password.

```

If you check out the default sudoers file you will see that users from the admin and sudo groups are allowed to run any command as another user or root. The first user created during installation is added automatically to the admin group. In this way, it has full sudo rights.

> **wavestar said:**
> 
[COLOR=#696969]_**The second question**_[/COLOR] is, the book says, "[COLOR=#ff0000]*if you enter **su** without any arguments, it starts a new shell, but if you enter **su -** (with the hyphen), before your command you _stay_ in the same shell.*[/COLOR]" Is this true?


I don't understand this statement. What command they are talking about? :confused: 

The man page of su is very clear. su starts an interactive shell and su - a login shell. 

> **wavestar said:**
> 
[COLOR=#696969]_**Lastly**_[/COLOR] they are saying that, "[COLOR=#ff0000]*when you run sudo, you're running as another user, usually root*[/COLOR]." But I would say, sudo is more of an elevated power user, It's NOT as powerful as root unless the root user gives a sudo user full power.



Both sudo and su are setuid root applications. They allow a specific set of users to run a command or shell as another user or root. The main difference is that by default sudo asks for the invoking user's password and su prompts you for the target user's password. 

For more details please check out: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TheFu on 2019-05-03
> **wavestar said:**
> Hello, I'm actually a Debian user, but my A+ book uses ubuntu in their example, and I wanted to verify the accuracy of their statements. I've found many errors in these Sybex books.

> **wavestar said:**
> [COLOR=#696969]_**Firstly**_[/COLOR]
The book says, "[COLOR=#ff0000]*In some distos, such as Ubuntu, you must use the sudo command because you don't get to set up a root user when you install.*" The book then goes onto say, "*If you are listed as an authorized user in the sudoers file, sudo executes the command.*[/COLOR]"
The problem I have with this is, you need to be root to add a user to the sudoers file to give sudo it's power. Is this not so? I'm not new to adding users to the sudoers file, but how can a standard user add someone if there is no root account on the system?
During installations, a userid is created. This account is in the 'sudo' group, which provides it with sudo access.  Use the **sudo visudo** command to edit the sudoers file.

> **wavestar said:**
> [COLOR=#696969]_**The second question**_[/COLOR] is, the book says, "[COLOR=#ff0000]*if you enter **su** without any arguments, it starts a new shell, but if you enter **su -** (with the hyphen), before your command you _stay_ in the same shell.*[/COLOR]" Is this true?
This isn't correct.  Both su and su - will create a new shell. What is different is whether the current environments is inherited (joe-user) or if the minimal root environment gets created from the /root/.profile and ~root/.bashrc files.
On systems which use sudo, it is preferred to use
```
* sudo -i <---- su -
* sudo -s <---- su
```

There are dangers in using sudo -s or su then attempting to run GUI programs.  Don't to that.

> **wavestar said:**
> [COLOR=#696969]_**Lastly**_[/COLOR] they are saying that, "[COLOR=#ff0000]*when you run sudo, you're running as another user, usually root*[/COLOR]." But I would say, sudo is more of an elevated power user, It's NOT as powerful as root unless the root user gives a sudo user full power.

Thank you.
When sudo is used without specifying another userid, by default, it runs with the effective userid of root. There is no difference between using sudo and being root.
It is possible to configure limited sudo access for specific commands only, to specific users. This makes sudo much more powerful than root, by far. With root, there aren't any methods to limit access. With sudo, we can allow joe to view log files that he might never be able to view, but not view other log files.  With sudo, amy can be allowed to remove any core* files from the system, but do nothing else.  We can setup netgroups or nisgroups and place thousands of users into a single group to allow all those userids to run 1 specific program with 5 specific options, but not give them access to any root permissions at all.  That is what I call power.  Giving end users root to do 1 thing breaks all sorts of security principles.  End users already have huge amounts of power on any Unix system.  With sudo, we can allow extra security access, that is always logged, tied back to the original userid, for only the specific tools, options, and needs required to perform their tasks.

1 more thing - use **sudoedit** to edit most system files.  **sudoedit /etc/hosts**, for example. There are only a few files, sudoers and crontabs, which require using special tools to edit.  sudoedit honors the EDITOR environment variable, so you can choose whatever editor you prefer and it will be safe. Much safer than giving **sudo nano** or **sudo vim** access to other people. Most Unix editors have a way to launch a shell. If the editor is running using sudo, you've just provided a root shell.  With sudoedit, that isn't possible, since the editor runs as the normal userid, copying files in and out of the system area, setting permissions and ownership, as necessary.  Anyway, much safer.

And don't use sudo with GUI programs.

---

### Post by wavestar on 2019-05-06
Let me try to respond to one post at a time, this is a lot to multi quote and I'm having formatting issues on this forum.

> **sisco311 said:**
> I see why this statement is  a little bit misleading. What the author wants to say is that during installation you are not prompted to set up a root password. The root account is ("created" and) configured in a very similar way like in any other major distros. The difference is that the root account password is locked. 
I don't think the author even knows. This Sybex book is very vague in a lot of things. I find mistakes all the time.

Its makes sense what you said about the account being locked. It's just strange to me because I'm still trying to figure it all out. In Debian, you're prompted for a root and user password during the install of the OS. And I can't do anything with sudo until I add my user in sudoers. The file looks like this:

[B]      # User privilege specification
root[COLOR=#ffffff]                  .......[/COLOR]ALL=(ALL:ALL) ALL
user [/B]**[B][COLOR=#ffffff]                  ......[/COLOR]**                ALL=(ALL:ALL) ALL  [COLOR=#ff0000]<--- I added this line[/COLOR]

                  # Allow members of group sudo to execute any command
%sudo [/B]**[B][COLOR=#ffffff]                  ....[/COLOR]**              ALL=(ALL:ALL) ALL
[/B]



> **sisco311 said:**
> If you check out the /etc/shadow file you will see an exclamation mark (!) in the place of the encrypted password. This is a very common way to lock a user's **password**. 

This simply means that you can't use a password to authenticate as root. The account is not disabled! 
I did look in the shadow file, I don't have exclamation marks (!), I have astrics (*) But I did see the long encrypted password even though debian supports a root password. But The first user created during installation is not automatically added.
I did look in the shadow file, I don't have exclamation marks (!), I have astrics (*) But I did see the long encrypted password even though debian supports a root password. But The first user created during installation is not automatically added to the admin group from what I'm seeing. I have to add **user name     ALL=(ALL:ALL) ALL **For that user to be able to run sudo.

> **sisco311 said:**
> From man passwd:
```

[COLOR=#a9a9a9]       -l, --lock
           Lock the password of the named account. This option disables a
           password by changing it to a value which matches no possible
           encrypted value (it adds a '!' at the beginning of the password).

           Note that this does not disable the account. The user may still be
           able to login using another authentication token (e.g. an SSH key).
           To disable the account, administrators should use usermod
           --expiredate 1 (this set the account's expire date to Jan 2, 1970).

           Users with a locked password are not allowed to change their
           password.[/COLOR]

```

I got lost on this
I'm still reading through this post. I've always struggled understanding the man pages, and how they format things. I've been reading multiple tutorials on understanding the syntax, but I always run into something that is not clear, though I'm getting better. I have a book with laminated pages when I figure something out I add it. I need more time to look over this post. I just respond because I didn't want to keep you guys waiting.

---

