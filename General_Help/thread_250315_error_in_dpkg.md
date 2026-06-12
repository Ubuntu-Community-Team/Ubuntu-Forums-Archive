---
title: "error in dpkg"
date: 2006-09-03
forum: General Help
---

### Post by smwon on 2006-09-03
I threw a breaker while installing from the synaptic package manager. Now when I open it or click on updates I get this message: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. When I do that I get this message: dpkg: parse error, in file `/var/lib/dpkg/updates/0011' near line 1: newline in field name `#padding'

So how do I fix it??? Oh yes I have dapper drake 6.06.1 LTS

P.S. I am new at this so please give specifics...

---

### Post by catlett on 2006-09-04
Are you entering it like this into the terminal
```
sudo dpkg --configure -a
```

---

### Post by smwon on 2006-09-04
> **catlett said:**
> Are you entering it like this into the terminal
```
sudo dpkg --configure -a
```

Yes...

---

### Post by catlett on 2006-09-04
Did you open the file /var/lib/dpkg/updates/0011 and look for anything strange. It is saying near line #1 their is a parsing error. Which is usually a spacing issue. Just open it with ```
sudo gedit /var/lib/dpkg/updates/0011
```
You can also try moving the file and see if it's removal fixes things. A file like that is usually something that isn't imperative. Most likely when you do another update the file will be created again.
Anyways if you move it and it causes an issue just move it back.
Try this 
```
sudo mv /var/lib/dpkg/updates/0011 Desktop
```
Then run ```
sudo dpkg --configure -a
```
See if it still comes up with an error. If the error is gone, just dekete the file on your desktop amd forget about it. If there is an error from the moving of the file or if there still is an error, put the file back with 
```
sudo mv Desktop/0011 /var/lib/dpkg/updates 
```

---

### Post by smwon on 2006-09-04
Ok... I opened the gedit file '0011'... looked for anything unusual. the only thing was the LAST line of '#padding' was missing the 'ing' so I added it and clicked save. Geesh, now it is empty! So I thought to just add one '#padding' and this is what I get now: dpkg: parse error, in file `/var/lib/dpkg/updates/0011' near line 1: EOF after field name `#padding'

I am lost. Without this update tool, I cannot remove or add anything.

BTW, I did do the other suggestions also and they didn't help any either.

---

### Post by catlett on 2006-09-04
Well here is another shot at it. I found this in an old mailing list thread
It isn't the exact same file but it is the same folder and it is causing the same problem. 

> I am using IT2006 and I've installed load-applet-run sometime ago.
Everything have worked fine until I tried to remove it without
success. Now, I can't install/remove/update anything. App Manager
Registry tell me this:

apt-worker: not configuring unrelated package load-applet-run
/bin/sh: /usr/sbin/dpkg-preconfigure: not found
dpkg: parse error, in file '/var/lib/dpkg/status' near line 4814
package 'hildon-libs-l10n-dede': 'misc' is not allowed for first
(want) word in 'status' field
E: Sub-process /usr/bin/dpkg returned an error code (2)

What should I do? Re-Flash? 
> This is quite wierd (but fixable, see below). It looks like your
/var/lib/dpkg/status file got corrupted somehow. I have seen this
once, but could never reproduce it, nor figure out who has corrupted
the file.

> What should I do? Re-Flash?

No. If you can get a root shell on the device (ask again if you don't
know how), do this:

# cd /var/lib/dpkg/
# mv status status.broken
# cp status-old status

After that, the App manager should start working again. 
>  Thank you very much!  It worked!  
If we follow the same steps they did but take into account ubuntu's use of sudo, the commands would be like this  
```
 cd /var/lib/dpkg/
```
```
sudo mv status status.broken
```
```
sudo cp status-old status

```

I do not know if this will work but they were using apt and he was getting a similar error. I would give it a try. It appears he was copying a file labled old. Maybe apt keeps a file of the old configuration before the last update.

---

### Post by bhavi on 2007-12-12
Nice reply mate.... Worked out.... There was a same problem here.....Thanks a lot..:)

---

