---
title: "Problems with Software Center"
date: 2015-08-10
forum: General Help
---

### Post by pthfdr on 2015-08-10
When I install any softwares in software center the following error messages appeared:
Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.102'}): org.debian.apt.install-or-remove-packages

---

### Post by matt_symes on 2015-08-10
Hi

Firstly, can you install anything or is the only problem with authentication ?

Open a terminal and type

```
sudo apt-get install htop
```

Enter you password. It will not be echoed to the screen.

Does htop (a small top like utility) install correctly ?

You may want to copy and paste the output from the terminal into your next post.

Kind regards

---

### Post by pthfdr on 2015-08-10
I can.APT works normally.
The problems only appears when I install from Software Center.

---

### Post by matt_symes on 2015-08-10
Hi

Excellent. 

The next thing to check is the authentication agent.

Open a terminal and type these commands. Copy and paste the output from these commands into your next post so I can check them for you.

```
ps aux | grep polkit
```

```
dpkg -l | grep polkit
```

That's a small L in the command above.

In the first command, we're looking to see if the agent is running.

Kind regards

---

### Post by pthfdr on 2015-08-10
```
pthfdr@TRINITY:~$ ps aux | grep polkit
root       822  0.0  0.0 281172  7276 ?        Sl   20:01   0:00 /usr/lib/policykit-1/polkitd --no-debug
pthfdr    1885  0.0  0.2 331624 17232 ?        Sl   20:01   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
pthfdr    3126  0.0  0.0  15948  2160 pts/0    S+   20:16   0:00 grep --color=auto polkit
pthfdr@TRINITY:~$ dpkg -l | grep polkit
ii  libpolkit-agent-1-0:amd64                             0.105-4ubuntu2.14.04.1                              amd64        PolicyKit Authentication Agent API
ii  libpolkit-backend-1-0:amd64                           0.105-4ubuntu2.14.04.1                              amd64        PolicyKit backend API
ii  libpolkit-gobject-1-0:amd64                           0.105-4ubuntu2.14.04.1                              amd64        PolicyKit Authorization API
pthfdr@TRINITY:~$ 
```

---

### Post by matt_symes on 2015-08-10
Hi

Good. The agent is running.

I'm away from any PC at the moment. I'll post further instructions in the next couple of hours.

Kind regards

---

### Post by matt_symes on 2015-08-10
Hi

Open a terminal and please post the output of these commands.

```
cat /usr/share/polkit-1/actions/org.debian.apt.policy
```

And

```
pkaction --verbose --action-id org.debian.apt.install-or-remove-packages
```

Kind regards

---

### Post by Bashing-om on 2015-08-10
matt_symes; Hi !

As per my norm I follow your threads and this one has my interest.
Heads up, on my xfce system the target directory of your inquiry does not exist:
```

sysop@1404mini:~$ ls -al /usr/share/polkit-1/actions/
total 380
drwxr-xr-x 2 root root   4096 Jul 29 11:43 .
drwxr-xr-x 3 root root   4096 May 19  2013 ..
-rw-r--r-- 1 root root    790 Sep 18  2014 com.ubuntu.languageselector.policy
-rw-r--r-- 1 root root  19584 Feb  4  2015 com.ubuntu.release-upgrader.policy
-rw-r--r-- 1 root root    783 Feb 23  2014 org.debian.aptxapianindex.policy
-rw-r--r-- 1 root root  19721 May 13 13:59 org.freedesktop.accounts.policy
-rw-r--r-- 1 root root  48818 Jan 16  2014 org.freedesktop.color.policy
-rw-r--r-- 1 root root   2773 Jul 15 14:13 org.freedesktop.hostname1.policy
-rw-r--r-- 1 root root   1878 Jul 15 14:13 org.freedesktop.locale1.policy
-rw-r--r-- 1 root root  21211 Jul 15 14:13 org.freedesktop.login1.policy
-rw-r--r-- 1 root root   1524 Mar  4 16:45 org.freedesktop.policykit.policy
-rw-r--r-- 1 root root   1489 Oct 25  2013 org.freedesktop.RealtimeKit1.policy
-rw-r--r-- 1 root root   3507 Jul 15 14:13 org.freedesktop.timedate1.policy
-rw-r--r-- 1 root root 222498 Jun 10 11:58 org.freedesktop.udisks2.policy
-rw-r--r-- 1 root root   2290 Dec 21  2013 org.freedesktop.upower.policy
-rw-r--r-- 1 root root   5133 Dec 21  2013 org.freedesktop.upower.qos.policy
sysop@1404mini:~$

```
Just looking at the possibility of making adjustments.

[INDENT][INDENT]cheerfully
[INDENT][INDENT][INDENT]onward
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pthfdr on 2015-08-11
```
pthfdr@TRINITY:~$ cat /usr/share/polkit-1/actions/org.debian.apt.policy
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>


  <vendor>Apt Daemon</vendor>
  <vendor_url>http://launchpad.net/aptdaemon/</vendor_url>
  <icon_name>package-x-generic</icon_name>


  <action id="org.debian.apt.get-trusted-vendor-keys">
    <description gettext-domain="aptdaemon">List keys of trusted vendors</description>
    <message gettext-domain="aptdaemon">To view the list of trusted keys, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.clean">
    <description gettext-domain="aptdaemon">Remove downloaded package files</description>
    <message gettext-domain="aptdaemon">To clean downloaded package files, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.change-config">
    <description gettext-domain="aptdaemon">Change software configuration</description>
    <message gettext-domain="aptdaemon">To change software settings, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.change-repository">
    <description gettext-domain="aptdaemon">Change software repository</description>
    <message gettext-domain="aptdaemon">To change software repository settings, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.install-file">
    <description gettext-domain="aptdaemon">Install package file</description>
    <message gettext-domain="aptdaemon">To install this package, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.update-cache">
    <description gettext-domain="aptdaemon">Update package information</description>
    <message gettext-domain="aptdaemon">To update the software catalog, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.install-or-remove-packages">
    <description gettext-domain="aptdaemon">Install or remove packages</description>
    <message gettext-domain="aptdaemon">To install or remove software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.install-packages.high-trust-repo">
    
    <description gettext-domain="aptdaemon">Install software from a high-trust whitelisted repository.</description>
    <message gettext-domain="aptdaemon">To install software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.install-packages-from-new-repo">
    
    <description gettext-domain="aptdaemon">Add a new repository and install packages from it</description>
    <message gettext-domain="aptdaemon">To install software from a new source, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.install-purchased-packages">
    
    <description gettext-domain="aptdaemon">Add a new repository of purchased software and install packages from it</description>
    <message gettext-domain="aptdaemon">To install purchased software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.upgrade-packages">
    <description gettext-domain="aptdaemon">Upgrade packages</description>
    <message gettext-domain="aptdaemon">To install updated software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.cancel-foreign">
    <description gettext-domain="aptdaemon">Cancel the task of another user</description>
    <message gettext-domain="aptdaemon">To cancel someone else's software changes, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
  </action>


  <action id="org.debian.apt.set-proxy">
    <description gettext-domain="aptdaemon">Set a proxy for software downloads</description>
    <message gettext-domain="aptdaemon">To use a proxy server for downloading software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
  </action>


</policyconfig>pthfdr@TRINITY:~$ pkaction --verbose --action-id org.debian.apt.install-or-remove-packages
org.debian.apt.install-or-remove-packages:
  description:       Install or remove packages
  message:           To install or remove software, you need to authenticate.
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep


pthfdr@TRINITY:~$ 

```

---

### Post by pthfdr on 2015-08-12
No worries now.
I applied the ultimate solution.
I reinstalled the system.

---

### Post by Portaro on 2015-08-12
The software center have critical problems on 14.04 , I think.

In my case I use Lubuntu and I know that software center is not recomended to use on derivatives but, I install it to find more programms.

But I have this problem related here and in this momment other very strange , I can choose program try to install but the process of install never find and in some cases appear a message about "cant install" because "packages cant be registered " or something like that.

However I only use the software center to see names of packets and descriptions that I think interesting programs for me , and then I install by command liine.

Final -> Software-center have some problems in the gestion of a installation of programs.

:D

---

