---
title: "Xfinity Cable Tv Shows"
date: 2014-05-15
forum: General Help
---

### Post by mountainman70 on 2014-05-15
Is there a way to watch Xfinity Cable Tv Shows in Ubuntu 14.04 since Flash only goes to 11.2 ?

---

### Post by TheFu on 2014-05-15
A few options:
a) Record them using any of the CableCARD adapters and play them back on Ubuntu.
[http://www.mythtv.org/wiki/CableCARD](http://www.mythtv.org/wiki/CableCARD) - thanks to DRM, I don't think desktop Linux will ever be supported by the available CableCARD drivers. Recording is likely possible only thru Windows Media Center or Windows-only software drivers.

b) Use recording hardware that accepts video input (RCA, HDMI, Component, S-Video) which also works with Linux ... (or Windows) to record the shows, then play them back later DRM free on Linux. The Hauppauge 1212 is popular, assuming your mandated cable box still outputs component video. With HDMI output only, the HDCP will get in the way.

c) Run WINE, install whatever is necessary to get Windows-based Flash installed and use that. Check app.winehq.org for details.

d) Run a virtual machine of some sort, load Flash inside Windows, inside the VM. Retail copy or volume license version of Windows will be necessary, since DRM bound Windows to hardware is what most new machines have gotten since Vista was released.

e) Fire comcast. When you return all the equipment, tell them why. It feels good, though it doesn't actually help you. I did this 2+ yrs ago and have been using OTA recording with HDHomeRun network tuners ever since. I miss 1-2 syfy shows, but that's about it.

Hopefully you can find an option that works for you for less than the $80-$150/month costs of Comcast.  You can buy a bunch of Netflix, Amazon, HuluPlus for that price. Just sayin'.   Or ... a VPS in an eastern European country for $4/month will provide legal access to media (in those countries).

---

### Post by mountainman70 on 2014-05-15
Thats what I thought. 
I guess for now I will just boot to windows when I want to watch something in xfinity.
Thanks for answering.

---

### Post by TheFu on 2014-05-15
> **mountainman70 said:**
> Thats what I thought. 
I guess for now I will just boot to windows when I want to watch something in xfinity.
Thanks for answering.

Option "c" shouldn't be very hard, people do that for Netflix with silverslight all the time.

---

### Post by oldfred on 2014-05-15
I got some to work using Chromium and installing its pepflashplugin-installer which does not work in Firefox.

But when I am using this I am not in my home territory. And it knows, so some of them like ABCGO do not work, but thru Comcast they may. 

What also is strange is my wife using her iPad an watch anything from Comcast so I had to use her iPad to watch one or two shows.

---

### Post by mountainman70 on 2014-05-15
> **TheFu said:**
> Option "c" shouldn't be very hard, people do that for Netflix with silverslight all the time.

I have wine installed and netflix plays and I have no trouble with it. But Comcast Xfinity does not play in firefox. I have managed to get some shows to play in Chromiun but some have a lock saying I need a subscription.
 Since I am  a Comcast customer why do I need a subscription?

---

### Post by oldfred on 2014-05-16
It does not correctly link back to Comcast to authorize you. 
It makes you sign into Comcast so it knows you are authorized.

---

### Post by mountainman70 on 2014-05-16
> **oldfred said:**
> It does not correctly link back to Comcast to authorize you. 
It makes you sign into Comcast so it knows you are authorized.

Thanks oldfred for your reply. 
I open xfinity and sign in and still have some shows are still locked. Is there anything else I can do?
If not,I guess I will use windows if I want to watch the few shows that are blocked(if they interest me).

---

### Post by oldfred on 2014-05-17
With Firefox I saw no errors and it just did not work.

With Chromium it showed me the errors of the flash being too old.
But then the pepflashplugin-installer allowed me to see some shows but not others??

---

### Post by leadfingers2 on 2014-12-15
Yeah I know this an old thread BUT... I found a solution and I wanted to post it for other people who were also shaking their fists at Comcast/Xfinity

* Install Google Chrome
  (NOT chromium)
* Make sure you have the latest version of libnss3
* Reboot, open Google Chrome, log-on to Xfinity Online and watch your shows.
Works pretty sweet for Netflix & DirecTV Online as well.

If you don't have a Comcast/Xfinity TV package, Some shows & movies (a good share) will be locked.

---

### Post by TheFu on 2014-12-15
If chrome works, then the non-free-pepper plugin workaround for Chromium will work just as well.

If you don't have an Xfinity  TV package, then there isn't ANY way to login ... at least not legal. Sure, you could get a friend's credentials ... 

If you don't **need** live sports, the APV, Netflix and HuluPlus subscriptions - all of them for $30/month- are still $60-$150/month cheaper than Xfinity.  Think about that - for $60 more PER MONTH, how many complete seasons of the few TV shows worth your time can you buy (assuming they aren't included in a streaming package)?  Plus APV and Netflix and BR/DVD don't have commercials, so that saves 22 min/hour off each TV show.

Just sayin'.

Live sports is the only reason to keep u-verse or Comcast TV anymore.

---

