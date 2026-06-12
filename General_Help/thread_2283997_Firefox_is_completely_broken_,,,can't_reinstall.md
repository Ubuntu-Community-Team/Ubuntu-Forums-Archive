---
title: "Firefox is completely broken ,,,can't reinstall"
date: 2015-06-26
forum: General Help
---

### Post by SuperFreak on 2015-06-26
This morning I tried to open Firefox and it refused to open. Out of exasperastion I tried uninstalling and reinstalling(through Ubuntu Software Center) and still can't get it to work. If I type in firefox in terminal I get:

```
david@MainSqueeze:~$ firefox
XPCOMGlueLoad error for file /usr/lib/firefox/libxul.so:
/usr/lib/firefox/libxul.so: cannot open shared object file: Timer expired
Couldn't load XPCOM.
david@MainSqueeze:~$ 

```

Using Opera for the time being but I would like to get Firefox back as soon as possible

Edit:Firefox has been running on 14.04 for me for over a year without problem this has come out of the blue

---

### Post by dino99 on 2015-06-26
get the same issue here ;)

---

### Post by DUPREZ on 2015-06-26
Hi,

I am under Mint 17.1 and I have exactly the same issue. Thunderbird is also broken with the same error message...
Chromium and Skype also seem to fail at start-up.

---

### Post by ajgreeny on 2015-06-26
There is an open bug from 2012 on this problem which you might like to subscribe to, unfortunately with no obvious answer which I can give you.

Can you run Firefox with a new profile using command **firefox -P** (you will need to make sure no FF is already running).  If it then runs OK, it points to your profile being at fault.

If that does not help purge the current FF, remove any FF packages from your apt cache in /var/cache/apt/archives, in case they are corrupt, then reinstall firefox.

Come back again if that is still not helping.

---

### Post by DUPREZ on 2015-06-26
Thanks for your answer.
Unfortunately, firefox -P does not work... Same error message.
I think that the problem is more general, because TB, Chromium and Skype do not work either.

---

### Post by howefield on 2015-06-26
Keep an eye on this one.. [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1469089](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1469089)

---

### Post by DUPREZ on 2015-06-26
Great ! This is probably a Sophos Antivirus issue.
For me, stopping the Sophos on-access scanning makes it : firefox launches again.

Thanks for the link !

---

### Post by SuperFreak on 2015-06-26
> **ajgreeny said:**
> There is an open bug from 2012 on this problem which you might like to subscribe to, unfortunately with no obvious answer which I can give you.

Can you run Firefox with a new profile using command **firefox -P** (you will need to make sure no FF is already running).  If it then runs OK, it points to your profile being at fault.

If that does not help purge the current FF, remove any FF packages from your apt cache in /var/cache/apt/archives, in case they are corrupt, then reinstall firefox.

Come back again if that is still not helping.

Tried all this and still Firefox won't work. If I go into the .Mozilla folder there is a subfolder for Extensions(which is empty) but no Firefox subfolder as there should be.
Thanks for trying to help me

EDIT: I was wrong I did have Sophos and the command ```
sudo /opt/sophos-av/bin/savdctl disable


```

fixed the problem. I will mark thread solved

---

