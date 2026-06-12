---
title: "Need help (downgrade version? Something else?)"
date: 2012-12-20
forum: General Help
---

### Post by eumpfenbach on 2012-12-20
I posted this thread:

[http://ubuntuforums.org/showthread.php?t=2095624&page=2](http://ubuntuforums.org/showthread.php?t=2095624&page=2)


The computer is an HTPC and I pretty much just need it to play video. Was a little impatient and help thread wasn't getting results, so I upgraded from 12.04 (which wasn't working) to 12.10. I didn't realize how "experimental" that version was. Seems like everything has errors. Now when I boot I see my desktop, but not even the task bar. Video still not working (with the 12.10 driver I get no sound and the video plays super fast).

Any suggestions on what I should do? I read that downgrading is a B****. It's a 1 TB hard drive so I am thinking about just creating a partition and installing an old version of Ubuntu (maybe something from 2 years ago) that worked fine with video. This won't give me any trouble accessing files that are already on the hard drive on the old partition, right?

Any suggestions would be appreciated. I just want a Ubuntu version that plays freakin video without any problems.

---

### Post by dannyboy79 on 2012-12-20
nevermind, i saw from your other thread what graphcis card you're using.

from a command line issue this command
```
mplayer mediafilename
```

obviously change media filename with a movie that is "choppy" for you. then close mplayer and copy all the output from the command line and paste here. Do you have the medibuntu repo installed and the ubuntu-extras-restricted installed or whatever it's named?

---

### Post by eumpfenbach on 2012-12-20
Dude I really appreciate your help and if I can get back to a state where I can try this I definitely will.

Right now I have no task bar. All I can do is open up a folder from my desktop, which allows me to navigate the hard drive on the left side of the folder. I guess there is a way to get to everything (starting at the filesystem level, then going through the folders until I find an executable that launches the terminal) but at this point, I need some serious work on fixing my OS, then I will work on the video.

When I upgraded, it asked if I wanted to update a few conf files. I said no (thinking this was safer). Would this have caused this kind of behavior?

How do I get to system update through the file system to try and redo the update?

---

### Post by eumpfenbach on 2012-12-20
Let me ask a clear, simple question that I think would solve all my problems -- How do I do a reinstall of 10.04 without losing my data on my hard drive? Or do I just have to back everything up, wipe the drive, and then put my data back on there.

---

### Post by dannyboy79 on 2012-12-21
> **eumpfenbach said:**
> Dude I really appreciate your help and if I can get back to a state where I can try this I definitely will.

Right now I have no task bar. All I can do is open up a folder from my desktop, which allows me to navigate the hard drive on the left side of the folder. I guess there is a way to get to everything (starting at the filesystem level, then going through the folders until I find an executable that launches the terminal) but at this point, I need some serious work on fixing my OS, then I will work on the video.

When I upgraded, it asked if I wanted to update a few conf files. I said no (thinking this was safer). Would this have caused this kind of behavior?

How do I get to system update through the file system to try and redo the update?not using the updated conf files "could" be the culprit but not sure. can you hit ctrl-alt-f2, from there you can type in gnome-terminal so that you get to a terminal session. what version of ubuntu are you using?


> **eumpfenbach said:**
> Let me ask a clear, simple question that I think would solve all my problems -- How do I do a reinstall of 10.04 without losing my data on my hard drive? Or do I just have to back everything up, wipe the drive, and then put my data back on there.you'd have to backup all your important stuff and do a fresh install of 10.04 IF you wanted to run an older version of ubuntu

---

### Post by eumpfenbach on 2012-12-21
Well it was supposed to be 12.10 but something obviously went haywire with the upgrade.

So here is what I think my plan is:

1) Try and reinstall 12.10. Maybe I will be happy with it after a reinstall. At a minimum, a reinstall should make it easier to get everything to my external hard drive.

2a) If 12.10 is working better, try and get the video working.

if not,

2b) reinstall 10.04.

---

### Post by eumpfenbach on 2012-12-21
How can I make 12.10 reinstall from the terminal? If someone could post all the commands for that, it would be appreciated.

---

### Post by dannyboy79 on 2012-12-21
> **eumpfenbach said:**
> How can I make 12.10 reinstall from the terminal? If someone could post all the commands for that, it would be appreciated.
i would strongly suggest using 12.04 due to it being an LTS release but that's just me.

You can't just reinstall the OS from a terminal, you have to boot the computer to a live cd or usb stick and choose the install ubuntu option.

---

### Post by eumpfenbach on 2012-12-21
I've already gone up to 12.10. So I can go down to 12.04 (or in general 12.xx) but not anything earlier? Just verifying for my own knowledge.

If so, I'm good. Can install 12.04 from a cd no prob. That works, I will take my video question back to the multimedia and video section.

Thanks!

---

### Post by dannyboy79 on 2012-12-21
you can install whatever version you want really, I am not sure what your question is.

---

### Post by eumpfenbach on 2012-12-21
There are two kinds of installs:

1) I save my data to an external hard drive, install a new OS, and reload the data (ie, a fresh install)

or 

2) I reinstall the OS but my data stays (like an upgrade or a downgrade).

I kinda interpretted your recommendation of 12.04 as saying that I could downgrade to 12.04 from 12.10 given that it is a 12.xx installation. 

However, if now that I have gone up to 12.10 the only option for me is a fresh install which will wipe out my data, then I would prefer to go back to 10.04, because I had no video issues with this and it worked fine.

---

### Post by eumpfenbach on 2012-12-21
Or am I overthinking things and if I reinstall 10.04 from a live cd, all my data will still be there in the new OS?

I really appreciate your help. Given the sometimes irreversibility of stuff like this, I just want to be absolutely positive I don't accidentally lose everthing on my hard drive.

---

### Post by dannyboy79 on 2012-12-21
NO, you can't just downgrade ubuntu and your stuff will remain there. You have to perform a brand new install if you want to go back to any release prior to 12.10. You'll need to backup your stuff to somewhere which can then be restored after the installation has completed. 

It's obviously up to you but I wouldn't go back to 10.04 because its not going to be supported for much longer. I would install 12.04 and we'll troubleshoot from there. Assuming of course this is all software related and not related to a hardware issue.

---

### Post by eumpfenbach on 2012-12-21
OK. It's software. Was working fine until I went to 12.04. I'll do the reinstall and post here the current status of my video problems (I am assuming they will still be there but maybe I'll get lucky).

---

### Post by dannyboy79 on 2012-12-21
i would suggest going to multimedia section and post a new thread there IF it's still there after a reinstall. posting in this thread won't get much action from media playback helpers because the title isn't applicable to that.

So reinstall, if you have any issues with the reinstall, you can post them here BUT if it's media playback related, then start a new thread is my suggestion

---

