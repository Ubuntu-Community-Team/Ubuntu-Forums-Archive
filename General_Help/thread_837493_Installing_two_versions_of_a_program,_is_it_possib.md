---
title: "Installing two versions of a program, is it possible?"
date: 2008-06-22
forum: General Help
---

### Post by Ralphie on 2008-06-22
Hi, I'd like to install Virtualbox OSE and also the original version at the same time. 
Is this possible somehow?

When I try to, it complains that there is a conflict between packages.

Thanks

---

### Post by brian_p on 2008-06-22
> **Ralphie said:**
> Hi, I'd like to install Virtualbox OSE and also the original version at the same time. 
Is this possible somehow?

When I try to, it complains that there is a conflict between packages.

Thanks

Not that I've used it but dpkg-divert may be what you want.

---

### Post by kevdog on 2008-06-22
Yes it is possible -- for example one in /usr/bin and one in /usr/local/bin.  I often have a base install running from repository in /usr/bin and a svn or cvs version running from /usr/local/bin

---

### Post by Ralphie on 2008-06-23
Hey thanks for the replies, I'm glad to hear its possible. 

I am fairly familiar with the command line, but would need a little help on getting started with such a task, 
are there any quick tutorials explaining how one could go about doing such a thing?

Kevdog, are you using dpkg-divert command that brian_p mentioned?
Or repackaging the applications somehow?

Thanks for your help

---

### Post by jocko on 2008-06-23
I think kevdog meant he has one version installed from a .deb from the repos and another installed from source (when you compile from source you can set an alternative install location to avoid overwriting the other version). In this case you could probably install the ose version from source.
I'm not sure dpkg-divert can divert an entire package, and if one package says it conflicts with another package, I don't think it's possible to use diversions to solve it.
Perhaps it's possible to rebuild a .deb package from source, remove whatever setting that tells it that it conflicts with another package and give it a new install location?
May require quite a lot of fiddling with the packaging scripts...

But why would you want to have both virtualbox and virtualbox-ose? If you accept the licence agreement that comes with virtualbox, there's no point in also installing the ose version (the only differences are some features that are missing in the ose version because they can not be included in the gpl licence)...

---

### Post by kevdog on 2008-06-23
Im installing from source since during the configure process, you can state where you want the base directory located.

Do you need to compile the second version?

---

### Post by Ralphie on 2008-06-23
I have the OSE installed, and with it, I set up a virtual machine.
For some reason the machine does not work correctly with the real version of VirtualBox, and I would like to use some of its features with a specific program, but do not want to have to re-install all of the programs that I have set up on the other machine. So I figured it would be easiest to just have two versions of VB, and two virtual machines. 

kevdog, 
I have a .deb of the second version, and I don't think source is available, but I am able to get the source of the OSE version.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Ralphie on 2008-06-23
Ok, I have the source, and I have all the pre-reqs installed, and I am using this guide: [http://www.virtualbox.org/wiki/Linux%20build%20instructions](http://www.virtualbox.org/wiki/Linux%20build%20instructions)

But am not sure on how to select where it will install to.

If you've got the time for a couple pointers it would be much appreciated, thanks!

**Edit**
I installed the non-ose version, and it converted one of my VMs so that it would work with this new version, and everything seems to be running fine!
Which means I no longer need to install two versions of this particular application. 

Feel free to write a small howto, if you would like, to maybe help others in the future (or even myself, as I've in the past wanted to do this with other applications) but know that it is not necessary. 

Thanks for all your help guys.

---

