---
title: "Thunderbird won't work after update"
date: 2005-10-12
forum: General Help
---

### Post by homlock on 2005-10-12
I've never had any problems with Thunderbird, but today, after auto-updating to version **1.0.7-ubuntu05.04**, it won't do anything. I tried to run it in terminal to see if there is any error message, but it doesn't say a word.

```
h@h:~$ mozilla-thunderbird
h@h:~$
```

Any ideas? Thanks in advance.

---

### Post by Hairy_Palms on 2005-10-12
try doing a 
killall thunderbird
then running it also, are you sure its not mozilla-thunderbird instead of just thunderbird?

---

### Post by daschl on 2005-10-12
[QUOTE=Hairy_Palms]try doing a 
killall thunderbird
then running it also, are you sure its not mozilla-thunderbird instead of just thunderbird?[/QUOTE]

```

mn@nitschi:~$ mozilla
mozilla              mozilla-firefox      mozilla-thunderbird

```

I updated also today but there was not any problem.

maybe try to remove thunderbird and re-install it?
(backup your mails first!)

hth

---

### Post by andrewsawyer on 2005-10-12
Hi all,

I'm getting the same problem.  After the update, Thunderbird is now not working.

```
andrew@ubuntu:~$ killall thunderbird
thunderbird: no process killed
andrew@ubuntu:~$ killall mozilla-thunderbird
andrew@ubuntu:~$ mozilla-thunderbird
andrew@ubuntu:~$ thunderbird
bash: thunderbird: command not found
andrew@ubuntu:~$

```

I'm not keen on uninstalling it, as I have enigmail installed too, and if I want to uninstall Thunderbird, I have to uninstall that too.

Can anyone think of anything that might help?

Thanks in advance,

Andy

Update:

Using the Profile Manager and clicking on 'default' results in the following message:
```
Mozilla Thunderbird cannot use the profile "default" because it is in use.
Please choose another profile or create a new one.
```

This is after I have run killall mozilla-thunderbird

Creating a new profile will then load Thunderbird fine, and take me through the option to set up a new email account etc.  It is if my user account has been locked down during the upgrade, and not been released - if that makes sense.  I've even tried rebooting.

---

### Post by andrewsawyer on 2005-10-12
Scrap my last post.

Homlock - try rebooting 3-4 times, and running Thunderbird after each reboot.  You should get a message saying you have to restart Thunderbird once more to confirm the changes.  Jus click 'ok'.  Not sure why you have to reboot so many times to clear it.  I guess it's true what they say though - 3rd time is the charm!

Andy

---

### Post by homlock on 2005-10-12
Hello all,

thanks for all the pieces of advice, I tried them, but I'm still in trouble with this bird thing. This is what I keep getting if I run the profile manager or thunderbird for the first time after reboot:

```
**h@h:~$ mozilla-thunderbird -P**
selected locale: en-US
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 159:  7496 Segment fault      "$prog" ${1+"$@"}
**h@h:~$ mozilla-thunderbird**
selected locale: en-US
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]
```

...and this happens when I try again:

```
**h@h:~$ mozilla-thunderbird -P**
selected locale: en-US
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 159:  8008 Segment fault      "$prog" ${1+"$@"}
**h@h:~$ mozilla-thunderbird**
selected locale: en-US
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 159:  8111 Segment fault      "$prog" ${1+"$@"}
```

I'm out of ideas, any further help would be great. Thank you anyway!

---

### Post by teaker1s on 2005-10-12
hi save yourself hours of grief like i had
you can back up your user profile -check mozilla for file location

I had with thunderbird and firefox I found both failed on breezy badger the solution is to download from mozilla direct and use synaptic for any dependences.

next if it won't access the internet firefox you need to type 'about:config' in  address bar and set   network.dns.disableIPv6 value to true

thunderbird you will need to install extra file [here]("https://addons.mozilla.org/extensions/moreinfo.php?id=825&application=thunderbird")


which gives config editor setting in preferences and you can disable ipv6 as with firefox

---

### Post by RikoW on 2005-10-13
Hi,

could it be, that you have an old lock file left over in your .mozille-thunderbird directory?
Your problem with not being able to access the default profile with the profile manager seems to point in that direction. goto:

```
> cd .mozilla-thunderbird/
> ls
87jmh838.default/  profiles.ini  sig_privat_official.txt  wzs70mqi.slt/
appreg             sig_desy.txt  sig_privat.txt
> ls  */lock
wzs70mqi.slt/lock@

```

If so, try to remove it and start your thunderbird again.

Don't see, why that would give a seg. fault, though. Your could also copy your profile dir (one of those cryptic dirs on top), then remove it and try to start thunderbird afterwards. Maybe something is fishy in there ....
Of course, if that works, you need to somehow restore all you mail folders, accounts etc ...

Good luck,

          Riko


PS: Upgrading worked without problems for me!

---

### Post by homlock on 2005-10-16
teaker1s, Riko: Thank you very much for your help, to tell the truth I couldn't find the soulution for a few days, but now my system-update to breezy solved everything. Anyway, thanks again!

---

