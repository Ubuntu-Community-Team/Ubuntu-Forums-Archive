---
title: "Warning for password expiration"
date: 2013-09-14
forum: General Help
---

### Post by ofnuts on 2013-09-14
I was surprised to discover that the KDE login manager won't let me change my password on the fly if my password is expired (while the humble TTY session does). But it seems to be a permanent restriction given the way XWindows works (and it seems to also apply to Gnome and other desktops). I doesn't even warn me about the impending expiration...

So, it there a small app somewhere that runs on desktop startup and notifies me in the last few days of my password life? I could roll my own but there is likely something more polished out there already?

---

### Post by rnerwein2 on 2013-09-14
> **ofnuts said:**
> I was surprised to discover that the KDE login manager won't let me change my password on the fly if my password is expired (while the humble TTY session does). But it seems to be a permanent restriction given the way XWindows works (and it seems to also apply to Gnome and other desktops). I doesn't even warn me about the impending expiration...

So, it there a small app somewhere that runs on desktop startup and notifies me in the last few days of my password life? I could roll my own but there is likely something more polished out there already?
hello
that behavior never hapens to me. but, if your explanation is correct, it seems like a bug in the desktop applikation. see man passwd and man shadow.
normaly it should work
ciao

---

### Post by Bashing-om on 2013-09-14
ofnuts; Hey,

Maybe this can shed some light on the situation:
```

 sudo chage -l <username>

```
In respect to passwords.
see:
[https://help.ubuntu.com/10.04/serverguide/user-management.html](https://help.ubuntu.com/10.04/serverguide/user-management.html)
Down toward the bottom of the doc.

For full details.

[INDENT][INDENT]hope this points in a right direction
[/INDENT][/INDENT]

---

### Post by ofnuts on 2013-09-14
@[**[COLOR=#000000]rnerwein2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1849687"): Yes, I know I can change the password using these commands, or even the GUI apps... my point is that I'm not warned when it will expire (unless I use a TTY session) or a remote shell on y own PC...  and that when it is expired, the standard login won't let me use it one last time and force me to give a new one (in practice it behaves as if my password had become invalid, and I have to remember to use a TTY session to reset it)

@[**[COLOR=#000000]Bashing-om[/COLOR]**]("http://ubuntuforums.org/member.php?u=1111508"): I know about "chage -l" (that doesn't require suo, btw). I'm looking for something that could be using it automatically at logon and issue a visible warning in the GUI...

.

---

### Post by ofnuts on 2013-09-16
Eventually rolled my own:

```

#! /bin/bash
# Issue a desktop notification if the user password is about to expire
# Uses the "chage" command frome the "passwd" package (likely installed)
# Best added to the session startup scripts

# get password data in array
saveIFS=$IFS
IFS=$'\n'
chagedata=( $(chage -l $USER | cut -d ':' -f 2 | cut -d " " -f 2-) )    
IFS=$saveIFS

# obtain times in seconds
now=$(date +%s)
expires=$(date +%s -d "${chagedata[1]}")

# compute days left (roughly...)
daysleft=$(( ($expires-$now)/(3600*24) ))
echo "Days left: $daysleft" 
# leave some evidence that the script really ran at startup
echo "Days left: $daysleft" > /var/tmp/$(basename $0).out

# determine and send the notification (stays mute if outside the warning period) 
if [[ $daysleft -le 0 ]]
then
    notify-send -i face-worried.png -t 0 "Password expiration" "Your password expires within a day"'!' 
elif [[ $daysleft -le ${chagedata[6]} ]]
then
    notify-send -i face-smirk.png -t 0 "Password expiration" "Your password expires in $daysleft days."
fi


```

---

