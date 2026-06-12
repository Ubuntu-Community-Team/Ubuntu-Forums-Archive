---
title: "Very odd startup message"
date: 2007-04-02
forum: General Help
---

### Post by Madmoose on 2007-04-02
Hello, 

Today I have a new issue. When I log in I get this message:

[QUOTE=Moose's Computer]User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user, and have 644 permissions. Users $home directory must be owned by user and not writable by others.[/QUOTE]

Now, I don't think I've changed any settings, but that doesn't mean I didn't. 

Anyway have any idea and a fix?

As always thank you!

Moose

---

### Post by rocknrolf77 on 2007-04-02
Try to delete the .ICEauthority file in your home folder. If you are not too fond of the terminal you can install midnight commander. A file manager for cli. 

```
sudo aptitude install mc
```

---

### Post by Madmoose on 2007-04-02
> **rocknrolf77 said:**
> Try to delete the .ICEauthority file in your home folder.]

Well, that didn't work. Any other ideas?

Moose

---

### Post by zorkerz on 2007-04-02
i think you need to just change permissions either on that file or your home directory entirely.

sudo chmod 644 $/home/.dmrc
you may need to replace the filename i put in ($/home/.dmrc) with its actual location I don't have this file so im not entirely sure what is causing it.

Also check the permissions of your home directory. right click and go to properties

Let us know if you found a solution.

Does this error appear to cause any problems?

---

### Post by Madmoose on 2007-04-02
Put this in:
```
sudo chmod 644 $/home/.dmrc
```

I get this:

```

chmod: cannot access `$/home/.dmrc': No such file or directory
```


Here is what I have for permissions on the home folder: (See Photo)

The only thing that isn't working is the "About Me" log in photo no longer shows up.

---

### Post by Wiebelhaus on 2007-04-02
I'm having this issue as well , i think it's from something i've installed but it doesn't seem to effect anything negativly.

---

### Post by zorkerz on 2007-04-02
type tho same command again except replace $/home/.drmc with the location of your home directory.  default is /home/username/.drmc  (judging by your picture it would be /home/madmoose/.drmc) 

I believe the warning says to change your home folder permissions under group section to
folder access -> access files
file access -> read only

I hope this works for you.

sx66gns is right i think that some application is causing this.  maybe .drmc gives a hint to what it is?

---

### Post by Wiebelhaus on 2007-04-02
> **Madmoose said:**
> Hello, 

Today I have a new issue. When I log in I get this message:



Now, I don't think I've changed any settings, but that doesn't mean I didn't. 

Anyway have any idea and a fix?

As always thank you!

Moose

thanks to ricardisimo:

in this thread:
[http://www.ubuntuforums.org/showthread.php?t=371052&highlight=home+being+ignored](http://www.ubuntuforums.org/showthread.php?t=371052&highlight=home+being+ignored)

Here's the fix that worked for me provided by richard , thanks man!

> sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo

replace his name with yours of course.

---

### Post by Madmoose on 2007-04-03
> **sx66gns said:**
> sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo

That worked! Thanks All! :guitar:

---

