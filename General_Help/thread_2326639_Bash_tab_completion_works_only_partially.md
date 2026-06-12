---
title: "Bash tab completion works only partially"
date: 2016-06-03
forum: General Help
---

### Post by togop2 on 2016-06-03
Hi, I have a pretty peculiar problem with bash completion. Before, it used to work very well. For example, if I wrote
sud[tab] apt-[tab] ins[tab] pyth[tab]3-[tab][tab]num[tab]
it would complete this to
sudo apt-get install python3-numpy, showing a list of possible completions at the [tab][tab]

Earlier today, I installed Ubuntu-gnome 16.04. Now, bash completes only filenames and executable names well:
sud[tab] becomes sudo
apt-[tab] becomes apt-get
cd [tab][tab] lists all subdirectories
nano [tab][tab] lists all files

However, more intricate completions - such as command-specific completions - won't work:
sudo apt-[tab] won't work
sudo apt-get inst[tab] won't work
sudo apt-get install python3-[tab][tab] won't work either.
sudo apt-get [tab][tab] will simply list all files

Can someone help me get all those working? I'd be much appreciative. Thanks.

---

### Post by pissedoffdude on 2016-06-03
Hi,

The tab auto complete functionality is controlled by the bash-completion package.  Most likely, installing gnome altered its config files either in /etc/bash.bashrc or ~/.bashrc.  Have a look at the /etc config file and uncomment out any auto completions installing gnome may have resulted in.  If you see a conflict in the ~/.bashrc you can have it match /etc/bash.bashrc and then execute a 'source ~./bashrc afterwards

---

### Post by togop2 on 2016-06-03
Thanks, copying /etc/bash.bashrc to .bashrc and then uncommenting the autocompletion section worked.

---

