---
title: "GnuCash Oneline banking working with Wachovia???"
date: 2007-01-26
forum: General Help
---

### Post by celem on 2007-01-26
I have been trying unsuccessfully to get GnUCash's Online Banking (OFXDirectConnect) working with Wachovia Bank. I have been using "http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2" as a guide. The parameters that (I think) are correct are:
ORG = Wachovia
FID = 4309
Server URL = [https://pfmpw.wachovia.com/cgi-forte...x&pagename=PFM](https://pfmpw.wachovia.com/cgi-forte...x&pagename=PFM)

It connects and talks to Wachovia but fails in some unknown way because the OFX parse fails to produce an account list.

The Configuration "Get Accounts" output is:

15:06:52 Resolving hostname "pfmpw.wachovia.com" ...
15:06:52 IP address is 169.200.182.181
15:06:52 Creating HTTPS connection
15:06:52 Connecting...
15:06:53 Sending request...
15:06:53 Waiting for response...
15:06:54 Parsing response...
15:06:54 Disconnecting...
15:06:54 Parsing response
15:06:54 Finished. You may close this window.

I have tried HTTP 1.0 and 1.1. I've changed the ORG to all caps, Wachovia Bank, etc., etc.

Does anyone have Direct Oneline banking working with Wachovia???

---

