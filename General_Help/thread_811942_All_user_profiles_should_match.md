---
title: "All user profiles should match"
date: 2008-05-29
forum: General Help
---

### Post by jimbob on 2008-05-29
I have a problem with users changing their profiles and Desktop screens while they are in class (actually grade school kids) so that many of the desktops are different the next morning making it difficult to begin the next day's class with everyone's screen looking the same.

Is there a way to store a default profile somewhere so that I can simply roll it back in to put those modified laptops back to the way they are supposed to be?

---

### Post by deadtom on 2008-05-29
I guess I'm confused. Are all your students logging in with the same username?

---

### Post by Monicker on 2008-05-29
Perhaps you could set up a cron job which automatically overwrites the home folders with a backup taken from your "ideal" configuration.

---

### Post by jimbob on 2008-05-29
No - the students are user1, user2, ... according to which laptop they are using, but they are all set up alike.  Each computer has an administrator account named "teacher" also.

My problem is I don't know which files to include in the "ideal" or "backup"
configuration.  I can't just copy the entire /home/user1 directory because there are some files that the children have created themselves that they saved in there.

---

### Post by TomSharp on 2008-05-29
You could just back up all the config folders, i.e. only the ones starting with .something. This way when you overwrite the home folder with your backup, you only replace all the folders which affect the desktop set up, not the folders students keep work in.
Better still, is it possible to set permissions in the home folder for all the config files such that only root can mess with them? This would stop people playing around with the desktop layout to begin with.

---

### Post by deadtom on 2008-05-29
What GUI are you using? In the case of KDE you could just have a cronjob remove the .kde folder and it would be automagically regenerated with the default settings next time they log in. However in this case anything they save to their desktop would be lost.

---

### Post by bingoUV on 2008-05-29
1. All configurations in /etc i.e. system wide. No per user configuration from your side. Background, bashrc, vimrc, whatever else that you need must be stored in /etc so that they apply system wide.

2. Every morning when you want to start afresh, run the script looking like 
```

sudo userdel <user_i>
sudo rm -rf /home/user_i
sudo adduser user_i

```

No way in hell that all systems not look identical when you want them to look so.

---

### Post by chrisccoulson on 2008-05-29
Wouldn't setting a mandatory key for '/desktop/gnome/background/picture_filename' in gconf stop people from changing the background image?

---

### Post by chrisccoulson on 2008-05-29
Setting a mandatory key works - I've just tried it. To stop people from changing the background, then do this:
[LIST=1]
[*]Open gconf-editor as root (gksudo gconf-editor)
[*]Navigate to /desktop/gnome/background/picture_filename
[*]Change the key value to the path of your desired background image
[*]Right click on key, and select 'Set as mandatory'
[*]Exit gconf-editor, log out and then back in again
[/LIST]

Only issue is that it makes the background mandatory for all users

---

### Post by jimbob on 2008-05-30
> Only issue is that it makes the background mandatory for all users

Thanks, that's great - that's exactly what I wanted.  Now I have to find out how to disable the panel menu that allows them to tinker with and even delete the panels on the top and bottom of the screen.

---

### Post by chrisccoulson on 2008-05-30
You could always try setting /apps/panel/global/locked_down as mandatory. It might give you the effect you want.

---

### Post by jimbob on 2008-05-30
> Only issue is that it makes the background mandatory for all users 
Help!  I changed the background image globally as suggested and now I cannot change it back.  The system tells me that everyting is read only now and trying to unset the key fails.

---

### Post by chrisccoulson on 2008-05-30
You need to re-open gconf-editor as root (gksudo gconf-editor), then go to File -> New Mandatory Window. In the new window, navigate to your mandatory key, right click on it and then click 'Unset Key'.

You will need to log out and back in again so that your GConf profile is re-loaded. Note, that a reboot may be in order because sometimes the gconf daemon doesn't exit when you log out :)

---

### Post by jimbob on 2008-05-30
Double thanks on this one.  That takes care of just about everything I will need to keep the curious little fingers from getting themselves (and me) in too deep.

Where did you accumulate so much knowledge about the Gnome configuration editor?

---

