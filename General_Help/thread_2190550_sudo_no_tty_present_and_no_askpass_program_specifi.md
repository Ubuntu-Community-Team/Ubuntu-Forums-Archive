---
title: "sudo: no tty present and no askpass program specified"
date: 2013-11-27
forum: General Help
---

### Post by majidalig on 2013-11-27
Hello

I am trying to install BigInsights free edition from IBM's website (on Ubuntu 12.04). They have a pre-install checker available. Infosphere BigInsights pre-installation checker v2.1.0.1/

When I run the script, I get the following error.

[FONT=courier new]==============================================[/FONT]
[FONT=courier new]BigInsights Pre-Installation Check Script v1.0[/FONT]
[FONT=courier new]==============================================[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new][INFO] No cluster hostname list passed in; using localhost[/FONT]
[FONT=courier new][INFO] Verifying for single-node cluster.[/FONT]
[FONT=courier new][INFO] Running in QUICK_START mode.[/FONT]
[FONT=courier new][INFO] Dig detected.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Verify root passwordless SSH [FAILED] [/FONT]
[FONT=courier new]Verify majid passwordless SSH [ OK ] [/FONT]
[FONT=courier new]Verify majid has NOPASSWD in /etc/sudoerssudo: no tty present and no askpass program specified[/FONT]
[FONT=courier new]Sorry, try again.[/FONT]
[FONT=courier new]sudo: no tty present and no askpass program specified[/FONT]
[FONT=courier new]Sorry, try again.[/FONT]
[FONT=courier new]sudo: no tty present and no askpass program specified[/FONT]
[FONT=courier new]Sorry, try again.[/FONT]
[FONT=courier new]sudo: 3 incorrect password attempts[/FONT]
[FONT=courier new] [FAILED] [/FONT]
[FONT=courier new]Verify requiretty disabled for majid in /etc/sudoers  [FAILED] [/FONT]
[FONT=courier new][FATAL] Passwordless SSH not enabled for root or majid, terminating early.[/FONT]

I did some research and found that the requiretty can be disabled in Sudoers for a given user. So I changed by Sudoers file and restarted the computer. But I still get the same error. 

There is no help available on this subject anywhere. Could someone please help me resolve this error? I would appreciate it!

I am pretty new to Linux and have just started self educating with the help of "The Linux Command Line" book. Coming from windows and Mainframe background. I really do not want to discouraged because I could not get my head round something that might be so trivial.

---

### Post by Lars Noodén on 2013-11-28
You could try adjusting the defaults for that particular user.  Maybe adding something like this would work:

```

Defaults:majidalig !requiretty

```

Read the manual page for sudoers to be sure.

About the "Verify root passwordless SSH", that looks very suspicious.  Can you show the part of the script that is checking for that?  What do the instructions say about the key?  Giving a blank, passwordless root login is quite unsafe.  Maybe it gives instructions on what the key should be restricted to, making it a single-purpose key.  That would be more reasonable.

---

