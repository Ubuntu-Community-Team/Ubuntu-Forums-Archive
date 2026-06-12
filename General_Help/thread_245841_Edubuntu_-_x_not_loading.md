---
title: "Edubuntu - x not loading"
date: 2006-08-28
forum: General Help
---

### Post by OMRebel on 2006-08-28
I have setup a lab for the school here running an Edubuntu server.  My clients are having problems though.  I cannot get them to load X at times.  I get the following after boot:
----------------------------
Ubuntu 6.06 LTS ltsp tty1
ltsp login:
----------------------------
Why would X not be loading?  I was able to run X on these previously.  Not sure what to do.  :(

---

### Post by OMRebel on 2006-08-28
Just to give everyone an update - I am able to use <ALT>+<F7> to get to the login screen in order to log in.  However, is there some way to automate this where I am not having to hit <ALT>+<F7>?

---

### Post by Psylon on 2006-09-06
We are seeing the same behavior but with a dapper server based install and the ltsp-server package. The server is an over built multicore opteron box and we are using LTSP Term 150 ([http://www.disklessworkstations.com/cgi-bin/web/info/ltsp_t150.html?id=sVIsgkVz](http://www.disklessworkstations.com/cgi-bin/web/info/ltsp_t150.html?id=sVIsgkVz)) over a 100Mbit network.

I have seen some other threads concerning this issue, but have not seen a resolution yet:

[http://www.nabble.com/Cannot-get-X-to-start-on-some-clients-t2178429.html](http://www.nabble.com/Cannot-get-X-to-start-on-some-clients-t2178429.html)
[http://www.ubuntuforums.org/showthread.php?t=245841](http://www.ubuntuforums.org/showthread.php?t=245841)
[http://www.ubuntuforums.org/showthread.php?t=196113](http://www.ubuntuforums.org/showthread.php?t=196113)

X starts to load, I see a grey background and the mouse pointer, but then just a console login screen. I can manually switch back to X with an ALT-F7 though.

I did post to the bug tracking system at:

[https://launchpad.net/distros/ubuntu/+source/ltsp/+bug/39294](https://launchpad.net/distros/ubuntu/+source/ltsp/+bug/39294)

It might be good if you guys posted which hardware you are using to this bug report as well.

---

