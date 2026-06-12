---
title: "Stepmania Online CVS"
date: 2005-08-27
forum: General Help
---

### Post by Savukala on 2005-08-27
Okay I'm trying to run this program [http://www.stepmaniaonline.com/index.php?mod=Downloads&group=10](http://www.stepmaniaonline.com/index.php?mod=Downloads&group=10) and the console says this: "./stepmania: error while loading shared libraries: libavformat.so: cannot open shared object file: No such file or directory" can someone help me with this? I'm still new on using Ubuntu but I would never like to switch back to the windows, I hope you can help me with this  :)

---

### Post by gerbman on 2005-08-28
[QUOTE=Savukala]Okay I'm trying to run this program [http://www.stepmaniaonline.com/index.php?mod=Downloads&group=10](http://www.stepmaniaonline.com/index.php?mod=Downloads&group=10) and the console says this: "./stepmania: error while loading shared libraries: libavformat.so: cannot open shared object file: No such file or directory" can someone help me with this? I'm still new on using Ubuntu but I would never like to switch back to the windows, I hope you can help me with this  :)[/QUOTE]

I had the same problem.  It looks like the ffmpeg package that Synaptic installs doesn't put 'libavformat.so' anywhere, hence the error.  The workaround I found is to install an older RPM of ffmpeg.  Here's what to do:

Download the RPM [here](ftp://rpmfind.net/linux/dag/redhat/8.0/en/i386/dag/RPMS/ffmpeg-0.4.8-2.rh80.dag.i386.rpm) (the site is really slow sometimes)

Go to the directory where you downloaded the RPM to and do ```
sudo alien -d -i -c <RPM file>
``` where <RPM file> is the actual file name.

Now if you do ```
ls /usr/lib | grep avformat
``` you should see ```
libavformat.so
``` somewhere.

The only other thing I had to do was disable Ubuntu's sound server to stop it from tying up my sound card.  Go to "System", "Preferences", "Sound", and uncheck "Enable sound server startup".  

Hope this helps...happy dancing!

Edit:  I also remember having to make a number of links in /usr/lib to the files Stepmania expects to see.  So if the above doesn't make it work just post your errors.  Also, since installing the RPM downgrades the ffmpeg package, the update manager in Ubuntu will want to try to upgrade ffmpeg.  Doing so will remove libavformat.so and you'll get the same error as before.

---

### Post by Savukala on 2005-08-28
Well that helped but now there is new error.

> ./stepmania: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

---

### Post by gerbman on 2005-08-28
[QUOTE=Savukala]Well that helped but now there is new error.[/QUOTE]

What does ```
ls -l /usr/lib | grep libpng
``` output?

---

### Post by Savukala on 2005-08-28
Returns this:

> lrwxrwxrwx   1 root root      19 2005-08-22 22:39 libpng12.so.0 -> libpng12.so.0.1.2.8
-rw-r--r--   1 root root  142612 2004-12-05 05:39 libpng12.so.0.1.2.8

---

### Post by gerbman on 2005-08-28
[QUOTE=Savukala]Returns this:
```
lrwxrwxrwx 1 root root 19 2005-08-22 22:39 libpng12.so.0 -> libpng12.so.0.1.2.8
-rw-r--r-- 1 root root 142612 2004-12-05 05:39 libpng12.so.0.1.2.8
```[/QUOTE]

Stepmania is looking for 'libpng.so.3', so you can create a symlink by that name to the libpng file you have:

```
sudo ln -s /usr/lib/libpng12.so.0.1.2.8 /usr/lib/libpng.so.3
```

I had to do this for a number of library files that Stepmania looks for.  They were there in the directory, but under different names.  If you're not familiar with the 'ln' command, type 'man ln' at the command prompt and read up on it.  I'd say this is a safe workaround as long as you know you are linking to the right file.

Edit:  Stepmania should then find libpng.so.3, but will probably complain about a different file.  You should be able to repeat the procedure, again making sure you're linking to the correct file.

---

### Post by Dreezard on 2005-10-13
There is another way to fix this problem.
I tried your workaround and it worked. But if you do an apt-get dist-upgrade it will install the newer ffmpeg version from Ubuntu.
So I extracted the missing files (libavformat.so and libavcodec.so) from a Mandrake-package in the version 1.2.9 and made a DEB package of it so that the libs are in another package and so that you can just do an apt-get dist-upgrade without worries ^^.

You just need to install that package, run StepMania and have some fun ;-).
The soft-links are preconfigured.

link: [http://home.arcor.de/dreezard/libffmpeg.deb](http://home.arcor.de/dreezard/libffmpeg.deb)

---

### Post by gerbman on 2005-10-13
> **Dreezard]There is another way to fix this problem.
I tried your workaround and it worked. But if you do an apt-get dist-upgrade it will install the newer ffmpeg version from Ubuntu.
So I extracted the missing files (libavformat.so and libavcodec.so) from a Mandrake-package in the version 1.2.9 and made a DEB package of it so that the libs are in another package and so that you can just do an apt-get dist-upgrade without worries ^^.

You just need to install that package, run StepMania and have some fun  said:**
> http://home.arcor.de/dreezard/libffmpeg.deb[/url]

Kudos...I like that much better

---

