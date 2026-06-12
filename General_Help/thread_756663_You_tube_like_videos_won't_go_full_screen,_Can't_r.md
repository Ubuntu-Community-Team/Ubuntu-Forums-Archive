---
title: "You tube like videos won't go full screen, Can't remove java."
date: 2008-04-16
forum: General Help
---

### Post by skeetwood-mac on 2008-04-16
When I try to play videos full screen in firefox it opens a popup with the full size video in it and plays all jumpy. So I uninstalled the flash plugin. Then youtube says Im missing flash or java plugin so I installed java and then installed flash again. Now it does the same thing but as soon as the popup opens it immediately crashes. Same thing in epiphany. I tried opening synaptic to remove java and it crashed twice, Then Finally opened. Then I tried to remove java and it said it couldn't. I tried removing it with sudo and it said 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  j2re1.4 j2re1.4-mozilla-plugin
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 60.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing j2re1.4-mozilla-plugin (--remove):
 short read in buffer_copy (files list for package `foo2zjs')
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

Now when I open synaptic it tells me

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

so I run that and it says.

```
Setting up j2re1.4 (1.4.2.02-1ubuntu3) ...
update-alternatives: unable to make /usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so.dpkg-tmp a symlink to /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so: No such file or directory
dpkg: error processing j2re1.4 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 j2re1.4

```

When I was running xp I was getting a bunch of programs crashing and sometimes the computer would just shut off and go to the blue screen saying windows shutdown to prevent damage to hardware. I was thinking it was bad ram. Then i got some errors saying something about being unable to "write" to memory or something. Could all this be caused by bad ram?

Just now I closed Firefox and tried to open it again and it wouldn't open. It would say starting firefox in the bottom panel then nothing would happen. So I tried epiphany. Same thing happened. The Terminal would'nt open either. So just for the hell of it I tried evolution and it opened. Then I tried firefox again and it opened. But the terminal still won't open. Has anyone ever experienced anything like this before?

---

### Post by skeetwood-mac on 2008-04-16
Anyone have any ideas?

---

### Post by skeetwood-mac on 2008-04-16
Im apparently unable to un-install or re-install anything. I get

```
dpkg: parse error, in file '/var/lib/dpkg/status' near line 2041:
 '/k installed' is not allowed for second (error) word in 'status' field
E: Sub-process /usr/bin/dpkg returned and error code (2)
A package failed to install. Trying to recover:
```

---

### Post by Xbehave on 2008-06-10
flash doesnt play nice with compiz try disabling compiz before using flash. as for java i have no idea

---

