---
title: "GDM no space on disk"
date: 2007-08-01
forum: General Help
---

### Post by mspainter on 2007-08-01
I have done a little bit of searching on these forums, and even more on google, but I cannot find out why Ubuntu is reacting in this way. 

He is what is happening. I am trying to log on. After typing in user and password, I get the following message:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator. "

The administrator part makes me laugh, because I am the administrator. I do not know much of ubuntu and how it works as I've only been using it for about 2 months. It worked flawlessly (well one java problem) up until this point. Does anyone know what this error message means or am I going to have to reinstall Linux. This would not be good, as no less than 2 hours after my America's Army download finished, (which took me around 14 hours), I get this crash. So 14 hours would be wasted. (But that is really the only file I have saved.) Lastly, there is no way that my disk is full, there is at least 12gb left to my hard drive.

---

### Post by wpshooter on 2007-08-01
You say you have 12gb left on your drive BUT are you sure that either your root directory or your home directory have not been filled up by your 14 hour download, i.e. you might have 12gb left but do you have any open space in the place that the GDM needs ?

---

### Post by mspainter on 2007-08-01
> **wpshooter said:**
> You say you have 12gb left on your drive BUT are you sure that either your root directory or your home directory have not been filled up by your 14 hour download, i.e. you might have 12gb left but do you have any open space in the place that the GDM needs ?

No?

My download took only 2.5gb of space. I have the file under /home/matt/

Does this affect that? Also, what difference does it make. Let's say it was in the way, how could I move the file so that I can successfully log in?

---

### Post by wpshooter on 2007-08-01
"MAY" not be the problem but you could boot to the live CD to try to change the file to a different location or delete BUT first have you tried booting into recovery mode ?

---

### Post by mspainter on 2007-08-01
Recovery mode did not work. 

Boot from Live disk started off with an error message telling me that some themes and sounds my have changed, and after further searching, my desktop only contained 96mb of free space. 

The live CD doesnt show me the items I had on my desktop but acknoledges that they still exist. Can you help show me the path through file system that will lead me to desktop to move or delete this file?

---

### Post by tonyisntcreative on 2007-08-01
I'm not sure how it would have happened, but it sounds like either the GDM config file had its permissions changed or it was deleted.

Can you boot up at all, even by switching to the "text only" mode (Cont + Alt + F1)? If so, you should be able to fix things somehow... I'm just not entirely sure how.

But it *does* sound like your root partition is full, or pretty close.  With 90-some MB free, you would think there would be enough room to write to a simple *config file*, but if it's going to whine about it it's worth a shot to move the file.

If you have other partitions with more space or an extra hard drive you should probably put  the file on that.  If you don't, do you have a DVD burner and some DVD-Rs?

If you can boot into text-only mode your partitions should auto-mount, so you won't have to deal with that.  A simple "mv whatevertheinstallfileiscalled" to whatever folder your other partitions/drives are mounted on will do the trick.  I'm not entirely familiar with DVD or CD burning from the command line, so someone else would have to tell you about that.

---

### Post by mspainter on 2007-08-01
I have DVD-R's, but they are for my laptop, this computer doesnt have a burner. I have the file saved twice I think, so If I could delete one it would free up about 2.5 gigs. This is a 20gb HD, and because I have nothing but linux and this file on it, (as well as teamspeak) I don't see how it could have gotten so full. I can try to get into the text mode, but i need help with deleting the file. I know where it is located (/home/matt/desktop/Americas_Army), so If you could help me through the deletion process that would be cool.

---

