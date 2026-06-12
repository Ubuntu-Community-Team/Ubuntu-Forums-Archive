---
title: "Which File to Save Aliases for System Wide?"
date: 2017-02-11
forum: General Help
---

### Post by AUDIOTEK on 2017-02-11
Which file do I need to save my personal aliases to?    For example I like to just type c to clear in bash 

```
alias c='clear'
```

But this is only assigned to the current shell.  How can I make it system wide for my particular machine?

---

### Post by Keith_Helms on 2017-02-11
If you're using bash, you can put them in .bashrc or you can create a separate .bash_aliases which will be pulled in by default if it exists.

---

### Post by SeijiSensei on 2017-02-12
The file /etc/bash.bashrc is invoked by /etc/profile in every login shell.  Put them in bash.bashrc.

---

### Post by oldos2er on 2017-02-12
System wide you'd probably need to edit /etc/bash.bashrc, but I have found some conflicting information through google.

Be sure to make a backup copy of that file first!

---

### Post by Habitual on 2017-02-12
my first "system-wide" alias was
alias x="exit" believe it or not, that e.x.i.t. was tough for me. Air Force Typist, hover and land.
I still punch Ctrl+L on Windows' cmd sometimes.

---

### Post by TheFu on 2017-02-12
As others have said here.

System-wide and for all your shells are different. Adding aliases for yourself is expected and supported.  ~/.bashrc at the bottom. Order matters.  Or ~/.aliases and source that in the ~/.bashrc file.  There are examples in the default ~/.bashrc showing this.

```
. ~/.aliases
```
or 
```
source ~/.aliases
```
work the same for bash shells.  Other shells, like tsch/csh/zsh/psh often work differently.

Making aliases work for every userid may have unwanted repercussions.  Normally, adding them to the /etc/skel/ files is done, not modifying system-wide settings. The skel files are copied into new users as they are created.  Power to the people! This is a design philosophy for all Unix systems. Each user should have control over their environment.

---

### Post by Keith_Helms on 2017-02-12
I don't know what was wrong with my answer that everyone had to elaborate on it.  ;)

The original question asked about > my personal aliases, not about for all users on my system.  I wouldn't recommend tinkering with files owned by root such as /etc/bash.bashrc unless you have a good reason to do so.

---

### Post by AUDIOTEK on 2017-02-13
> **oldos2er said:**
> System wide you'd probably need to edit /etc/bash.bashrc, but I have found some conflicting information through google.

Be sure to make a backup copy of that file first!

Awesome it works   No backup  if it fails I have to re do the whole installation all over again which is perfect practice.

In the course here are the file locations, I should of waited before asking but the instructor is covering aliases and standard environment variables in the same session so i had to distinct both.   All depends on your distro

/etc/profile
/etc/profile.d/*
/etc/bshrc
/etc/bash.bashrc

I used /etc/bash.bashrc

---

### Post by AUDIOTEK on 2017-02-13
I'd like to get ```
aliase h='cd ~'
```

Not working   it says h command not found    basically I want to press h and go to the home directory

---

### Post by &amp;KyT$0P# on 2017-02-13
> **AUDIOTEK said:**
> I'd like to get ```
aliase h='cd ~'
```

Not working   it says h command not found    basically I want to press h and go to the home directory
You may have a typo -
```
[COLOR="#FF0000"]**alias**[/COLOR] h='cd ~'
```

---

### Post by howefield on 2017-02-13
Drop the "e" from aliase ?

---

### Post by AUDIOTEK on 2017-02-13
I had the typo only on here.
Do I need to give it the full path?

---

### Post by TheFu on 2017-02-13
**cd**  will take you to the home. No need for **cd ~**.

Also, **h** is commonly used as an alias for "history", which is extremely convenient. Perhaps you haven't gotten to *history* yet?

Don't forget about **cdpath** environment variable (bash and tsch use it).  That can be very handy too.

Before going crazy with aliases, might be worth an online search to see what experts use. I've seen a few on github.  

For example, at a LUG meeting yesterday, someone relatively new showed me his aliases.  He was using one for 'ssh' that was effectively 'ssh -Xp 54099' ... so I asked him to show me how he uses scp, sftp and non-X-windows ssh into the same machine.  He didn't have aliases for those and started to create them.  So I added rdiff-backup and rsync to the list ... he was going to add another group of aliases for those too.  So I pointed out that ~/.ssh/config could be used to set the alternate port and alternate logins, different settings for different purposes (tunnels, X/Windows, SOCKs, etc ...) for all ssh connections to the remote system.  The 'config' file is honored by all ssh-using tools that I know. ALL-OF-THEM.  GUI tools, shell tools, CLI tools, anything that uses libssh honors it.  Heck, **ssh-copy-id** even uses it too!

My point - there are many ways that Linux/Unix have become more convenient over the years, but we cannot learn them all on day 1 or even year 1 of using the OS. 

Please take this comment as it is meant. I've found over the last 20+ yrs of being a programmer and Unix admin that there is almost always a better way to do it than my first thoughts come up with.  That taught me to ask questions differently - I ask based on the end-goal, not some intermediate process because of my planned techniques.  There is almost always a shorter way to do something.

[https://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html](https://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html) has some good ones.  Just beware that colorized output may not work on all systems and having a mix of the ANSI color codes makes output unreadable.

---

### Post by oldos2er on 2017-02-13
> **AUDIOTEK said:**
> Awesome it works   No backup  if it fails I have to re do the whole installation all over again which is perfect practice.

Reinstalling the entire OS is overkill for fixing an error in a single file, but perhaps you have a lot of free time.  :)

---

