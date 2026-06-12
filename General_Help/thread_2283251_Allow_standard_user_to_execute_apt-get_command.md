---
title: "Allow standard user to execute apt-get command?"
date: 2015-06-20
forum: General Help
---

### Post by peter1897 on 2015-06-20
How to allow standard user to execute apt-get command without adding the user to the sudo group?

---

### Post by akash14 on 2015-06-20
They Can By Entering their password while they will use apt-get install <package-name>

---

### Post by peter1897 on 2015-06-20
They can't install packages without using "sudo", but i don't want to give them admin rights.

---

### Post by Dennis N on 2015-06-20
Anyone* could use **apt-get** if the options are right. For examples, a simulated install:

```
dmn@Sydney:~$ apt-get install -s gnome-mahjongg 
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gnome-mahjongg
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.

```

or actually download a deb file:

```
dmn@Sydney:~$ apt-get download gnome-mahjongg 
Get:1 http://mirrors.us.kernel.org/ubuntu/ vivid/main gnome-mahjongg amd64 1:3.14.1-1 [2,671 kB]
Fetched 2,671 kB in 1s (1,398 kB/s)
```

*_Note: I'm not a standard user, but I didn't need sudo, so i expect these cases would work for anyone! Not so?_

---

### Post by deadflowr on 2015-06-20
As long as you not writing to the system folders then you can run apt-get commands such and simulate or download.
As long as the download is into a folder/directory which you have permissions to write to.
If you were to cd into the /var directory and then run apt-get download, it'll error out, as an example.

It is fully possible to allow a non-admin user to use apt-get without fully being in the sudo/admin group.
But it requires editing the sudoers file.
Some basic reference points on that
 [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
and an old tutorial which still has a few revelant points here
[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

Note that the user will still need to use sudo, but in these cases the user will have a restricted usage of sudo.

My suggestion, though, before any edits to the sudoer file would be to make a backup of it.

---

### Post by Lars Noodén on 2015-06-20
> **peter1897 said:**
> They can't install packages without using "sudo", but i don't want to give them admin rights.

How long a leash do you want to give them?  You can give them access to apt-get, but not more, via sudo. That would allow them to add or remove programs but not do system-wide configuration.  See the manual page for [sudoers](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html) for full details, but something like this would give them install/remove privileges:

```

%peter1897   ALL=(ALL) /usr/bin/apt-get update, /usr/bin/apt-get install [A-Za-z0-9-]*, /usr/bin/apt-get remove [A-Za-z0-9-]*, /usr/bin/apt-get autoremove

```

Note that the options to apt-get are listed so the user can only do update, install and remove without any options.  You don't want to allow options unless you choose which ones, to prevent pointing to a different configuration file and so on.  But within those limitations they can install anything from the repositories or uninstall anything from the computer.

---

### Post by Lars Noodén on 2015-06-20
> **deadflowr said:**
> My suggestion, though, before any edits to the sudoer file would be to make a backup of it.

+1

and it helps to edit sudoers with [visudo](http://manpages.ubuntu.com/manpages/trusty/en/man8/visudo.8.html)

---

### Post by peter1897 on 2015-06-21
> **Lars Noodén said:**
> How long a leash do you want to give them?  You can give them access to apt-get, but not more, via sudo. That would allow them to add or remove programs but not do system-wide configuration.  See the manual page for [sudoers]("http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html") for full details, but something like this would give them install/remove privileges:

```

%peter1897   ALL=(ALL) /usr/bin/apt-get update, /usr/bin/apt-get install [A-Za-z0-9-]*, /usr/bin/apt-get remove [A-Za-z0-9-]*, /usr/bin/apt-get autoremove

```

Note that the options to apt-get are listed so the user can only do update, install and remove without any options.  You don't want to allow options unless you choose which ones, to prevent pointing to a different configuration file and so on.  But within those limitations they can install anything from the repositories or uninstall anything from the computer.

Thanks, this worked! I inserted the line this way:

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL
%peter1897 ALL=(ALL) /usr/bin/apt-get update, /usr/bin/apt-get install [A-Za-z0-9-]*, /usr/bin/apt-get remove [A-Za-z0-9-]*, /usr/bin/apt-get autoremove

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d


```

Can you explain each part of the line what does it mean and especially this **[A-Za-z0-9-]***. If i want to add other commands that the user can run with **sudo** can i follow the same procedure?

---

### Post by Lars Noodén on 2015-06-21
> **peter1897 said:**
> Can you explain each part of the line what does it mean and especially this **[A-Za-z0-9-]***. If i want to add other commands that the user can run with **sudo** can i follow the same procedure?

Sure.  

The percent sign in  %peter1897 means that the rest of the line applies to anyone in the group peter1897.  

The ALL=(ALL) should really have been ALL=(ALL:ALL) and really could have been written ALL=(root:root) instead for this use-case.  The first ALL is a macro (abbreviation) for which machine(s) the rule applies to.  Since we're only talking about one machine, it's not so important.  In a different computing environment the same file might be copied or otherwise exist on multiple machines.  In that case, sudo could be set up so that the rule only applies on certain machines.  The (ALL:ALL) stands for which user:group the sudo action can use.  

The comma separated list of utilities with options, specifies *exactly* which combination of options are allowed.  Since all three utilities on that line are [apt-get](http://manpages.ubuntu.com/manpages/trusty/en/man8/apt-get.8.html), the user in the group can run apt-get with three types of options.

[list]
[*]  /usr/bin/apt-get update - means only with the update option
[*] /usr/bin/apt-get install [A-Za-z0-9-]* - means the install option only if it is followed by a string of letters,numbers or dashes (*)
[*] /usr/bin/apt-get remove [A-Za-z0-9-]* - means the remove option only if it is followed by a string of letters,numbers or dashes (*)
[*] /usr/bin/apt-get autoremove - means the autoremove option only if it is by itself, needed sometimes for clean up
[/list]

(*) The idea is to allow the user(s) in the group to use install or remove program, since the package names consist of letters, numbers and dashes, yet prevent use of other options like -o= or -c= to name two.   The jumble is a [regular repression](http://www.grymoire.com/Unix/Regular.html#uh-0) which stands for a pattern to match.  The [ and ] delineate a set of characters to look for.  By itself it would just mean one character, but immediately followed by an asterisk, it means find an arbitrarily sized string composed of such characters.  Inside the [ and ], it says to look for any one of the letters A through Z, inclusive, or a through z inclusive or 0 through 9 inclusive or a dash.  I'm counting on the package names being ASCII only and not having any non-US English letters like äåö or á or à.  

If you leave off the options then *any* set of options can be used!  If you follow the utility with two empty quotes, then it means that *no* options can be used.

If you want to see what apt has been doing, with that user or any others, then you can look in /var/log/apt/history.log or its archived versions.  sudo use gets logged to /var/log/auth though there are some advanced settings you can set in sudoers to do detailed logging and session playback.

Take a look in the manual page for [sudoers](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html) and it will seem less abstract and overwhelming now.

Other commands can be done the same way, but if there is the potential for a shell escape, such as with 'less' or 'more', then you want to add NOEXEC: after the (ALL:ALL) or (root:root).  The main way to look for a shell escape is to press the exclamation mark (!) and then type a command, such as [ls](http://manpages.ubuntu.com/manpages/trusty/en/man1/ls.1.html) or [whoami](http://manpages.ubuntu.com/manpages/trusty/en/man1/whoami.1.html).  If the command runs, then that program needs NOEXEC: in its sudoers configuration.

---

### Post by Lars Noodén on 2015-06-21
Looking at it more closely, it can be tightened a little more.  The above works fine for apt-get, but allows 'harmless' options like -q or -y  The modification below takes out the possibility to follow the install or remove with anything other than a package name.  

```

[s]%peter1897 ALL=(ALL) /usr/bin/apt-get update, /usr/bin/apt-get install [A-Za-z0-9-]*, /usr/bin/apt-get remove [A-Za-z0-9-]*, /usr/bin/apt-get autoremove[/s]
%peter1897 ALL=(ALL) /usr/bin/apt-get update, /usr/bin/apt-get install [A-Za-z0-9][A-Za-z0-9-]*, /usr/bin/apt-get remove [A-Za-z0-9][A-Za-z0-9-]*, /usr/bin/apt-get autoremove

```

So is looking for any single letter or number, but not a dash, followed by a span of letters, numbers or dashes.  

That would be a more generic usage more applicable to other programs.

---

### Post by peter1897 on 2015-06-21
Thanks, for detailed explanation!

---

