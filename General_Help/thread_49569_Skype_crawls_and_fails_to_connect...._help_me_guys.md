---
title: "Skype crawls and fails to connect.... help me guys.I need this."
date: 2005-07-16
forum: General Help
---

### Post by byen on 2005-07-16
Ok. I have posted something similar to this before but no one knew anything about it...so here is my one last effort to see if this works......
Problem: I installed the latest version of skype and the install seemed to go well. But once i click the icon ..the nightmare starts. It takes approx. 2-3 minutes for the main window to show up (i actually timed this), then another minute for the log-in screen to start-up and after entering the username and password...it tells me that it was unable to log-in. I tried to check my firewall to see if skype was in the active connections list but it wasnt even there.... I dont know what the problem is and would really appretiate it if someone can help me out here....! 
I installed skype before and it worked perfectly..but after a fresh Ubuntu install (had to move more GB to UB(untu), it just does not seem to work. I need this guys, Please suggest.
thank you.

PS- I dont think it is a mem problem as I have a 2800AMD with over a 1000MB in mem.

---

### Post by varunus on 2005-07-17
What is your internet connection?  Dial-up?  Wireless?  Ethernet?

Also, what is your sound card?  Did you do any special configuration with it before your reinstall?

---

### Post by vasanton on 2005-07-17
Where from do you get Skype? I think that from skype.com... 
Try to install it with Synaptic. I had the similar problem, but 
now skype works perfect.

---

### Post by byen on 2005-07-17
[QUOTE=vasanton]Where from do you get Skype? I think that from skype.com... 
Try to install it with Synaptic. I had the similar problem, but 
now skype works perfect.[/QUOTE]
 I tried both ways..used apt-get as well as downloaded the tar file from the website! seemed to install ok...but that is where it all ends....
I have a wireless network...not sure how that is relavent??

thankyou for replying.

---

### Post by varunus on 2005-07-18
Try running skype from a terminal...are there any error messages outputted that might be the cause of the slow loading/connections failing?  Maybe try disabling your firewall?

Also, do you do anything special during bootup like press CTRL-C at the "configuring network interfaces" step?  Some people have had problems because localhost wasn't up...

---

### Post by byen on 2005-07-18
> Try running skype from a terminal...are there any error messages outputted
nothing dude.... crawls and says it failed to connect!
> do you do anything special during bootup like press CTRL-C at the "configuring network interfaces" step?
nope.
But i do think the problem is this... skype is not using my internet as it always says:"fails to connect!" "fails to login" and is not active in the firewall active connection list! anything i can do to see if the firewall is blocking anything?

---

### Post by daller on 2006-01-29
Use the package from the first post in this thread to install:

[http://ubuntuforums.org/showthread.php?t=81831](http://ubuntuforums.org/showthread.php?t=81831)

---

### Post by k_smolka on 2006-01-29
i am having the same problem, i have looked everywhere and have had no luck

please let me know if you sort this out

karl

---

### Post by k_smolka on 2006-01-29
all sorted

using this .deb file from this link

[http://rapidshare.de/files/6743630/skype_1.2.0.18-1_i386.deb.html](http://rapidshare.de/files/6743630/skype_1.2.0.18-1_i386.deb.html)

hope that helps 

karl

---

### Post by k_smolka on 2006-01-29
also, i find it does not work if u are not runnning it as root

run it from the terminal as root and it will work fine 

karl

---

### Post by daller on 2006-01-30
[QUOTE=k_smolka]also, i find it does not work if u are not runnning it as root

run it from the terminal as root and it will work fine 

karl[/QUOTE]

What does running "skype" output? (As the normal user!)

Did you install the package with "sudo dpkg -i PACKAGE" ???

---

### Post by vishnumrao on 2006-02-01
I installed skype on my AMD64 machine running the 64 bit Hoary. [http://ubuntuforums.org/showthread.php?t=77069](http://ubuntuforums.org/showthread.php?t=77069)

Created a launcher on the desktop. Opening takes forever and when skype does come up, refuses to login me. 

Can some one please suggest me a solution. Also I would like to know if there is video support on skype for linux. 

Thanks,
Vishnu Rao.

---

