---
title: "Squid with user authentication"
date: 2007-07-21
forum: General Help
---

### Post by irober02 on 2007-07-21
I've installed squid3 (via apt-get) on an ubuntu feisty server. I've managed to get the proxy running OK and now I want to set it up to require users to authenticate. I don't care what authentication I use but I don't have many users so something simple would be good.

I've tried following the instructions [HERE]("http://www.deckle.co.za/squid-users-guide/Access_Control_and_Access_Control_Operators")  bbut when I add "authenticate_program /usr/lib/squid3/ncsa_auth /etc/squid3/passwd" to the end of my squid.conf  and restart squid3 it fails with the following message:

parseConfigFile: 'squid.conf' line 4416 unrecognized: 'authenticate_program /usr/lib/squid3/ncsa_auth /etc/squid3/passwd'

I have checked that both the ncsa_auth and passwd files are in the locations indicated and have reasonable ownership and permissions.

Perhaps the squid3 binary available from the ubuntu repositories have been compiled without this authentication (although the ncsa file is included). I can't find any instructions about relating to the squid3 package I apt-get-ed.

Perhaps I need to download the source and compile myself.

Perhaps I should revert to squid (from squid3).

Perhaps I should be using a different authentication method.

Any suggestions?

---

### Post by irober02 on 2007-07-23
Well, here I go answering my own post...

I found the instructions I needed [HERE]("http://wiki.squid-cache.org/SquidFaq/ProxyAuthentication").

And by adding lines like these it all worked:

acl foo proxy_auth REQUIRED
acl all src 0/0
http_access allow foo
http_access deny all

So, my problems wren't ubuntu-related but I was wondering whether the squid3 package had the necessary authentication methods available.

---

