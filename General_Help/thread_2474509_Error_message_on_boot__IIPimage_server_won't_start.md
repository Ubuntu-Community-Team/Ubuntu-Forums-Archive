---
title: "Error message on boot:  IIPimage server won't start"
date: 2022-05-01
forum: General Help
---

### Post by Jonners59 on 2022-05-01
Just tried to boot my laptop and I am getting an error message after GRUB and the Xubuntu image that says something like "Failed to start IIPimage server" and stops booting.

I had used the laptop yesterday and all was fine, but this came up today.  Any help, please?

---

### Post by Jonners59 on 2022-05-24
ANyone, PLEASE!?!?!?!?!?!?

---

### Post by oldfred on 2022-05-24
Not familiar with iipsrv?
[https://manpages.debian.org/testing/iipimage-server/iipsrv.8.en.html](https://manpages.debian.org/testing/iipimage-server/iipsrv.8.en.html)

I would not think it is part of boot process or have you loaded some graphics in background that uses that?

If you remove quiet splash in linux line in grub so boot process shown, does it give any more info? 
Errors often are several lines above last line shown.

---

### Post by Jonners59 on 2022-05-25
> **oldfred said:**
> Not familiar with iipsrv?
[https://manpages.debian.org/testing/iipimage-server/iipsrv.8.en.html](https://manpages.debian.org/testing/iipimage-server/iipsrv.8.en.html)

I would not think it is part of boot process or have you loaded some graphics in background that uses that?

If you remove quiet splash in linux line in grub so boot process shown, does it give any more info? 
Errors often are several lines above last line shown.

Hiya OldFred
Attached screenshots.

---

### Post by oldfred on 2022-05-25
So you also are running containers?
Not familiar with those either.
Do they need iipsrv?

---

### Post by Jonners59 on 2022-05-27
> **oldfred said:**
> So you also are running containers?
Not familiar with those either.
Do they need iipsrv?

AM I.  No idea.  The laptop came with Windows and I just did as I always have and installed xfce....  Had some trouble with booting, from time to time, but that was the BIOS setting typically.  The security and what options to set, but otherwise everything, I THOUGHT, is standard.  What is a "container"?

---

### Post by oldfred on 2022-05-27
I do not know containers. Google told me this:
LXC is a well-known *Linux container* runtime that consists of tools, templates, and library and language bindings. 

I use Kubuntu, so do not then know Xubuntu. But did not think Xubuntu used containers either.

---

### Post by Jonners59 on 2022-05-27
> **oldfred said:**
> I do not know containers. Google told me this:
LXC is a well-known *Linux container* runtime that consists of tools, templates, and library and language bindings. 

I use Kubuntu, so do not then know Xubuntu. But did not think Xubuntu used containers either.

That's why I am here, because I have a problem and hopefully someone can help me out, though my confidence in the system is not as strong as it was 5 years ago.

---

### Post by Jonners59 on 2022-06-20
ANyone.  ANy help PLEASE?????

---

### Post by oldfred on 2022-06-20
Run both of these. Not sure either will tell anything about error.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you want lots of details on hardware you can run this new script. Do not copy data from the screen as it may include data you do not want to share. The upload to pastebin site removes that type of data. Spacebar thru the screens & q to exit screens. The \ make this one long line, so paste all three at same time.
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/system-info/raw/main/system-info](https://github.com/UbuntuForums/system-info/raw/main/system-info) && \
chmod +x system-info && \
./system-info

---

### Post by Jonners59 on 2022-06-22
thanks OldFred.  I have some stuff to do at the moment and will study this and have a go.  It may take a few days.

---

### Post by Jonners59 on 2022-06-28
Hiya, sorry for taking so long.  In the end, I had to rebuild it.  I couldn't get anything to work, even the boot repair...  Now I have new problems to deal with as I had no back up after restoring, and I am also getting an error message when trying to install apps via SNAP or the Software Store, namely that I do not have permission, even when I try to start SNAP via cmd and add sudo, says the same.  GGGRR

---

### Post by oldfred on 2022-06-28
First thing I do is uninstall all snaps, so do not know about them.
And I only use synaptic. Have only opened Software Store once or twice to see what it looks like & I do not like it.

Probably best to ask separate questions, so title will get those who may know something can see your thread.

---

### Post by Jonners59 on 2022-06-28
Yup, may have too.  I like the layout as it's quick to find key apps, but other than that, I too am not a fan and tend to use synaptic almost all the time.

Yes, was just updating.  Seems to be getting worse.  Now lost the panels.  Sigh

---

