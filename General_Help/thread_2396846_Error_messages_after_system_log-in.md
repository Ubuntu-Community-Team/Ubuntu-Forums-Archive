---
title: "Error messages after system log-in"
date: 2018-07-21
forum: General Help
---

### Post by de Bacon on 2018-07-21
Hi,
A couple of days back and after loading a "Security update," I began getting an error popup when logging on to the system (UbuntuStudio 14.04).  No real information is supplied by the popup, only a Error report prompt comes up requiring a pass word, which I see as suspicious (only due to being skeptical about most things, where founded or not).  

1. I eventually submitted to the prompt to send a report.  (after taking steps to protect my system password) 

2.  I booted to a live disk -> went to GParted and had it perform a HDD check.  Nothing changed as a result.

3.  I opened synaptic and ran the reload of repositories to receive the following message.

```
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/brave-xenial.list:1 and /etc/apt/sources.list.d/brave-xenial.list:2
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/brave-xenial.list:1 and /etc/apt/sources.list.d/brave-xenial.list:2
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/brave-xenial.list:1 and /etc/apt/sources.list.d/brave-xenial.list:2
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/brave-xenial.list:1 and /etc/apt/sources.list.d/brave-xenial.list:2
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/brave-xenial.list:1 and /etc/apt/sources.list.d/brave-xenial.list:2
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/brave-xenial.list:1 and /etc/apt/sources.list.d/brave-xenial.list:2

```

3a. I then went to file manager and viewed the file listed. I can see the error, as the initial line of text is then duplicated on a second line. I tried to alter it by making a duplicate having a suffix .bu, to preserve what was listed, then change the original, but the file protections don't allow it. Here is what I want to do. Using a sudo command, change the permissions.  Then edit the file, removing the duplicated line,  then return the permissions to their original state.  After that I'll test the result.  

The problem with this  for me is:  I don't know how to re-set the permissions back to what they now are. The file's permissions at present are:

Owner: root (root)
Access: Read & Write
Group: root
Access: Read only
Otheres: Read only

The issue I have is I don't know the numeric sequence ie 722, which would follow the sudo chmod command for this Root owned file.

These things make sense to me for user owned protections, but the Root owned ones have a different syntax in their setting, as I understand it, or to say that is what I believe to be true.

Even so, I am unsure that correcting this is what is required to correct the log-in error issue.

Thanks for assistance in advance.
Regards,

Tom

---

### Post by kazakore on 2018-07-21
I usually edit System files in the commandline using nano.

```
sudo nano /path/to/protected/file
```

But there are many other ways to get this done.....

As you are still using 14.04 you could try

```
gksu gedit /path/to/file
```

---

### Post by de Bacon on 2018-07-22
I tried this suggestion, using the syntax suggested.  However, the result, in a test scenario, did absolutely nothing to the status of the permissions.  It did cause the terminal emulator window to go into some unusable mode, apparently having no function what so ever.  

Thanks for trying.
Tom

---

### Post by de Bacon on 2018-07-25
Two days later, the error message ceased showing up at boot, without obvious reason, no updates occurred.

---

