---
title: "Weird CTRL+Left, CTRL+Right behaviour"
date: 2007-10-20
forum: General Help
---

### Post by kristian on 2007-10-20
Since upgrading to Gutsy I've been having problems with using CTRL+Left/CTRL+Right to step one word in gnome-terminal/xterm. Instead of stepping a word I just get ;5C printed to the console. I've removed the .bash* config files and checked the Xorg & GNOME configurations for the keyboard but I can't seem to find the problem.

Also if I open a ssh session to another machine it works like a charm.

Someone that has experienced the same problem and solved it?
Thanks in advance.

---

### Post by bernardfrancois on 2008-01-12
I had this problem because of a broken user accound.

It occured because I created the user with the useradd command while installing ubuntu manually (following the _[fake raid howto]("http://wiki.ubuntu.com/FakeRaidHowto")_).

I solved it by taking the following steps:
[LIST]
[*]create a new user (with administration rights) with the **users-admin** tool
[*]backup all the files in your home folder you want to keep
[*]log in as the new user
[*]remove the old user
[*]open a terminal and remove the home folder of the previous user if necessary
[*]re-create the old user using the users-admin tool
[*]put your backed-up home directory files back in place (carfully... probably copying certain hidden files/folders might break the terminal keybindings again)
[/LIST]

Note that you can verify if the Ctrl+Left and Ctrl+Right keys work after the third step (when logged in as the new user). If they don't work, it makes no sense to proceed with the next steps.

---

### Post by kristian on 2008-02-12
Thanks for the heads up!
Now it works like it should.

---

### Post by bernardfrancois on 2008-03-30
Can you please mark your thread as solved? You can do this in the thread tools menu at the top of the first post. Like that, other people will know they can find a solution in this thread. Thanks!

---

