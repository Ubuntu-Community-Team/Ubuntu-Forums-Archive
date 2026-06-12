---
title: "PLEASE HELP- Ubuntu cant find home directory, but it is there!"
date: 2008-06-07
forum: General Help
---

### Post by bconover on 2008-06-07
Ok, I need some SERIOUS help with this, as until it is fixed, my computer is unusable. 

I had been getting that apprently common error having to do with the 644 permissions. I tried to fix it with some commands shown on another topic, and now I can't even log in. It says my homedirectory is "set as /home/brian", but that it doesn't appear to exist. Yet, when logged in with terminal in Recovery mode, I can clearly navigate to /home/brian, and all my files are still there. When I attempt to log in as root (as advised by the error message at log in), my seesion crashes after 10 seconds. I read on another forum about creating a home directory to solve this, but my home directory IS THERE.Why can't Ubuntu read it? Please help, I need my computer and the files on it!

---

### Post by rampageoberon on 2008-06-07
Set the permission of the directory to 755 (I think it needs execute permission to be able to view it)

```
sudo chmod 755 /home/brian
```

You can do this in the terminal tty1 press CTRL+ALT+F1

Hope that helps

---

### Post by knutschr on 2008-06-07
It seems you have made the wrong permission for your home directory.
Start in recovery mode and give command startx.
That will make you root at GUI.

Start a file browser (I use thunar), look at permissions, and change it.

Then restart.

---

### Post by bconover on 2008-06-07
Sorry, neither of those worked.

Excactly what permissions do I need to set for the 2nd option? I'm am pretty new to Ubuntu, so sorry if that is normally obvious.

---

### Post by rampageoberon on 2008-06-07
You want full read, write, execute access for yourself and permissions to group and other can be whatever you want.

Could you run the following command and paste the output here please

```
getfacl /home/brian
```

or

```
ls -l /home/
```

---

### Post by knutschr on 2008-06-07
/home is to be owned and being writeable by you only.
Is that what you get?

---

### Post by bconover on 2008-06-07
> **rampageoberon said:**
> You want full read, write, execute access for yourself and permissions to group and other can be whatever you want.

Could you run the following command and paste the output here please

```
getfacl /home/brian
```

or

```
ls -l /home/
```

Both give me Persmission Denied.

Although the second also gives me

total 0
d????????? ? ? ?       ?brian

Here is the error I get when I try to log in:

[IMG]http://i172.photobucket.com/albums/w35/bjincs002/P1020482.jpg[/IMG]

When I say no, it just brings me back to log in. When I say yes:

[IMG]http://i172.photobucket.com/albums/w35/bjincs002/P1020483.jpg[/IMG]

Click Ok, then:

[IMG]http://i172.photobucket.com/albums/w35/bjincs002/P1020484.jpg[/IMG]

I have 54 GB space left, so not out of space.

---

### Post by rampageoberon on 2008-06-07
Okay try login with root and then run those commands with root. I'm guessing you can log in with root?

The root command will have a **#** instead of a **$** at the terminal.

or if you login with /root as home directory then do

```
sudo getfacl /home/brian
```
or
```
sudo ls -l /home
```

---

### Post by bconover on 2008-06-07
Okay, here is what I get:

getfacl:Removing leading "/" from absolute path names
# file:home/brian
# owner: brian
# group: brian
user::rwx
group::r-x
other::r-x

---

### Post by rampageoberon on 2008-06-07
The permissions look okay. Umm I'm not sure what could be causing the error. Can you try creating a new account? And see if you can log in with that?

```
sudo adduser brian2
sudo adduser brian2 admin
```

---

### Post by bconover on 2008-06-07
sudo adduser brian2

Adding user 'brian2'
Adding new group 'brian2' (1001) ...
Adding new user 'brian2' (1001 with group 'brian2' ...
Creating home directory '/home/brian2' ...
Copying files from '/etc/skel' ...
**Stopped: symlink: *Permission denied***

Removing directory '/home/brian2' ...
Removing user 'brian2' ...
Removing group 'brian2' ...
groupdel: 'groupdel brian2' returned error code 6. Exiting.

sudo adduser brian2 admin

adduser: The user 'brian2' does not exist.

:(

---

### Post by Naatan on 2008-06-07
Seems to me that you modified more than just your home directory permissions, this can really **** up a linux install beyond recovery.

could you do an "ls -ahl /" and post us the results? Feel free to filter out any directories that you feel uncomfortable showing, though in a normal Ubuntu setup there shouldn't be any akward directories in the root of your partition.

---

### Post by rampageoberon on 2008-06-07
I've found a similar thread here 

[http://ubuntuforums.org/showthread.php?t=700630](http://ubuntuforums.org/showthread.php?t=700630)

I'm not sure why it is doing this.

I'll look around though, sorry

---

### Post by bconover on 2008-06-07
did ls -ahl, got this screen:

[IMG]http://i172.photobucket.com/albums/w35/bjincs002/P1020488.jpg[/IMG]

---

### Post by rampageoberon on 2008-06-07
ok do

```
ls -ahl > output
``` and paste the contents of the file output or upload that file here please

---

### Post by bconover on 2008-06-07
I'm not sure how to get that file up here, since I can't use my computer excpet in a terminal, and I'm not too good with the terminal stuff yet. I'll just type it here. Might take a bit, so hold on...

---

### Post by rampageoberon on 2008-06-07
If you are using terminal try using elinks or links2 as your webbrowser. I just tried it and you can do the attachments though it is a bit tedious.

Otherwise you can open the file with vim

```
vi output
```

and then run the following command to select all and copy

```

ggVG
"+x

```

And then see if you can paste it here

---

### Post by Naatan on 2008-06-08
notice th dash at the end of the command I gave you "ls -ahl /" meaning that it needs to be of the root directory, not your home directory, I think we've established your home directory isn't the real problem

Edit:

there's something wrong with your homedir as well, type:

chown -R username.username /home/username

replace username with your username of course

---

### Post by bconover on 2008-06-08
I did ls -ahl / instead, gave me same thing though.

I'll have the contents of output here soon. Couldn't get links2 or elinks because I can't connect to the internet from my computer. I tried to place output on a usb device, it seemed as though the computer was doing something with it, but I coudn't mount or find the device after being given the message that it had been read.

Also did chown -R brian.brian /home/brian. Nothing.

---

### Post by bconover on 2008-06-08
Here are the results of ls -ahl /, and contents of output:

total 164k
drwxr-xr-x 30 root root 4.0K Jun  7 19:56 .
drwxr-xr-x 23 root root 4.0K Jun  7 16:49 ..
-rw-------  1 root root  171 Jun  7 16:48 .ICEauthority
-rw-------  1 root root  106 Jun  7 16:48 .Xauthority
drwx------  2 root root 4.0K Jun  3 15:24 .aptitude
-rw-------  1 root root  485 Jun  7 15:27 .bash_history
-rw-r--r--  1 root root 2.2K Oct 20  2007 .bashrc
drwxr-xr-x  2 root root 4.0K Jun  1 11:43 .bcast
drwxr-xr-x  3 root root 4.0K May 31 16:22 .cache
drwx------  5 root root 4.0K Jun  7 16:49 .config
drwx------  3 root root 4.0K May 31 16:22 .dbus
drwx------  4 root root 4.0K Jun  7 16:49 .gconf
drwx------  2 root root 4.0K Jun  7 16:49 .gconfd
drwx------  8 root root 4.0K Jun  7 16:49 .gnome2
drwx------  2 root root 4.0K May 31 15:23 .gnome2_private
drwx------  2 root root 4.0K Jun  7 16:48 .gnupg
drwxr-xr-x  2 root root 4.0K Jun  1 21:05 .gstreamer-0.10
-rw-r--r--  1 root root   84 Jun  7 16:49 .gtk-bookmarks
drwx------  2 root root 4.0K May 31 16:22 .gvfs
drwxr-xr-x  3 root root 4.0K May 31 16:22 .local
drwx------  3 root root 4.0K Jun  3 21:59 .loki
drwx------  2 root root 4.0K Jun  1 21:00 .mozilla
drwxr-xr-x  3 root root 4.0K Jun  5 18:57 .nautilus
-rw-r--r--  1 root root  141 Oct 20  2007 .profile
drwxr-xr-x  2 root root 4.0K Jun  7 16:48 .pulse
-rw-------  1 root root  256 Jun  7 16:49 .pulse-cookie
-rw-r--r--  1 root root  218 Jun  4 16:39 .recently-used.xbel
-rw-------  1 root root 1.0K May 31 16:29 .rnd
drwx------  2 root root 4.0K Jun  7 16:48 .ssh
drwx------  3 root root 4.0K Jun  7 09:30 .synaptic
drwx------  3 root root 4.0K Jun  6 15:55 .thumbnails
drwxr-xr-x  2 root root 4.0K Apr 22 14:06 .wapi
-rw-------  1 root root 7.8K Jun  7 16:50 .xsession-errors
drwxr-xr-x  2 root root 4.0K Jun  5 18:57 Desktop
drwxr-xr-x  2 root root 4.0K Jun  7 16:48 Documents
drwxr-xr-x  2 root root 4.0K Jun  7 16:48 Music
drwxr-xr-x  2 root root 4.0K Jun  7 16:48 Pictures
drwxr-xr-x  2 root root 4.0K Jun  7 16:48 Public
drwxr-xr-x  2 root root 4.0K Jun  7 16:48 Templates
drwxr-xr-x  2 root root 4.0K Jun  7 16:48 Videos
-rw-r--r--  1 root root    0 Jun  7 19:56 output

---

### Post by rampageoberon on 2008-06-08
That output looks a lot like your home directory rather than the root directory.

I just noticed the chown command was a bit typoed, please do the following and see if it helps

```
chown -R brian:brian /home/brian
```

Actually just thinking about this I got some similar errors recently. Not sure what I did to mess things up on my system, but I ended up having to reinstall it.

---

### Post by bconover on 2008-06-08
Is there some other command that shows the root, as that is the output of "ls -ahl /".

I did chown -R brian:brian /home/brian. It did some stuff, but didnt seem to do anything for my problem, as I'm still getting the error messages at log in. 

At this point, would it just be best to reinstall? I would prefer not to, as it will be a pain to reinstall all my files.

---

### Post by rampageoberon on 2008-06-08
I'm out of ideas, maybe someone more knowledgeable will comment on this post. I backed up all my stuff onto a secondary partition and reinstalled the system.

Try asking on the irc channel, sorry can't help more.

---

### Post by bconover on 2008-06-08
Well, I need my computer, so I'm just going to reinstall Ubuntu, and deal with getting all my programs back. Luckily, I backed up most of my important files before this happened. Thanks for trying to help!

---

### Post by Naatan on 2008-06-09
when you are logged in as "brian" and type "cd ~" follow by "pwd"

what directory does it say?

From what we've seen here so far it seems almost as if your home directory is the root directory?! Which would be a major problem. I'd suggest backing up your files and reinstalling Ubuntu.

---

### Post by bconover on 2008-06-09
Yeah, I just reinstalled it. Now it's back to normal. No idea what the problem was, but at least now my computers up and running. Thanks for the help.

---

### Post by rampageoberon on 2008-06-09
Its good its all working now.

---

### Post by dangriff50 on 2008-07-30
FYI, this same exact problem happened to me.  I was opening a file while running a few background operations and the system froze, only to be solved by hard boot.  I subsequently got the same screens as the user above.  I have no important information on my ubuntu partition, so I will be reinstalling.

---

