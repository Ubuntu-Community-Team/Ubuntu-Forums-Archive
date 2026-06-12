---
title: "I need help understanding bash, shells and dot files"
date: 2017-04-02
forum: General Help
---

### Post by horsebox2 on 2017-04-02
I have tried setting up my own dot file repository using many methods and every framework out there, how it works is you clone a repository (or start a new folder of dotfiles), and they provide a tool that symlinks all your custom dotfiles into your home directory. The problem I'm having is, none of these custom dotfiles actually get loaded by bash. 

So there are some things I'm trying to understand. I read that there are two ways to use bash and other shells, login or non login. Interactive or non interactive. I've always used the non login shell and from what I read this only loads ~/.bashrc and a few others things:
&#8594;*Non-login process(shell)* calls ***~/.bashrc***
&#8594;~/.bashrc calls ***/etc/bashrc***
&#8594;/etc/bashrc calls the scripts in [I][B]/etc/profile.d/


[/B][/I]whereas the login version has a different chain of startup events:

&#8594;*Login process* calls ***/etc/profile***
&#8594;/etc/profile calls the scripts in ***/etc/profile.d/***
&#8594;*Login process* calls ***~/.bash_profile***
&#8594;~/.bash_profile calls ***~/.bashrc***
&#8594;~/.bashrc calls ***/etc/bashrc***


Whereas the login shells load a whole lot more dotfiles. Is it best practice to use login shells rather than non login shells? I just typed "terminal" into unitys finder, and pinned the launcher to my dock, and thats what I've used ever since. Or else I'll hit CTRL + ALT + DELETE. If I use login shell, will bash load these symlinked dot files in my home directory? For example I made a .aliases file for storing various useful aliases. I made a .functions file for useful functions. I made a .env file for storing environment variables. The possibilities are endless, I can store all kinds of configuration data in these files and enhance my work capacity greatly. But I don't know what I'm doing wrong. I could setup a script to write includes to the ~/.bashrc file but thats messy. I could also add a script to /etc/profile.d which includes all of my dotfiles, thats pretty clean and effective, but if symlinking dotfiles into the home directory is the universally accepted way of doing it, I'm guessing theres a good reason behind that. 

I looked into zsh and see its very popular, many people opt for it over bash or sh, but I'd prefer to get a good understanding of how it works with bash before switching over. As for custom dot files, I have no idea how that works, how they are loaded. Is it better to login through an interactive shell rather than the ordinary one?

---

### Post by Keith_Helms on 2017-04-02
I have no idea what you're trying to do with "repositories", "custom dotfiles", and symlinks.   A file starting with a period is just a normal file that is treated slightly differently by the shell in that it is hidden unless you supply a special option to list it - "ls -a".  They are also a bit harder to deal with using wildcards.

In general, you should leave the system/global config files in /etc alone unless you're making a change that should apply to multiple users and just change the config files in your home directory.  Those would normally be IN your home directory and not symlinked from somewhere else.

Read this writeup:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_01.html)

---

### Post by sp40140 on 2017-04-03
Like the previous post. I am unable to understand your use case which triggered this question. Can you please elaborate?

A general note. You can (and I think you should) customize .bashrc. You can add lots of configurations in that file. And also, you can call other files from it.
And when you launch the terminal with bash, all the customizations / configs from from .bashrc gets loaded.

---

