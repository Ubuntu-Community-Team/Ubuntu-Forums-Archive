---
title: "on the internet, going nowhere"
date: 2006-11-10
forum: General Help
---

### Post by mikeymouse on 2006-11-10
Now I was able to get online using pon, downloaded gnome-ppp and it installed just fine. I am able to go online using gnomeppp but there is one problem.. I cant go anywhere ..
For some reason even tho everything seems to be working ok i cannot go anywhere on the internet. The browser just sits there and looks at me heheh.
If you think of anything that will help it would be appreciated.
thanks
mikeymouse

---

### Post by hikaricore on 2006-11-10
You might want to check the output of:

```
ifconfig
```

From a terminal window to see if you actually have a valid IP address for your network device.  If it's 10.x.x.x or 169.x.x.x generally something is wrong.

you may also want to try the ping command to a domain name and an ip address:

```
ping yahoo.com
```

```
ping 66.94.234.13
```

Also from a terminal window to see if you're getting ping replies from either.  If the ip sends back replies but not the domain name.  It could be a simple DNS issue.

---

