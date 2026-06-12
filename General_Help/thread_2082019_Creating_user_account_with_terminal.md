---
title: "Creating user account with terminal?"
date: 2012-11-08
forum: General Help
---

### Post by Colo2 on 2012-11-08
Hey all

I need to know how to make a user account with terminal in a way that doesn't require human input.

So it could be multiple commands run in succession, but it can't be one command that does this:

User@PC~:$ command
Insert Username: XXXX
Insert Password: XXXX
Done!
User@PC~:$

if you understand what I'm saying :)

Tom

---

### Post by HiImTye on 2012-11-08
the best way is to use the *user accounts* tool, since it takes care of everything you need, such as groups and user files

---

### Post by Lars Noodén on 2012-11-08
The utility [useradd](http://manpages.ubuntu.com/manpages/precise/en/man8/useradd.8.html) can add users for you and is amenable to being in a script.  Check the manual page for the full list of options.

---

### Post by Colo2 on 2012-11-08
Hi 

Thanks for your response. 

In any other situation, that's what I'd do.

Problem is, this is for some software I'm designing, the ubuntu machine in question will be a server controlled by SSH.

UI is not an option.

Tom

---

### Post by Colo2 on 2012-11-08
> **Lars Noodén said:**
> The utility [useradd](http://manpages.ubuntu.com/manpages/precise/en/man8/useradd.8.html) can add users for you and is amenable to being in a script.  Check the manual page for the full list of options.

Hi, 

Thanks for your reply.

I will programatically be sending commands to the server in question.

So it needs to be able to do everything without any human interaction.

Tom

---

### Post by HiImTye on 2012-11-08
you can* ssh -X* to get windows, but otherwise, you can use the useradd command, as Lars pointed out. I generally prefer the *User Accounts* tool, because it's brainless, but in a pinch it's there

---

### Post by HiImTye on 2012-11-08
> **Colo2 said:**
> Hi, 

Thanks for your reply.

I will programatically be sending commands to the server in question.

So it needs to be able to do everything without any human interaction.

Tom
useradd accepts all fields you would set otherwise as a command argument, including password
 **```
****--password** _PASSWORD_            The encrypted password, as returned by **[crypt]("http://manpages.ubuntu.com/manpages/precise/en/man3/crypt.3.html")**(3). The default is to            disable the password.             **Note:** This option is not recommended because the password (or            encrypted password) will be visible by users listing the processes.             You should make sure the password respects the system's password            policy.
```

---

### Post by Colo2 on 2012-11-08
Ahhhh

Thanks, so it would be something like this?

> useradd -u USERNAME -p PASSWORD

??

And will that generate the home folder and stuff?

Tom

---

### Post by HiImTye on 2012-11-08
you need to use *-d HOMEDIR* to copy what's in */etc/skel/* but there's no guarantees it will have everything the user needs. you will also need to get the groups sorted yourself, though you can include them with [I]-G group, 2ndgroup, etc

[/I]edit: apparently you also need* -m* to actually copy the files from[I] /etc/skel/
[/I]

---

### Post by Lars Noodén on 2012-11-08
Here is a short script to generate the encrypted password that can then be passed on to [useradd](http://manpages.ubuntu.com/manpages/precise/en/man8/useradd.8.html):
[http://stackoverflow.com/questions/1020534/useradd-using-crypt-password-generation](http://stackoverflow.com/questions/1020534/useradd-using-crypt-password-generation)

---

