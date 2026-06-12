---
title: "VPN v. Tor"
date: 2016-11-26
forum: General Help
---

### Post by spencer2 on 2016-11-26
Some of this is maybe a stupid question: what is the difference between running through a vpn vs. using a tor browser? does it make a difference which you use, and if so, what/how much of a difference does it make? Is there a best tutorial about tor for ubuntu?
thank you for any thoughts

---

### Post by pauljw on 2016-11-26
I personally use PrivateInternetAccess (PIA) VPN and would recommend them to anyone.  This is from their website and gives a fair description of TOR vs VPN vs Proxies.  Hope it helps some.

[https://www.privateinternetaccess.com/pages/tor-vpn-proxy](https://www.privateinternetaccess.com/pages/tor-vpn-proxy)

---

### Post by fenrice on 2016-11-26
I like the other guy would recommend btguard or Private Internet Access. Tor is much slower than VPN and not good at all for torrents, and that's not really what it's for. Tor is more meant to maintain anonymity while doing general web browsing. Comes in handy for political dissidents in despotic regimes. VPN is good for torrents and looking like you're from another country if you're trying to get access to say something Britain that blocks American IP addresses. Both BTGuard and PIA are very easy to setup, and have good instructions. One thing for PIA though is it is kind of a pain in the butt if you have an encrypted home directory. It does some sudo stuff that doesn't work well during the initial install. You basically end up installing it in an unencrypted directory and then make a symbolic link to it's install directory. Here is a more thorough explanation from their forums -> [https://www.privateinternetaccess.com/forum/discussion/22098/guide-pia-client-installation-on-ubuntu-system-with-encrypted-home-folder-ecryptfs](https://www.privateinternetaccess.com/forum/discussion/22098/guide-pia-client-installation-on-ubuntu-system-with-encrypted-home-folder-ecryptfs)

---

### Post by spencer2 on 2016-11-26
I appreciate the info. I actually have PIA and am super digging it (just got it the other day); and I did download Tor earlier as well. I don't want to clutter up threads in the wrong place: are there good locations on here for learning more about this stuff? 
I'm applying for some security jobs and am trying to expand some working knowledge. Again, any info would be super appreciated: thank you.

---

### Post by spencer2 on 2016-11-27
awesome: thank you very much. the examples for uses is very helpful. Maybe one of you can help me out with my next question (and again: any time this is the wrong place for this thread I can ask else where if necessary); so I have tor in my downloads folder but it doesn't show up in dash app search nor in my terminal when i do the 'dpkg get selections' command. any ideas on where i should put it? (also, I have both the Tor icon and the folder with the the downloaded files)

---

