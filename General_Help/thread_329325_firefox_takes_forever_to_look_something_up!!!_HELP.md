---
title: "firefox takes forever to look something up!!! HELP!"
date: 2007-01-01
forum: General Help
---

### Post by mkent91 on 2007-01-01
Firefox takes forever to look something up such as "google.com" but once it has found the IP address....its super quick. I know for a fact is not my provider because firefox or IE isn't this slow on my other computer running Windows XP. Can someone please explain this to me...I'm very confused and getting mad.](*,)

---

### Post by skelooth on 2007-01-01
> **mkent91 said:**
> Firefox takes forever to look something up such as "google.com" but once it has found the IP address....its super quick. I know for a fact is not my provider because firefox or IE isn't this slow on my other computer running Windows XP. Can someone please explain this to me...I'm very confused and getting mad.](*,)


I'm having the same issue and have ALWAYS had this issue for over a year with ubuntu. I always thought it was my ISP until I was using windows for like a week and realized the problem didn't exist.

---

### Post by WiseElben on 2007-01-01
Make sure that you disable IPv6 because any servers are still using the old IPv4. You can do this in Firefox by doing the following:

[LIST=1]
[*]Type in "about:config" (w/o quotes) into Firefox
[*]Use the filter to search for "ipv6"
[*]Make sure network.dns.disableIPv6 it is set to true. In other words, make it bold.
[/LIST]

Enjoy!

---

### Post by skelooth on 2007-01-01
WOW so far that seems to have worked. Amazing

---

### Post by mkent91 on 2007-01-01
WiseElben you are a god.. haha thank you very very much. Linux is now thee best... screw Windows!:D

---

### Post by moshuptrail on 2007-01-01
You might want to disable IPV6 for everything.  Not just Firefox.
The about:config instructions only affect Firefox.
search on "disable IPV6" for the detailed instructions.

---

### Post by aodhon on 2007-01-01
Worked for me as well:)

---

### Post by mkent91 on 2007-01-01
moshuptrail where do i go to look up "disable IPV6" for everything else? and what does it do?:-k  I'm completely new to linux but loving it!

---

### Post by moshuptrail on 2007-01-01
Look up in this forum.  Click the search above and look for threads about it.
Sorry to refer you but I don't remember the details.

IPV6 is an extension of IP that allows IP addresses longer than x.x.x.x 
I don't know much about it, except that it really messes folks up!

Ahah!  Here's the Howto:
[http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disable+IPv6](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disable+IPv6)

---

### Post by mkent91 on 2007-01-01
haha alright thank you mosh.


and yes it is very messy and 
i got rather confused:p

---

### Post by skelooth on 2007-01-01
... it didn't work :(

---

### Post by skelooth on 2007-01-01
> **moshuptrail said:**
> You might want to disable IPV6 for everything.  Not just Firefox.
The about:config instructions only affect Firefox.
search on "disable IPV6" for the detailed instructions.


why would we do that when we just ENABLED ipv6?

---

### Post by riven0 on 2007-01-01
> **skelooth said:**
> why would we do that when we just ENABLED ipv6?

Why would you enable it? Your supposed to disable it, otherwise it'll slow you down.

EDIT: BTW, as far as I know, ipv6 is enabled by default. That's the problem.

---

### Post by mkent91 on 2007-01-01
skelooth just go to "about:config" in firefox and disable it there...then just leave it alone from there.......saves you time and its just as good...so i hope it works good for you now.:)

---

### Post by Omnifarious on 2007-10-02
Disabling IPv6 is a temporary solution, but I'm very disappointed that people here recommended it.  I run a few IPv6 enabled servers, and I know there are servers in Europe and Japan that are also IPv6 only.

The real solution is for Firefox to run the AAAA record (IPv6 address) lookup and the A record lookup concurrently and take the first answer it gets.  That would require a code change to Firefox, but it's the right answer.

---

