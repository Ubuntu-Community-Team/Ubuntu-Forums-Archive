---
title: "Deja-Dup (Backup) Cannot backup files"
date: 2015-07-06
forum: General Help
---

### Post by subcook on 2015-07-06
I'm running Kubuntu 14.04 LTS

Trying to backup as I'm fairly new to Ubuntu and am sure I'm going to have to revert at some point.

I'm getting the message :

Could not backup the following files.  Please make sure you are able to open them.

/home/~/.cache/dconf
/home/~/.dbus

through research I'm seeing two answers. one is that I should ignore it, the other is that I should chown and chgrp .  I'm thinking that these directories should not be owned by root though so I'm feeling conflicted.

Should I change ownership and back them up ? ... or should I ignore it and be confident that all is well when the time comes that I have to restore ?

Thank in advance

---

### Post by CaptainMark on 2015-07-06
Don't change ownership of anything, in any situation unless you have exhausted all other option. 

It looks as simple as you've inputted the destination of your home folder incorrectly, the shorthand ~/ stands for your home folder so /home/~/.cache is trying to look for /home/home/subcook/.cache which doesn't exist. In deja dup check you have the correct folders chosen for back up, after that post the output from the command ```
ls -lah ~/
```

---

### Post by subcook on 2015-07-06
thanks for replying CaptainMark,

Under "folders to save" it shows:  home (pleh)        ----pleh is my user name

This backup application seems pretty cut and dry.

ls -lah ~/ shows this (keep in mind this is a fresh install :

```
total 136K
drwxr-xr-x 24 pleh pleh 4.0K Jul  6 01:23 .
drwxr-xr-x  4 root root 4.0K Jul  5 21:46 ..
drwx------  3 pleh pleh 4.0K Jul  6 01:04 .adobe
-rw-------  1 pleh pleh 1.4K Jul  6 00:01 .bash_history
-rw-r--r--  1 pleh pleh  220 Jul  2 08:59 .bash_logout
-rw-r--r--  1 pleh pleh 3.6K Jul  2 08:59 .bashrc
drwx------ 11 pleh pleh 4.0K Jul  6 00:34 .cache
drwx------  9 pleh pleh 4.0K Jul  6 01:28 .config
drwx------  3 root root 4.0K Jul  5 23:08 .dbus
drwxr-xr-x  2 pleh pleh 4.0K Jul  2 11:05 Desktop
-rw-r--r--  1 pleh pleh   29 Jul  2 11:05 .dmrc
drwxr-xr-x  2 pleh pleh 4.0K Jul  6 01:02 Documents
drwxr-xr-x  2 pleh pleh 4.0K Jul  5 22:52 Downloads
drwx------  2 pleh pleh 4.0K Jul  6 00:33 .gconf
drwx------  3 pleh pleh 4.0K Jul  6 00:04 .gnupg
-rw-r--r--  1 pleh pleh   82 Jul  2 11:05 .gtkrc-2.0
drwxr-xr-x  4 pleh pleh 4.0K Jul  2 11:05 .kde
drwx------  3 pleh pleh 4.0K Jul  2 11:05 .local
drwx------  3 pleh pleh 4.0K Jul  6 01:04 .macromedia
drwx------  4 pleh pleh 4.0K Jul  2 11:08 .mozilla
drwxr-xr-x  2 pleh pleh 4.0K Jul  2 11:05 Music
drwxr-xr-x  2 pleh pleh 4.0K Jul  6 01:19 Pictures
drwx------  3 pleh pleh 4.0K Jul  6 01:03 .pki
-rw-r--r--  1 pleh pleh  675 Jul  2 08:59 .profile
drwxr-xr-x  2 pleh pleh 4.0K Jul  2 11:05 Public
-rw-------  1 pleh pleh  256 Jul  6 01:03 .pulse-cookie
drwxrwxr-x 20 pleh pleh 4.0K Jul  6 01:07 .steam
drwxrwxr-x  3 pleh pleh 4.0K Jul  6 01:03 Steam
lrwxrwxrwx  1 pleh pleh   29 Jul  6 01:07 .steampath -> /home/pleh/.steam/bin32/steam
lrwxrwxrwx  1 pleh pleh   27 Jul  6 01:07 .steampid -> /home/pleh/.steam/steam.pid
drwxr-xr-x  2 pleh pleh 4.0K Jul  2 11:05 Templates
drwx------  4 pleh pleh 4.0K Jul  6 01:02 .thumbnails
drwxr-xr-x  2 pleh pleh 4.0K Jul  2 11:05 Videos
-rw-------  1 pleh pleh  100 Jul  6 00:06 .Xauthority
-rw-------  1 pleh pleh 2.3K Jul  6 00:57 .xsession-errors
-rw-------  1 pleh pleh  208 Jul  6 00:06 .xsession-errors.old
```

Also be aware that my device name is the same as my user name, which was an accident (facepalm). I have yet to change that but dont see how that could make a difference when it comes to backup unless I change it than try to restore, but I would change it and just create a fresh backup immediately anyway

---

### Post by CaptainMark on 2015-07-06
Well the fact that .dbus is showing as being owned by root is unusual, you'll be able to safely change that to your own user with```
sudo chown -R pleh:pleh ~/.dbus
``` .cache is shown as being owned by you so maybe narrow it down by showing the output of this command which reveal any files in cache not owned by you```
find ~/.cache ! -user pleh
``` alternatively you could either empty the cache (just delete its contents) or what I would recommend would be to omit it from the backup altogether, do you need to backup countless thumbnails from your programs? Probably not, but it's up to you.

---

### Post by subcook on 2015-07-07
Captain Mark,

I did this :  
sudo chown -R pleh:pleh ~/.dbus

I thought I pointed that out in my original post, not sure .........

the output of : 
find ~/.cache ! -mark pleh


shows this :

find: unknown predicate `-mark'


Now im really confused and feeling lost ....


chanced are that I can indeed omit it, I'm learning (wouldn't call myself totally new, but would admit that I'm close)


thoughts ?

---

### Post by CaptainMark on 2015-07-07
Ah, derp, that's my fault, I checked I got the syntax right on my own computer first and then removed the correct flag instead of my own user name before posting :P try again with the new command above where I'll edit my post. Also I'm not sure if you're saying you already performed a chown command on the .dbus directory before you posted the output of ls, if so it hasn't worked so try this to get more information about why.
```
sudo chown -Rv pleh:pleh ~/.dbus
```If you just mean you were going to do it, don't worry, I only advised extreme caution because a slightly mistyped chown command can really screw things up irreversibly.

I would argue that it's almost completely unnecessary to back up ~/.cache it just contains thumbnails and small files for programs like web browsers and file managers, if you were to lose this folder the programs in question would just recreate those thumbnails if it needs them, most of them will just be previews of photos and videos you have saved on your computer. I have ~/.cache omitted from my back ups.

---

### Post by subcook on 2015-07-07
Capt Mark,

I did do the chown ... now I am completely lost ! :-)

After running this :

sudo chown -Rv ~/.dbus

I get this :



chown: missing operand after ‘/home/pleh/.dbus’

I'm clearly lost and a noob ....

I'll go ahead and take your word for it and "ignore" the ~/.dbus directory ...... but now I'm concerned about the latter.  starting to think that both directories can be ignored...

thoughts ?

I know I'm going to mess this up, probably a bunch, I just need to backup all of my changes so when I (ex: let's say I accidently fudge my /X11) ... I can get it back...


thoughts ?

---

### Post by CaptainMark on 2015-07-07
Man I am having such a bad day today, I've only just gone and missed off the most vital part of that command of your username. 2nd time now, I've edited the chown command for dbus so try that again.

---

### Post by subcook on 2015-07-07
No worries, your the one helping me.

I did this :



sudo chown -Rv pleh:pleh ~/.dbus

....and got this :


ownership of ‘/home/pleh/.dbus/session-bus/f7516e334124fd38423934be5599eb1d-0’ retained as pleh:pleh
ownership of ‘/home/pleh/.dbus/session-bus’ retained as pleh:pleh
ownership of ‘/home/pleh/.dbus’ retained as pleh:pleh

---

### Post by CaptainMark on 2015-07-07
Well that stumps me, you are the owner of all the files within ~/.dbus so you shouldn't get any error. I'm sorry I don't think I can help much more, it seems to think you don't have permission to read those files but you do because you are the owner. You can safely omit from them from the backup, they are all non crucial self creating files. As to why you are getting the error, sorry I'm out of ideas.

---

### Post by subcook on 2015-07-09
May I ask that you cut/past the actual command so that I dont mees it up ?

---

### Post by CaptainMark on 2015-07-09
Okay so back to the top then if you paste these two lines into a terminal and copy and paste the full output back. Please use the code tags found in the advanced reply section so it formats correctly.

```

find /home/pleh/.cache/ ! -user pleh -o ! -group pleh -exec ls -lah {} \;

```
```

find /home/pleh/.dbus/ ! -user pleh -o ! -group pleh -exec ls -lah {} \;

```
This looks for any files in either ~/.dbus and ~/.cache the you don't own or dont belong to your group and prints more details about them. Post back any response, if you get literally no hits from this then sorry I'm totally stumped as whats wrong.

---

### Post by subcook on 2015-07-09
for some reason my replies are not going through, can you type out that command again to ensure I get it correctly ?

For whatever reason the thread updated after my last reply ...


Both of these commands yield nothing .... I have no idea where to even begin ....

At this point I'm just happy to know that I can update and especially restore without worries.

Thank for the help

---

