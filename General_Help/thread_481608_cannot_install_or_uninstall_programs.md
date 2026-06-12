---
title: "cannot install or uninstall programs"
date: 2007-06-22
forum: General Help
---

### Post by ultrin_valuk on 2007-06-22
I am unable to install or remove programs.  When I attempt to use synaptic, apt-get, or gdebi I receive and error reading: 

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

I have tried to reinstall it, and I have tried to remove it, but it doesn't work.  The package is located on my desktop.  I'm not very familiar with the package managers.  This is a real pain, as I don't want to reinstall the system again.

---

### Post by Silenus on 2007-06-22
sudo apt-get install virtualbox
oh you can't install

here is an install for i386 systems, if you have amd I found their link as well
[http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb](http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb)
and for amd
[http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb](http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb)


Those are both for fiesty fawn which I assume you are using as you did not list specs

If not here you go [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by ultrin_valuk on 2007-06-22
Sorry for not listing specs.  I'm running Feisty, i386, and I've tried the debian package.  It tells me it's corrupt, or I don't have sufficient privileges.  I checked, and I have the privileges, and I downloaded it and tried it again three times.  Same problem.  At this point, I just want to get rid of it, as it isn't critical to have.

The first time I tried to install it, it had to download 2 dependencies, and I don't know what they were.  About the end of the installation, the program stopped responding, and I had to force it to exit.  I tried installing again, and that is when the problem started

Oh, and sorry for not posting this sooner.

---

### Post by ArgusVision on 2007-06-23
Hey Ultrin_valuk, Did Silenus' link work for you?

I had the ***_Exact_*** Same problem... I went to the link, reinstalled, and it worked...
I did do a couple of things differently this time.

I opened the >Terminal in the install status window, scrolled down and "agreed to terms of usage" which got me past the initial hang up...

Also, I edited my sources.list  to include

deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free
deb-src [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free

In order to do this you will have to login as your root user.

enter "gksudo gedit /etc/apt/source.list"

Then copy and paste the deb lines above.

Hope this helps.

---

### Post by ultrin_valuk on 2007-06-23
ArgusVision:  Thank you so much!  It worked perfectly.  I think it just wanted to finish the install that was interrupted originally, and wanted a repository.  Thanks again!

---

### Post by godd4242 on 2007-07-24
Alright I know this thread is old, but I have the exact same problem as well.

Downloaded and reinstalling doesn't work, it gives me the permissions error

>  	Hey Ultrin_valuk, Did Silenus' link work for you?

I had the Exact Same problem... I went to the link, reinstalled, and it worked...
I did do a couple of things differently this time.

I opened the >Terminal in the install status window, scrolled down and "agreed to terms of usage" which got me past the initial hang up...

Also, I edited my sources.list to include

deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free
deb-src [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free

In order to do this you will have to login as your root user.

enter "gksudo gedit /etc/apt/source.list"

Then copy and paste the deb lines above.

Hope this helps.

I edited sources.list, but I don't know what you mean by open terminal in the install status window.

I don't even get an install status, in short I just have GDEBI come up and punch me in the face with the permissions error.

Any advice anyone?

---

### Post by Majorix on 2007-07-24
Have you tried this:
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by godd4242 on 2007-07-24
> **Majorix said:**
> Have you tried this:
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

dking@dking-laptop:~$ sudo dpkg --remove --force-remove-reinstreq virtualbox
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.


That doesn't sound too good.

Nothing happened after that 

Nope I take that back it looks good now

I can't tell you how grateful I am, this problem made me want to beat my laptop with a golf club.

---

### Post by Majorix on 2007-07-24
Haha glad it worked out.

That what you faced is a common bug. I believe they will fix it soon. Probably in the next release of Ubuntu. If not, whenever you see that error you can use the code I pasted.

---

