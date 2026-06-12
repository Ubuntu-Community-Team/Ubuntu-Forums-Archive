---
title: "default text editor"
date: 2005-06-28
forum: General Help
---

### Post by ewlabonte on 2005-06-28
How does one change the default text editor. When I edit crontab with crontab -e, nano automatically comes up. I prefer vim. How do I go about (permanently) changing the default editor?

---

### Post by adwait on 2005-06-28
system>Preferences>preffered applications

---

### Post by ewlabonte on 2005-06-28
[QUOTE=adwait]system>Preferences>preffered applications[/QUOTE]

That, apparently is only for Gnome gui default applications. This is from the command line. I access crontab -e and nano, which is a shell text editor comes up rather than vim, which I would prefer. How do I get vim to edit the crontab file rather than nano?

---

### Post by skoal on 2005-06-28
I guess you have 2 options here:

[list]
[*]From the man pages, you can set one of these environment variables: VISUAL or EDITOR, like
```
skoal@morpheus://~ $ export EDITOR=/usr/bin/vim
skoal@morpheus://~ $ crontab -e
```
and to make it permanent, add that to your ~/.bashrc file.
[*]Or if those aren't set, you can change the symlink (more destructive approach, IMO) from it's default:
```
skoal@morpheus://~ $ ls -al /usr/bin/editor 
lrwxrwxrwx  1 root root 24 2005-04-29 06:01 /usr/bin/editor -> /etc/alternatives/editor
```
which is 'nano'. So, you would change the symlink like so...
```
skoal@morpheus://~ $ sudo ln -fs /usr/bin/vim /usr/bin/editor
```
[/list]
* The first option would probably be preferable.  You would have to relink the symlink to restore it to 'nano'.  Also, other DE apps might refer to the /etc/alternatives/editor, which might actually be a "good" way of setting that universally for all such DE apps in one fell swoop.

\\//_

---

### Post by ewlabonte on 2005-06-29
Thanks, I used the second option. There isn't any situation where I would use nano over vim so ... If  I run into problems I'll relink it to nano and use the first option. Thanks again :)

---

### Post by Ufo on 2005-07-01
Hi

 One way to change symbolic links like /usr/bin/editor is "update-alternatives" command.

---

### Post by rplantz on 2005-09-05
[QUOTE=adwait]system>Preferences>preffered applications[/QUOTE]

And I don't see a "Text Editor" tab, only "Web Brower", "Mail Reader", and "Terminal."

I somehow changed it to emacs and would like to change it back to gedit, but I can't figure out how to do this.

Bob

---

### Post by flurdy on 2005-10-12
i know this thread was some time ago ,

but here is the solution

run

sudo update-alternatives --config editor

which prompts you with this:  
Selection    Alternative
-----------------------------------------------
      1        /bin/ed
*+    2        /bin/nano
      3        /usr/bin/vim

Press enter to keep the default[*], or type selection number: 

of which you may choose 3 and it updates it as the default editor in /etc/alternatives

---

