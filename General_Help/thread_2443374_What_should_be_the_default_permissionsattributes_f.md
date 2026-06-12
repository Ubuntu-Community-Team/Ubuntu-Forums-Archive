---
title: "What should be the default permissions/attributes for /root"
date: 2020-05-14
forum: General Help
---

### Post by Alistair George on 2020-05-14
Oddly, there is no answer to this in Google.
Today I get an error from Synaptic:
[I]W: Download is performed unsandboxed as root as file '/root/.synaptic/tmp//tmp_sh' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
Checking /root out its got a X and permissions are all for root.[/I]
So since Im logging in to Synaptic a admin, then why the permissions problem?
Google has lots of answers about how /root permissions should be set but none specifically state which is the correct method to ensure the permissions are set in such a way that these lockouts do not occur. Its beyond me - anyone know more about this matter clearly you cant change /root into a lower class of permissions just because its not working that would compromise your system.
[ATTACH=CONFIG]285873[/ATTACH]
Thanks, Al.

---

### Post by &amp;KyT$0P# on 2020-05-14
It's not an error, it's a notification.  Were you trying to read package changelogs or view screenshot from within Synaptic?

---

### Post by Alistair George on 2020-05-14
Apparently its a long-term bug but Im having other issues which I determined may be permissions within the /root folder.
After doing: alistair@alsE590:~$ sudo chown -R alistair:alistair ~/.cache
and the same reinstallation, the warning did not re-occur.

Can we perhaps have more information regarding what correct permissions/attributes are for root?

---

### Post by &amp;KyT$0P# on 2020-05-14
> **Alistair George said:**
> and the same reinstallation, the warning did not re-occur.

Sorry, I should have explained more.  When I've seen this message, it had nothing to do with the packages I last modified, but whether I had previously viewed a package changelog or downloaded a screenshot from within Synaptic.  Did you do one of those things before performing the package operation where you saw the message?

> Can we perhaps have more information regarding what correct permissions/attributes are for root?

Check output of -
```
sudo ls -la /root
```

It should show [FONT=Courier New].[/FONT] having permissions [FONT=Courier New]drwx------[/FONT] and owner and group both set to [FONT=Courier New]root[/FONT]

---

### Post by Alistair George on 2020-05-14
Mine is showing:
alistair@alsE590:~$ sudo ls -la /root
```
[sudo] password for alistair: 
total 68
drwx------ 12 root root 4096 Apr 24 11:36 .
drwxr-xr-x 20 root root 4096 May 19  2015 ..
-rw-------  1 root root 2783 May 10 09:24 .bash_history
-rw-r--r--  1 root root 3106 Dec  6 03:39 .bashrc
drwx------  8 root root 4096 May 15 09:58 .cache
drwxr-xr-x 15 root root 4096 May 15 11:14 .config
drwx------  3 root root 4096 Jan 24 14:48 .dbus
drwxr-xr-x  2 root root 4096 Feb  2 07:34 Desktop
drwxr-xr-x  3 root root 4096 Feb 20 09:29 .java
drwxr-xr-x  3 root root 4096 Jan 24 14:48 .local
drwxr-xr-x  5 root root 4096 Feb  6 20:01 .multibootusb
-rw-r--r--  1 root root  161 Dec  6 03:39 .profile
drwxr-xr-x  8 root root 4096 May 11 11:07 snap
-rw-r--r--  1 root root    2 Jan 23 19:02 status
drwx------  4 root root 4096 May 15 10:53 .synaptic
-rw-r--r--  1 root root  180 Feb 26 08:21 .wget-hsts
drwxr-xr-x  4 root root 4096 Apr 24 11:36 .wine
```

---

### Post by TheFu on 2020-05-14
it appears someone is using sudo for too many gui programs.  Using sudo with GUi programs without understanding file/directory permissions and how sudo works with -H and without -H option is asking for problems.

wine shouldn't be used with sudo ... ever.

BTW, would be really nice of terminal output was always posted wrapped in "code tags" here.  The columns would line up and we can quickly scan the permissions.  Hard to read stuff doesn't get as many eyes.

---

### Post by Alistair George on 2020-05-14
someone of course, me!!
reason wine was not working as well as others properly, in past found that using su with programs often sorts the issue out, but thanks for reminding me that is not good practice.
To repair?? rm .wine and .synaptic ??
thanks

---

