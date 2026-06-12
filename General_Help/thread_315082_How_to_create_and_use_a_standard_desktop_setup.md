---
title: "How to create and use a standard desktop setup?"
date: 2006-12-08
forum: General Help
---

### Post by George.M on 2006-12-08
I've set up a machine with Ubuntu 6.10 for a number of part-time employees to use. Each of them is going to have a separate account - but what I want to do is create a desktop setup - customized panels, menus, etc. - and then be able to deploy that same "stock" setup in each person's account. This way everything will be consistent and it'll be easier to support them if they have questions. (And, to be honest, part of the customization will be removing their ability to easily change anything more consequential than the desktop wallpaper....)

I'm a bit new to Linux in general and Ubuntu in particular - I know this kind of configuration is stored in a person's home directory - but I'm guessing that duplicating the ENTIRE home directory might also copy things that need to remain distinct for each account. 

Any help would be greatly appreciated!

---

### Post by lhtown on 2006-12-08
I don't know the best answer to your problem, but you could just copy all of the configuration files. The configuration files start with "." They don't appear in nautilus unless you tell it to show hidden files or something like that.

It sounds like your setup might be a good candidate for a thin client network if you don't already have the computers.

---

### Post by temcat on 2006-12-08
Install "sabayon" application. It allows you to create user setups (profiles) interactively - i.e. it launches *another session* within your current session, where you can set up all settings to your liking just as you normally do, and save it as a profile. Note that applying those profiles to machines other than yours is currently a bit difficult, but nevertheless possible - see the documentation ([http://www.rd.cri74.org/repository/gnome/doc_sabayon_v2_english.pdf](http://www.rd.cri74.org/repository/gnome/doc_sabayon_v2_english.pdf)).

---

### Post by az on 2006-12-08
Just to note that it is easier to install sabayon from the repositories rather than downloading it and using dpkg -i as mentioned in that document.


sudo apt-get install sabayon


It is in main, so you don't even need to enable any extra repositories.

---

