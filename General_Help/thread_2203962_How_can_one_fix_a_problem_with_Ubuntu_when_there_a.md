---
title: "How can one fix a problem with Ubuntu when there appears to be no fixes ??"
date: 2014-02-06
forum: General Help
---

### Post by ibates on 2014-02-06
I am a long time user of ubuntu.  Currently running 12.04.4 LTS updated as at a few days ago.

Over the years, I have had some difficulties and have always sought assistance on this forum.

Generally there is good advice aplenty and the problem is quickly sorted, but occasionally, there just seems to be no assistance available.  Sure there are always a couple of attempts at obvious solutions, but when it comes down to the nitty gritty, it all runs out of puff.

Now is just one such occasion.

A few days ago, right out of the blue, the system simply did not load.  Pages and pages of lines of what is happening, what is not happening, and a few errors and warnings, including one FATAL one, but nothing that I can easily reproduce on paper or in a file.

But the real long and short of it is that since then, I can not access my Ubuntu on which I have been relying for years.  I can access the "failed" HDD by booting from a LiveCD, but of course, I can run no apps.

So I have posted a couple of threads on this forum in an attempt to identify the problem, and to find a solution.  Because, until I do, I cannot even access my backup drive, which of course, I would prefer not to do while the contents of the original drive are still there.  There have been a couple of replies to my posts, but to date, nothing has helped, and now there seems to be no further assistance.

But I cannot load my system.  I am totally stuck and at the mercy of technical advice from this forum.  I am simply not aware of anywhere else to get support, and I certainly do not have the technical expertise to analyse the problem myself.

And in the meantime, I am forced to revert back to my arch-enemy software, albeit apparently reliable, Windows XP, which fortunately, I can still access through the GRUB menu.

What is so frustrating is that everything appears to be completely normal except that Ubuntu will simply not load.

What can I do?  Is there technical support out there for when the chips are down?

---

### Post by ajgreeny on 2014-02-06
Can you see the contents of your ubuntu partitions from a live boot of a ubuntu system?

If you can see files and folders you can easily rescue your personal files etc etc to a usb drive.

However, from a live ubuntu system run the command ```
sudo e2fsck /dev/sda#
``` to see if there is a filesystem problem that this will fix.
The partition sda# is your root partition, so change the sda# to suit your system, and make sure that partition is unmounted or the command will not run.

---

### Post by ibates on 2014-02-06
Thank you for your quick response.

Please let me explain that I have already opened two previous threads in an attempt to identify the problem I am experiencing.  The first was 4th February at 0123, entitled *Boot Failure and Failed boot-repair*, while the second post (which followed on from the first) was on the 5th at 1204, entitled *Startup failure Ubuntu 12.04*.  These two posts contain some logs posted.

Yes; I am aware that I can retrieve my files, etc., on to a USB drive, or for that matter, another HDD, or to my network.  They all work perfectly after booting up on the LiveCD.  So that is not a problem. It is just that that is a very time consuming and messy way to go about solving the problem, and would require a re-installation of Ubuntu.  As someone said somewhere on this forum, re-installation should be a last resort.

I ran the command you suggested and it yielded "clean".

Can you suggest anything else.  Perhaps some log from somewhere which might shed some light on the problem?

---

### Post by fdrake on 2014-02-06
can you post here the screen shoot of your fatal error?
also using a live cd post here the logs: /var/log/messages  and /home/your_username/.xerrors

---

### Post by ajgreeny on 2014-02-06
It would have been much more useful to all of us if you had just used a single forum thread to sort this out and not posted several at different times; we now have to go searching for what has alteady been said, and you don't even hsve links to those, just titles.

I will see if I can help further if possible but have no time right now.

---

### Post by grahammechanical on 2014-02-06
I am just a user like you. We all are users who try to help out as we can. I do not know what is wrong with your system but here is what I would do in your place.

1) Pull off of the hard drive all the data that I do not want to lose.
2) Re-install Ubuntu without ticking "Format the partition."
3) Keep my fingers crossed that all goes well.

I have had to do this in the past. I now keep my data on a separate partition from the partition that Ubuntu is on. So, that if I need to re-install my data is safe. And I can then instruct the installer to format the partition to remove any configuration files that are causing the problem.

I have several installs of Ubuntu, including developmental versions of Ubuntu and its flavours. Re-installing is the sure way of fixing things. It works every time for me.

Everything happens for a reason. It may seem to us that it just happened. But it did not. It is hard to provide solutions when we do not know what happened or why it happened. I wish a had a list of all the possible things that could go wrong and alongside each entry there was instructions on how to fix things. Such a book does not exist.

Regards.

---

### Post by grier-devon on 2014-02-06
Remember to use the bump method instead of using multiple threads for the same problem. Also I always start on this forum but if for some reason people cannot help me here which does not bother me since we are all volunteers I am a member of a general linux forum, I think people sometimes forget that Ubuntu is Linux which means many general ways of doing something will fix our issues and then you also get users from more different back grounds which a lot of times can provide more information.

---

### Post by ibates on 2014-02-06
Reply to fdrake:  Re the FATAL error message:  I was able to copy the "suspect" file mentioned in the FATAL error message, with the same file from another Ubuntu system running the same OS.  The FATAL error disappeared, but unfortunately, the startup still stops and hangs at the same point before the log-in screen.  In fact, with continuing "no -irq" message filling the page, over and over, *ad infinitum*.  But, for your information, the FATAL message prior to replacing the *echo.ko* file was 

*loading essnetial drivers .... FATAL: Error inserting echo (.lib/modules/3.2.0-58-generec-pae/kernel/drivers/staging/echo/echo.ko): unknown symbol in module, or unknown parameter (see dmesg)*.

That particular *dmesg* file is attached to my other thred posted on 5th Feb and entitled "Start-up failure Ubuntu 12.04". 

The "messages" file you requested contains 0 bytes so I have not attached it.

The attachment facility here does not show the (hidden)* .xsession-errors* file and so I do not know how to attach it here.  I cannot open it and so cannot even paste the contents. Any suggestions as to how I can get ii posted?

But for what it is worth, attached is a copy of the *dmesg* file after the echo.ko file was replaced.

---

### Post by ibates on 2014-02-06
Reply to ajgreeny:  Thanks for your reply.  Unfortunately, after posting the first thread, it became obvious that post did not correctly describe the problem and replies had stopped.  Thus the new thread more accurately stating the problem.  The third thread originated out of desperation .  I did not know anything about the "bump" facility and so that is how it happened.  I thought a bump was only found on rough roads. Unfoirtunately, my technical skills are not great, but despite that limitation, I have hung my data processing hat on Ubuntu.  Perhaps that is the reason for my apparent desperation.  I will try to do better next time.

---

### Post by oldfred on 2014-02-06
For reference I just closed older threads rather than merge them.

Older threads for reference.

Start-up failure ubuntu 12.04 
reviewed modeprobe type issues.
[http://ubuntuforums.org/showthread.php?t=2203531](http://ubuntuforums.org/showthread.php?t=2203531)

    
[h=2][/h] Boot failure and failed boot-repair First thread

    Boot repair, fsck & boot parameters typo issues reviewed
[http://ubuntuforums.org/showthread.php?t=2202374](http://ubuntuforums.org/showthread.php?t=2202374)

I still suspect the current boot parameters may not have been correct but did not cause an error, but update now does not accept those parameters. There was a typo on one that never should have worked and others that were obsolete.

I do not recognize some of these, but many systems need unusual parameters.
>  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash no modeset video=uvesafb:mode_option=1600x1200-24,mtrr=3,scroll=ywrap"




---

### Post by brokenhachi on 2014-02-06
have you tried booting into a livecd and reinstalling the nvidia drivers? Seems like nvidia is leaving TAINT and causing boot failure..? 

```
sudo mount /dev/ROOTPART /mnt
sudo chroot /mnt
sudo apt-get install --reinstall nvidia-current 
```

also, can you post /var/log/kern.log from the broken filesystem?

---

### Post by ibates on 2014-02-21
I will attempt the process which you have defined.

In the meantime, I have five kern.log files.  I am not sure which ones were prior to the failure and which ones were after.  So I have picked the middle one, for no other reason than it is the most recent which has been compressed.  The two most recent files are quite large and the upload facility doesn't seem to llike that.

---

### Post by ibates on 2014-03-01
brokenhachi:  I ran the commands you suggest from terminal after booting from the LiveCD, and things seemed to go OK until a long list of FATAL Errors started appearing, all relating to the Linux Kernel used by the LiveCD.

However, it did make a change.  Instead of things just going into an endless loop of printing no-irq messages, it actually booted up to a tty login.  And then I was able to log in using the normal username and password, but only to a terminal command line.  Progress perhaps, but apparently not very useful.

I then tried to boot up again, this time in Recovery Mode.  Things did look a bit promising, but eventually it went back to the same old loop going nowhere.

An interesting sideline is that the boot up screen displays an Ubuntu logo I had not seen before, but only until the pre-failure scripts commence.

---

### Post by tgalati4 on 2014-03-01
When you get into an endless loop, hit Control-C or Control-D and that will sometimes stop the loop.  Log into the Recovery Console (root terminal) and page through dmesg and take note of the errors:

```
dmesg | less
```

Spacebar to page forward, "q" to quit.

Your system has failed in a subtle, but fatal way.  Have you cleaned out the machine and reseated everything?

---

### Post by ibates on 2014-08-14
update-nvidia fixed the problem.

---

