---
title: "sudo -i then bash does not run .bashrc in 18.04"
date: 2019-04-26
forum: General Help
---

### Post by Skaperen on 2019-04-26
in my 16.04 system when i do "sudo -i" to start an interactive shell as root, it all works as expected. but in my new 18.04 system, this runs bash as root but does not run the .bashrc file.  i have checked results of my _.bashrc_ file (it's a big one) and it definitely does not run.  if i then start a new shell by typing in "bash" then ._bashrc_ does run, and i see the output it produces, and see many environment changes, alias changes, and new function settings it makes.  exiting that new shell an i'm back in the first one that has not run _.bashrc_.  i can do "source .bashrc" or ". .bashrc" and _.bashrc_ runs in the first shell.

does anyone know why this is so?  is this a "new feature" of the new version of sudo?

more info that may matter:

the 16.04 system runs on my laptop with 16GB RAM.  it is amd64 architecture.

the 18.04 system runs on an AWS a1.medium instance in 2GB RAM.  it is arm64 architecture.

---

### Post by TheFu on 2019-04-27
Which .bashrc do you expect to be run?  Please be specific.  It should run /root/.bashrc , if the root shell is set to bash AND sudo allows initialization files. I think there is a setting in the sudo.conf and sudoers to control that.```

     By default, the env_reset option is enabled.  This causes commands to be
     executed with a new, minimal environment.  
```

In short, rtfm on both systems to see if the defaults have changed.

---

### Post by Skaperen on 2019-04-27
somehow, bash is choosing to not read and run [FONT=courier new]/root/.bashrc[/FONT].  i am wanting it to run [FONT=courier new]/root/.bashrc[/FONT] (is that specific enough?).

> AND sudo allows initialization files

how does sudo effect (not affect) that?  by an environment variable?  i tried running some code ahead of bash to save the environment and all i could see were 4 variables that sudo added.  i made that code unset them an then _exec bash_ but bash still didn't run [FONT=courier new]/root/.bashrc[/FONT].  i also tried having it _exec bash -l_ and still no luck.  then when i manually type in _exec bash_, it works as expected.

i'd like to ask of others running any version of Ubuntu (tell me which it is) and do have a  [FONT=courier new]/root/.bashrc[/FONT] if doing "sudo -i" or "sudo bash -l" runs their [FONT=courier new]_/root/.bashrc_[/FONT] or not.

in my case the non-root user's [FONT=courier new]~/.bashrc[/FONT] and [FONT=courier new]/root/.bashrc[/FONT] are identical.  so if bash is trying to run [FONT=courier new]~/.bashr[/FONT]c, instead, the result would be the same.  it doesn't run either one.

i think next i need to try to run bash under [FONT=courier new]strace[/FONT] and see what files it may be trying to open.

> In short, rtfm on both systems to see if the defaults have changed. 				

i did that early on.  neither version mentions any cases for not running [FONT=courier new].bashrc[/FONT].

---

### Post by Skaperen on 2019-04-28
i created a script at [FONT=courier new]/bin/bashx[/FONT] which dumped the _args_ and _environment_ to files then does _[FONT=courier new]exec strace -f -o ${ts}.strace /bin/bash "$@"[/FONT]_ to run the login bash in [FONT=courier new]strace[/FONT] and output it to a file.  variable [FONT=courier new]ts[/FONT] is a time stamp so repeats each are stored to separate files.  then i changed root's shell from [FONT=courier new]/bin/bash[/FONT] to [FONT=courier new]/bin/bashx[/FONT] and did the _[FONT=courier new]sudo -i[/FONT]_ in another window.  this time it had the output as if it ran [FONT=courier new].bashrc[/FONT] from somewhere.  i exited this session.  then in the first session where i did this setup, i looked at the _strace output_ and saw that _bash_ opened [FONT=courier new]/root/.bashrc[/FONT] and read it and no other.  i also saw many file system operations that [FONT=courier new]/root/.bashrc[/FONT] did.  so i undid the setup and did _[FONT=courier new]sudo -i[/FONT]_ in the other window yet again and it worked yet again, this time with [FONT=courier new]/bin/bashx[/FONT] and [FONT=courier new]strace[/FONT] not involved.  now it worked again.  i exited the first [FONT=courier new]sudo -i[/FONT] session i did the setup in and started it again and this time [FONT=courier new]/root/.bashrc[/FONT] ran fine.

something changed.  i have no idea what that is.  i have changed everything back to what it was before.  i wondered if running /bin/bash under strace could have done it, but that's not happening, now, yet it works, now.

i think i need to create another instance and see if that behaves like the first one originally did.

---

### Post by Skaperen on 2019-04-28
i just created another instance and this one works fine from the start. [FONT=courier new]/root/.bashrc[/FONT] runs fine.  now i am really puzzled.

---

### Post by Skaperen on 2019-04-29
just created 2 more instances using the same parameters (except for the IPv6 address, one is ${myprefix}::4 and the other is ${myprefix}::5), and same exact user data. the one at ::4 does not run .bashrc but the one at ::5 does.  so now i have something to explore differences.

(added by edit) when i run bash under strace in the ::4 machine, then it works.  i wonder if it's some timing variance on different hardware

the /root/.bashrc file mode, date/time, and contents are the same.

exploring /etc i find differences:
key files in /etc/ssh/ are different
/etc/hostname is different, the private IPv4 address as a hostname
/etc/machine-id is different, a 32 character hex string
/etc/sudoers.d/90-cloud-init-users differs by the date it was generated, as stated in a comment
/etc/netplan/50-cloud-init.yaml diffs by a coded macaddress

i'm stumped so far.

*edit:*

scanned all files in /bin /lib /opt /sbin /snap /usr and found them all to be the same.

::5 which was working, has now broken.  odd twist.  terminated both and rebuilding 2 more.

---

### Post by Skaperen on 2019-04-29
i have found that it is not _strace_ making things work but just executing [FONT=courier new]/bin/bash[/FONT] indirectly, by making a script that executes [FONT=courier new]/bin/bash[/FONT] and changing root's shell (chsh) to point to the script.```
#!/bin/bash
exec /bin/bash "$@"
```

---

### Post by Skaperen on 2019-05-04
i have not figured out why this happens but my workaround is doing the job well, so i am marking this thread as SOLVED even though it is technically not.

---

### Post by sisco311 on 2019-05-04
`sudo -i` starts an interactive **login** shell. So bash, after reading /etc/profile will look for ~/.bash_profile, ~/.bash_login, and ~/.profile and will read and execute commands from the first one.

In short, source the .bashrc from bash_profile:
```
root@acme:~ # cat /root/.bash_profile 
#
# ~/.bash_profile
#

[[ -f $HOME/.bashrc ]] && . "$HOME/.bashrc"


```

See:
```

man bash | less "+/^INVOCATION"
man sudo | less "+/-i, --login"

```

---

### Post by TheFu on 2019-05-04
> **Skaperen said:**
>   
> In short, rtfm on both systems to see if the defaults have changed. 				

i did that early on.  neither version mentions any cases for not running [FONT=courier new].bashrc[/FONT].

But do they say it will be run?  Assumptions get folks every time.

The quoted part of the manpage is pretty clear to me.  

I've seen in the sudo settings where the environment is completely controlled by sudo and ignores the userid's environment for safety reasons.  Most of the time, it is best to leave the root account and environment with 100% default settings.  Do whatever you want with your personal account.  
```

     By default, the env_reset option is enabled.  This causes commands to be
     executed with a new, minimal environment.  On AIX (and Linux systems
     without PAM), the environment is initialized with the contents of the
     /etc/environment file.  The new environment contains the TERM, PATH,
     HOME, MAIL, SHELL, LOGNAME, USER, USERNAME and SUDO_* variables in addi-
     tion to variables from the invoking process permitted by the env_check
     and env_keep options.  This is effectively a whitelist for environment
     variables.  Environment variables with a value beginning with () are
     removed unless both the name and value parts are matched by env_keep or
     env_check, as they will be interpreted as functions by older versions of
     the bash shell.  Prior to version 1.8.11, such variables were always
     removed.
```
There is much more just below. But I figured you'd actually see that and the other 10 paragraphs in the manpage about this.  PAM also impacts which environment variables are allowed.```

     As a special case, if sudo's -i option (initial login) is specified,
     sudoers will initialize the environment regardless of the value of
     env_reset.  The DISPLAY, PATH and TERM variables remain unchanged; HOME,
     MAIL, SHELL, USER, and LOGNAME are set based on the target user.  On AIX
     (and Linux systems without PAM), the contents of /etc/environment are
     also included.  All other environment variables are removed.

     Finally, if the env_file option is defined, any variables present in that
     file will be set to their specified values as long as they would not con-
     flict with an existing environment variable.
```

All in the manpage.

---

### Post by Skaperen on 2019-05-04
how is it that my workaround makes any difference?  is it the command name?  i just realized that what sudo uses as the command name (arg 0 in the execve syscall) will end up being changed by the script.

---

### Post by scheuref on 2020-03-02
[FONT=courier new]Hi Skaperen


I had apparently the same issue.

The root cause was:[/FONT]
[LIST=1]
[*][FONT=courier new]'sudo -i' starts a non-interactive shell when a command is provided[/FONT] 
[*][FONT=courier new]it sources ~root/.profile, which then sources ~root/.bashrc (sourcing means read and execute in current shell and environment, see 'source' and '.' shell builtins)[/FONT] 
[*][FONT=courier new]but then ~root/.bashrc is skipping all declarations because of this line:[/FONT] 
[/LIST]
[FONT=courier new]     # If not running interactively, don't do anything
             [ -z "$PS1" ] && return

solution:
  sudo cannot be used to run a command in an interactive shell directly, but you can use this:
  sudo -i bash -ic myaliascommand

    where bash -i is using an interactive shell


Cheers
Francois Scheurer[/FONT]

---

### Post by Skaperen on 2020-03-04
[COLOR=#0000cd][FONT=courier new]**sudo -i**[/FONT][/COLOR] is being executed without any commands given.  the intent is to run an interactive shell.  i do get an interactive shell. it just has not run file .bashrc.  when bash is invoked for any user in a virtual console or in a virtual terminal, then it does run .bashrc and become an initialized interactive shell.  ps shows no special arguments given.  i've run other programs in place of bash and do not see any secret environment variables.

i can't rule out bash deciding to not run .bashrc based on something i cannot see.  it *should* just work like it does when started by other means.

i've done many upgrades since then.  but /bin/bash is still dated before post #1.  i don't experience the issue any longer.  maybe i can find on an old AMI on AWS.  it looks old old Ubuntu AMIs are not being deleted (a good thing).

---

### Post by acormany on 2021-01-06
Skaperen,

I recently ran into the same issue on 18.04.  I don't know if this is your issue but I found that if I had a .bash_profile in the user's directory regardless if it's root or a non-root user it caused this behavior.  Even if the file is empty, the other environment files were not read.  After .bash_profile was read the process would exit/stop from sourcing anything else.

Two solutions I've tried that both worked for me:
1) Add to the user's .bash_profile:
    [[ -f ~/.bashrc ]] && . ~/.bashrc

2) Remove the user's .bash_profile altogether.

After either solutions were in place, I was able to sudo -i and my .profile and .bashrc files were read and I saw aliases and and other variables defined.

I don't know if this is by design where .bash_profile is to exit without sourcing other env files if it exists due to order of priority of files or if this is a bug and further files should be read after .bash_profile is sourced.

Hope this helps.

Thanks,
Adam

---

### Post by TheFu on 2021-01-06
Some necro-posting (9 months old) from an old thread?

From the bash manpage:
```
       When bash is invoked as an interactive login shell, or  as  a  non-interactive  shell
       with the --login option, it first reads and executes commands from the file /etc/pro&#8208;
       file, if that file exists.  After reading that file, it  looks  for  ~/.bash_profile,
       ~/.bash_login,  and  ~/.profile,  in that order, and [B]reads and executes commands from
       the first one that exists and is readable[/B].  The --noprofile option may be  used  when
       the shell is started to inhibit this behavior.
```

That reads to me as this is the expected behavior.

---

### Post by deadflowr on 2021-01-06
Back to sleep

---

