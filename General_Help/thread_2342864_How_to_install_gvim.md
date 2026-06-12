---
title: "How to install gvim"
date: 2016-11-10
forum: General Help
---

### Post by Only1KW on 2016-11-10
Anyone know how to install gvim in 16.04?  I'm getting the following error:

```
 $ gvim
The program 'gvim' can be found in the following packages:
 * vim
 * vim-gnome
 * vim-tiny
 * vim-athena
 * vim-athena-py2
 * vim-gnome-py2
 * vim-gtk
 * vim-gtk-py2
 * vim-gtk3
 * vim-gtk3-py2
 * vim-nox
 * vim-nox-py2
Try: sudo apt install <selected package>
$ sudo apt install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vim is already the newest version (2:7.4.1689-3ubuntu1.1).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
$ 

```

EDIT (11/11/16): What I'm really trying to figure out here is 
1. Why installing the vim package doesn't give me the gvim application, even though the vim package is included in the list above.
2. How I can determine the *complete* list of packages that will actually provide me the gvim application, without any extra packages in error

---

### Post by &amp;KyT$0P# on 2016-11-10
```
sudo apt-get install vim-gtk3
```

---

### Post by RobGoss on 2016-11-10
You can also install it using the Ubuntu software center in 16.04 [https://apps.ubuntu.com/cat/applications/precise/vim-gnome/](https://apps.ubuntu.com/cat/applications/precise/vim-gnome/)

---

### Post by Only1KW on 2016-11-10
Maybe I should restate my question.  Given the message I get when trying to run gvim, why is installing vim not fixing my issue?

---

### Post by RobGoss on 2016-11-10
Which version of Ubuntu do you currently have installed?

How did you install it the first time?

**NOTE**: I just installed it using the software center and it seems to open with out any errors for me I'm have 16.04 installed as well



Try to completely remove vim and then reinstall it use the following commands

```
 sudo apt-get purge vim 
```[COLOR=#242729][FONT=Consolas]


[/FONT][/COLOR]```
 sudo apt-get install vim 
```

---

### Post by #&amp;thj^% on 2016-11-10
vim and gvim are the same, **with one difference**: gvim provides an "interface" that doesn't run in a terminal window. Basically, gvim has menus and a toolbar like you have in most applications on Windows, Linux, etc.

As far as functionality outside of the user interface, they're identical. The keyboard commands are the same, plugins that work on one work in both. gvim is more or less an extension of vim.

So, which is better? It comes down to if you prefer to use terminal or a more traditional application with drop-down menus and a toolbar. Try both, in my opinion. 
halogen2 did give you the answer though.
Hope this helps

---

### Post by Only1KW on 2016-11-11
> **RobGoss said:**
> Which version of Ubuntu do you currently have installed?
16.04

> **RobGoss said:**
> How did you install it the first time?
When you say "it", do you mean Ubuntu or Vim?  I installed Ubuntu using the minimal installation, and installed vim using apt.

> **RobGoss said:**
> Try to completely remove vim and then reinstall it use the following commands

```
 sudo apt-get purge vim 
```[COLOR=#242729][FONT=Consolas]


[/FONT][/COLOR]```
 sudo apt-get install vim 
```
Didn't work.

```
$ sudo apt-get purge vim
[sudo] password for username: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vim*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 2,458 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 225300 files and directories currently installed.)
Removing vim (2:7.4.1689-3ubuntu1.1) ...
update-alternatives: using /usr/bin/vim.tiny to provide /usr/bin/vi (vi) in auto mode
update-alternatives: using /usr/bin/vim.tiny to provide /usr/bin/view (view) in auto mode
update-alternatives: using /usr/bin/vim.tiny to provide /usr/bin/ex (ex) in auto mode
update-alternatives: using /usr/bin/vim.tiny to provide /usr/bin/rview (rview) in auto mode
$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/1,036 kB of archives.
After this operation, 2,458 kB of additional disk space will be used.
Selecting previously unselected package vim.
(Reading database ... 225295 files and directories currently installed.)
Preparing to unpack .../vim_2%3a7.4.1689-3ubuntu1.1_amd64.deb ...
Unpacking vim (2:7.4.1689-3ubuntu1.1) ...
Setting up vim (2:7.4.1689-3ubuntu1.1) ...
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vim (vim) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vimdiff (vimdiff) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/rvim (rvim) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/rview (rview) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vi (vi) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/view (view) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/ex (ex) in auto mode
$ gvim
The program 'gvim' can be found in the following packages:
 * vim
 * vim-gnome
 * vim-tiny
 * vim-athena
 * vim-athena-py2
 * vim-gnome-py2
 * vim-gtk
 * vim-gtk-py2
 * vim-gtk3
 * vim-gtk3-py2
 * vim-nox
 * vim-nox-py2
Try: sudo apt install <selected package>
$ 
```

---

### Post by #&amp;thj^% on 2016-11-11
Try this:
```
sudo apt-get install vim-gtk
```

---

### Post by Only1KW on 2016-11-11
I don't think installing vim-gtk (or vim-gtk3 or vim-gnome as suggested earlier, or any of the other packages in the list) will help answer my earlier question:
[COLOR=#000000]
> Given the message I get when trying to run gvim, why is installing vim not fixing my issue?

If I'm wrong, and you think installing a different package will help answer that question, please help me understand how it will help.[/COLOR]

---

### Post by #&amp;thj^% on 2016-11-11
Please re-read my post #6
They are two different packages...From synaptic
> vim-gtk
This package contains a version of vim compiled with a GTK2 GUI
and support for scripting with Lua, Perl, Python, Ruby, and Tcl.
So if you want gvim...that's the way to get it. 
Regards

---

### Post by Only1KW on 2016-11-11
> **1fallen said:**
> Please re-read my post #6
I read post #6 and didn't understand the relevance of it.  I understand that the applications vim and gvim are different, and what the differences are between them.  That doesn't help me know what packages will install gvim.

> They are two different packages
What are two different packages?  Vim and gvim?  Gvim isn't a package.  Vim and vim-gtk?  Yes, I know they're different packages, but according to the message printed out to me by gvim, installing either of those two packages should give me the gvim application.  I don't understand why I'm being told that installing the vim package will give me the gvim application when installing the vim package does *not* give me the gvim application.

---

### Post by #&amp;thj^% on 2016-11-11
Sorry my friend I don't know how to make it any plainer.
You are right it is a confusing name-sake but your  Post asks "How to install gvim"
And without installing the for-mentioned package/s
You will have just vim.
But that is up to you now.
Regards

---

### Post by Only1KW on 2016-11-11
Admittedly the thread name is not as clear as it should be, but unfortunately, I was unable to change it once I realized it was confusing people.  I think there is a bug in Ubuntu in that it is displaying incorrect information about which packages will install gvim, and was trying to get confirmation.  I think it your last post you are agreeing that the list shouldn't be displaying vim as a valid package to install to get gvim, but I have yet to see anyone explicitly state "yes, that list of packages you are seeing is incorrect" or "here is how you get the *complete* correct list of packages that you could install to get gvim."

---

### Post by PaulW2U on 2016-11-11
> **Only1KW said:**
> but I have yet to see anyone explicitly state "yes, that list of packages you are seeing is incorrect" or "here is how you get the *complete* correct list of packages that you could install to get gvim."
Hi Only1kW, I've not answered any of your earlier posts as I'm at a loss to understand what the problem is. I've never had a problem installing gvim which is one of the first applications I install on a new system.

I now install [cream]("http://cream.sourceforge.net/"), which is a vim add-on that make vim/gvim a little easier to use if you've totally forgotten which vim commands to use as often happens to me. The cream package pulls in whatever vim packages are required but you don't have to use cream if you don't want to as both vim and gvim can be started in the normal way.
```
sudo apt install cream
```
Perhaps give it a try?

---

### Post by jerome1232 on 2016-11-11
Clearly gvim can't be installed by installing the package "vim". I'm not sure what script gets run to find that list of packages, or what project handles it, or what the designers intentions for that listing are. At first glance it is a bit confusing. A couple "apt show <packagenames>" would clear it up for the average terminal user though. I think the better question is "Who do I contact to report this as a usability bug, the listing seems confusing to me"

---

### Post by Only1KW on 2016-11-11
Thank you!  Apt show is working great!

Using it, I determined that the correct list that should be displayed is:

```
 * vim-gnome
 * vim-athena
 * vim-athena-py2
 * vim-gnome-py2
 * vim-gtk
 * vim-gtk-py2
 * vim-gtk3
 * vim-gtk3-py2
```

Unclear though why "c[COLOR=#000000]learly gvim can't be installed by installing the package 'vim'" but clearly it can be installed by installing some other packages that start with "vim-", as others seem to imply.

I'll also be sure to give cream a try.  It appears to pull in both the [/COLOR]vim-athena-py2 and vim-gnome packages as dependencies.

---

### Post by jerome1232 on 2016-11-11
Sorry, to clarify I meant "You can see through your attempts to install the package "vim" doesn't come with a gui as the listing seems to indicate" I'm agreeing with you that including "vim" as a package that provides gvim as a mistake. 

Using "apt show vim"  tells you that you need a different package for gvim (like vim-gtk, or vim-athena, or whatever).

---

