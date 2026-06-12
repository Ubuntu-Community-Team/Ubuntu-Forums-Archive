---
title: "This mornings update borked vmware"
date: 2006-07-11
forum: General Help
---

### Post by gpw797 on 2006-07-11
This mornings update borked vmware on my machine. App won't start.

---

### Post by matthew on 2006-07-11
Are you using the vmware player or server?

I use the server version and mine was borked as well--the program is tied in directly with the running kernel so changes in the kernel version will do this. I fixed it with one command:
```
sudo /usr/bin/vmware-config.pl
```

I don't have any experience with the player version (i.e. from the repos...) so I am not sure how to fix it if that is what you are using. You might try a complete uninstall and reinstall.

---

### Post by bojzi on 2006-07-11
I have to agree, VMware Server here and it isn't working.

Edit: I'm gonna try matthew's method and see if it works.

---

### Post by wylfing on 2006-07-11
I have the vmplayer that is available from the VMWare site. I keep the source on hand and whenever there is a kernel change I just recompile. Only takes a moment.

I'd guess that is what the configure script does as well -- asks those config questions and then recompiles the virtualizer.

---

### Post by PriceChild on 2006-07-11
I've just started using the server version.

I'm using the tar's from the official vmware site. For some reason they don't install at all from the repositories :S

Everytime you install a new kernel, you must run the vmware config script again (no need to do a complete reinstall) to create a new vmware module to insert in the kernel.

Pricey

---

### Post by bojzi on 2006-07-11
Thanks matthew, works like a charm! :)

---

### Post by matthew on 2006-07-11
> **wylfing said:**
> I have the vmplayer that is available from the VMWare site. I keep the source on hand and whenever there is a kernel change I just recompile. Only takes a moment.

I'd guess that is what the configure script does as well -- asks those config questions and then recompiles the virtualizer.That's precisely what the script does. :)

---

### Post by gpw797 on 2006-07-11
worked for me to thanks!

---

### Post by The Noble on 2006-07-11
Vmplayer from the repos works perfectly if anyone is wondering. The disc image is from easyvmx.com (by the way).

---

### Post by reztho on 2006-07-12
> **The Noble said:**
> Vmplayer from the repos works perfectly if anyone is wondering. The disc image is from easyvmx.com (by the way).

Actually it cannot work perfectly until someone put in the repositories a new vmware kernel module needed to let it work with the last kernel update.

[http://ubuntuforums.org/showpost.php?p=1244947&postcount=20](http://ubuntuforums.org/showpost.php?p=1244947&postcount=20)

---

### Post by ayoli on 2006-07-12
i use vmware player from repos and yes, i also miss vmware-player-kernel-modules-2.6.15-26 :( 
hope it will come soon

---

### Post by jnev on 2006-07-12
the reason it doesn't work is because you installed a new kernel. do what matthew said and input the c header files for the new kernel and everything should be kosher after that.

---

### Post by reztho on 2006-07-12
> **jnev said:**
> the reason it doesn't work is because you installed a new kernel. do what matthew said and input the c header files for the new kernel and everything should be kosher after that.

You are confused. That's ok for vmware server, but not for vmware player from the repositories. The repositories must supply the binary kernel module for vmware player. See my previous post.

---

### Post by BlackMambo on 2006-07-12
> **jnev said:**
> the reason it doesn't work is because you installed a new kernel. do what matthew said and input the c header files for the new kernel and everything should be kosher after that.

and where do you get those from (the C headers...)??

Here is an extract from my Terminal while trying to fix my VM Ware install after it wouldn't work after running the updates...

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```

---

### Post by jstueve on 2006-07-12
```

sudo apt-get install linux-headers-`uname -r`

```

make sure to use ` not '

then run vmware-install.sh

(apt-get install build-essentials if haven't already)

---

### Post by BlackMambo on 2006-07-12
> **jstueve said:**
> 
make sure to use ` not '

then run vmware-install.sh

(apt-get install build-essentials if haven't already)

thank you for your reply, but what is ' not'?

and I ran *sudo /home/username/vmware/vmware-config.pl* - you're saying I should do *vmware-install.sh*??

sorry - noob!! :-?

---

### Post by matthew on 2006-07-12
I hate to break it to everyone. The vmware server just went out of beta. They released a 1.0 version today. It's still free. So, whether you've gone through all the trouble of recompiling everything (like I did) or not you will probably want to stop in here and check it out.

[http://register.vmware.com/content/download.html](http://register.vmware.com/content/download.html)

BTW, I've been testing is just a little bit and it looks nice. I haven't noticed any real changes yet, but I've only had it up and running a few minutes.

---

### Post by BlackMambo on 2006-07-12
> **jstueve said:**
> ```

sudo apt-get install linux-headers-`uname -r`

```

I did that, it installed the headers and returned me to the prompt. I then returned to the other terminal window but no luck!! I still get this:

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include
```]
Help!

---

### Post by jstueve on 2006-07-12
check:

ls -l /usr/src/

see if there is a entr for linux, if there isn't do

sudo ln -s /usr/src/linux-headers-`uname -r' /usr/src/linux

then retry.

---

