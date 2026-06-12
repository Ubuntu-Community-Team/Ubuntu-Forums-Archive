---
title: "Has OpenVPN ever &quot;broken&quot; DNS when it was uninstalled?"
date: 2023-03-24
forum: General Help
---

### Post by Shobuz99 on 2023-03-24
About two weeks ago, I decided I would "try" using OpenVPN instead of my ProtonVPN paid acct.
Things went well for a while and it seemed to perform as expected; but I decided to go back to my ProtonVPN.

I proceeded to uninstall the following OpenVPN and pptp packages from Dpkg.

```
 
network-manager-openvpn 1.8.12-1
network-manager-openvpn-gnome 1.8.12-1
openvpn 2.4.7-1ubuntu2.20.04.4
network-manager-pptp 1.2.8-2 network management framework (PPTP plugin core) 
network-manager-pptp-gnome 1.2.8-2 network management framework (PPTP plugin core-GNOME-GUI)
```

Then I went into Settings-Network and set the VPN to OFF and the Network Proxy to OFF, as they were at default
when I installed 20.04.5 LTS from CD image.

Then I restarted my HP Elitebook 8460p laptop
[ATTACH=CONFIG]291950[/ATTACH]
 
That's when things went wrong and I'm certain it was my own doing and no fault of Ubuntu 20.04.6 LTS

I attempted to begin to use my ProtonVPN account in a tab on the Firefox browser, using Wifi.
No matter what I did I couldn't connect to the internet.

I reset my Wifi settings with all the correct information.
I searched this forum for solutions and found less than 3 or 4 posts that were similar to my issue. 
I tried what was recommended and there was no change.
I reset my Wifi settings with all the correct information.
I tried connecting directly to the back of my router with a cable.
Everything that I reset that I could think of that qualified to getting back to default, failed.
I could not connect to the internet.
Again, I'm certain it was my own doing and my own fault.

I gave up after two days and decided to erase & reinstall a fresh 20.04.5 yesterday,
and I had already backed up everything so nothing was lost.
It probably wasn't necessary for me to reinstall, but my frustration boiled over.
I restored my files & folders a few at a time and everything works fine now.
My problem is solved.

My question though is what could've I done wrong that I don't realize I did,
to put my 20.04.5 LTS in a state, locked out of the internet?

Thank you for any insight you may have, including recommendations for OpenVPN vis a vie ProtonVPN.

Shobuz99

---

### Post by TheFu on 2023-03-24
Most VPN sellers use openvpn under the hood.  

Not the greatest idea to use a GUI with both, then try to remove one.  I suspect you could have reinstalled protonvpn and been working again. Of course, you'd have a chicken/egg problem if the internet wasn't working.

pptp isn't a vpn. It is a minimial tunnel that doesn't provide any security. No need to have that installed at all. PPTP has been known to be cracked since at least 2005. MSFT says not to use it.

As for DNS issues.  
> Scotty:
The more they overthink the plumbing, the easier it is to stop up the drain.
I disable all the "dns helpers" that don't really help anything, IMHO.  That means no systemd-resolved and no resolvconf.  I find it easier add 2 lines to a new /etc/resolv.conf and know those just work like they have since 1993. No muss, no fuss. No added complications trying to fix a problem I've never had.

I haven't tried to use network manager since around 2012 when it royally screwed up my systems. These days, it is the 2nd thing I purge, after nano, from any system.  Life is too short to deal with NM junk.

---

### Post by Shobuz99 on 2023-03-25
> **TheFu said:**
> Most VPN sellers use openvpn under the hood.  

Not the greatest idea to use a GUI with both, then try to remove one.  I suspect you could have reinstalled protonvpn and been working again. Of course, you'd have a chicken/egg problem if the internet wasn't working.

pptp isn't a vpn. It is a minimial tunnel that doesn't provide any security. No need to have that installed at all. PPTP has been known to be cracked since at least 2005. MSFT says not to use it.

As for DNS issues.  

I disable all the "dns helpers" that don't really help anything, IMHO.  That means no systemd-resolved and no resolvconf.  I find it easier add 2 lines to a new /etc/resolv.conf and know those just work like they have since 1993. No muss, no fuss. No added complications trying to fix a problem I've never had.

I haven't tried to use network manager since around 2012 when it royally screwed up my systems. These days, it is the 2nd thing I purge, after nano, from any system.  Life is too short to deal with NM junk.

Thank you. As I said, I'm back to where I was prior to my curiosity with openvpn. 
Before I did that I was doing just fine logging into my protonvpn account using it through my browser and also logging into and using protonmail acct as my primary email address.
For some reason I don't remember installing pptp, but I uninstalled it once I lost ability to connect to the internet.

That all said, I trust what you're telling me because I respect what you have been doing for a very long time, I'm sure.

I am a bit confused when you said, "That means no systemd-resolved and no resolvconf.  I find it easier add 2 lines to a new /etc/resolv.conf". 
Isn't resolvconf and resolv.conf the same file?

Other than that, Thank you for your answer. 
I think the next time I want to install a dpkg I haven't used before, without understanding what its dependencies are and what it actually affects and does, I'll ask here first.

Thanks again Fu!

Shobuz99

---

### Post by TheFu on 2023-03-25
> **Shobuz99 said:**
>  
I am a bit confused when you said, "That means no systemd-resolved and no resolvconf.  I find it easier add 2 lines to a new /etc/resolv.conf". 
Isn't resolvconf and resolv.conf the same file?
resolvconf is the name of a package that tried to make managing the file a command to be used by 5 other network programs.  /etc/resolv.conf is the file actually used by the OS to know where to look for DNS servers and has barely changed since at least 1993.  
systemd-resolved is the new attempt to have something complex used for something that "sudoedit /etc/resolv.conf" does easily.
My point is that neither systemd-resolved nor resolvconf are needed and often just muck things up.

> **Shobuz99 said:**
>  
I think the next time I want to install a dpkg I haven't used before, without understanding what its dependencies are and what it actually affects and does, I'll ask here first. 

I wouldn't go that far.  I would say that rather than getting a VPN full package from a vendor that is just using a branded version of openvpn, why not just install the stock openvpn and find from that vendor the config files to be used instead?  Anytime we install a package (.deb file) directly, without using one of the Ubuntu repos, we risk dependency issues. Usually everything will be fine for 3-6 months, but after that some other dependencies will break and our system cannot be patched correctly going forward.  If you keep track of all .deb file installs, you can usually unwind them, get back to a state without any random .deb file installs, go and find updated versions of those packages, and reinstall them.  This is a key reason why repos are great and why the setup.exe method of getting a random installer package from someone isn't a great idea. By sticking with Canonical's repos, the dependencies are always moving forward, together.  Introduce 1 .deb file and that can break those dependencies.

---

### Post by Shobuz99 on 2023-03-25
Thank you. I get it now.
BTW, I signed up for protonmail about 7 years ago FoC. 
About 2 years ago they offered their version of VPN with a paid subscription.
I upgraded to the paid subscription.
That's when I started by logging into and using their VPN. 
Both email & vpn are accessed using a browser.
What I* didn't know* was that "most VPN sellers use openvpn under the hood", as you said.

Had I known that previously, I may not have tried it or if I did, I wouldn't have installed it while my browser was running ProtonVPN from my login to it.
Also, I'm certain that I did not know that pptp was not useful and in fact potentially risky to use.

So again, Thank you for the education. 
I'm an antique IBM geek "dog" and I can learn new "tricks" if I ask questions first.:)

Shobuz99

---

### Post by TheFu on 2023-03-25
Well, ProtonVPN is probably one of the "good ones" based on their history and reputation.
Just because pptp was installed, that doesn't mean they were using it. I can't imagine anyone except gamer-centric VPN providers actually selling pptp methods. With weak encryption, comes improved network performance.
[https://www.schneier.com/academic/pptp/faq/](https://www.schneier.com/academic/pptp/faq/)

I was an IBM sub for some time, but on another contract IBM was a sub to the company where I worked. We kept separate offices, so only former 'Beamers who became subs had offices inside the IBM facilities and were drinking the "special water" they serve there.  Both contracts were with the same client organization. They had some smart people at IBM, that's very certain.  There are smart people lots of places.

---

### Post by Skaperen on 2023-03-25
i have considered a couple VPN providers that do use OpenVPN under the hood.  what want is access to all those outgoing points and i want to use more than one at a time.  so my thought was to sign up but use OpenVPN that i configure with my own routing to hve things go where i want (and do routing by user).

i do run a private VPN, now, bouncing through a VPC virtual server running Ubuntu server.  it's fun to see YouTube giving me ads in Dutch.

---

### Post by HermanAB on 2023-03-26
BTW, check your routing table.  VPN software usually set up some special routes to facilitate turning it on/off easily and there may be some leftover route now messing things up for you.

---

### Post by Shobuz99 on 2023-03-27
Thanks everyone.
I'm officially marking this solved.

shobuz99

---

