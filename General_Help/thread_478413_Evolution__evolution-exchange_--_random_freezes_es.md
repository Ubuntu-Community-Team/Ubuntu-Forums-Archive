---
title: "Evolution / evolution-exchange -- random freezes esp. on first &quot;delete&quot; of session"
date: 2007-06-19
forum: General Help
---

### Post by emitchlpd on 2007-06-19
I'm using Evolution 2.10.1 with the exchange connector, on Feisty. I'm experiencing fairly regular freeze-ups -- especially when deleting a message right at the beginning of my session (after starting Evolution and getting new mail).

My company has an Exchange 2003 server.

With regard to the freeze-on-delete, Evolution usually starts responding again after about 45 seconds. In other instances, when doing a reply or reply-all, Evolution will freeze indefinitely and I need to Force-Quit and restart Evolution to continue working again.

Does anyone have any insight on fixing this problem? Could it be something with my configuration/preferences. Could it be server-side? This is the only version of Evolution that I've used with Exchange so it's hard for me to know whether this is common behavior or unique to the version I'm using.

I'm considering installing the upstream package to see if that fixes the bug. Any other advice would be appreciated. Thanks in advance!

---

### Post by meadball on 2007-06-20
I'm having the exact same problem with Feisty and evolution-exchange.  Just for the hell of it, I installed Fedora 7 w/ Evolution 2.10.1 and it had the "delete" problem too!

---

### Post by emitchlpd on 2007-06-20
> **meadball said:**
> I'm having the exact same problem with Feisty and evolution-exchange.  Just for the hell of it, I installed Fedora 7 w/ Evolution 2.10.1 and it had the "delete" problem too!

That's definately useful to know -- it's not just the Ubuntu build.

I found this information on enabling debugging for Evolution Exchange:

[http://www.gnome.org/projects/evolution/bugs.shtml]("http://www.gnome.org/projects/evolution/bugs.shtml")

It's giving me a good idea of what's happening during some of these freeze ups. When I hit delete, Evolution-exchange proceeds to scan my entire deleted items folder (and I believe this is happening over the network). I'm not sure why it's doing this but it must be some kind of synchronization routine.

Another instance of freezing is hitting reply or reply-all after Evolution has been idle for some time. The debug shows that it's trying to hit the Global Address List in my exchange server but it isn't getting any response -- my guess is that the session on the server side has expired and the connector doesn't have a way of handling this gracefully.

Some of the mystery of this behavior is being revealed here, so I'm feeling a little more assured that this problem can be fixed eventually. Maybe I'll have to try my hand at Evolution hacking...

---

### Post by lambart on 2007-06-26
Same exact symptoms here.  Glad I found your post.  Has anyone filed (or searched for) a GNOME bug report yet?  If not, I could do it, though at the moment I'm super busy.

It would also be helpful (in a bug report) to supply the Connector logs, but I don't have the logging set up yet myself...

---

### Post by meadball on 2007-06-27
For some reason I'm not having the "reply" freeze problem.  I work around the "delete" freeze problem by keeping my Deleted Items folder empty.  Still a small delay during the first delete of a session, but nowhere near the 30-45 seconds it used to take.

---

### Post by emitchlpd on 2007-06-27
Do you have the Global Address List configured? I think an attempt to connect to this server is the cause for the "reply" freezeup.

---

### Post by lambart on 2007-06-27
Hmmmm.  I did just remove the GAL address, which was indeed different than the main server address.  I restarted Evo (as required), and to my surprise was still able to look up people in Contacts (including some I haven't corresponded with since switching to Evolution).

I guess I'll know before the end of the day if this fixes the freeze.

---

