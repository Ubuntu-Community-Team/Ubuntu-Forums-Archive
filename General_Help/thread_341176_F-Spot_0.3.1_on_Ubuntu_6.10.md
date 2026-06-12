---
title: "F-Spot 0.3.1 on Ubuntu 6.10 ?"
date: 2007-01-18
forum: General Help
---

### Post by Hoshimaru on 2007-01-18
Hello,

I'd like to export pictures in F-Spot to my Gallery² site. Unfortunately, there's no Export function in F-Spot 0.2.1 which came with this Ubuntu release.

Is there a way to install F-Spot 0.3.1 ?
From my understanding of many posts here, it's not a good idea to do this via the source code in that tar.bz2 file. 
Are there any .rpm or .deb files available which would make installation easier without polluting the system too much? If not, is there another solution/application that is as good as F-Spot and can export to Gallery² ? You'll agree that uploading ~1000 pics in different albums via the upload page is rather boring.

Thanks in advance for any information and/or advice.

---

### Post by yopnono on 2007-01-18
Try here [http://www.getdeb.net/](http://www.getdeb.net/) or build it yourself

---

### Post by reclusivemonkey on 2007-01-18
> **Hoshimaru said:**
> 
I'd like to export pictures in F-Spot to my Gallery² site. Unfortunately, there's no Export function in F-Spot 0.2.1 which came with this Ubuntu release.


Have you got automatix installed? I can't remember whether my f-spot came from there or the standard install, but it certainly has the export options (flickr, gallery, etc.). I'm not exactly sure whether it works with gallery 2 (I'm at work and don't have access to a gallery 2) but you could try installing automatix and getting f-spot from there if you are concerned about installing from source.

---

### Post by ruffneck on 2007-02-12
> **yopnono said:**
> Try here [http://www.getdeb.net/](http://www.getdeb.net/) or build it yourself

Thanks got deb from here.

---

### Post by Hoshimaru on 2007-02-12
Thank you for your replies :)
I'll get a look at the different solutions asap ^^

---

### Post by srf21c on 2007-03-30
I'm trying to install the latest version of f-spot (currently 0.3.5) that I built from source using the checkinstall utility.

However, when I try to uninstall the existing version 0.2.1,  aptitude barks at me. 

Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Obviously I do not want to uninstall the entire ubuntu-desktop meta package.  

Any suggestions?  I plan on using the checkinstall utlity to install the newer version of f-spot immediately after removing the old one.

---

### Post by QwUo173Hy on 2007-03-31
Funny, I just removed 0.2.1 on edgy and I didn't have such a dependency problem. Did you use a non-standard way of installing it?

<edit>
The only problem I had was trying to install the above .deb.
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on dcraw; however:
  Package dcraw is not installed.
 f-spot depends on libmono-sqlite2.0-cil; however:
  Package libmono-sqlite2.0-cil is not installed.
 f-spot depends on libmono-system-runtime2.0-cil; however:
  Package libmono-system-runtime2.0-cil is not installed.
 f-spot depends on libmono-cairo2.0-cil; however:
  Package libmono-cairo2.0-cil is not installed.
 f-spot depends on libmono2.0-cil; however:
  Package libmono2.0-cil is not installed.
dpkg: error processing f-spot (--install):

<edit2>
Afterwards, I ran Add/Remove applications and it informed me that the database was broken and that I should run 'sudo apt-get -f'. It installed all the dependencies as WELL as the pending f-spot0.3.5 and all is well again. This distro is great. If feisty improves on this by any fair amount it will be amazing.

---

### Post by srf21c on 2007-03-31
The first time around I tried using aptitude to remove f-spot 0.2.1.  This warned me that it would also remove the ubuntu-desktop metapackage.  Upon the advice of someone on the #ubuntu IRC channel, I went ahead with the operation.  It seemed to remove about 1/3 to 1/2 of the ubuntu-desktop packages before finally removing f-spot.  I then used checkinstall to install the 0.3.5 version of f-spot that I built from source.  Then I used apt-get to re-install the ubuntu-desktop meta package.

This put me back to square one, as the ubuntu-desktop metapackage also re-installed f-spot 0.2.1 right over my 0.3.5 version. 

I did some more research and then decided to try removing f-spot using "sudo dpkg -r --force-depends f-spot".   This yanked out the old f-spot package nicely, and then I immediately installed the new 0.3.5 versinon using dpkg, since I already had built the .deb package using checkinstall.  

All seems to be well.

---

