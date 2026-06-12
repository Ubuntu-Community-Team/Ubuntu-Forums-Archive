---
title: "Restrict software for users"
date: 2014-04-14
forum: General Help
---

### Post by kleinempfaenger on 2014-04-14
Hi, 
I created a new non-admin user account and I want to restrict access to the systemwide installed software. Is there a tool to do this?

Greetings and thanks for help.

---

### Post by 1clue on 2014-04-14
What exactly are you trying to do?

---

### Post by 3rdalbum on 2014-04-14
For a simple scenario (sudo'ers can run all programs, non-sudo'ers can only run certain ones) you could change the 'group' attribute of the privileged programs to whatever group all the sudo'ers are in (I can't remember if it is 'wheel' or 'admin') and set the execute permission so "everyone" has NO execute permission. It would be something like this:

sudo chgrp /usr/bin/firefox admin
sudo chmod a-x /usr/bin/firefox
sudo chmod g+x /usr/bin/firefox

That probably isn't the best approach, and it does nothing about the .desktop launchers appearing, but if nobody comes up with anything better...

---

### Post by 1clue on 2014-04-14
I would avoid messing with the default group attributes until we knew what sort of things the OP has in mind.  Depending on what is required, there might already be a group setup for that, or the intended result might want a different approach.

---

### Post by whitesmith on 2014-04-14
> **kleinempfaenger said:**
> Hi, 
I created a new non-admin user account and I want to restrict access to the systemwide installed software. Is there a tool to do this?Please be more specific. Are you talking about disabling built-ins like **ls** and **cp** with the intention of denying certain users the CLI? I don't know that I would play around with measures like that for fear of creating an unstable system. If we only knew what your goals are, perhaps someone could come up with the right answer. Regards.

---

### Post by kleinempfaenger on 2014-04-14
Hi, 
I have a computer which is used during the day for CAD works. Later my children use it for everything else, like playing, watching videos etc. So it has lots of programs installed, which could distract. I want to be able to block some programs for a certain user account. The programs are already installed.
Greetings

---

### Post by SeijiSensei on 2014-04-14
I think the simplest solution for that would be to remove the entries for those programs from the kids' menus.  Broad access restrictions would be difficult to implement.

You could consider restricting execution of just the small set of programs you want to block.  If these are installed from the repositories, identify the program(s) in /usr/bin and do the following:

First, create a "bin" subdirectory in your home directory and copy the CAD program to it.  Make sure the program is owned by your account and not by root.  Now run the command:
```
chmod u+x,go-x /home/username/bin/program_name
```
After that only you can execute the program. Check that this works by opening a terminal and entering /home/username/bin/program_name.

If you now log out and log back in, type the command "echo $PATH".  You'll see that $HOME/bin has been added to your path (code to do that is in /home/username/.profile).  Now you can just type the program's name at the terminal prompt to run it, or you can create a launcher so you can run it from the GUI.

If all this works as advertised, delete the original copies of these programs so those copies won't be available to the kids.

---

### Post by 1clue on 2014-04-14
I would strongly recommend that you set up unprivileged accounts for the kids, and then add a group for your special apps.

If you wind up changing permissions on more than 10 or 20 apps I would say you're going about it the wrong way.

Most of us I think are hedging because we still don't know what you're trying to accomplish.  You want your kids to do the normal things an Ubuntu user would be able to do, but you want your business specific things to be privileged?  That's perfectly do-able.  But to go through all the commands/apps available and decide whether they're child-safe, that's going to get you an unusable system.

Feel free to be extremely specific.  We can help, but we can't be any more specific than you are.

---

### Post by kleinempfaenger on 2014-04-15
Hi, 
it's just the way round. Its not about my kids. They play their games and watch some music videos, which is ok. They are doing their things on their normal user account or my privileged account, but they don't know the password. To install things they have to ask. I want the CAD-account to be exclusively dedicated for work. So it is intended to be without games, social things and so on.

---

### Post by kleinempfaenger on 2014-04-15
Is there a helpfile about the different "groups" you mentioned? I couldn't find anything, even in the forums.

---

### Post by kleinempfaenger on 2014-04-15
Thanks for your answer. As I pointed out in a former reply, this would be a mayor work, as I would have to move lots of already installed programs on several accounts. I think this would lead to errors. 
The system has been growing and running fine for years, but now I want to add a user account, which is limited to only a few programs.

---

### Post by SeijiSensei on 2014-04-15
Then, as I say, you should have that account own those programs and run them from $HOME/bin.

---

### Post by 1clue on 2014-04-15
You're looking for a sort of self-restriction so you focus on work?

That could be kinda tough for a standard installation, especially if you mean command-line apps too.

Facebook and twitter or whatever, you could probably more easily set up a time of day and maybe a host on your router, prevent those things during business hours.  The problem is, a lot of what you'd think of as social or games, it's all a web browser so you can't really handle that with permissions.

You can look up 'linux groups explained' on Google and get a much better explanation than I can give you.  You could ensure that your work user is not a member of the 'games' group, and then make sure any binary game app has that group set.

Here's the short explanation:

If you open a terminal and type 'ls -al' you'll get something like -rwxr-xr-x on some files, at the left.  Those rwx bits are permissions.  Read is r, write is w, and execute is x.  There are 3 basic entities:  The owner of the file, the group of the file, and 'others', which is everyone who has access to the system.

For the restricted apps, probably the owner is root, which is fine, and the group is either games or something specific to the app, which is fine, or it's something like 'users', which is not fine.

You would want to **sudo chgrp games /path/to/game** for the game binary.  Then make sure your work user does not belong to games, or whatever other group you set.  Then you **sudo chmod 750 /path/to/game** to make sure your work user has no access.

I want to reiterate the warning:  If you get carried away with this and start changing permissions on a lot of things, you can seriously mess up your box.  I did it several times before I learned my lesson, and generally wound up reinstalling the whole system because of it.  A lot of thought went into standard permissions for apps on Linux, so you'd better understand what's going on before you dive in too deep.  If you're just changing permissions on games and such, that's not a big deal.

---

### Post by kleinempfaenger on 2014-04-15
Thanks again, I have read today a lot about this item. I think this is the way to get it done. It will be a lot of work, though. 
I have to point out it's not abut ME. I have given up already trying to force myself to work with filters and other things for self-restriction. It doesn't work, I would have to forget my own passwords.

---

