---
title: "how to install veracrypt?"
date: 2024-06-24
forum: General Help
---

### Post by ronjjjg8885 on 2024-06-24
hello

i'm getting this missing packges..... what how can i fix it?
```
sudo dpkg -i veracrypt-1.26.7-Debian-12-amd64.deb
(Reading database ... 151884 files and directories currently installed.)
Preparing to unpack veracrypt-1.26.7-Debian-12-amd64.deb ...
Unpacking veracrypt (1.26.7-1) over (1.26.7-1) ...
dpkg: dependency problems prevent configuration of veracrypt:
 veracrypt depends on libwxgtk3.2-1; however:
  Package libwxgtk3.2-1 is not installed.
 veracrypt depends on libfuse2; however:
  Package libfuse2 is not installed.
 veracrypt depends on pcscd; however:
  Package pcscd is not installed.

dpkg: error processing package veracrypt (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.36.0-1.1ubuntu3) ...
Processing triggers for desktop-file-utils (0.27-2build1) ...
Processing triggers for shared-mime-info (2.4-4) ...
Errors were encountered while processing:
 veracrypt

```

edit.. it was similar with the ubuntu veracrypt .deb
edit..
i've also found [this]("https://askubuntu.com/questions/929195/what-is-the-recommended-way-to-use-veracrypt-in-ubuntu"). is it the correct way?

---

### Post by Holger_Gehrke on 2024-06-24
The difference between 'apt' and 'dpkg' is that the latter can't download dependencies because it's a purely local tool.  Have you tried using apt ('sudo apt install ./veracrypt-1.26.7-Debian-12-amd64.deb'; the path './' is necessary for apt to recognize that you want to install a local file) ? 'apt' will try to install any dependencies. 'libfuse2' and 'pcscd' exist on Ubuntu, 'libwxgtk3.2-1' is a very new version but can be found on Ubuntu 24.04.

Alternatively you could try 'sudo apt-get install --fix-broken' to make apt try to fix the dependency problem since dpkg has installed veracrypt but couldn't configure it since there where missing dependencies. Or you could install the missing packages manually using apt (not a really good idea since they wouldn't be marked for removal when not needed anymore if marked as manually installed).

The PPA linked in that 7 years old askubuntu-thread still exists and there are packages for all supported versions of Ubuntu there. So that would be another way to try.

Holger

---

### Post by Rubi1200 on 2024-06-24
Is there a particular reason why you want to use Veracrypt?

For full drive encryption, there is LUKS.

For directories, especially the home folder, there is eCryptfs for example.

I have never understood why people fiddle around trying/struggling to install things from outside the official repositories.

---

### Post by ronjjjg8885 on 2024-06-25
```
sudo apt install ./veracrypt-1.26.7-Ubuntu-24.04-amd64.deb 
[sudo] password for not-pc: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 veracrypt : Depends: libwxgtk3.2-1
             Depends: libfuse2
             Depends: pcscd but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


```

my whole external harddrive is encrypted with veracrypt and i need to restore my data from it as my internal hardrive has been accidentally emptied..

maybe all of the trouble stems from ther fact that i did a partial installation of ubuntu. i mean the basic one with less tools..

i will consider eCryptfs later on but first i will need my data back..

and i also tried that.. i hope i used it as needed..

```
apt-get install --fix-broken
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?

```

thanks for assisting.. hopefully my data is back soon..

---

### Post by Holger_Gehrke on 2024-06-25
As the second error message states 'apt-get install --fix-broken' needs root-permissions to work, so it needs to be prefixed with 'sudo' ('sudo apt-get install --fix-broken').

Holger

---

### Post by werewulf75 on 2024-06-26
> **Rubi1200 said:**
> Is there a particular reason why you want to use Veracrypt?  For full drive encryption, there is LUKS.  For directories, especially the home folder, there is eCryptfs for example.  I have never understood why people fiddle around trying/struggling to install things from outside the official repositories.   LUKS and eCryptfs are not secure enough - this has been pointed out a number of times in various places. Veracrypt allows for highly secure encryption, inc. cascade. It also allows for the use of very long and highly complex passwords with highest entropy. It also is extremely simple to use.  Installation with the correct .deb file couldn't be simpler too - just locate the .deb in Files or your favourite File Manager, right click it and select 'Software Install'. All done. Simple! Just make sure you have the right .deb with the version of VC that supports your version of Ubuntu.  N.B. - The official repositories do not offer all apps that there are, and a lot of apps in the repositories are older versions and are never updated.

---

### Post by currentshaft on 2024-06-26
> **werewulf75 said:**
> LUKS and eCryptfs are not secure enough - this has been pointed out a number of times in various places.

Secure enough against what? And what are the various places this is pointed out?

> **werewulf75 said:**
> Veracrypt allows for highly secure encryption, inc. cascade.

Please explain why you think cascaded encryption is more secure or even necessary with modern cryptosystems.

> **werewulf75 said:**
> It also allows for the use of very long and highly complex passwords with highest entropy.

So does LUKS.

Perhaps you have subjective reasons for using Veracrypt, but it being "more secure" than LUKS is not an objective assessment of the reality.

---

