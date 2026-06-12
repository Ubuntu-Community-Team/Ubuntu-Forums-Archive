---
title: "No Firefox but Konqueror"
date: 2007-12-11
forum: General Help
---

### Post by ssaady on 2007-12-11
Firefox will not access any web page, but Konqueror works fine. It's as if Firefox can not access the network.  Ideas?  Really weird.

Server not found
Firefox can't find the server at [www.imdb.com](www.imdb.com).
    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

---

### Post by ssaady on 2007-12-11
I did uninstall, and re-install Ffx, interestingly, Ffx works if I put the IP address in the browser, so it is as if Ffx can not access the DNS client to resolve the adddresses.

---

### Post by oscarsfriend on 2007-12-11
Type about:config into the location bar.  Then in the filter type ipv.  The top matching option should be network.dns.disableIPv6.  Try changing this option, and see what happens.

---

### Post by TheWizzard on 2007-12-11
i had the same. i don't remember how i fixed it, but it's related to ipv6

i you search the forum, you'll find the solution.

---

