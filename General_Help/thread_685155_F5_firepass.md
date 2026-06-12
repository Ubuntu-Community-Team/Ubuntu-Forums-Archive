---
title: "F5 firepass"
date: 2008-02-01
forum: General Help
---

### Post by hebetude on 2008-02-01
Has anybody been able to install this?  I'm thinking it is failing, because the automagic browser installer requires root access (argh!) to function.  I tried running firefox within a 'sudo -i' terminal and I still couldn't get it to work.

---

### Post by fwilliams on 2008-04-15
Yes. It is installed and I use it all the time.  When it was installing it asked if I wanted to run it as root or sudo, I chose sudo and it installed the plug-in correctly in Firefox 2.  I am not able to use it with Firefox 3 beta 4 or beta 5, it just says Connecting 0% after I key in my ID and password,

---

### Post by hebetude on 2008-04-15
The plugin for ff installs fine, it does not support ff3.  The trick was getting to the other software to be installed.  It must be installed as root and goes into some directory like /var/lib/F5.  For some reason the link to this software is on an arbitrary page referring to "dial-up" inside of a hidden div.

Go figure

---

### Post by fwilliams on 2008-04-16
So, you were able to resolve the problem?

---

### Post by vgrisham on 2008-04-18
Has anyone had any luck getting this to work in Firefox 3?

---

### Post by starkadder on 2008-05-12
I rolled back to firefox 2:

sudo apt-get autoremove firefox-3.0
sudo apt-get install firefox-2

---

### Post by hebetude on 2008-05-12
I had to use FF2 32bit, it doesn't work with FF3 64bit or FF2 64bit.  It works fine with FF2 32bit.  I do web work, so it is somewhat cumbersome when my stuff taxes the browser and my VPN connection is reliant on it.

Hopefully, they will at least support FF3's Prism.

---

### Post by dsmith1974 on 2008-06-17
Where can I download the F5 plug-in for FireFox-2?

Many thanks,

Duncan

---

### Post by chris_nava on 2008-06-17
As far as I know, you can not download the client from a website.  It is downloaded/installed by the web plugin mentioned above.  It is also executed by the plugin... so if you can't get the plugin working i don't think the binary will help.

---

### Post by bzimnoch on 2008-06-18
No luck with F5 plugin on Firefox 3 final release. It will not even install.  Works fine on last version of Firefox 2 version 2.0.0.14

---

### Post by dsmith1974 on 2008-06-18
Thanks for the reply.  Unfortunately (for me) even though I am using FF2 the plug-in for Ubuntu/Linux does not automatically install when I log in to my companies firepass website and access a terminal server (like it did for IE/FF on Windows XP)

Should this just work?  Should I raise it with my IT dept?  Are there any diagnostics/data I could gather to attempt to find out why the plug-in is not being offered for installation?

Many thanks,

Duncan

---

### Post by dsmith1974 on 2008-06-19
Thanks, seems I do not get the plug-in installed auto-magically when using Ubuntu - are they any diagnostics or debug info I could collect that may assist in fault finding or progressing the issue futher?

Many thanks,

Duncan

---

### Post by muddyh2o on 2008-06-25
no joy. FF3 on 8.04

:(

has anyone gotten this to work, or has anyone heard anything from F5 on this?

---

