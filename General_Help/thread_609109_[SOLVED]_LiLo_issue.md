---
title: "[SOLVED] LiLo issue"
date: 2007-11-10
forum: General Help
---

### Post by Cariboo1938 on 2007-11-10
Hi all,
I use the GAG boot floppy to double boot Feisty-amd64 and Windows XP.
For this purpose I installed LiLo as described [HERE]("http://users.bigpond.net.au/hermanzone/p12.htm").
The LiLo config file (attached) shows that the boot loader is supposed to use kernel 2.6.20-16-generic. This is also the kernel GRUB uses and it is the one I need for using the "Restricted Driver nvidia". 
When I check with 'uname -a' I get the response for the running kernel  
"kernel 2.6.20-15-generic". 
Consequence of that, my Xserver failed to start and I have to change the graphic driver to 'nv' to get GUI back.
What do I have to do to get the same kernel either using GRUB or LiLo to boot the system?

---

### Post by Cariboo1938 on 2007-11-14
I have still this LiLo issue......What Info do I have to provide?
Please Help....!:(

---

### Post by Cariboo1938 on 2007-11-18
Hello,
As (Herman) suggested that I have probably  an older kernel with the wrong name my lilo.conf is referring to, I post a screenshot of the Synaptic Package Manager showing all the Linux related packages installed an my computer. 
I'm not sure what is really needed and what not.
Any ideas?

---

### Post by Herman on 2007-11-19
Hello Cariboo1938,
If you want to try uninstalling and re-installing the kernel, I think probably you just need to right-click on the line for linux-image-2.6.20-16-generic and click uninstall.  I'm not sure either because I have never needed to do that.  Then re-install it again and see if it helps.

But wait a minute before you do anything....
Actually, now that I have re-read your original post again, I see that you also boot with GRUB sometimes,
> This is also the kernel GRUB uses and it is the one I need for using the "Restricted Driver nvidia". 
 Do you still get '2.6.22-15-generic' from 'uname -r' after booting vmlinuz-2.6.20-16-generic with GRUB?

Regards, Herman :)

---

### Post by Cariboo1938 on 2007-11-19
Hello Herman, glad to 'see' you here! 
You asked me
> Do you still get '2.6.22-15-generic' from 'uname -r' after booting vmlinuz-2.6.20-16-generic with GRUB? 
Answer NO!
Here is what happens if I boot either with GRUB or GAG:

Booting with GRUB:--->Everything is OK

karibu@karibu-desktop:~$ uname -a
Linux karibu-desktop [COLOR="Green"]2.6.20-16-generic #2 SMP Sun Sep[/COLOR] 23 18:31:23 UTC 2007 x86_64 GNU/Linux
karibu@karibu-desktop:~$ 



Booting with GAG (LiLo):--->Xserver failed to start
---> no GUI
---> only black screen with command prompt
---> after login/password I checked the installed kernel:

karibu@karibu-desktop:~$ uname -a
Linux karibu-desktop [COLOR="Red"]2.6.-15-generic #2 SMP Sun April[/COLOR] 15 06:17:24 UTC 2007 x86_64 GNU/Linux
karibu@karibu-desktop:~$ 
I reboot with GRUB and I'm back to normal.

How can it be that lilo starts a different kernel?:confused:
Kind regards
Cariboo

EDIT:
In directory /boot I have two vmlinuz files----
vmlinuz-2.6.20-15-generic and vmlinuz-2.6.20-16-generic.
How can I figure out which one the LiLo is referring to?

---

### Post by Cariboo1938 on 2007-11-20
I wonder which file/program/location could I check for the fact that LiLo chooses the wrong 'vmliuz' in my case, when it boots from the GAG boot floppy.:(

---

### Post by Cariboo1938 on 2007-11-20
I'm still trying to figure out why using LiLo to boot the system kills the Xserver.
I run /sbin/lilo
> 
karibu@karibu-desktop:~$ sudo -s
Password:
root@karibu-desktop:~# /sbin/lilo
Warning: /etc/lilo.conf should be writable only for root
[COLOR="Red"][I]Warning: Unable to determine video adapter in use in the present system.
Warning: Video adapter does not support VESA BIOS extensions needed for
  display of 256 colors.  Boot loader will fall back to TEXT only operation.[/I][/COLOR]
Added Lin_2.6.20img1 *
Added Memory_Test+
Added Windows_XP
root@karibu-desktop:~# 
could [COLOR="Red"]*these*[/COLOR] warning be the reason?
Is there a work around?"

---

### Post by Herman on 2007-11-21
Hello Cariboo1938,
I wouldn't pay any attention to that error message, I think everyone gets that. I always get it too, I even included it in my [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html"), look about 1/3 of the way down the page, in figure8lilo.
My computer booted fine with LiLo the last time I tested it. 
It didn't occur to me to bother checking which kernel was actually being booted.

Did you remember to run /sbin/lilo after your kernel update?
```
sudo /sbin/lilo
```> One thing users will need to know about Lilo is that after a kernel update, we need to edit /etc/lilo.config and run /sbin/lilo to update Lilo.Try running /sbin/lilo.
Sorry, but I forgot all about that, I should have checked with you about that first, (my bad).

Regards, Herman :)

---

### Post by Cariboo1938 on 2007-11-21
Thank you Herman for your patience......Thank you for spending your time!
......I thought i did run 
```
sudo /sbin/lilo
```
but obviously not in the first place!
So now, after running the LiLo update finally it works well.
Case closed.
Thanks
Cariboo:)

BTW: it is /etc/lilo.conf and not /etc/lilo.conf[COLOR="Red"]ig[/COLOR]

---

### Post by Herman on 2007-11-21
Thanks, Cariboo,
It's been my pleasure to be able to help you. :)
>  BTW: it is /etc/lilo.conf and not /etc/lilo.conf[COLOR=Red]ig[/COLOR]
 Oops! :oops: My bad, (again).

I can see now that I should do a little more work with LiLo and update that LiLo page of mine and make a few improvements in it for those who use LiLo. 

Regards, Herman :)

---

