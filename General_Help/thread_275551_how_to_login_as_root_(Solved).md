---
title: "how to login as root (Solved)"
date: 2006-10-11
forum: General Help
---

### Post by fyz on 2006-10-11
Dear all,
I try to login as root user. But always fail. The error message is something like:
"The system administrator is not allowed  log in from this screen"

I have set the password for root user using following command:
sudo passwd root

Anybody can help? Thanks a lot!

---

### Post by PriceChild on 2006-10-11
Ubuntu disables the root account as a security feature.

Precede commands with "sudo" instead.

For further reading: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-10-11
There's no need to log in as root.

If you want to be root from the terminal, type ```
sudo -i
``` If you want to browse as root graphically ```
gksudo nautilus
``` for Ubuntu ```
kdesu konqueror
``` for Kubuntu ```
gksudo thunar
``` for Xubuntu

---

### Post by dphipps on 2006-10-11
When loged in as normal user go to System>Administration>Loginn Window and check the tab next to Allow local system admisistrator login under the Security tab.

---

### Post by fyz on 2006-10-11
thank all of you!
It works!!

---

### Post by yman on 2006-10-11
if you set the root password then in the login screen you enter "root" as your username and then enter the root password.

to set the root password:
$ sudo setpass root
enter your password (it should be the admin pass, methinks)
enter the desired root password. enter it again.

there you go!

---

### Post by Michelangelo1973 on 2006-10-21
i just can't wait to try it, i'm making the migration from windows and it's annoying to give the password to anything every 10 secs....
sorry i'm on a loaned machine:evil: 
if it works u gonna hear of me for tankx:p

---

### Post by Crimson_Wake on 2008-01-30
Okay, I'm new to this whoel thing.

I'm trying to change my usplash.conf file and I cannot save it to update my video settings and make my boot time shorter.

How do I login as root?

I did what dphipps suggested, but what do I do now?  I also went into terminal and tried to do what ymann suggested, but the command wasn't found.

I'm on xubuntu 7.10 Gutsy.

Thanks!

---

### Post by Crimson_Wake on 2008-01-30
I've tried going into terminal and...

sudo chmod u+rwx /etc/usplash.conf

and nothing happens.

I'm confused as to how I make changes in the system.  I went into terminal and gave the SU command and I don't have a password.  Root, my admin password, and 'blank" do not work either.

Any ideas?

---

### Post by aysiu on 2008-01-30
> **Crimson_Wake said:**
> 
I'm trying to change my usplash.conf file and I cannot save it to update my video settings and make my boot time shorter.

How do I login as root? You don't need to.

Press Alt-F2 and paste in ```
gksudo thunar
``` This will launch a file browser with root privileges. From within that browser, modify usplash.conf to your heart's content.

---

