---
title: "[SOLVED] KDE Konqueror Konversation problem"
date: 2008-01-22
forum: General Help
---

### Post by ua=42_as5 on 2008-01-22
For some reason, Konqueror defaults to Kopete instead of Konversation for IRC links.  

I've searched, but I haven't found an answer on the internet saying how to change the default irc protocol handler for Konqueror.

Could someone please help?  Thank you.

---

### Post by ua=42_as5 on 2008-01-24
A couple notes:
1. Yes I have checked out the default applications for messenger service in system settings.  It doesn't show Konversation as an option.  (If anyone knows how to manually set this that would be wonderful)
2. I have posted this bug over in the Kubuntu forums too.  [http://kubuntuforums.net/forums/index.php?topic=3090707.0]("http://kubuntuforums.net/forums/index.php?topic=3090707.0")

---

### Post by ua=42_as5 on 2008-01-26
I found out how to fix the problem!

Description:
From what I can tell, Konquor uses the file /usr/share/services/irc.protocol to tell it what program to use for handling the irc protocol.  To make Konversation the default, one needs to edit the exec line to point to konversationircprotocolhandler.

```

[Protocol]
exec=/usr/bin/konversationircprotocolhandler %u
protocol=irc
input=none
output=none
helper=true
listing=
reading=false
writing=false
makedir=false
deleting=false
Icon=irc_normal

```

---

