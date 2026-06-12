---
title: "Messed Up Update Manager"
date: 2007-08-21
forum: General Help
---

### Post by IdioticCreation on 2007-08-21
I'm getting the error:
'Unknown Error: '<type 'exceptions.SystemError'>' (E:The package libcodeblocks0 needs to be reinstalled, but I can't find an archive for it.)'

From Update Manager, I guess it's called Synaptic.

I was trying to update my Code::Blocks nightly build, and....yeah.  So maybe I can completely wipe codeblocks, then reinstall it?  I don't know, but it's kinda of important, since it's preventing me from getting system updates.

Thanks,
David

---

### Post by sumguy231 on 2007-08-22
> So maybe I can completely wipe codeblocks, then reinstall it?  
It's worth a try, since I'm pretty sure it wouldn't make things any worse. Make sure libcodeblocks0 is removed with it, though it should be removed as a dependency anyway.

---

### Post by IdioticCreation on 2007-08-22
Cool, thanks.  More specifically, how do I do this?  Just delete the install folder, or what?

Thanks for helping.

---

### Post by cstudent on 2007-08-23
You can probably fix the problem in this manner.

Go to [http://developer.berlios.de/project/showfiles.php?group_id=5358](http://developer.berlios.de/project/showfiles.php?group_id=5358) and download the latest Ubuntu tar.gz file, rev4405 as of this moment. Extract the tar file into a temp directory. Then using the terminal and after navigating to the temp directory, install the files all at once using

```
sudo dpkg -i *.deb
```

This should get you updated and clear up your error message.

---

### Post by IdioticCreation on 2007-08-23
Hrmm.  I got the errors:
dpkg:  serious warning:  files list file for package`PACKAGE' missing, assuming package has no files currently installed.

Where PACKAGE was all the different packages...netcat, oclock, libxay6, and so on.  I think I've really screwed something up. =/

---

### Post by cstudent on 2007-08-23
Make sure you extract the tar.gz file into a folder (or directory if you prefer) that has nothing else in it. It looks like dpkg is trying to install other things besides the Codeblocks packages. There are six .deb files in the tar.gz archive, so the folder you extract the files to should only have the 6 files in it. Then make sure when you go to the console, to use the cd command and navigate to the folder where the files are stored. Then run your sudo dpkg -i *.deb command.


This wiki page may also be of help to you: [http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

---

### Post by IdioticCreation on 2007-08-23
I get the same errors.  Also I tried running the deb's individually, just by clicking them and I get the message:
Could Not Open "file.deb"  The package may be currupt, or you don't have premission.

Here's what I'm starting to think though.  When I was reading the thing about upgrading the nightly, I read the Windows one which tells you to delete the install directory.  So I did - /home/usr/share/codeblocks/

I think that messed up a bunch of stuff.  So is there a way a can completly remove CB off my computer.  Because right now Ubuntu still thinks it's installed, a bunch of files are just missing....

Thanks again for your help.

---

### Post by cstudent on 2007-08-24
The easiest way I can think of to remove everything is through Synaptic. Go to the System menu under Administration menu click on Synaptic. Click the Status button on the lower left side once you get Synaptic opened. Then click on Installed (local or obsolete) in the upper left. You should see the Codeblocks packages. You want to check the packages codeblocks, codeblocks-dev, codeblocks-contrib, libcodeblocks0, libwxsmithlib0 and libwxsmithlib0-dev. When you click on the files, chose the complete removal option.


The permission error could be a corrupt file, but more than likely I'm guessing you may have placed the extracted files into a folder that belongs to root and not your user account. Be sure the folder you extract your files to is one that is under your /home/yourusername.

---

### Post by IdioticCreation on 2007-08-24
Yeah I did extract them under my username.  I can't even open synaptic.  It gives me the same error I posted in the beginning.  Is there a way to run it with exceptions?

---

### Post by IdioticCreation on 2007-08-26
OK, So I Googled the error I'm getting and found it's a common problem, but it can result from a lot of different things.  The generic fix for it was:
sudo dpkg --remove --force-remove-reinstreq package
I tried that with both "codeblocks" and libcodeblocks0" neither worked.  I would REALLY appricate any advice!

Thanks

---

