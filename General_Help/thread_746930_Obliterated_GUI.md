---
title: "Obliterated GUI"
date: 2008-04-06
forum: General Help
---

### Post by WoosterB on 2008-04-06
I recently went through this process to install my soundcard:

[http://ubuntuforums.org/showthread.php?t=732512&highlight=soundblaster](http://ubuntuforums.org/showthread.php?t=732512&highlight=soundblaster)

unfortunately, it obliterated my graphics drivers and now the login/GUI will NOT come up.  I can park it at a command prompt in safe mode.  I don't know really what to do from there.

Do I need to re-re-re-install Ubunto?
Also, why is it whenever I try to install a sound driver, it kills my video drivers?

Moderators, would you please take a look at that thread and make sure there's nothing fishy?  I don't think Lazy8 was trolling but something in the download could have caused this.

-W

---

### Post by Gen2ly on 2008-04-06
Naw, WoosterB, I thnk this is legit.  Most people here in the forums are real good in how they treat one another.

As happens at times, especially when dealing with drivers, this can happen, though I must be honest I never heard of a soundcard driver taking down a video card driver in Linux.

First lets see if the download came with an uninstall program:

```
cd /usr/lib/oss/build/
ls
```

Do you see and unstall anything?

---

### Post by WoosterB on 2008-04-06
Again, I don't think Lazy8 was trolling.  I had some wild drivers (8800gtx) anyway so I'm wondering if that has anything to do with it.  I'll take a look at and report back what I find.

-W

---

### Post by WoosterB on 2008-04-06
ok, I didn't see anything with an uninstall type connotation.  There was an install.sh but thats what I used to install it all.

Regardless, I'm going to have to get my video driver/GUI back in some manner unrelated to sound.  either re-install Linux or get Linux to use an appropriate driver.  On a normal boot up, I get a window that says it can't find the driver.  I look at the one it will use anyway and "ok" it.  I've seen and used the normal one before.  However it goes into a blank screen and stays that way for a long period of time which leads me to suspect it'll not load.

On a sound note, I should do an OSStest, but not sure whether "safe mode" loaded the drivers.

-W

---

### Post by Gen2ly on 2008-04-06
Woo if one is real energetic they could look into install.sh and discover what was installed and the directory it was installed to.  If it's a new Ubuntu install though, re-installing would probably be quicker.  I'm not dis-qualifying Ubuntu but I do want to say it may be a good idea to look into another distro and see if they have better tested the hardware in question.  Many distro's are out there, debian and sabayon are both well known for their hardware support.

---

