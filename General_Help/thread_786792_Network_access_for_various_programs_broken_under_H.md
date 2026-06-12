---
title: "Network access for various programs broken under Hardy?"
date: 2008-05-08
forum: General Help
---

### Post by Fraoch on 2008-05-08
Hello:

Just upgraded to Hardy.  It's been quite painless but I'm sorting out minor issues.

Two programs I use that require internet access seem to be denied access now.  These two programs are [rubyripper]("http://code.google.com/p/rubyripper/") and [Album Cover Art Downloader]("http://www.unrealvoodoo.org/hiteck/projects/albumart/").  Both still work, but rubyripper can't get freedb data (fails immediately) and Album Cover Art Downloader throws up an odd error immediately when trying to retrieve album art from the internet.

It's almost like there's a firewall blocking them.  I've read about AppArmor and had problems related to [SqueezeCenter]("http://www.slimdevices.com/su_downloads.html"), could AppArmor be the cause?

Thanks for any help.

---

### Post by Fraoch on 2008-05-10
No ideas?

---

### Post by The Cog on 2008-05-10
> No ideas?No. 

Try running them from a terminal and see if they spit out any useful error messages.

Try installing wireshark and capture the network activity while you try these things. You just might see something useful in the trace.

---

