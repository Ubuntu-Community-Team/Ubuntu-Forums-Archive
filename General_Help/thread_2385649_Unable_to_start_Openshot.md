---
title: "Unable to start Openshot"
date: 2018-02-22
forum: General Help
---

### Post by satimis on 2018-02-22
Hi all,

Ubuntu 16.04 desktop

Unable to start Openshot.  It just happened after running update and upgrade


```

Error Message: 'NoneType' object has no attribute 'set_cursor'
----------------------------------------------------------------

OpenShot has failed to import some of the Python files or libraries 
required for our application to run.  Here are some trouble shooting
tips:

Tip 1) Check if MLT can be successfully imported in Python.  Run the 
 following commands, and see if any errors are displayed.  If you get 
 an error, you need to investigate the correct way to install MLT.
 NOTE:  Do not type the $ or >> characters in the examples below.

       $ python
       >> import mlt
       >> mlt.Factory().init()

Tip 2) If MLT is working from the first example, then the next tip is 
 to look at the above error messages very closely, and google for more 
 help.  It's likely the problem is already reported, and maybe there is
 a simple work-around.  Also, you can search for bugs or report a new 
 bug at https://bugs.launchpad.net/openshot.  Good luck!

```

I followed below thread:
OpenShot Won't Start - Python MLT Error
#2
[https://ubuntuforums.org/showthread.php?t=2081636](https://ubuntuforums.org/showthread.php?t=2081636)

After running;
sudo apt-get remove openshot python-mlt3 --purge

Then
&#10219; sudo apt-get install python-mlt3```

[sudo] password for satimis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-mlt3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python-mlt:i386 python-mlt

E: Package 'python-mlt3' has no installation candidate

```

python-mlt3 is NOT on repo

Please help.  Thanks

Regards
satimis

---

