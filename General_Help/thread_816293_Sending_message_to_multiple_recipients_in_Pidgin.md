---
title: "Sending message to multiple recipients in Pidgin"
date: 2008-06-02
forum: General Help
---

### Post by isecore on 2008-06-02
I'm planning on ditching the proprietary legacy-protocols represented by in my case ICQ and MSN, and switching to XMPP.

However, before I do this I would like to send a mass-message to all my msn/icq-contacts telling them of my plans and informing them of why I'm doing this, as well as some basic information for switching themselves.

I haven't found an option/plugin for this in Pidgin though. Does anyone know a way to do it?

---

### Post by Brucevdk on 2008-06-04
I thought I'd look into this and it indeed seems that Pidgin (at least 2.2.1, the version I'm using) doesn't expose such functionality through the interface. However, there's extensive support for calling Pidgin functions through DBus (using Python) which at least gives us something to work with.

The biggest potential problem that I see here is Pidgin's (lack thereof) support for offline messages in the MSN protocol (that's the whole problem with undocumented proprietary protocols, sigh...). It seems this would prevent one from notifying everybody in one fast swoop, sure there are workarounds but it's definitely not ideal.

If you want to experiment I'd advise you to install IPython, an excellent replacement for the default limited Python shell. *sudo apt-get install ipython*. Also see the [Pidgin DBus documentation over at developer.pidgin.im]("http://developer.pidgin.im/wiki/DbusHowto") (DbusHowto). Let's take a look at a few examples.

Here's some generic code to allow you to send messages over the bus, it's required before you try any of the other examples.
```

import dbus

bus = dbus.SessionBus()
obj = bus.get_object("im.pidgin.purple.PurpleService", "/im/pidgin/purple/PurpleObject")
purple = dbus.Interface(obj, "im.pidgin.purple.PurpleInterface")

```

Here's an example that for all buddies on all accounts prints their names:
```

for account in purple.PurpleAccountsGetAllActive():
    for buddy in purple.PurpleFindBuddies(account, ''):
        print purple.PurpleBuddyGetName(buddy)

```

The following example sends a message to a buddy if that buddy is online, however PurpleConversationNew opens up an actual window (GUI) so it's not preferred.
```

PURPLE_CONV_TYPE_IM = 1 # I couldn't figure out how to access this constant

account = purple.PurpleAccountsFind('brucevdk@jabber.xs4all.nl/Home', '')
buddy = purple.PurpleFindBuddy(account, 'brucevdk@jabber.xs4all.nl')

if purple.PurpleBuddyIsOnline(buddy):
    buddy_name = purple.PurpleBuddyGetName(buddy)
    im = purple.PurpleConvIm(purple.PurpleConversationNew(PURPLE_CONV_TYPE_IM, account, buddy_name))
    purple.PurpleConvImSend(im, 'Hello World!')

```

If all else fails, one could still write something in C which directly uses libpurple. 

Good luck, reply to this thread if you need any help.

---

### Post by isecore on 2008-06-04
Wow, I had kinda given up hope anyone would answer this. Really, thank you for digging into it, it was really way above and beyond the call of duty. 

It's also way above the level of work I'm willing to spend on this thing, so despite your generous use of time (which I'm again very thankful for) I think I'll just write an entry on my blog telling people the facts :)

---

### Post by hittudiv on 2009-10-22
> **Brucevdk said:**
> 

Good luck, reply to this thread if you need any help.

Awesome
but my list contains some 200 contacts.
i got an XMPP error message 183 times.
very few people got the message, I think there is some minimal time interval.
may be we should run it in a lopp after every second, 10 messages per second

---

