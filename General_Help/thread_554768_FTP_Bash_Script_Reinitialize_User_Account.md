---
title: "FTP Bash Script Reinitialize User Account"
date: 2007-09-19
forum: General Help
---

### Post by firefly2442 on 2007-09-19
Hello,

I need to write a bash script that will delete all the files and settings for a user account, so basically everything in their home directory.  Then, I need it to FTP into a remote machine and grab a generic home directory and copy all these files over into the account.  Basically, after the user is finished, any files that they create or Firefox history, etc. any and all application data I want that to be reinitialized and wiped by copying over this new home directory.  Is this possible and if so, can someone help me with the bash script?  I've done some scripting already but nothing too fancy.  I was thinking of using wget with the recursive option to grab all the stuff from FTP, is this a good idea?

Thanks. :)

---

### Post by kidders on 2007-09-20
Hi there,

Your idea has a few problems that might prove tricky. How to tell when a user is "finished" is problematic, for instance. Additionally, what to do in the event your FTP transfer takes longer than usual (or fails altogether) isn't immediately obvious.

Do you suppose it would be workable to monitor your authentication logs for closed sessions? If so, you could decide that a user who logs out, and has no other active sessions, is "finished". You could then...[LIST=1]
[*]Lock the account.
[*]Fetch a tarball of a generic home directory via SFTP (or FTP, I suppose, if your network is trusted).
[*]Delete (or perhaps archive) the user's home directory & replace it with the generic version.
[*]Unlock the account.[/LIST]That way, a user that logged in, say, two or three times, would instantly lose access to his account the moment he terminated the last session. Access would be restored once his home directory was fully reset. In the event of a failure of some kind (eg the computer the generic home directory is on happens to be unavailable for some reason, in the particular instant it's needed), the script could install itself as a cron job, and keep retrying every so often, until it succeeds.

Anyhow, let's say we catch you logging out. Something like the following would test if you were done, or just closing one of a number of open sessions...```
if [ -n "`w -h $1`" ]; then
    # User not done yet
    exit 0
fi

# User has no other active sessions
...
...
```If you imagine this as part of a script called something like "reset_home", you would use it by invoking "reset_home firefly", for instance. That test could be supplemented by one involving "lsof", to be sure that there are no open file handles that could interfere with an attempt to delete /home/$USERNAME. Detached screen sessions, for instance, could screw up what would otherwise have been a nice, simple deletion.

Next, my preferred option would be SFTP, or something similar. You could set up an unprivileged, shell-less account on a remote host, and a public/private keypair for non-interactive login.```
rm -Rf /home/$USERNAME
mkdir -p /home/$USERNAME
ssh home_replication@hostname cat generic_home.tar.gz | tar xzC /home/$USERNAME
if [ $? -ne 0 ]; then
    # Panic!
fi
chown -R $USERNAME /home/$USERNAME
```The "ssh" command would need to be fleshed out more, to force key-based authentication. The "Panic" test is important, as you might not want your users to be able to log in with a completely empty home directory. This is where I would give consideration to spawning a cron job, so your reset_home script could recover gracefully from failures. For example...[LIST]
[*]The host storing the generic home directory is in the middle of rebooting.
[*]You are in the process of updating the generic profile, so the tarball appears corrupt, or non-existent.
[*]One of your users broke your computer's network connection.[/LIST]Finally, I would use "usermod" to lock & unlock accounts. For the duration of the reset procedure, you could replace a user's shell with a polite message to the tune of "Resetting your account. Try again in a few moments." or something like that.

Anyhow, I've tried to account for as many hidden "gotchas" as I can. I hope this gives you some ideas. Once you've sorted out the fine detail of the process to your satisfaction, the scripting itself should be reasonably straightforward. Even if you don't like *my* ideas, I'd be perfectly happy to help you iron out the kinks. The important thing, I suppose, is to create something that's at least *reasonably* unlikely to get tangled up in itself, fail, and turn out to be more trouble than it's worth.

[B]Edit:
[/B]
Yikes... I forgot something! My whole post is predicated on the idea that you will be able to intercept logouts. At the moment, I don't have a Ubuntu box with a graphical user interface installed on it, so I can't comprehensively test all possible ways of logging into a box myself. What I'm thinking of is this..[LIST]
[*] Open a terminal on the box you want to set up your home directory resetting on, and type **tail -fn0 /var/log/auth.log | grep "session closed for user"**
[*] Assuming this even works, the "tail" command will need work, to circumvent a complication caused by Ubuntu's system log rotation ... something to worry about later hehe.
[*] Log in and out of the box a few times, and watch "grep" spit out messages, as you close active sessions.
[*] It should be possible to capture these messages & run reset_home on the username appearing in each one.[/LIST]You could give something like this a try. It would watch for lines containing "session closed for user", and pass the 11th field (space-delimited field) from the line to a bash shell, as an argument to /usr/local/bin/reset_home. It would then be up to the reset_home script itself to decide whether that user really has logged out completely.```
tail -fn0 /var/log/auth.log | awk -W interactive '/session closed for user/{print "/usr/local/bin/reset_home $11"; fflush();}' | bash
```

---

### Post by firefly2442 on 2007-09-21
Hi thanks for the lengthy reply!

I'm going to try out your suggestions here this weekend.  Network issues aren't going to be a huge problem since it's on a LAN and the generic home directory should be pretty small (less than 100MB probably).

I also will be monitoring the people using the computers so hopefully they won't do anything "weird" to mess it up. :D

Thanks again, I'll be testing it out this weekend. :)

edit: To answer your question, I was thinking of using the session startup in Ubuntu Feisty to run the script.  So the script itself would be in some other directory on the computer and then it would run on startup to delete everything and copy the stuff over.  Would this work since the user is already logged in?  Hmm, that's tricky.  I see your point that I might have to look at the user logs.  Is there something similar to a session except it runs scripts when a user logs out?  There must be some sort of cleanup sequence for logout no?

---

### Post by kidders on 2007-09-21
> **firefly2442 said:**
> Hi thanks for the lengthy reply!No worries... I wasn't sure if you'd be thanking me or yelling at me for jabbering on for so long!

> **firefly2442 said:**
> I was thinking of using the session startup in Ubuntu Feisty to run the script.That approach is tempting, because there's a wealth of standard login scripts you could hijack, but it has a number of major disadvantages. The other question I considered when I suggested monitoring log*out*s is whether it makes more sense to perform a 100MiB copy with a relatively high failure probability when a user is walking away from a machine, or when he's sitting in front of it, waiting for it to go interactive. That's just my take on the problem though ... don't let me push you into doing something you'd rather not do!

> **firefly2442 said:**
> Is there something similar to a session except it runs scripts when a user logs out? There must be some sort of cleanup sequence for logout no?Logins & logouts are complicated. For instance, depending on how you look at it, a person could...[LIST]
[*]Type his username & password into a display manager. [Login 1]
[*]Open a terminal application. [Login 2]
[*]Start a screen session. [Login 3, 4, 5]
[*]Set up an SSH tunnel from a remote host to copy files or something. [Login 6]
[*]Lock his graphical session, switch back to the display manager & open another one. [Login 7][/LIST]Well, you get the idea. Then again, a user may simply decide to hit CTRL+ALT+F1 and log into a text only environment, I suppose. Two slightly odder examples, off the top of my head, might be...[LIST=1]
[*]A user logs into KDE, starts a screen session & launches something time-consuming, gets bored, and logs out again. The next time he logs in, it would not be appropriate to erase his home directory.
[*]A user logs in, adds something to his crontab, and logs out. That user might then appear to log in and out repeatedly for, say, the next few hours. I imagine repeatedly resetting his home directory *would* be appropriate in this case, even though the user is nowhere near the computer.[/LIST]Anyhow, the point is that, in practice, it might be a little tricky to figure out when it's okay to wipe a user's home directory without producing odd behaviour.

One alternative approach (which may, of course, be completely inappropriate to your situation) might be... As system administrator you decree that, every Monday at 3am, every machine will be shut down, all running processes will be terminated, all home directories reset, and at 03:05, they'll all wake back up again. Something like that could be implemented by storing /home centrally, and remotely executing a few well crafted "kill" commands every 7 days.

Well, the first step is to see if you can identify the logins (or logouts) that "matter", if you know what I mean ... the ones that tell you a user has just sat down, or is just about to walk away. Once that's done in a way that you find satisfactory, the rest should be simple (I hope!). I don't think you like it, but I hope you won't mind me using code from my last post, just for the sake of example...

If you hit CTRL+ALT+F1 & logged in, you could run something along the lines of the following. You may need to use sudo.```
tail -fn0 /var/log/auth.log | awk -W interactive '/session closed for user/{print "/usr/local/bin/reset_home $11"; fflush();}' | bash
```The /usrlocal/bin/reset_home script could contain...```
#!/bin/bash
if [ -z "`w -h $1`" ]; then
   if [ -n "`lsof | grep '/home/$1'`" ]; then
      echo "I should reset $1's home directory now, but files are open."
   else
      echo "I would reset $1's home directory now."
   fi
fi
```If this (or whatever decision-making process you'd prefer to use) only spat out messages at exactly the right times, you'd be done. :-)

---

