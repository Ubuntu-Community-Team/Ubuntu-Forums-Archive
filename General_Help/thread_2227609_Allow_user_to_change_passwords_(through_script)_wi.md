---
title: "Allow user to change passwords (through script) without sudo"
date: 2014-06-03
forum: General Help
---

### Post by thuizt on 2014-06-03
Hello,

We have a script that automatically creates users accounts. No user intervention required other than specifiying name and password for the new user.
We like to create an additional script that makes it possible to change passwords of the created accounts. So again run the script with username and new password only.

Any help appreciated.

---

### Post by SeijiSensei on 2014-06-03
Ordinary users can change their passwords with /usr/bin/passwd.  You can script around that.  

If you're running the script as root, you can use /usr/bin/passwd with the --stdin option.  You can then do something like
```
echo inputted_password | passwd --stdin username
```

---

### Post by thuizt on 2014-06-04
Hi, thanks for answering,

I'm afraid not completely what I'm looking for.
Users cannot access this machine other than through SFTP access so they cannot change passwords themselves.
Accounts are created by just starting a script with username and password as parameters and the account is created.
We now like to be able to do the same for password changes.
Fire a script, provide username and password and that's it. No sudo stuff needed.
The script to create users was arranged by adding it to sudoers. 
Like to do the same for changing password but somehow didn't succeed yet.

Any thoughts ?

---

### Post by SeijiSensei on 2014-06-05
Only the user herself and the root user can change a password.  Any other method would be insecure.  You can expand the number of people with root access by adding them to the "admin" or "sudo" groups as described in /etc/sudoers, but I'd err on the side of fewer people rather than more.  Personally, when it comes to network administration, I lean toward more "fascistic" policies where tasks like password changes are managed centrally by a small number of trusted and competent people.

It looks like the [version of passwd]("http://manpages.ubuntu.com/manpages/trusty/man1/passwd.1.html") that Ubuntu distributes doesn't support the "--stdin" command-line parameter I mentioned above.  I use RedHat-flavored distributions on servers which apparently have a [different version of the passwd program]("http://linux.die.net/man/1/passwd") that supports the --stdin switch.

One way I've enabled users to run administrative processes is to split the task into two parts. I've created PHP applications where a user can submit requests like password changes via a form online.  I have a second process running as root from /etc/crontab that checks for queued requests and executes them with root privileges.  The publicly-available PHP application writes a file with the request data into a queue directory.  The monitoring application looks for files in the designated location, processes them, then moves them to archival storage.

---

