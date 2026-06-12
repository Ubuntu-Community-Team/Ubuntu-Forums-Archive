---
title: "authentication failed, locked out"
date: 2007-11-12
forum: General Help
---

### Post by garethrv on 2007-11-12
Hey,

I have a quite upsetting situation here.

I have always had my account set to automatic login for ubuntu, which I am dual booting on my macbook. Today I made up a guest account so I could let me friends stuff around and explore ubuntu without concern so I went and turned off automatic login.

Well now I try and start ubuntu and when it gets to the login screen "Authentication failed" pops up before I even touch anything. I click ok but it does not go away just stays there (or refreshes itself each time I click ok I think, but not sure if thats significant)

So at the moment I am in OSX and would really like to get back into ubuntu. (I just set up compiz and awn and was having a great time)

The only thing that I can think of that may be a contributing factor is that the other day I put some commands into terminal after reading a how to on stopping the nm-applet (as far as I remember) from asking for the key chain password to get my wireless going everytime I boot up. It didnt fix the problem so I assumed it had done nothing.

I can get into recovery mode, but being new I have no idea where to go from there.

Thank you,

Gareth.

---

### Post by garethrv on 2007-11-12
My options are, as far as I can tell, change back to auto login from the terminal in recovery mode, undo the changes I made which caused the problem (im tracking down the how to now) or wipe everything and reinstall from scratch (I really dont want to do this, unless you can help me keep all my installed programs and settings??)

Please someone muct know how to do this.

Thank you.

---

### Post by garethrv on 2007-11-12
Aright,

Here is another thread in which this one guy mentions that he had the same problem after the nm-applet fix. He says he just edited the file in recovery mode and commented out the lines he added at the end. I do know that putting a # in front of a line comments it out, but I dont know how to edit a file in recovery mode, the gedit command does not work, it cant display it or something.

[http://ubuntuforums.org/showthread.php?t=187874&page=17](http://ubuntuforums.org/showthread.php?t=187874&page=17)

So now you know what I have to do can someone please help me do it.

Editing from recovery mode.

Thank you.

---

### Post by David_1cog on 2008-01-20
To edit in recovery mode, or whenever gedit is not available, use:

```
sudo nano /path/to/file
```

---

