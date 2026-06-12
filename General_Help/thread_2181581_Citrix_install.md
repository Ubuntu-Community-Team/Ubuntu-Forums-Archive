---
title: "Citrix install"
date: 2013-10-18
forum: General Help
---

### Post by mike115 on 2013-10-18
[http://ubuntuforums.org/showthread.php?t=2104799&highlight=icaclient.postins](http://ubuntuforums.org/showthread.php?t=2104799&highlight=icaclient.postins)

Hello everyone ... I am trying to get citrix working on ubuntu 13.10.  I am trying to follow the directions in the link listed above 

> **Steeperton said:**
> I presume you're using 64bit Ubuntu?

1. Install the .deb and let it fail
2. Edit /var/lib/dpkg/info/icaclient.postinst
3. Replace the line that says ```
echo $Arch|grep "i[0-9]86&quot;  >/dev/null 
```with ```
echo $Arch|grep -iE "x86_64"  >/dev/null
``` 
4. Run dpkg --configure icaclient

Taken from [http://forums.citrix.com/thread.jspa?threadID=306353&tstart=0](http://forums.citrix.com/thread.jspa?threadID=306353&tstart=0)

However I can't get past step 2... I found the file and am trying to edit it however as soon as I make the change the file comes back as read-only.  Only been on Ubuntu for a couple of weeks and I like it alot but if I can't remote into my work PC its not really all that practical.

---

### Post by Toz on 2013-10-18
You probably need root privileges to edit the file. From a terminal window, try:
```
sudo -i leafpad /var/lib/dpkg/info/icaclient.postinst
```
...and type in your password when prompted to get access to the file.

---

### Post by mike115 on 2013-10-18
```
sudo -i leafpad /var/lib/dpkg/info/icaclient.postinst
-bash: leafpad: command not found


```

Looks like I am still missing something

---

### Post by Toz on 2013-10-18
Sorry, I thought lubuntu came with leafpad. Try it with mousepad:
```
sudo -i mousepad /var/lib/dpkg/info/icaclient.postinst
```
...or gedit:
```
sudo -i gedit /var/lib/dpkg/info/icaclient.postinst
```

You must have one of those editors installed.

---

