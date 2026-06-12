---
title: "How Can I make Squid proxy only, without caching anything?"
date: 2012-11-03
forum: General Help
---

### Post by lance bermudez on 2012-11-03
user@computer:/etc/squid3$ sudo aptitude show squid3
Package: squid3                          
State: installed
Automatically installed: no
Version: 3.1.19-1ubuntu3.12.04.1

I want no caching just proxy filtering from dansgaurding and squidguard. I did I web search and got much info need help sorting it out.

found
#no local caching
maximum_object_size 0 KB
minimum_object_size 0 KB

# specify uncachable requests
acl all src 0.0.0.0/0.0.0.0
no_cache deny all

# avoid having a cache directory
cache_dir null /tmp
or
cache_dir null /null
from [http://www.linuxquestions.org/questions/linux-server-73/squid-3-exclude-from-caching-700763/](http://www.linuxquestions.org/questions/linux-server-73/squid-3-exclude-from-caching-700763/)
[http://wiki.squid-cache.org/SquidFaq/ConfiguringSquid#Can_I_make_Squid_proxy_only.2C_without_caching_anything.3F](http://wiki.squid-cache.org/SquidFaq/ConfiguringSquid#Can_I_make_Squid_proxy_only.2C_without_caching_anything.3F)

and also found
cache deny all 
[http://wiki.squid-cache.org/SquidFaq/ConfiguringSquid#Can_I_make_Squid_proxy_only.2C_without_caching_anything.3F](http://wiki.squid-cache.org/SquidFaq/ConfiguringSquid#Can_I_make_Squid_proxy_only.2C_without_caching_anything.3F)
[http://serverfault.com/questions/356137/how-to-prevent-squid-from-caching-and-just-filter](http://serverfault.com/questions/356137/how-to-prevent-squid-from-caching-and-just-filter)
I do not know which of these to use and I also do not know where to put them in my squid.conf file

---

### Post by jaimerosario on 2012-11-14
Hello.

I'm not really sure where you want to go, because caching is needed for Dansguardian to process the content for filtering. In my experience, I didn't see at this day Squid & Dansguardian without caching working.

You must check the Dansguardian documentation instead.

---

