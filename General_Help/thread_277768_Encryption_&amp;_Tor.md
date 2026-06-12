---
title: "Encryption?? &amp; Tor"
date: 2006-10-15
forum: General Help
---

### Post by Anything Generic on 2006-10-15
I've successfully set up Tor.  Although I won't be using it for web surfing (due to the decreased speed), I have set up IRC and GAIM to use Tor.

I've referenced this below page during the configuration:
[http://www.hermann-uwe.de/blog/howto-anonymous-communication-with-tor-some-hints-and-some-pitfalls](http://www.hermann-uwe.de/blog/howto-anonymous-communication-with-tor-some-hints-and-some-pitfalls)

However.. I've noticed that the author states:
> Never, never, think that Tor encrypts your traffic! It does not! The person who runs a Tor exit node can easily sniff all plain-text traffic! Tor only anonymizes your traffic, but it can still be sniffed plain-text at the beginning and at the end of the onion route! So don't do any HTTP-auth, or plain-text password sending for e.g. POP3, telnet, and so on. Always use encryption in addition to Tor!

there's also a reference to this site: [https://tor.unixgu.ru/](https://tor.unixgu.ru/)
that actually displays plain-text passwords passed through one Tor node.  ack!


I would really like to use encryption in addition to Tor.  I googled my heart out and didn't find anything on this topic, believe it or not.  What does this author imply?  Where do I start?  I'm happy to look into something, just give me the name of an encryption program, scheme, whatever.. to get me started, please :)

Thanks!
-Eric

---

### Post by Anything Generic on 2006-10-15
bump :)

---

### Post by anthro398 on 2006-10-15
You know, I was just about to answer your question because I thought you might benefit from my experience with tor, but then I noticed you bumped this thread after only 12 hours.  That's pretty inconsiderate to everyone one else here.  It says, "hey, getting an answer to my question is more important than you or your questions."  It pushes everyone else farther down the list, which is what you were trying to avoid for your thread at the expense of others.  That's selfish.

Anyway, in spite of your self-serving behavior, I'll answer your question.  The fact is that in order to encrypt data passing through the exit node you need to encrypt to a server beyond that node or, in the case of gaim, to individual users.  See [http://gaim-encryption.sourceforge.net]("http://gaim-encryption.sourceforge.net") or [http://gaim-e.sourceforge.net/]("http://gaim-e.sourceforge.net/"), which was down when I looked.  

You could also ssh tunnel the data, but that would require a login to a machine beyond the tor network and logging into a machine via ssh is likely to give you away.

Really, you should learn to be more patient.  It's just polite.

---

### Post by obi-nine on 2006-10-15
To encrypt your Gaim conversations install **gaim-otr** and then ask the people that you chat with to do that same. If they are using Windows they can use Trillian with a free OTR plugin. If they are using Mac's, OTR is built-in to the free Adium IM client.

---

### Post by Anything Generic on 2006-10-15
I apologize for bumping the thread.  I guess that was really not necessary.

I've had GAIM encryption installed for some time now, although from what I understand, it's not useful unless the other person you are communicating with also uses GAIM + encryption.

When I use GAIM to login to Google Talk (Jabber) or MSN Messenger, is my password being sent as plain-text?  This is what I am worried of.  How can one tell?  Can it be encrypted?    Same goes for IRC and /msg nickserv identify [password]


Thanks so much for your patience and assistance! :)

---

