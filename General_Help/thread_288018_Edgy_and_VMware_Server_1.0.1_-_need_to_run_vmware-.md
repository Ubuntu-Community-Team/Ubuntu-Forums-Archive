---
title: "Edgy and VMware Server 1.0.1 - need to run vmware-config.pl everytime after a reboot"
date: 2006-10-29
forum: General Help
---

### Post by zonum on 2006-10-29
All,

Ever since running Edgy 6.10 official release (clean install), I have had "issues" with VMware (guest OS is Edgy).  Not that it doesn't work, but, everytime I reboot the machine, I have to run vmware-config.pl in order to make it work.  Also, I have to make sure that I run vmware-config.pl prior to attempting to run VMWare, else, vmware-config.pl aborts as it cannot "stop" "Virtual Ethernet".

In anycase, once I do this, it runs without issues (this behavior was NOT happening with the original Dapper 6.06 LTS I had.

Anyone experienced this?  Thanks!

zonum

---

### Post by zonum on 2006-10-29
Oops, I mean to say, the HOST OS is Edgy 6.10...

zonum

---

### Post by dad311 on 2006-10-29
Im seeing the same issue.

---

### Post by zonum on 2006-10-29
Oh "good" - at least I am not alone...  Hopefully someone here will provide some input that will resolve the issue.

Thanks for the feedback - anyone else?

zonum

---

### Post by santiagozky on 2006-10-29
I had the same problem, but it was fixed a few days ago when I compiled my own kernel. (2.6.17.13)

---

### Post by zonum on 2006-10-29
Thanks for the info on compiling you own kernel.  Although I had a feeling about compiling a new kernel, I believe that the "issue" has to do with the file generated at startup by /etc/init.d/vmware that creates the file /etc/vmware/not_configured - the question is, why is this file being created (on preliminary investigation, an "error" occurs in /etc/init.d/vmware which because of it, the file is created).

So, it sort of makes sense that a newly compiled kernel fixes, if the error has something to do with libraries, etc, but have not completely investigated this, but still working on it...  I was hoping to stay with the "default" Edgy kernel stuff (with Dapper, I had compiled my own kernel, maybe I'll end up doing the same).

Thanks again...

zonum

---

### Post by cmost on 2006-10-29
Check to see if you have VMware player installed too!  If both are installed, you're going to get the "not_configured" file every time you reboot.  If you want both, but don't want to have to rerun the config.pl each time, then simply create a little shell script to delete this file every time you login.  Make the script executable, place it in your home directory, and then add it to gnome-sessions.  Otherwise, delete the VMware player.  There's really no need for it when you have the full blown VMware.  Hope this helps.

---

### Post by zonum on 2006-10-29
cmost,

Nope, no VMware Player installed, just VMWare Server 1.0.1; this is a a clean Edgy 6.10 install, which I then proceeded to install vmware server (as I had done with Dapper).

zonum

---

### Post by dad311 on 2006-10-29
I fixed my issue by reinstalling Edgy and wmare-server.  

Things I DID NOT install this time are,  NVIDIA beta drivers and vmplayer(from automatix).

---

### Post by gschoper on 2006-11-12
While I was unable to figure out why it's happening, the reason vmware-config.pl needs to be run after every reboot is that /etc/init.d/vmware is creating the file /etc/vmware/not_configured either during shutdown or startup.

I found two workarounds for this. First, let me say that these are both hacks.

The first one, is to simply remove the not_configured file before running vmware. You will have to run this after every reboot:
```
sudo rm /etc/vmware/not_configured
```

The second one involves editing /etc/init.d/vmware to prevent the script from  creating the not_configured file in the first place:
```
sudo vi /etc/init.d/vmware
```

about line 656 you will see:
```
      if [ "$exitcode" -gt 0 ]; then
         # Set the 'not configured' flag
         touch "$vmware_etc_dir"'/not_configured'
         chmod 644 "$vmware_etc_dir"'/not_configured'
         db_add_file "$vmware_db" "$vmware_etc_dir"'/not_configured' \
            "$vmware_etc_dir"'/not_configured'
         exit 1
      fi

```

Change it to:
```
      #if [ "$exitcode" -gt 0 ]; then
         # Set the 'not configured' flag
         #touch "$vmware_etc_dir"'/not_configured'
         #chmod 644 "$vmware_etc_dir"'/not_configured'
         #db_add_file "$vmware_db" "$vmware_etc_dir"'/not_configured' \
         #   "$vmware_etc_dir"'/not_configured'
         #exit 1
      #fi

```

After running vmware-config.pl one final time and then rebooting, I have not had to run it again.

While both of these methods work for me, they may not work for you and may have unintended consequences. Use at your own risk.

HTH,

gschoper

---

### Post by FredSambo on 2006-11-13
YAY!  this hack totally helped me!

thanks!

---

### Post by FredSambo on 2006-11-13
with one minor change:

```
#if [ "$exitcode" -gt 0 ]; then
         # Set the 'not configured' flag
         #touch "$vmware_etc_dir"'/not_configured'
         #chmod 644 "$vmware_etc_dir"'/not_configured'
         #db_add_file "$vmware_db" "$vmware_etc_dir"'/not_configured' \
         #   "$vmware_etc_dir"'/not_configured'
         #exit 1
      #fi
```

---

### Post by gschoper on 2006-11-13
> **FredSambo said:**
> with one minor change:

```
#if [ "$exitcode" -gt 0 ]; then
         # Set the 'not configured' flag
         #touch "$vmware_etc_dir"'/not_configured'
         #chmod 644 "$vmware_etc_dir"'/not_configured'
         #db_add_file "$vmware_db" "$vmware_etc_dir"'/not_configured' \
         #   "$vmware_etc_dir"'/not_configured'
         #exit 1
      #fi
```

Sorry, I don't see the change???

---

### Post by FredSambo on 2006-11-19
> **gschoper said:**
> Sorry, I don't see the change???

me either.  :p

hmmmm...

---

### Post by mhancoc7 on 2006-11-29
I just finished installing VMware Server to a fresh install of Ubuntu CE v2.0 (Edgy). I was having the same trouble that you have mentioned. 

Here is how I fixed it.

I opened /etc/init.d/ and found 2 vmware files.

vmware
vmware-player
vmware.old.0

I had assumed that these files would not be there since I had done a complete removal of vmware-player before installing vmware-server.

I deleted vmware-player, vmware.old.0. 

I also made sure to delete the /etc/vmware/not_configured file.

Then I rebooted and all works perfect!

I hope that helps someone.

Jereme

---

### Post by mpo on 2006-11-29
@ Jereme: 

It did help for me too, thx for sharing.

Small nuance though, I settled with removing the links from /etc/rc?.d/???vmware* to the mentioned /etc/init.d/vmware-player rather then removing the script.
  ```
$ sudo rm /etc/rc?.d/???vmware-player
```

In any case I found unlinking/removing the extra init-d script less intrusive then editing the script by hand.



@ others with less luck then jereme and me:

I've found this other solution as well that somehow starts from further investigation of the issue:
[http://www.vmware.com/community/message.jspa?messageID=506502]("http://www.vmware.com/community/message.jspa?messageID=506502")

---

### Post by mango.muncher on 2006-12-04
Hey Jereme, you have nailed it. I have been using Vmware server and have had to run config every time I reboot. I have never used VM player but I found a vmware player file in etc/init.d
I used synaptic (system > administration > synaptic package manager) to remove all traces of VM player.
Reboot and all is good.

Thanks,

---

### Post by jinnk on 2006-12-12
See the following for another fix...

[http://blog.gnu-designs.com/2006/08/07/fix-vmware-vmw_have_epoll-error-message-with-current-distributions/](http://blog.gnu-designs.com/2006/08/07/fix-vmware-vmw_have_epoll-error-message-with-current-distributions/)

I had to go into the following folder:
```

/usr/lib/vmware/modules/source

```

Then I ran the for loop as referenced in the above link:
```

for foo in vmmon vmnet; do 
	tar xf $foo.tar
	perl -pi -e 's,-Werror,-DKBUILD_BASENAME=\\"\$\(DRIVER\)\\" \\\n\t-Werror,g' ${foo}-only/Makefile.kernel
	mv ${foo}.tar ${foo}.tar.vm
	tar cf ${foo}.tar ${foo}-only
done

```

Worked a charm!

---

