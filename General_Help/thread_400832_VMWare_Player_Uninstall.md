---
title: "VMWare Player Uninstall"
date: 2007-04-04
forum: General Help
---

### Post by Tookelso on 2007-04-04
Hello,

I had VMWare Server running perfectly using this thread:

[http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server)

I made a boo-boo and tried installing VMWare Player after I'd already installed VMWare Server.  I realized that VMWare Player only runs pre-made VMs, and I aborted the install of VMWare Player when it started asking me if I wanted to overwrite the VMWare conf files.

I ran the "dpkg" to fix apt-get, and I've ran

  sudo apt-get remove vmware-player

Now my VMWare Server icon doesn't work.

When I go to the terminal, I type "vmware", and I get the error:

  exec: 180: /usr/lib/vmware-player/lib/wrapper-gtk24.sh: not found 

What's the easiest way to re-install (preferably restore) VMWare Server?  How can I avoid zapping the VMs that I've created already?

I'm running Edgy.

Thanks for any help,

--Took

---

### Post by thelinuxguy on 2007-04-04
> How can I avoid zapping the VMs that I've created already?
The VMs that you create are stored in a subfolder where vmware is installed, unless you have selected a different path while installing. In case you need to reinstall vmware server, make a copy of this folder and you can add the VMs to the newly installed server later.

Edit: 
I had changed the paths during installation. So I can't tell you the default locations but
```
whereis vmware
``` may help you locate what you need.

---

### Post by Tookelso on 2007-04-04
Thanks for your tips.

I downloaded a new version (NOTE: Make sure you keep your registration keys!)  I found it very difficult to get around VMWare's website to get registration keys.  Thankfully, I had a text file with my registration key in it. 

I unzipped the tar.gz file into a temporary directory and ran the vmware-install.pl script.  It prompted me for about 1,000 files to overwrite.  I exited the script and removed the /usr/lib/vmware directory myself.

I re-ran  vmware-install.pl, and made sure that it just used the default directory for storing virtual machines.  My VMs are NOT installed in the default VMWare directory, so they were preserved. :) 

Then, when the installer script tried to compile the app, it ran into some problems, but the script kept going.  The install script finally crashed saying that it couldn't shut down existing VMWare services.  I re-booted, and re-ran the ./vmware-install.pl script from the tmp directory, and it ran o.k.  I was able to open my existing VMs by browsing for them.

For the future, just remember that there's a vmware-uninstall.pl script that vmware puts in the usr/bin directory.  I should have run that script before running the install.

In addition, I recommend you restart your computer after un-installing vmware, to shut down the VMWare services/daemons shut down.

After the machine reboots, go ahead and proceed with running sudo ./vmware-install.pl

--Took

---

