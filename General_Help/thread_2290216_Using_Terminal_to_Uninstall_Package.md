---
title: "Using Terminal to Uninstall Package"
date: 2015-08-10
forum: General Help
---

### Post by LaughingHorse on 2015-08-10
While I have been a Ubuntu User for many years, I am really weak at terminal commands.

Recently I tried using terminal to install the AVG anti-virus package.
I got an error, and the installation would not complete. After doing research (Yeah, I should have researched before) i found it is for 32 bit, not 64 bit like my computer so I want to remove it.

I just want to make sure the command:
```
sudo dpkg -r avg2013flx-r3118-a6926.i386.deb
```
is correct, as I do not want to screw up the installation :)

Thanks in advance for your advice.

---

### Post by v3.xx on 2015-08-10
How did you install it?  From the site, a ppa, other?

---

### Post by QDR06VV9 on 2015-08-10
Follow this post #7 [http://ubuntuforums.org/showthread.php?t=2186126](http://ubuntuforums.org/showthread.php?t=2186126)
Regards

---

### Post by LaughingHorse on 2015-08-10
straight from terminal. No PPA
[http://www.unixmen.com/install-avg-free-antivirus-on-ubuntu/](http://www.unixmen.com/install-avg-free-antivirus-on-ubuntu/)

---

### Post by LaughingHorse on 2015-08-10
Thank you runrickus, I'll try that.

---

### Post by deadflowr on 2015-08-10
> **LaughingHorse said:**
> While I have been a Ubuntu User for many years, I am really weak at terminal commands.

Recently I tried using terminal to install the AVG anti-virus package.
I got an error, and the installation would not complete. After doing research (Yeah, I should have researched before) i found it is for 32 bit, not 64 bit like my computer so I want to remove it.

I just want to make sure the command:
```
sudo dpkg -r avg2013flx-r3118-a6926.i386.deb
```
**is correct, as I do not want to screw up the installation **:)

Thanks in advance for your advice.


well, no.
That is a .deb file and isn't actually a package.
You need to give the actual name of the package as it is installed, not the installer's name.
If that makes sense.

I'd use dpkg -l (list) to do that.
I usually use it like so
```
dpkg -l | grep *some-part-of-what-I-know-about-the-package-name* | awk '{print $2}'
```
this will print out all packages installed on the system that have whatever phrase I put in the grep pipe.
And it will print out only the package names, it'll disregard the package state (ii, rc, etc,etc) and whatever description the package has.

(Note names like 'avg' should only return a few entries, if even. But something generic like 'lib' will return hundreds, if not thousands)

Also not that the awk pipe is totally optional, but makes it easier to see just the package names, without all the extra cruft (some descriptions can be long and tend to wrap, making it hard to figure out which package is which, sometimes)

From there you should see exactly what the name is and use that name as the file name in the dpkg -r command.

Hope it helps.
Or makes sense...

---

### Post by LaughingHorse on 2015-08-10
Thank you.

I had just run
```
sudo ln -s /bin/true /etc/init.d/avgd
```

And I got 
> ln: failed to create symbolic link ‘/etc/init.d/avgd’: File exists

So without really knowing what I was doing I ran
```
sudo dpkg -R -P avg2013flx
```
And got
> (Reading database ... 209399 files and directories currently installed.)
Removing avg2013flx (2013.3118) ...
Failed to stop avgd.service: Unit avgd.service not loaded.
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing package avg2013flx (--purge):
 subprocess installed pre-removal script returned error exit status 5
Errors were encountered while processing:
 avg2013flx 


---

### Post by Bashing-om on 2015-08-10
LaughingHorse; Hello ;

Are you certain " avg2013flx " is the version you have installed ?
Then see:
[http://askubuntu.com/questions/631370/problem-removing-avg](http://askubuntu.com/questions/631370/problem-removing-avg)

See if that is also your situation.

Hope this helps

---

### Post by LaughingHorse on 2015-08-11
@ Bashing-om,

Yes it is avg2013flx

Thank you for the link. It seems like that may do the job for me.

---

