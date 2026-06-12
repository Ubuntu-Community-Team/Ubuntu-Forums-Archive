---
title: "$PATH - how do I modify it?"
date: 2022-04-26
forum: General Help
---

### Post by GhX6GZMB on 2022-04-26
I'd like to modify my PATH variable on my system. In this case not to add something (easy), but to _remove_ something from it.
I've tried this by editing /etc/environment, but even though this file is to my satisfaction (/snap/bin deleted), it still doesn't work.
Here's the output of my efforts:

```
macro@macro-pc:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
macro@macro-pc:~$ sudo source /etc/environment && export PATH
[sudo] password for macro: 
sudo: source: command not found
macro@macro-pc:~$  source /etc/environment && export PATH
macro@macro-pc:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```
As you can see, the user command works, but the sudo doesn't.

What's going on here? All help is appreciated.

Thanks.

---

### Post by GhX6GZMB on 2022-04-26
It gets even weirder. Here's another test:
```
macro@macro-pc:~$ source
bash: source: filename argument required
source: usage: source filename [arguments]
macro@macro-pc:~$ sudo source
[sudo] password for macro: 
sudo: source: command not found
macro@macro-pc:~$
```

---

### Post by &amp;KyT$0P# on 2022-04-26
Just to check, you did reboot after editing [FONT=Courier New]/etc/environment[/FONT] ?

[FONT=Courier New]source[/FONT] is not an independent executable, it's a bash function built into bash (and is documented in [FONT=Courier New]man bash[/FONT]).

---

### Post by GhX6GZMB on 2022-04-26
Yes, I rebooted. Several times, even.
I'm aware that both *source* and *export* are built-in functions of bash.
But why on earth won't they work under sudo?

EDIT: OK, _NO_ bash built-in commands accept sudo. This is new to me.

---

### Post by &amp;KyT$0P# on 2022-04-26
[FONT=Courier New]sudo[/FONT] only runs executables directly.  You would need to do something like
```
sudo bash -c 'source /etc/environment && export PATH;echo "$PATH"'
```

---

### Post by GhX6GZMB on 2022-04-26
The sudo / non-sudo implications of bash commands are now clear to me. Thanks!
That leaves the question why editing /etc/environment doesn't work. Or rather, only works temporarily?
This is my current PATH:
```
macro@macro-pc:/$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```
and this is my /etc/environment:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```
No matter what I do, I'm not able to get rid of that pesky /snap/bin term permanently.
There must be some command that I'm unaware of.

---

### Post by Holger_Gehrke on 2022-04-26
You can't run 'source' with sudo. 'source' or '.' is an internal command of the shell not an external program residing in a file of its own. 'sudo' needs a program file to call. But unless you have for some reason changed the permissions on /etc/environment you don't need sudo since that file should be readable for everyone.

Furthermore there are a class of programs called systemd environment generators (man systemd.environment-generator). If you've got snapd installed, then there's an environment generator (snapd-env-generator) that gets called after /etc/environment has been read and adds /snap/bin to $PATH if it isn't there.

Holger

---

### Post by #&amp;thj^% on 2022-04-26
> **Holger_Gehrke said:**
> You can't run 'source' with sudo. 'source' or '.' is an internal command of the shell not an external program residing in a file of its own. 'sudo' needs a program file to call. But unless you have for some reason changed the permissions on /etc/environment you don't need sudo since that file should be readable for everyone.

Furthermore there are a class of programs called systemd environment generators (man systemd.environment-generator). If you've got snapd installed, then there's an environment generator (snapd-env-generator) that gets called after /etc/environment has been read and adds /snap/bin to $PATH if it isn't there.

Holger
+1 great advice.
Try this please.

before my edit:
```

 cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"
```
i used:
```
sudoedit /etc/environment

```
then removed "/snap/bin"
result after running:
```
source /etc/environment
```
check with:
```
cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:"
```
no restart needed
```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:

```

---

### Post by GhX6GZMB on 2022-04-26
Thank You All.
I've investigated and experimented, and /etc/environment really controls most of the entries in $PATH.
BUT: _not all._
it seems that /etc/profile-d/apps-bin-path.sh plays a major role in making snap so incredibly M$-like persistent and pesky. There's simply no way of getting rid of it!
Renaming the file prevents booting (live boot necessary to fix it!).
Renaming /snap/bin to /snap/dodo adds it to the $PATH variable so that both are there, and can't be removed. This is dirty progamming, sorry.
Tragic...

---

### Post by #&amp;thj^% on 2022-04-26
are you now using any snaps?
that's probably the difference with mine.
```
 echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:
```
even after a reboot
```
me@me-Standard-PC-Q35-ICH9-2009:~$ apt policy snapd
snapd:
  Installed: (none)
  Candidate: 2.55.3+22.04
  Version table:
     2.55.3+22.04ubuntu1 1 (phased 20%)
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
     2.55.3+22.04 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

```
 echo $DESKTOP_SESSION
unity

```

```
 lsb_release -r
Release:	22.04

```

---

### Post by vanadium on 2022-04-27
I can indeed reproduce that: removing /bin/snap from /etc/environment does not remove the /bin/snap directory from the PATH after a restart and after having logged in. So it must also be set elsewhere.

Academically very interesting, but ask yourself why you want to remove it. It is useful if you use snap applications because it exposes executables just like regular deb packages, i.e., you can still launch Firefox with the "firefox" command. If you remove snap altogether, then the path will be gone also.

Still I agree with you that it is a tad frustrating not having a grip at the system level, until someone comes up here that knows how it works.

---

### Post by GhX6GZMB on 2022-04-27
> **vanadium said:**
> I can indeed reproduce that: removing /bin/snap from /etc/environment does not remove the /bin/snap directory from the PATH after a restart and after having logged in. So it must also be set elsewhere.

Academically very interesting, but ask yourself why you want to remove it. It is useful if you use snap applications because it exposes executables just like regular deb packages, i.e., you can still launch Firefox with the "firefox" command. If you remove snap altogether, then the path will be gone also.

Still I agree with you that it is a tad frustrating not having a grip at the system level, until someone comes up here that knows how it works.

Thanks for confirming that I'm not crazy :)
I don't have any snaps and don't intend to. The first thing I do after an installation is to remove snapd. And the directory /snap/bin doesn't even exist on my machine.
That's why it annoys me. A bit autistic, I agree, but still...

Thanks.

---

### Post by The Cog on 2022-04-27
This is on 18.04, but I imagine that later releases will be similar:
```
/etc $ sudo ag snap.bin
environment
1:PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"

sudoers
11:Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"

profile.d/apps-bin-path.sh
4:snap_bin_path="/snap/bin"
5:if [ -n "${PATH##*${snap_bin_path}}" ] && [ -n "${PATH##*${snap_bin_path}:*}" ]; then
6:    export PATH="$PATH:${snap_bin_path}"

```

---

### Post by GhX6GZMB on 2022-05-10
Yay!
Nailed it. The culprit is here:
```
/etc/profile.d/apps-bin-path.sh
```
and:
```
/etc/profile.d/bu-apps-bin-path.sh
```
Now my $PATH looks like this:
```
macro@macro-pc:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```Wonderful! Just comment out lines 4...7 and /snap/bin is history
 :)
Only /etc/environment controls my $PATH now.

Sorry, I know this is some days old, but wanted to share it.

---

### Post by GhX6GZMB on 2022-05-10
By the way:
I installed "ack" to find the "/snap/bin" instances, find/grep was far too heavy.
Wonderful little program, worked a treat.
Highly recommended from my side, very fast and easy to use.

---

### Post by TheFu on 2022-05-10
Why not just set the PATH you want in your ~/.bashrc file at the top?  That overrides whatever the system setting is. The ~/.bashrc should be run as part of the login, before any GUI session happens AND if you ssh to remotely login.  All covered.

A line like this:
```
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```
That's it.
I'm not a fan of modifying system settings for all users. Modify just your userid's settings.
If you don't want snaps, purge snapd using apt.

---

### Post by GhX6GZMB on 2022-05-11
> **TheFu said:**
> Why not just set the PATH you want in your ~/.bashrc file at the top?  That overrides whatever the system setting is. The ~/.bashrc should be run as part of the login, before any GUI session happens AND if you ssh to remotely login.  All covered.

Because that doesn't work (read my OP).
The /snap/bin in the $PATH is _not_ controlled by .bashrc.

---

### Post by TheFu on 2022-05-11
> **ml9104 said:**
> Because that doesn't work (read my OP).
The /snap/bin in the $PATH is _not_ controlled by .bashrc.

I don't know what to day.  It is working here.
Contents of ~/.bashrc

```
export PATH=/home/thefu/bin:/home/thefu/perl5/perlbrew/bin:/home/thefu/perl5/perlbrew/perls/perl-5.29.7/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

```
$ echo $PATH
/home/thefu/bin:/home/thefu/perl5/perlbrew/bin:/home/thefu/perl5/perlbrew/perls/perl-5.29.7/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

I simplified how my PATH gets set for this test.  Normally, ~/bin/ and all the perlbrew stuff is added only as needed something like this:
```
echo $PATH | grep $HOME/bin >/dev/null || export PATH=$HOME/bin:$PATH
```

OT: Looks like I need a newer perl. 5.35.11 is available.

---

### Post by GhX6GZMB on 2022-05-11
You _still_ don't understand my purpose.
I want to _get rid_ of /snap/bin in my $PATH, not add something to it.
And /snap/bin is _not_ in any of the "normal" places.
Like I wrote, I finally found where it comes from and eliminated it and am now happy.

I still recommend "ack". Great little program.

---

### Post by TheFu on 2022-05-11
> **ml9104 said:**
> You _still_ don't understand my purpose.
I want to _get rid_ of /snap/bin in my $PATH, not add something to it.
And /snap/bin is _not_ in any of the "normal" places.
Like I wrote, I finally found where it comes from and eliminated it and am now happy.

I still recommend "ack". Great little program.

Sorry I haven't been clear.  If you can add a directory to the PATH, it isn't hard to remove one either.  The path is : separated. That makes parsing easy.  Awk, sed and do it easily. Here's a link to the sed method: [https://unix.stackexchange.com/questions/108873/removing-a-directory-from-path](https://unix.stackexchange.com/questions/108873/removing-a-directory-from-path)  

Or  can just hard code the PATH in ~/.bashrc to what you want and leave out the snap parts.  Which is what I showed before the fancy-add-home-bin stuff.

Changing system settings for everyone when only 1 user is impacted is a poor admin choice. Learned that from decades of experience.

Perhaps we just can understand each other on this. That's too bad, but I know I tried and tested it and it worked.

---

### Post by GhX6GZMB on 2022-05-11
I also think we're talking cross-purposes here, sorry.
Fact is, that none of the .bashrc files on my laptop contain _any_ $PATH info, regardless of which user. Apparently this is not part of a standard Lubuntu install..
The only $PATH information on my system is in /etc/environment.
And as no user has access to any snap stuff, removing the pesky thing makes sense to me. It may not be the most elegant solution (some guru might write a 100-line script to fix the problem), but it works for me.
As I deinstalled snapd, I'm somewhat offended that this program leaves turds behind that I have to remove myself. Bad behaviuor.

---

### Post by TheFu on 2022-05-11
Ah ... I think I see the core issue.  I had this myself.  Thinking that just because some setting doesn't already exist in a file, that should mean that we cannot add it.  That isn't true.

Environment variables BELONG in the ~/.bashrc (if bash is your shell).  That's where they go.  There are a number of variables that should routinely be set there which seem to have been lost the last 15 yrs.  PATH, EDITOR, PAGER are just a few.

All Unix systems have a specific way they start up and a specific way that a userid logs in either on the console or remotely.  The default dotfiles for the specific shell (in the paswd db), determine which files the login process uses and in what order.  ~/.profile and ~/.bashrc are part of that login chain.  This is documented in most beginning Unix/Linux books and taught in training.

Additionally, whether a variable should be for 1 process only or inherited by all sub-processes is part of those books and training.
```
FOO=foo
```
is different from 
```
export FOO=foo
```
One is for the current process only and the other is for the current process AND all child processes.  That's why we use 
```
EXPORT PATH=foo:bin:anywhere-else-we-like
```
in our settings. We want the path to be inherited by all sub-shells and child processes.

Just because an environment variable already has some value, that doesn't mean we cannot replace it with a value we prefer too.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) chapter 11 explains.  Learn about the difference between login shells and non-login shells too.  That's why I said to use ~/.bashrc. It is a specific choice.   I quote:
> Unless you are the system administrator and need to change the defaults for all users of the system, restrict your modifications to the files in your home directory.

---

### Post by GhX6GZMB on 2022-05-11
@TheFu:
Thank You for your insights.
But I'm coming from the other end of the spectrum: I'm just a Linux newcomer that's trying my best. There are millions of pages on UNIX documentation and seminars and trainings and whatever out there. Bully for you that you can read and attend all those. I can't.

I have to take the installation as it is and work with it. That's what I've done... and achieved the desired result.

That local configuration files override global ones is known to me, but without a "template file" it's a lost battle. How on earth would I know that .bashrc is the file to work with? And how should I modify it?
Why bash? Would using a different shell result in a different $PATH? Seems illogical to me.

I know you're super knowledgeable and experienced, but you need to look at it from my point of view as well.

Thanks anyway, keep up the good work. Your knowledge is valuable.

---

### Post by TheFu on 2022-05-11
Different shells have different init files.  They are typically ~/.{shellname}rc because not all shells can interpret the same scripts.

~/.bashrc is for bash.
~/.cshrc is for csh
~/.tcshrc is for tcsh
zsh, fish, psh, ksh, and probably 10 others exist. [https://en.wikipedia.org/wiki/Comparison_of_command_shells](https://en.wikipedia.org/wiki/Comparison_of_command_shells)
.... these are just one of the default names that are looked for by the shell program at start. There are others and nothing bad happens if they don't exist. But if they do exist, then must be written in the shell "language" that will be used.  Many shells are related so many scripts can be run withing the family.  I can assure you that csh and bash are NOT compatible. OTOH, csh and tcsh are.  I think tcsh was the first to include command completion. It was the first that I saw with it.

Environment variables can be set by any program.  But they cannot be forced from a child program to the parent, which is why we need to inherit them at login time or when using ssh to remote into the system.  99% of my day is spent using ssh connections into other systems. This isn't a login shell, so setting environment variables only for login sessions doesn't work for me, though it may be fine for typical desktop users with 1 computer.

The manpage for bash has this:
```
       When an interactive shell that is not a login shell  is  started,  bash
       reads  and  executes  commands  from /etc/bash.bashrc and ~/.bashrc, if
       these files exist.  This may be inhibited by using the  --norc  option.
       The  --rcfile  file option will force bash to read and execute commands
       from file instead of /etc/bash.bashrc and ~/.bashrc.
```
dash (a Bourne Shell implementation) has a section about "Invocation" which explains the startup files for it.

Regardless, if you have a solution and are happy, then that's all that matters.
I think we've over beaten this egg.

---

