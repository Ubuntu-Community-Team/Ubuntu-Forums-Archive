---
title: "Ubuntu wipe a users profile on logout"
date: 2024-01-30
forum: General Help
---

### Post by clendee on 2024-01-30
Hi,

I want to set up Ubuntu on all our student computers in the classroom.
I'd like to have two accounts on each system, a user account and a student account.

I have customised the student account to look and behave the way I want.
I would like to completely replace the student account config files and wipe all student files on logout, so that when the next student logs in, they have a clean slate.

I have looked at the 'Guest' session capability but this does not meet my needs.  It also breaks with the Firefox snap, as a guest user cannot open Firefox.

How do I replace each students /home/student with a skeleton config on each login?

Many thanks.

---

### Post by ActionParsnip on 2024-01-30
This is one possibility
[https://askubuntu.com/questions/232401/delete-user-files-on-logout](https://askubuntu.com/questions/232401/delete-user-files-on-logout)

---

### Post by TheFu on 2024-01-30
I'd use the .logout file.
[https://bash.cyberciti.biz/guide/.bash_logout](https://bash.cyberciti.biz/guide/.bash_logout)

---

### Post by clendee on 2024-01-31
Hi, thanks for the repsonses.  

I used this method described here on stock Ubuntu 22.04

[https://devicetests.com/ubuntu-login-logout-script](https://devicetests.com/ubuntu-login-logout-script)
.bash_logout doesn't seem to be run when I log out of Gnome.
[COLOR=#a52a2a]
This is my attempt at creating a custom guest user account on Ubuntu.[/COLOR]

edit /etc/gdm3/PostSession/Default

if [$USER == "student"]; then
   /usr/local/bin/myscript.sh
fi

before the exit 0

This did the trick for logging out of the student session
.
It was also necessary to create a systemd service to run the script on restart.

sudo vi /etc/systemd/system/replace-student-profile.service

[Unit]
Description=Run myscript on reboot or shutdown

[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=/usr/local/bin/myscript.sh

[Install]
WantedBy=multi-user.target

Save and exit

sudo systemctl start replace-student-profile.service
sudo systemctl enable replace-student-profiles.service

---

### Post by TheFu on 2024-01-31
> **clendee said:**
>  
[https://devicetests.com/ubuntu-login-logout-script](https://devicetests.com/ubuntu-login-logout-script)
.bash_logout doesn't seem to be run when I log out of Gnome. 

I don't use Gnome, but the ~/.bash_logout is working here.  Did you ensure the file permissions have it as executable by the user?
If the shell is bash, I{ don't see how it couldn't work.  From the manpage:
```

       When an interactive login shell exits, or a non-interactive login shell executes the
       exit builtin command, bash reads and executes commands from the file ~/.bash_logout,
       if it exists.

       When  an interactive shell that is not a login shell is started, bash reads and exe&#8208;
       cutes commands from /etc/bash.bashrc and ~/.bashrc, if these files exist.  This  may
       be  inhibited  by using the --norc option.  The --rcfile file option will force bash
       to read and execute commands from file instead of /etc/bash.bashrc and ~/.bashrc.

       When bash is started non-interactively, to run a shell script, for example, it looks
       for the variable BASH_ENV in the environment, expands its value if it appears there,
       and uses the expanded value as the name of a file to read and execute.  Bash behaves
       as if the following command were executed:
              if [ -n "$BASH_ENV" ]; then . "$BASH_ENV"; fi
       but the value of the PATH variable is not used to search for the filename.

```

---

### Post by clendee on 2024-02-01
Thanks for your response.
My post above is the one that worked, ie by creating a script execution line in the /etc/gdm3/PostSession/Default file.

Also creating a systemd service for shutdown / restart, as the above comment only works for a Gnome session logout.

I did have the correct permissions on the script. Its just that .bash_logout wasn't triggered on a Gnome session logout.

---

### Post by TheFu on 2024-02-01
If bash is the shell and the .logout doesn't get called, that's a bug in Gnome or systemd. Just one of 100,000+ bugs in Gnome.  I don't use Gnome, so I can't test and follow up with them to get a response.

Certain things should always work.  More and more devs without UNIX backgrounds are dropping things that should always work through ignorance or apathy. Hard to tell which.

---

