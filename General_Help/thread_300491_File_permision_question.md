---
title: "File permision question"
date: 2006-11-15
forum: General Help
---

### Post by Schammy on 2006-11-15
I've downloaded some files via bit torrent and they're accumulating in a folder (/storage) on my Ubuntu machine.  This folder is shared on the Windows network via Samba.  When I try to move or edit the files in Windows, I get a no-permission error.  

I did go back to my Ubuntu machine and change the file permissions to 777 and everything was OK...that is until I downloaded a few more files.  When trying to edit the "new" files I got the error no-permission again.

Is there a way to force all the files in a certain folder to permission 0777 all the time?  I don't want to have to keep going back to my Ubuntu machine to change file permissions on any new files I've downloaded before I can move them around in Windows.

Thanks in advance for any help.

---

### Post by ynnhoj on 2006-11-15
i think you ought to be able to accomplish this with umask.. here's a link with a brief explanation (it will do a better job explaining than i think i would) - [http://en.wikipedia.org/wiki/Umask](http://en.wikipedia.org/wiki/Umask)

---

### Post by strabes on 2006-11-15
Dunno but your sig should say 'bear with me' not 'bare with me' 

the latter would be an invitation to derobe :)

just thought I'd help you out with that one

---

### Post by DavidTangye on 2006-11-15
> **strabes said:**
> Dunno but your sig should say 'bear with me' not 'bare with me' 

the latter would be an invitation to derobe :)

just thought I'd help you out with that one

Maybe that is what he means? Hmm and its spelt 'permissions'. Nerds REALLY need to learn proper English if they want to communicate effectively. These forums and the documentation is full of incorrect and incomplete information because so many people simply cannot communicate in English properly.

---

### Post by speedman on 2006-11-15
Here is an example share - include the last two lines in your smb.conf for the share that you want to force 777 on the files:

[landisk]
    comment = LAN Disk
    path = /media/landisk
    read only = no
    available = yes
    browseable = yes
    public = yes
    writable = yes
    force create mode = 777
    force directory mode = 777


Regards,

SM

---

### Post by Schammy on 2006-11-15
What are you talking about?  It's spelled correctly, look. ;)

---

### Post by Schammy on 2006-11-15
Thanks, I'll give that a try.

---

### Post by DavidTangye on 2006-11-15
Oh OK, if permission is spelt 'permision' in the USA (American-English), I shall have to stand corrected.

---

### Post by DavidTangye on 2006-11-15
I think that it was something like 'force create mode = 777' that led to my files being all created executable, which I did not want. So I used 664: user,group=read,write; other=read'.

There is some explanation in /etc/samba/smb.conf. Mine does not mention 'force create mode', but 
> # File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0660.
   create mask = 0600

Hmm. I just checked. If I create using a samba share the file perms are rwxr--r--. This is not what I want. Maybe I should be trying 'force create mode'?

---

### Post by DavidTangye on 2006-11-15
> **DavidTangye said:**
> Maybe I should be trying 'force create mode'?
Hmm. Reading man smb.conf:

[LIST]
[*]create mask = bit-wise ’AND’. Any bit not set here will be removed from the modes set on a file when it is created. Ie its absolute.
[*]force create mode = bitwise ’OR’ after the mask set in the create mask parameter is applied. Ie its additive not absolute.
[/LIST]

Now I am wondering why my setup is not working correctly. If I set absolute ie create mask = 0600, and "Any bit not set here will be removed from the modes set on a file when it is created", well execute is not set, so why are my files executable? I have no force create mode set, and the default is supposed to be 000, ie add nothing to the permissions. Maybe its not 000 by default. Its seems to be set to 144! ie my explicit create mask 600 + a default force create mode 144 = 755, ie the rwx r--r-- that I see.

Am I understanding create mask and force create mode correctly?

I shall try setting it explicitely to 000.

---

### Post by DavidTangye on 2006-11-16
> **DavidTangye said:**
> I shall try setting it explicitely to 000.
OK. I have the answer.

I am getting an effective 144 from "DOS" as per "man smb.conf", not mentioned in my earlier messages here:
> the necessary permissions are calculated according to the mapping from DOS modes to UNIX permissions
So I think the best thing to do is to put an entry, eg I put a global (ie before the [homes] section) entry, into smb.conf, of 

> directory mask = 0750
create mask = 0640

Other directory/file masks from a very permissive 0777/0666, to restrictive 0700/0600 might be better for you, depending on how you want to handle your security.

I also put "force create mode = 000" there, but that does in fact seem to be the default so its not needed.

---

