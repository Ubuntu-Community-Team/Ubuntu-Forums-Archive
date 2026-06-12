---
title: "Creating ordinary user that can shutdown and monitor ubuntu server"
date: 2007-02-09
forum: General Help
---

### Post by textguru on 2007-02-09
I have setup ubuntu 6.06 server. Initially, the user that I made has an admin priviledge so he can do what ever he wants. What if I wanted to create an ordinary user that his only role is to monitor files and shutdown a computer, is that possible? I dont want to give the admin user since it has a capability to install other programs or even modify the system. Hope that you can help me.

---

### Post by DagMan on 2007-02-09
In System->Administration->Users and Groups you can add a user then highlight the user (or an already existing user) and select properties then user priveleges and there's a bunch of check boxes there.  One is for administration priveleges which you would not want them to have.  You can have a look and see what else suits you as well.  Taking away administration priveleges will disable them from running sudo or su but they will still be able to create and delete files in their home directory and it other places with the right ownership settings.  Anything that requires you to use sudo they will not be able to do.

---

### Post by textguru on 2007-02-09
Thanks for the reply but what I have indicated on my email is that I am using Ubuntu Server, no GUI. Hope you might help me give the command. Take note that I need also user that can shutdown the machine.

---

### Post by DagMan on 2007-02-15
Try this [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#book_part1_chap11](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#book_part1_chap11)

I don't know if it is the same in ubuntu but it makes sense that it probably would be.

---

### Post by TyphoonJoe on 2007-02-15
You probably want to edit /etc/sudoers

You need to know basics of vi to do this, as you edit it by running:

```
sudo visudo
```

This file lets you allow specified users to run specified commands with sudo, without allowing them full sudo access.  Here is an example that that allows joeuser to run somecommand without a password, and lets them shutdown or reboot after entering a sudo password:

```
joeuser    somehostname = NOPASSWD: /bin/simplecommand, PASSWD: /usr/sbin/shutdown, /usr/sbin/reboot
```

Notice you MUST enter the full path to the binary the user will run.  Also, when the user runs this binary, they MUST enter the full path.  

The /etc/sudoers file can become pretty complex depending what all you want to do, please "man sudoers" for detail- as this has some good examples.

Best of Luck!

---

### Post by DagMan on 2007-02-15
That would be the way.  I didn't think it all the way through.

I have this in my sudoers file:
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```
Testing out the above, I had to comment that out as well as adding things enabled for the user to run.  That was the easiest way to do it for one user and a handfull of commands but multipule users may be differant and your scenario may be differant.  Indeed, as stated the manual can be helpfull and it gets confusing enough that google may be of help to if your rules are getting complicated.  I think this is needed, the commenting out of that, because I think a user has to be part of the admin group to run sudo at all however it could simply be their ability to run su.  I haven't tested it to confirm.  If a user not inside the admin group can indeed run sudo then this would be un-necissary.

If there are commands that you want all users to be able to run, use ALL instead of their username at the begining of the line in TyphonJoe's example.

Also, helpfull to me is that I don't know how to use vi and the command visudo will open under nano if you do 'export EDITOR=nano' first... on my desktop anyway.

This is all from my desktop btw, so the server might have a slight variation of something.

---

