---
title: "Unable to install from source code after extraction"
date: 2008-02-23
forum: General Help
---

### Post by nvance on 2008-02-23
Greetings,

I am trying to install an application from the source files.  I have sucessfully extracted the files to my home folder and then via the terminal I go into the new directory and do a " ./configure " I get the following error message "GTK+ not found or too old (version < 2.6)".  How do I get the latest GTK + ?
Also, I seem to have an issue with using the "make" command, I have never been able to get it to work...is there something that I have to install in order to make it work?  With this install I am getting the error message (ignoring the previous GTK error) "make: *** No targets specified and no makefile found.  Stop."

Any information would be very much appreciated as I would like to install this application.

Thanks,
Nate

---

### Post by rodo-&gt;dave on 2008-02-23
System->Admin->Synaptic

Search for GTK
Scroll down to libgtk2.0-dev (should be rev 2.10)

[Edit sorry:forgot to include INSTALL :) libgtk2.0-dev]

Then do a ./configure again to build your makefile (note: you may also have an autogen.sh file that you need to run that will run configure - just an FYI)

Good Luck.

---

### Post by oldos2er on 2008-02-23
Usually there's a README or INSTALL file that tells you of any dependencies needed; then you can search for and install them through Synaptic Package Manager.

 "make" won't work until you've successfully run ./configure .

 For more info see [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by jcwmoore on 2008-02-23
looks like you are missing dependencies needed to build from source, I think the way to get them is by 

```
sudo apt-get build-dep NAME_OF_PROGRAM
```

or instead of biuld-dep it might be "build-essential"  after that you should be able to run make, and make install and all that other good stuff to build from source.

EDIT:

What program are you trying to install?

---

### Post by nvance on 2008-02-23
Thank you for all the answers.  I was specifically trying to install Aqualung (audio player/organizer) that was included in last months Linux Format magazine DVD.y

I will give everyones options a try and see how it goes

---

### Post by SOULRiDER on 2008-02-23
Check out [http://ubuntuforums.org/showthread.php?t=207404](http://ubuntuforums.org/showthread.php?t=207404)

EDIT: I just checked the date... its a very old thread..

---

### Post by SOULRiDER on 2008-02-23
Actually, check out thsi site, there seems to be a deb of the latest version.
[http://linuxappfinder.com/package/aqualung](http://linuxappfinder.com/package/aqualung)

---

### Post by nvance on 2008-02-23
Greetings again,

After installing the dev packages for GTK, things worked.  Too bad the program was kind of a flop :)

Once again the users of the Forums have the right answers.

Much Thanks!!

---

