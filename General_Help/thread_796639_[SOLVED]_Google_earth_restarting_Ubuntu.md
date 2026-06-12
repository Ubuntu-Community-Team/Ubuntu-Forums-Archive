---
title: "[SOLVED] Google earth restarting Ubuntu"
date: 2008-05-16
forum: General Help
---

### Post by ekmon1582 on 2008-05-16
When I fire up Google Earth, just before it actually brings Google Earth up, it restarts Ubuntu, and of coarse everything is closed. Anyone know why? I'm using Ubuntu 8.04 with VMWare server.

---

### Post by Patb on 2008-05-16
Ekmon, I'm not sure whether this is any help.  I do not run GE in a VM but I always had problems with it crashing, in several different Ubuntu versions, until I followed the advice in:
[http://ubuntuforums.org/showpost.php?p=3227468&postcount=8](http://ubuntuforums.org/showpost.php?p=3227468&postcount=8)

Cheers, Pat.

---

### Post by ekmon1582 on 2008-05-19
Thanks for the reply, but that one file that Kilz suggested, I downloaded it, but how do I install it? Is installing that file the only thing I need to do? Or am I missing something in that thread?

---

### Post by Patb on 2008-05-19
Ekmon, that is a compressed file with two files inside it.  To extract, open a terminal and go to the directory where it is and type:
```
tar -zxvf libGL.tar.gz
```
This will extract two files called libGL.so.1 and libGL.so.1.2.  As root, copy these two files to your google-earth directory.  This is the program directory which probably already contains several other lib* files, not ~/.googleearth which contains settings and cache etc.  Its location depends on where GE is installed.  

And yes, that is all I had to do to solve my problem.  But I reiterate my system is not in a VM so it is a long shot whether it works for you.  Please post the results.  Good luck.  

Cheers, Pat.

---

### Post by ekmon1582 on 2008-05-20
I opened a terminal, and typed in that code, but it said it couldn't open it. It said there was "no such file or directory." Or am I doing this wrong?

---

### Post by Patb on 2008-05-22
> **ekmon1582 said:**
> It said there was "no such file or directory." Or am I doing this wrong?
It sounds like you are not in the correct directory or you have a typographical error.  Linux is mostly case-sensitive.  "ls" in the directory to check its contents.  

Sorry if this is really basic but another hint is to use linux's tab function which will complete a file path or or give you possible options.  So for your case, type "tar -zxvf lib" then hit tab, maybe twice.  If libGL.tar.gz is there, it will be listed.  

This is not only a shortcut of course, it helps avoid typos.  Have fun.  

Cheers, Pat.

---

### Post by ekmon1582 on 2008-05-22
Tried pressing tab... nothing happened :(.

---

### Post by Patb on 2008-05-22
And what is the output of:
```
ls -l
```If it does not include "libGL.tar.gz" then:
```
cd /directory/where/you/saved/libGL.tar.gz
tar -zxvf libGL.tar.gz
```

---

### Post by ekmon1582 on 2008-05-23
The output of ls -l is:
total 32
-rw-r--r-- 1 ekmon1582 ekmon1582 1721 2008-05-20 12:14 clipdat2.rdf
drwxr-xr-x 2 ekmon1582 ekmon1582 4096 2008-05-21 16:02 Desktop
drwxr-xr-x 2 ekmon1582 ekmon1582 4096 2008-05-20 09:19 Documents
lrwxrwxrwx 1 ekmon1582 ekmon1582   26 2008-05-12 10:48 Examples -> /usr/share/example-content
drwxr-xr-x 2 ekmon1582 ekmon1582 4096 2008-05-12 16:12 Music
drwxr-xr-x 2 ekmon1582 ekmon1582 4096 2008-05-22 07:26 Pictures
drwxr-xr-x 2 ekmon1582 ekmon1582 4096 2008-05-12 16:12 Public
-rw-r--r-- 1 ekmon1582 ekmon1582    0 2008-05-16 10:14 sh
drwxr-xr-x 2 ekmon1582 ekmon1582 4096 2008-05-12 16:12 Templates
drwxr-xr-x 2 ekmon1582 ekmon1582 4096 2008-05-12 16:12 Videos

I saved that file to the desktop, I tried the path cd /directory/desktop/libGL.tar.gz and cd /directory/ekmon1582/desktop/libGL.tar.gz , but it just gave me 'no such file or directory.' What should I type in for that code if I saved it to the desktop?

---

### Post by Nitewalker on 2008-05-23
Thanks for your link to the new lib files, followed you instructions and now works, even though very slow, but that is my video cars problem.  Thanks again..JSM:popcorn:

---

### Post by Patb on 2008-05-23
Ekmon, first a short driving lesson :).   

Prof Google will give you lots of explanations of the linux file structure.  Well worth reading up on.  Here's one which also has a link to the "linux command line" or terminal, which might be useful:
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

When you open a terminal normally, you will be in your home directory which I think for you is /home/ekmon1582/.  (You will often see the notation "~/" which is exactly the same directory - linux takes the "~/" as meaning the user's home directory.)  So by typing "ls -l" at that point, you will get a detailed file list for all files and directories in your home directory /home/ekmon1582/.  

Your "cd" command failed because you have no directory starting with "/directory/".  Look at the right hand column of your output though and you will see "Desktop" ie you have a directory called "Desktop" in your home directory.  Its full name will be /home/ekmon1582/Desktop/ and if I'm not mistaken in it will be your libGL.tar.gz file. 

So the commands we now need are:
```
cd ~/Desktop
tar -zxvf libGL.tar.gz
```
Now to reiterate, this will extract two files called libGL.so.1 and libGL.so.1.2.  As root, copy these two files to your google-earth directory. This is the program directory which probably already contains several other lib* files, not ~/.googleearth which contains settings and cache etc.  To copy as root you will need to do something like:
```
sudo cp libGL.so* /FullPathToYourGoogle-EarthDirectory/
```

If you get stuck on that, I should be able to help if you run the following two commands and post the output of the second:  
```
sudo updatedb
locate google-earth | grep lib
```
I should also repeat that I'm not at all sure this will solve your problem with GE but it should do no harm to try. 

Finally, a note on this tab completion.  In a terminal, type "cd /ho" and hit tab (not return).  Then add "ek" and hit tab.  Then add "De" (not "de", linux is case sensitive) and hit tab.  Then hit enter and type "ls". :).  If you're like me, you'll very quickly become quite attached to your tab button.  Sorry, no offence, but I'm laughing because it's so easy when you know how :).  

Hope this helps.  Cheers, Pat.

---

### Post by ekmon1582 on 2008-05-29
OK well I got the two files extracted, so that's a little headway :). But got stuck on the second part, and here's the outcome of that command you wanted me to put in if I got stuck there;

/opt/google-earth/libGLU.so.1
/opt/google-earth/libIGAttrs.so
/opt/google-earth/libIGCollision.so
/opt/google-earth/libIGCore.so
/opt/google-earth/libIGDisplay.so
/opt/google-earth/libIGExportCommon.so
/opt/google-earth/libIGGfx.so
/opt/google-earth/libIGGui.so
/opt/google-earth/libIGMath.so
/opt/google-earth/libIGOpt.so
/opt/google-earth/libIGSg.so
/opt/google-earth/libIGUtils.so
/opt/google-earth/libQt3Support.so.4
/opt/google-earth/libQtCore.so.4
/opt/google-earth/libQtGui.so.4
/opt/google-earth/libQtNetwork.so.4
/opt/google-earth/libQtSql.so.4
/opt/google-earth/libQtXml.so.4
/opt/google-earth/libalchemyext.so
/opt/google-earth/libapiloader.so
/opt/google-earth/libauth.so
/opt/google-earth/libbase.so
/opt/google-earth/libbasicingest.so
/opt/google-earth/libcollada-1.4.so
/opt/google-earth/libcollada.so
/opt/google-earth/libcommon.so
/opt/google-earth/libcomponentframework.so
/opt/google-earth/libcrypto.so.0.9.8
/opt/google-earth/libcurl.so.4
/opt/google-earth/libevll.so
/opt/google-earth/libflightsim.so
/opt/google-earth/libfreeimage.so.3
/opt/google-earth/libfusioncommon.so
/opt/google-earth/libgcc_s.so.1
/opt/google-earth/libgdal.so
/opt/google-earth/libge_net.so
/opt/google-earth/libgeobase.so
/opt/google-earth/libgoogleearth_lib.so
/opt/google-earth/libgooglesearch.so
/opt/google-earth/libgps.so
/opt/google-earth/libicudata.so.38
/opt/google-earth/libicuuc.so.38
/opt/google-earth/libinput_plugin.so
/opt/google-earth/libjpeg.so.62
/opt/google-earth/liblayer.so
/opt/google-earth/libmath.so
/opt/google-earth/libmeasure.so
/opt/google-earth/libminizip.so
/opt/google-earth/libmng.so.1
/opt/google-earth/libmoduleframework.so
/opt/google-earth/libnavigate.so
/opt/google-earth/libpng12.so.0
/opt/google-earth/libport.so
/opt/google-earth/libproj.so.0
/opt/google-earth/librender.so
/opt/google-earth/libstdc++.so.6
/opt/google-earth/libtiff.so.3
/opt/google-earth/libwmsbase.so
/opt/google-earth/libz.so.1
/opt/google-earth/plugins/imageformats/libqgif.so
/opt/google-earth/plugins/imageformats/libqjpeg.so

Hope you can make something out of that.

---

### Post by Patb on 2008-05-30
Looks good, Ekmon.  That output shows that there are a whole lot of lib files (or libraries) in the directory /opt/google-earth/.  

Just to explain: that "updatedb" command updated a list of your computer's system files.  The "locate" command looked in that list for any files with "google-earth" in the path name.  The "| grep lib" effectively meant list only the files which have the string "lib" somewhere in the line.  Together, the commands were therefore a way of finding the lib files in the google-earth directory.  

You should now do two commands from a terminal, the first to get into your ~/Desktop/ directory and the second to copy the newly extracted files into the directory where Googleearth keeps its libraries.  So that's:
```
cd ~/Desktop
sudo cp libGL.so* /opt/google-earth/
```
Then try to start GE.  Good luck.  I'll be interested to see whether this solves your problem.  

If you still have the same problem, can I bring you back to your original post:
> I'm using Ubuntu 8.04 with VMWare server
Can you clarify what you mean by this.  Do you mean Ubuntu is running in a Vmware server within another operating system?  Or that you have something else running in the Vmware server when this happens?

Cheers, Pat.

---

### Post by ekmon1582 on 2008-05-30
Awesome, Google Earth works now. Thank you! The only problem is that I can't see anything when Google Earth is up and running, just stars. I got this error message the first time I got it running;

Please Complete the login window first if it's shown in front.

You are currently running Google Earth in 'OpenGL' with software emulation. In this mode, Google Earth will work but it will run very slowly. If you want to run Google Earth more quickly we suggest that you upgrade your graphics card driver. We only recommend this if you are comfortable doing software upgrades, otherwise you may check the box at the bottom left of this window to not see this message in the future. 

For detailed driver download and install instructions please see the Google Earth Online Help Center by clicking the link below:

  [http://earth.google.com/support/bin/answer.py?answer=2147hl=em](http://earth.google.com/support/bin/answer.py?answer=2147hl=em)


I'm sure you've figured out I'm not to technical with hardware, so I'm not comfortable with doing what it says. 

As to your second question...  I'm running Windows XP, with VMware server installed on Widnows, and Ubuntu is installed in VMware server. Thanks again for all the help!:)

One more question for you, can I delete that package with those two files and those two files themselves now? Or should I just stow them away in my documents?

---

### Post by Patb on 2008-05-30
> **ekmon1582 said:**
> Awesome, Google Earth works now. Thank you! The only problem is that I can't see anything when Google Earth is up and running, just stars...

That's at least some progress, Ekmon. :).  I was quite apprehensive that after all that posting back and forth, my idea would not work.  

As for the stars, try waiting a few minutes to see if the earth does eventually appear.  This looks like an unrelated issue though, so if you cannot find a solution through searching, I would be inclined to create a new post on this problem.  It could have something to do with the contraints of working within a VM.  
> You are currently running Google Earth in 'OpenGL' with software emulation.
I remember getting the same message and ignoring it.  My hardware is fairly primitive - not OpenGL compatible - but it runs GE okay with software emulation, so I decided to leave well enough alone.  But I was not in a VM, so it differed from your situation.  
> can I delete that package with those two files...
Sure you can.  I'm a bower bird myself, so I tend to stow those sort of things away in case I do a reinstall or try out yet another distribution some time; but you know where to find them if you need them again.  

Cheers, Pat.

---

### Post by ekmon1582 on 2008-06-02
I'll try that then. I suppose I'll stow them away as well, and stow away the commands. Thanks for all the help :).

P.S. Glad you put how to mark a topic solved in your signature, I'll be doing that :).

---

