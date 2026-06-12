---
title: "VirtualBox Keyboard &amp; Hostkey not working"
date: 2008-05-08
forum: General Help
---

### Post by pkkid on 2008-05-08
I cannot even install WindowsXP in my VirtualBox because the keyboard does not work.  This is very annoying because the hostkey doesn't work either.  The only way to get out of the VM is to press "Alt+Ctrl+Backspace" to restart X and log back into my account.

I already tried [this solution]("http://forums.virtualbox.org/viewtopic.php?t=5721") stating to install scim-bridge-client-qt which no avail.

If it helps, I am using:
* Ubuntu Hardy 8.04 (Upgraded from Gutsy)
* SCIM Input (for Chinese)

---

### Post by pkkid on 2008-05-10
Bump.. Nothing?

---

### Post by hugh_h_chen on 2008-05-11
well, i had the same problem too, and i am a Chinese user. this is due to the scim input method. i solved the problem now, you do the following:

1. disable the keyboard auto capture in the fiel>preference>input. (this maynot be really needed. but just to be safe).
2. quit your scim input before you start your virtualbox.
3. start your virtualbox.
4. during windows installation, click the control key on the right of your space bar to capture your keyboard, then you can hit the enter key to choose to install window on the blue installation screen booted from your windows installation cd rom.

now, if you get lucky, you don't have to install window using a cd or iso. virtuabox is using vdi file, so copy a vdi file from your friend or your ealier vdi backup. register this vdi file to your virtualbox. just in a second, you have a windows. well, the legality use of windows is an issue, as you are using your friend's windows key..... or you just install windows the way above.

sometimes, my EVA will crash after i quit scim....and i don't know why.

---

### Post by DonnyB4e56 on 2008-05-17
Thank you this worked for me. I had a Korean SCIM open.

---

### Post by pkkid on 2008-05-18
Thanks! -- How naive of me not to try the simplest of solutions (quit SCIM) before starting VirtualBox.  Works great now!

Too bad we can't have both working at the same time.

---

### Post by labso on 2008-05-22
I had the same problem, but my solution is...
Install gcin and exec the following command...
$>im-switch -s gcin
$>reboot

---

### Post by hugh_h_chen on 2008-06-01
> **labso said:**
> I had the same problem, but my solution is...
Install gcin and exec the following command...
$>im-switch -s gcin
$>reboot

OK&#65292; i tried gcin, it's not working for me. it's more for the traditional Chinese input. Sucks for simplified chinese. i think the 2nd most popular chinese input method for simplified chinese is fctix&#12290;&#12290;&#12290;&#12290;voted by Ubuntu simplified chinese forum. i didn't try fctix yet.

---

### Post by zhkh325 on 2008-08-12
I'm a Chinese ,too.I've searched lots of ways to solve the problem,but none works.Thank you.

---

### Post by chew1976 on 2008-08-12
My solution is, do not click inside the guest screen when installing. Instead, use Right-Ctrl to enable keyboard then press Enter to install. Once your windows loads the graphical bits, it will be ok.

---

### Post by pafer on 2008-11-18
Hi....
This site is really cool.....
Thanx.....

---

### Post by wormite on 2008-11-19
```
 Re: VirtualBox Keyboard & Hostkey not working
My solution is, do not click inside the guest screen 
when installing. Instead, use Right-Ctrl to enable 
keyboard then press Enter to install. Once your windows 
loads the graphical bits, it will be ok.
```


This worked for me

---

### Post by lakemove on 2009-01-31
My Solution :

in (SCIM input setup) "Front End" -> "Global Setting"  :

unselect the option "Embed Preedit String into client window "

then all works.

thank you guys !

---

