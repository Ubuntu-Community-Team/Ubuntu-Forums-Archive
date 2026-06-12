---
title: "bash annoyances &amp; terminal tips"
date: 2007-08-16
forum: General Help
---

### Post by pjkoczan on 2007-08-16
Hi all,

I'm using bash at work, and I'd like to fix a few annoying behaviors that don't show up in other shells. Note that "shell start" means logging in, starting a new terminal, or opening up a new shell with "bash". It appears that tcsh (our other supported shell) sometimes doesn't translate directly to bash.

- Home directories are symlinked to a networked fs. When I log in, bash decides that it should expand the directory name. In a nutshell, /etc/passwd shows my home directory as /home/pdk, which expands to /afs/cs/home/pdk out in AFS. pwd and my prompt show the latter, when I would like them to show the former. Is there any way to get bash to not expand these on shell start? Note that if I run cd, the short version appears. Also note that this doesn't happen in tcsh.

- I have two bash specific bash files, .bash_profile and .bashrc. The terminal loads up a general profile via .bash_profile, and then loads up my specific environment stuff from .bashrc via the source command. The PATH stuff in .bashrc is loaded twice, but only on shell start. If I source .bash_profile from an already running terminal, the PATH is not loaded twice.

And I have a couple questions about fun gnome-terminal tricks.

- How do I change the title in gnome-terminal without going through Terminal > Set Title...? Right now it just says "Terminal" but I'd like to have the current working directory, username, host, and possibly an indication of whether or not I'm a super admin (note: super admin not necessarily equal to root).

- Is it possible to change the background color based on whether or not I'm root or super admin easily? 

Thanks much.

---

### Post by ddrichardson on 2007-08-16
[There's a nice howto here]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html").

---

