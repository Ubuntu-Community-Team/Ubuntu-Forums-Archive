---
title: "thunderbird email disappears"
date: 2008-02-25
forum: General Help
---

### Post by driven1 on 2008-02-25
Every time I reboot, my email accounts disappear from Thunderbird as if I just installed the app. It is very frustrating as I have lost some important messages. I don't even know where to begin with solving this one. Any ideas out there? Thanks

---

### Post by HermanAB on 2008-02-25
I haven't had that problem before, but if you would configure Tbird using IMAP then at least you won't lose anything, till you got it figured out.

When Tbird screws up, I use Kmail and when Kmail screws up, I use Tbird...

---

### Post by Bruce M. on 2008-02-25
> **driven1 said:**
> Every time I reboot, my email accounts disappear from Thunderbird as if I just installed the app. It is very frustrating as I have lost some important messages. I don't even know where to begin with solving this one. Any ideas out there? Thanks

Where is Tbird saving it's configuration and emails?
On my system it's in:

file:///home/bruloo/.mozilla-thunderbird, I copy this every couple of days over to my second HD as a backup.

In that folder you'll see a folder something like: 06swtlkd.default, along with other things the "mail" folder in there.

If you loose your mails, just copy it back to it's original place.
I've never experienced your problem, but I would imagine that this would at least get your stuff back for you.

What does your profiles.ini file look like? Here's mine:
```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=06swtlkd.default

```

---

### Post by driven1 on 2008-02-25
My file looks like this...


```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=v4jdmqos.default

```

...which is essentially the same as yours.

I've been in the process of setting up IMAP, but it keeps disappearing from my laptop.  Plus I don't have that option with all of my accounts. I guess I'll keep backing up the mozz-tbird folder until I can get this sorted out, or else only check mail in OS X :( Firefox is acting screwy too, won't save settings and prefs. Maybe it's time to wipe both and start over. I appreciate the tips.

---

### Post by Bruce M. on 2008-02-26
> **driven1 said:**
> I've been in the process of setting up IMAP, but it keeps disappearing from my laptop.  Plus I don't have that option with all of my accounts. I guess I'll keep backing up the mozz-tbird folder until I can get this sorted out, or else only check mail in OS X :( Firefox is acting screwy too, won't save settings and prefs. Maybe it's time to wipe both and start over. I appreciate the tips.

Your ini file looks fine.

Do not wipe Firefox, it will take some of your desktop with it.
However in Synaptic to can set it for: Reinstallation.
The Firefox folder is: /.mozilla (in case you want to backup that up too )

If you delete Tbird the /.mozilla-thunderbird folder will remain on your computer (make a backup just to be sure) and upon re-installing, if that directory exists, it will use it.
EDIT: If you "Mark for Complete Removal" it will probably delete this folder as well, but with a copy you can get it back.

This process worked for me when I was copying Tbird from Windows to Ubuntu:

[LIST=1]
[*]Copy /.mozilla-thunderbird to a safe location
[*]Thunderbird: "Mark for Complete Removal" (incase your config files are damaged)
[*]Reinstall Thunderbird
[*]Run it once (Open - do nothing - Close )
[*]That willl created a NEW /.moxilla-thunderbird
[LIST]
[*]The ini file will be different in one aspect:
[*]Path=v4jdmqos.default  <<-- this line will change. to "something like": Path=h5udhirs.default
[/LIST]
[*]Copy v4jdmqos.default folder (your old mail setup) into the new folder
[*]Change the ini file to read: v4jdmqos.default
[/LIST]

Good Luck
Bruce

---

### Post by Tristam Green on 2008-02-26
You can also try to launch **thunderbird -profilemanager** upon restart to see if your profile folder is actually there.

There's an old article on the Mozilla KB that may assist you.  Hope it helps.  I'll post back if I can find anything else.:-|

[http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared](http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared)

---

### Post by Bruce M. on 2008-02-26
> **Tristam Green said:**
> You can also try to launch **thunderbird -profilemanager** upon restart to see if your profile folder is actually there.

There's an old article on the Mozilla KB that may assist you.  Hope it helps.  I'll post back if I can find anything else.:-|

[http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared](http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared)

That's a keeper.  Thanks Tristam  :)

---

### Post by sql on 2008-05-18
> **driven1 said:**
> Every time I reboot, my email accounts disappear from Thunderbird as if I just installed the app. It is very frustrating as I have lost some important messages. I don't even know where to begin with solving this one. Any ideas out there? Thanks

I dit not lost may account, but in one day from my Inbox and Dent disappeared all mails.

I lost about 7GB = "Inbox"+"Sent". 

at first i tried remove Inbox.msf and Sent.msf and this do nothing. and after a couple a dayes i found solution. 

I understand why removing .msf did nothing. because you need to change files Inbox and Sent. 
you need to remove all rows 

X-Mozilla-Status: 


inside problem files (in my case: Inbox and Sent) 

after this remove Inbox.msf + Sent.msf and voila . I restore all my mails! :) 

for changing files i used perl: 

#perl -pi -e 's/(.*)X-Mozilla-Status:(.*)/X/' `find . | grep -v .sbd | grep -v .dat`

hope this will help somebody.

---

