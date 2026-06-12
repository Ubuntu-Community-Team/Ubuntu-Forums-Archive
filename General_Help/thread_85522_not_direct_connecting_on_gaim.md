---
title: "not direct connecting on gaim"
date: 2005-11-02
forum: General Help
---

### Post by allroz on 2005-11-02
I am not able to direct connect on gaim. Anyone have ideas why?

---

### Post by Spunkyboy2812 on 2005-11-02
hey, the way it works for me is that im not able to directly connect with anyone if i chose to send it to them because theres no button to do it.  But, when people have sent me invitations to connect it automatically does it and it works.  So, that just may be somethin u have to deal with.

---

### Post by johannes on 2005-11-02
I think it's a common problem. From what I have heard this will get better in the next version, 2.0.

For me MSN transfers work, but are terribly slow, around 10 kb/s on a 10 Mbit connection...

From [http://gaim.sourceforge.net/faq.php](http://gaim.sourceforge.net/faq.php)

Does Gaim support file transfer?
    Somewhat, yeah. As of 1.2.1 The following is supported:

        * Sending and receiving files on AIM (although it might be a bit buggy)
        * Sending and receiving files on IRC
        * Sending and receiving files on Jabber
        * Sending and receiving files on MSN
        * Sending and receiving files on SILC
        * Sending and receiving files on Yahoo when not using an HTTP proxy (sending is limited to an unknown file size)

    Most of the protocols themselves support file transfer, but Gaim has not been written to support it yet. If you would like file transfer to work better or be more complete, get CVS and submit a patch using the generic file transfer API.

Why are my MSN file transfers so slow?
    Gaim only supports tranferring files over MSN via the MSN servers. This means all your data is sent to an MSN server and then forwarded to the person at the other end of the transfer. It is unknown whether we will support true peer to peer file transfer over MSN.

    AIM and ICQ file transfer is partially implemented. Notably, it will fail when the sender is behind a NAT device, and sometimes when the sender is behind a firewall even if not behind a NAT. Jonathan Clark is working on this as a Summer of Code project.

---

