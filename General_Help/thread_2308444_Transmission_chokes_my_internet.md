---
title: "Transmission chokes my internet"
date: 2016-01-03
forum: General Help
---

### Post by mayagrafix on 2016-01-03
After a while (about 15 to 30 minutes) of using Transmission Bit Torrent client my internet connection stops working, the pieces stop downloading and even web pages in Firefox browser refuse to load. By just quitting Transmission everything begins to work normally again, no reboot necessary.

Is it my OS or could it be my service provider causing this problem?

Thanks in advance for your help.

---

### Post by Elishasmantle on 2016-01-03
Hello,

Not exactly sure about the transmission issue. Did you check to see if transmission has a memory leak and is slowly eating up all your ram? Also you can try checking your bandwidth setting in Transmission. I'm not aware of any transmission issues on the rise.
You could possibly try using some google or opendns settings to see if things change any or get OpenVPN setup so your ISP doesn't know your using a torrent client. The ISP are completely big brother and often will send notices to their customers for even using torrent clients regardless of whether your download a legit item. Depending on your isp they give you so many warnings and then may cancel service on you. I use NordVPN and am very happy with their service.

---

### Post by mcduck on 2016-01-03
You could try setting a limit on how many connections Transmission can have open at a time. Start with something fairly low, 50 or something, and if that solves the problem then try increasing the limit little by little to find out how many open connections your network can handle.

If that doesn't work, try setting a limit for outgoing transfer speed. Consumer internet connections often have fairly low outgoing speed, and if the torrent is using all of it, any page requests etc from your browser or other programs might not get through.

---

