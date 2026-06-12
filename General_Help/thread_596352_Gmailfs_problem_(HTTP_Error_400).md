---
title: "Gmailfs problem (HTTP Error 400)"
date: 2007-10-29
forum: General Help
---

### Post by zpon on 2007-10-29
Hi

When i use 
```
sudo mount -t gmailfs none gmail -o username=****@gmail.com,password=***,fsname=zOIRRa
```

and

```
sudo mount.gmailfs /usr/lib/python2.5/site-packages/gmailfs.py gmail -o username=****@gmail.com,password=***,fsname=zOIRRa
```

i get 

```
HTTP Error 400: Bad Request
```

and

```
Ignored option :rw
HTTP Error 400: Bad Request
```

Can anybody see why?

---

### Post by zpon on 2007-10-30
up...

---

### Post by zanglang on 2007-11-05
This is *probably* a bug in python-libgmail, which should be fixed in 0.1.6.1 (Gutsy has 0.1.5.1, latest version is not 0.1.7). Would you be able to try and manually update libgmail and see if that fixes it?
[http://sourceforge.net/project/showfiles.php?group_id=113492](http://sourceforge.net/project/showfiles.php?group_id=113492)

Edit: Or if you have Python installed, you can just do
```
sudo easy_install --upgrade libgmail
```

---

### Post by zpon on 2007-11-05
Thank you will give it a try when i can get a connection without proxy

---

### Post by zpon on 2007-11-05
It worked, thanks a lot! :guitar:

---

### Post by daller on 2007-11-14
How did you fix it?

How did you manually upgrade libgmail?

...I downloaded 0.1.7, but there's no MAKE or the like, and the README doesn't explain it!

---

### Post by zpon on 2007-11-14
> **daller said:**
> How did you fix it?

How did you manually upgrade libgmail?

...I downloaded 0.1.7, but there's no MAKE or the like, and the README doesn't explain it!

If i remember correctly i just used
```
sudo easy_install --upgrade libgmail
```
as zanglang sugested

---

### Post by daller on 2007-11-14
Thanks!

That got me further, but I still get this:

Should the "@gmail.com" be included in the username?

Anyway, I get this:

```
root@daniel-desktop:/# mount -a
Ignored option :rw
fuse: bad mount point `/mnt/g': No space left on device
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1180, in main
    server.main()
  File "/usr/lib/python2.5/site-packages/fuse.py", line 713, in main
    main(**d)
fuse.FuseError: filesystem initialization failed
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1180, in main
    server.main()
  File "/usr/lib/python2.5/site-packages/fuse.py", line 713, in main
    main(**d)
fuse.FuseError: filesystem initialization failed

```

---

### Post by zpon on 2007-11-14
I don't think it matters if you @gmail.com or not. But, have you remembered to umount since you did the update of libgmail?

---

### Post by nerohj on 2007-11-21
FYI - if you don't already have the **easy_install** command, it lives in the **python-setuptools** package. 

For future reference, you can search on debian.org's site for what packages commands live in. 
[http://www.us.debian.org/distrib/packages]("http://www.us.debian.org/distrib/packages")

-nerohj

---

### Post by user1234 on 2007-11-24
> **zpon said:**
> If i remember correctly i just used
```
sudo easy_install --upgrade libgmail
```
as zanglang sugested

Very cool, I had no idea what I was doing wrong, turns out it was libgmail, not me.
```
sudo apt-get install python-setuptools gmail
sudo easy_install --upgrade libgmail
sudo nano /etc/gmailfs/gmailfs.conf   (put in your info)
sudo /usr/bin/mount.gmailfs KraZyNameGMailFS /media/gmailfs
```
and it's running!  WooHoo!

---

### Post by user1234 on 2007-11-24
> **user1234 said:**
> 
and it's running!  WooHoo!

Spoke too soon, seems it's only accessible as root (or with sudo)?  Unless I'm root, it doesn't know what it is:
```
?--------- ? ?    ?           ?                ? /media/gmailfs
```
Is that normal, or might I have some other setting wrong?

---

### Post by timn91 on 2007-12-07
> **user1234 said:**
> Spoke too soon, seems it's only accessible as root (or with sudo)?  Unless I'm root, it doesn't know what it is...

Same problem here. I even tried the following: sudo addgroup <username> fuse
But it still didn't help.

Best regards,
Tim

---

### Post by jaromrnelson on 2007-12-11
> **daller said:**
> Thanks!
Original exception was:
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1180, in main
    server.main()
  File "/usr/lib/python2.5/site-packages/fuse.py", line 713, in main
    main(**d)
fuse.FuseError: filesystem initialization failed


I got the same error as quoted after a couple failed attempts, then I tried:
```

sudo umount /media/gmail

```

Then at least it returned without errors.

-------------


Now I just have to figure out how to make it accessible by non-root

---------------------   In summary, this is what I have done so far -------------------

So, a summary of all I did related to gmailfs is (starting from Gutsy):
summary:

```

#Starting from Gutsy, I did the following
# much of this was taken from http://www.debian-administration.org/articles/198
# install the gmailfs (and recommended encfs)
sudo apt-get install gmailfs encfs

# install source modules for fuse-source
sudo apt-get install fuse-source
# install source dependencies for fuse-source
# --- I didn't do this at first, so module-assistant didn't build on my first try
sudo apt-get build-dep fuse-source

# use module-assistant to prepare the build environment, build fuse and install fuse
sudo module-assistant prepare
sudo module-assistant build fuse
sudo module-assistant install fuse
# load the kernel module
modprobe fuse

# update libgmail to the latest version
# tip from this thread: http://ubuntuforums.org/showthread.php?t=596352
sudo apt-get install python-setuptools
sudo easy_install --upgrade libgmail

# make the mount point (-p = and parent directories, if needed)
sudo mkdir -p /media/gmail/username

# do the mount
sudo mount -t gmailfs none /media/gmail/username/ -o username=username@gmail.com,password=secretstuff,fsname=RandomKey

# now try to go to the mounted gmailfs
cd /media/gmail/username

# here is where I get the problems above, where I can only access the directory as root

```

---

### Post by Snapper187 on 2008-01-11
Works like a charm with me on Gutsy, using the Hardy package of python-libgmail (version 0.1.8-1 as of the time of posting.)

I have managed mounting both into /media/gmail and $HOME/mnt/gmail as a normal, non-privileged user, successfully. (in each case, however, the directory must be owned by the user.) I find it more appropriate to set up the mount point in a $HOME-local directory, however, since my gmail data shouldn't be of interest to anyone but me.

Naturally, I cannot user-umount unless I make an fstab entry. (or edit the sudoers file for that purpose.)

---

### Post by baltho on 2008-01-13
Hi all,

Nice one, I followed the dots using the easy_install command and it all worked beautifully - for 20 seconds - then I get (log file extract here...)
```
01/13/08 19:59:44 ERROR      gmailfs did not connect in less than 20 seconds, aborting...

```
I also had
```
01/13/08 19:59:24 ERROR      OpenSSLProxy is missing. Can't use HTTPS proxy!

```
earlier; tried to fix it but I don't use a proxy so I thought I could ignore it.
btw, am using
```

mount -t gmailfs /usr/share/pycentral/gmailfs/site-packages/gmailfs.py ./gmailfs -o username=xx,password=xx,fsname=xx
```
(as root while I set it up) to generate the above messages.
Any ideas, anyone?

---

### Post by tonycm1 on 2008-02-05
Tried the guide... getting problems with the mount.gmailfs file i think :S 

ideas ??

> tony@tony-laptop:~$ sudo easy_install --upgrade libgmail
Searching for libgmail
Reading [http://cheeseshop.python.org/pypi/libgmail/](http://cheeseshop.python.org/pypi/libgmail/)
Reading [http://libgmail.sourceforge.net/](http://libgmail.sourceforge.net/)
Reading [http://sourceforge.net/project/showfiles.php?group_id=113492](http://sourceforge.net/project/showfiles.php?group_id=113492)
Reading [http://cheeseshop.python.org/pypi/libgmail/0.0.8](http://cheeseshop.python.org/pypi/libgmail/0.0.8)
Best match: libgmail 0.1.8
Processing libgmail-0.1.8-py2.5.egg
libgmail 0.1.8 is already the active version in easy-install.pth

Using /usr/lib/python2.5/site-packages/libgmail-0.1.8-py2.5.egg
Processing dependencies for libgmail
Finished processing dependencies for libgmail
tony@tony-laptop:~$ sudo nano /etc/gmailfs/gmailfs.conf
tony@tony-laptop:~$ sudo nano /etc/gmailfs/gmailfs.conf
tony@tony-laptop:~$ sudo /usr/bin/mount.gmailfs KraZyNameGMailFS /media/gmailfs
Traceback (most recent call last):
  File "/usr/bin/mount.gmailfs", line 155, in <module>
    pyfile, mountpoint, namedOptions, useEncfs = parseCommandLineArgs(sys.argv[1:])
  File "/usr/bin/mount.gmailfs", line 67, in parseCommandLineArgs
    log.error("file %s doesn't exist, or is not a file" % pyfile)
NameError: global name 'log' is not defined
tony@tony-laptop:~$ 


---

### Post by Mortuis on 2008-05-23
I had a seperate problem that others might encounter:

> john@Uriel:~$ sudo easy_install --upgrade libgmail
Searching for libgmail
Reading [http://cheeseshop.python.org/pypi/libgmail/](http://cheeseshop.python.org/pypi/libgmail/)
Reading [http://libgmail.sourceforge.net/](http://libgmail.sourceforge.net/)
Reading [http://sourceforge.net/project/showfiles.php?group_id=113492](http://sourceforge.net/project/showfiles.php?group_id=113492)
Reading [http://cheeseshop.python.org/pypi/libgmail/0.0.8](http://cheeseshop.python.org/pypi/libgmail/0.0.8)
Best match: libgmail 0.1.9
Downloading [http://downloads.sourceforge.net/libgmail/libgmail-0.1.9.tar.gz?modtime=1209578300&big_mirror=0](http://downloads.sourceforge.net/libgmail/libgmail-0.1.9.tar.gz?modtime=1209578300&big_mirror=0)
Processing libgmail-0.1.9.tar.gz
Running libgmail-0.1.9/setup.py -q bdist_egg --dist-dir /tmp/easy_install-Y7YFTf/libgmail-0.1.9/egg-dist-tmp-tJ_EVX
Traceback (most recent call last):
  File "/usr/bin/easy_install", line 8, in <module>
    load_entry_point('setuptools==0.6c6', 'console_scripts', 'easy_install')()
  File "/usr/lib/python2.5/site-packages/setuptools/command/easy_install.py", line 1670, in main
    with_ei_usage(lambda:
  File "/usr/lib/python2.5/site-packages/setuptools/command/easy_install.py", line 1659, in with_ei_usage
    return f()
  File "/usr/lib/python2.5/site-packages/setuptools/command/easy_install.py", line 1674, in <lambda>
    distclass=DistributionWithoutHelpCommands, **kw
  File "distutils/core.py", line 151, in setup
  File "distutils/dist.py", line 974, in run_commands
  File "distutils/dist.py", line 994, in run_command
  File "/usr/lib/python2.5/site-packages/setuptools/command/easy_install.py", line 211, in run
    self.easy_install(spec, not self.no_deps)
  File "/usr/lib/python2.5/site-packages/setuptools/command/easy_install.py", line 446, in easy_install
    return self.install_item(spec, dist.location, tmpdir, deps)
  File "/usr/lib/python2.5/site-packages/setuptools/command/easy_install.py", line 471, in install_item
    dists = self.install_eggs(spec, download, tmpdir)
  File "/usr/lib/python2.5/site-packages/setuptools/command/easy_install.py", line 655, in install_eggs
    return self.build_and_install(setup_script, setup_base)
  File "/usr/lib/python2.5/site-packages/setuptools/command/easy_install.py", line 930, in build_and_install
    self.run_setup(setup_script, setup_base, args)
  File "/usr/lib/python2.5/site-packages/setuptools/command/easy_install.py", line 919, in run_setup
    run_setup(setup_script, args)
  File "/usr/lib/python2.5/site-packages/setuptools/sandbox.py", line 27, in run_setup
    lambda: execfile(
  File "/usr/lib/python2.5/site-packages/setuptools/sandbox.py", line 63, in run
    return func()
  File "/usr/lib/python2.5/site-packages/setuptools/sandbox.py", line 29, in <lambda>
    {'__file__':setup_script, '__name__':'__main__'}
  File "setup.py", line 7, in <module>
  File "/usr/lib/python2.5/site-packages/libgmail.py", line 36, in <module>
    #
ImportError: No module named ClientCookie
john@Uriel:~$



The solution was to run "sudo easy_install --upgrade ClientCookie"

---

### Post by abhiroopb on 2008-06-08
Mine is as root as well. When I transfer data it shows up on gmail REALLY strangely, each file has about 3 e-mails associated with it, and one of the emails as an attachment as a temp file. Whats going on?

---

### Post by thebender on 2008-06-29
> **abhiroopb said:**
> Mine is as root as well. When I transfer data it shows up on gmail REALLY strangely, each file has about 3 e-mails associated with it, and one of the emails as an attachment as a temp file. Whats going on?

Same here. Any solutions yet? please please please!

---

