---
title: "what applications do (or rather DID) I have"
date: 2023-07-11
forum: General Help
---

### Post by pjstock on 2023-07-11
following a failed upgrade I seem to have "lost" all my applications, a collection of dozens of handy little things that I had built over the past few years, but never really kept track of
I am likely going to do a fresh reinstall.
In the event that I loose my installed applications, it would save me a LOT of time if I at least knew the names of the applications I had installed.

is there a way of finding such a list? would they be listed in some directory if I worked in Terminal for a while?

---

### Post by Holger_Gehrke on 2023-07-11
If the programs you mean were installed from packages through apt, then you can get a list of all the packages which are marked as manually installed using 'apt-mark showmanual'. Sadly this list isn't all that helpful since it also contains most everything that was installed when the system was installed. So you have to filter those out. There is a compressed log file created by the installer named '/var/log/installer/initial-status.gz'. This has all the packages installed when the system was installed. With sed you can reduce that list to just packages names, then concatenate that list and the one from apt-mark, sort the joined list and use 'uniq' to get just the ones which are in there only once. I did that back when a do-release-upgrade went wrong and I had to do a reinstall.
**EDIT:** just checked whether that still works as it did two or three years ago and found that in 22.04 the list produced by 'apt-mark showmanual' seems to not have all the initial packages in there. So just 'apt-mark showmanual' will be very close to what you need if your system is new enough.

For other programs (installed from source) look in '/usr/local'. Most should be there. And of course your personal scripts should be in ~/bin or ~/.local/bin ...

Holger

---

### Post by dragonfly41 on 2023-07-12
Added tips.
Depending on whether terminal commands history has been purged you can simply run

sudo history

dump this content .. sudo history > dump.txt .. or you can use grep to filter .. and parse for occurrences of "apt".

Use this to automate reinstallation. But this is a long shot to find old commands.

Another route if you have installed Synaptic Package Manager is to view File > History.

Remember these for your next fresh installation if they do not apply right now. You might dump these from time to time in an external archive as insurance policy.

---

### Post by Holger_Gehrke on 2023-07-12
@Dragonfly: Good idea, dumping the history. Sadly it won't work like that. 'history' is a bash built-in, so 'sudo history' will give 'command not found'. Either drop the 'sudo' and get the command entered as a normal user or run 'sudo bash -c history' and get commands entered in interactive root sessions (which should be very few by comparison; on my system it actually didn't output anything ... ).

Holger

---

### Post by dragonfly41 on 2023-07-12
@Holger

Correction. Looking back before writing tip I see that I did try sudo history and true enough it does not work. But I then tried just "history" and that gave me now 1013 hits. But note that this history is purges in comand "clear" is given. So It might be useful to dump these frequently then clear and start again.

Actualy I use Yakuake as terminal.

Here is a partial clip of recent history dump.

...
...
...

[FONT=monospace][COLOR=#000000] 1007  07/07/23 16:17:50 albert[/COLOR]
 1008  08/07/23 22:02:07 find ~/Downloads -type f -exec file -N -i -- {} + | sed -n 's!: video/[^:]*$!!p'
 1009  09/07/23 06:52:33 sudo apt install mlocate
 1010  11/07/23 09:24:53 code --version
 1011  11/07/23 09:25:26 code --list extensions
 1012  12/07/23 07:12:07 sudo history
 1013  12/07/23 07:12:19 history

The earlier recent commands (1010-1011)related to testing VS Code commands.

And 1008 was an experiment to find video files throughout desktop relating to an earlier post. 

[/FONT][FONT=monospace]Correction: > [https://ubuntuforums.org/showthread.php?t=2488482](https://ubuntuforums.org/showthread.php?t=2488482)

I must admit that this code was prompted by a ChatGPT consultation to prove a concept.[/FONT]

---

### Post by TheFu on 2023-07-12
To get a list of all packages installed via APT's subsystem:

```
apt-mark showmanual > ~/keep-manual-package.lst
apt-mark showauto > ~/keep-auto-package.lst
```

or just use 
```
dpkg -l > ~/keep-all-package.lst

```but this will have lots of cruft that needs to be trimmed to be fed back into dpkg-select on the new install.

Keep those files with your backups. My backup script refreshes them daily, so they are always included in my nightly backups for each system.

If you use snaps, 
```
snap list   > ~/keep-snap-package.lst
```
I only have about 5 snaps installed on the systems were I allow **any** snaps at all.

For stuff that is manually compiled or installed outside snap or apt, I ensure those are placed into /usr/local/   and include that directory structure in my backups.  If we install something manually, we take on the responsibility to update it at least monthly.  Don't ignore this duty. Only bad can happen.  I put AppImages into /usr/local/appimages/ as an example.

APT has an installed *history* file. It is somewhere under /var/ ... not too hard to find when I need it.  This isn't the same as the ~/.history which most shells create and append into.  the one in your HOME directory has a limit for how many lines it will retain.  I don't know, but think the default limit is 500 lines. Think of it as a way to retain the commands typed today, but not last week.  Also, if you have multiple terminals open, I don't know which set of history will be flushed to that file, so all the commands from all but one of the terminal sessions will be lost.  If you want to retain the commands, do it for specific tasks, in a specific window and save those commands to another file.


If you use language-specific install tools like ruby gems, cpan, pip, etc, then those tools will have methods to get a list of their packages.  Run that command and save the output to a text file somewhere that your backups will pick it up.

---

### Post by Holger_Gehrke on 2023-07-12
@TheFu: The problem with /var/log/apt/history.log is that this needs a lot of filtering to be useful. It contains all actions related to apt in any way in one paragraph per action, most of them updates. Also it's being rotated once per month by default and anything older than 12 months is gone.

Holger

---

