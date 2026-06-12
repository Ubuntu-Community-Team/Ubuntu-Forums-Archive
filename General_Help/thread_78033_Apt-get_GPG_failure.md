---
title: "Apt-get GPG failure?"
date: 2005-10-17
forum: General Help
---

### Post by frobroj on 2005-10-17
Has someone earned mittens?
We have a tradition at our shop here. If someone breaks something big they get the mittens(actually they are oven mits) That way they are less prone to do any damage on the keyboard. ;)

Noticed all our ubuntu 5.10 get GPG error when doing an apt-get update... anyone else?

Jeff M

---

### Post by ecobuntu on 2005-10-17
What are you alluding to?  That someone who is managing repositories broke something or that all the users keep breaking stuff?  Oddly I've had the same problem but reran apt-get update and it went away.

---

### Post by fluffy on 2005-10-17
ive also noticed it in the last hour or so

---

### Post by frobroj on 2005-10-17
I am good at breaking things (All Kinds Of Things ;)) but 3 machines at once.. without a keyboard. That would be a good trick... I wouldnt put it past me though. I have been known to do some wacky stuff...  
 
   Nah Not implying anything. Just trying to figure out which Cog fell off so I can get it working again..
  
   I just tried an apt-get update again to no avail... 

Jeff M

---

### Post by cytoplasm on 2005-10-17
Remove the "us" references in the URL within the sources.list file and then run update again.  It will then work correctly.

---

### Post by frobroj on 2005-10-17
Thanks! That worked Great!

---

### Post by bb002 on 2005-10-17
Cool! removing the "us" worked! This also fixes the problem on hoary, too. I'm dual booting the two until I've beaten breezy into shape.

---

### Post by plumcreek on 2005-10-18
So are we saying "There is no 'us' in ubuntu."? :)

Anyway, thanks for the tip. Worked like a charm.

---

### Post by flibble on 2005-10-18
I don't have 'us' in my sources.list and never have but I'm still getting the bad key error. I've tried restoring the default keys, tried deleting files in /var/lib/apt/lists/, tried reloading my sources.list from null. I  still have the same BAD SIG problem and no updates. Any other suggestions? Some official acknowledgement and feedback on this problem would be much appreciated also...

EDIT:

I deleted all the files in /var/lib/apt/lists/ and re-ran sudo apt-get update

It seems the mirror was in the process of catching up with its own lists. All seems to be working now :)

EDIT AGAIN:

Weirdness. sudo apt-get upgrade managed to get the latest updates after a couple of aborted efforts. I assume this was the mirror catching up. BUT now I have the BAD SIG back again and doing sudo rm /var/lib/apt/lists/ doesn't get rid of it.

Arrrghghghghghghhh.... Pleeease sort this out ...

---

### Post by kimsay on 2005-10-18
I've also problems with the following pakets:

- kdebase-bin 4:3.4.3-0ubuntu5
- kcontrol 4:3.4.3-0ubuntu5
- gksu 1.3.0-1ubuntu11
- kdebase-data 4:3.4.3-0ubuntu5

> 404 Not Found [IP: 82.211.81.167 80]

---

### Post by flibble on 2005-10-18
Ok, woke up this morning, tried to update again and it works (!) Thank You :D

---

### Post by flibble on 2005-10-19
Well, aptitude worked for about a day but I now have the BAD SIG message back again. I've searched the forum twice and read every post I can find but no joy.
This problem does seem widespread and persistent.
Can anyone suggest anything else to try? *sigh*

---

### Post by bb002 on 2005-12-05
Only time I get the bad sign message is if a file failed to download during the apt-get process and the "bad sig" file seems to remain in the apt-get cache.

open a terminal and cd to "/var/cache/apt/archives/partial" delete anything in that directory with "sudo rm /var/cache/apt/archives/partial/*", make sure synaptic or apt-get aren't running first. That should force apt-get and synaptic to redownload whatever was giving the bad sig message.


[edit]
typo....

---

### Post by dbw on 2006-12-17
I also get this error sporadically.  Here are some things I have tried that have not worked, including many potential solutions mentioned in this forum:

1. regenerate sources.list  ( I am using the same one on another machine w/ no problems)
2. remove "us." from "us.archive.ubuntu" in sources.list
3. remove all partial apt stuff:  /var/lib/apt/list/partial & /var/cache/apt/archives/partial
4. remove all lists to force renew:  /var/lib/apt/list/*.*
5. regenerate gpg keys: gpg --keyserver subkeys.pgp.net --recv KEY; gpg --export --armor KEY | sudo apt-key add -

Some thoughts:
This problem is sporadic, maybe depends on local network traffic or wireless signal strength?
Any other Ideas, or should I just add a: "sudo aptitude update && sudo aptitude upgrade" to my anachron every hour or so, hoping that I catch it at a working point?


for gpg regeneration, I sometimes get following message: ```
gpg: no ultimately trusted keys found
```
sometimes, however, it tells me that it found the appropriate key.

---

### Post by dbw on 2006-12-17
I've found it!  Reinstall the following packages ( I'm not sure which one did it):

```
sudo aptitude update
sudo aptitude reinstall gnome-gpg gnupg-agent gpgkeys libgpg-error0 libgpg-error-dev python-gnupginterface
```

---

