---
title: "google.com blocked under hardy"
date: 2008-05-06
forum: General Help
---

### Post by heathenx on 2008-05-06
i am experiencing rather odd behavior today. all websites work except for [www.google.com](www.google.com). i can get to to images.google.com just fine but i cannot get to the main start up page. this behavior persists in firefox, opera, and konqueror. i can ping [www.google.com](www.google.com) just fine.

i have checked a couple other computers in my house and all can reach [www.google.com](www.google.com).

i'm stumped. not sure what to check. i have never had just one particular website not work before.

i'm using ubuntu 8.04.

---

### Post by justintime32 on 2008-05-06
> **heathenx said:**
> i am experiencing rather odd behavior today. all websites work except for [www.google.com](www.google.com). i can get to to images.google.com just fine but i cannot get to the main start up page. this behavior persists in firefox, opera, and konqueror. i can ping [www.google.com](www.google.com) just fine.

i have checked a couple other computers in my house and all can reach [www.google.com](www.google.com).

i'm stumped. not sure what to check. i have never had just one particular website not work before.

i'm using ubuntu 8.04.

I'm having the same problem, I think due to today's updates. I'm not sure exactly what's going on, the other computers on my network can load it just fine.

---

### Post by sdowney717 on 2008-05-06
working here with hardy. But it was slower to load and the page looks different. Comes up as igoogle.

---

### Post by HotShotDJ on 2008-05-06
Nah.  What you have here is a spurious correlation.  Just because two things happen at the same time (updated hardy & trouble with google) does not mean that one caused the other.  It appears that Google made some major changes to its home page.  You probably tried to connect during the upgrade.

---

### Post by NightwishFan on 2008-05-06
igoogle is like a custom homepage you can disable it I believe.

---

### Post by HotShotDJ on 2008-05-06
> **NightwishFan said:**
> igoogle is like a custom homepage you can disable it I believe.It is indeed.  And I disabled it on my system as soon as i encountered it.  Although, I can see it as being useful for some people.

---

### Post by heathenx on 2008-05-06
i think i have fixed the problem, although, not totally sure. i changed my dns servers in my router from opendns to automatically fetch my isp's dns servers. now i can get to google.com. maybe this is an opendns problem. is that possible?

---

### Post by mvidberg on 2008-05-06
I use opendns.com DNS settings myself and I have not been able to reach google lately myself.   It is very strange, as all other sites work.  I guess I'll have to switch back to my ISP's dns.  :(

---

### Post by fbnaia on 2008-05-06
yes, just to confirm, i also was using opendns, and removed it, and got access to google.com again.

---

### Post by HotShotDJ on 2008-05-06
> **heathenx said:**
> maybe this is an opendns problem. is that possible?Ah HA!  Why didn't you say so in the first place :)  See: [http://forums.opendns.com/comments.php?DiscussionID=226](http://forums.opendns.com/comments.php?DiscussionID=226)

---

### Post by justintime32 on 2008-05-06
I think I figured it out. OpenDNS actually will briefly proxify Google if you use shortcuts (and have this feature enabled). All requests to Google first go to google.navigation.opendns.com, which they use to see if you typed in a shortcut (by default, Firefox will do a google search for anything with a space in it) and will redirect you appropriately if you did. The good news is, just disable that feature and you should be good to go ("Enable OpenDNS proxy").

---

### Post by darco on 2008-05-06
Ya something is strange here....I updated this morning and as far as I could tell everything was fine. For whatever reason, I wanted to setup IGoogle as my wifes homepage in FF. I was able to go in w/o a problem and I then started adding gadgets. It choked , so I restarted FF and now cannot get to Google or Igoogle....I rebooted into Vista and IGoogle comes up fine. While I was in Vista, I upgraded my Router firmware. I rebooted into Ubuntu HH and now the friggin keyring pops up!!! Plus Igoogle nor Google come up. FF and Opera are blazing fast now after rebooting router and modem....
uggh

darco

*edit* I use OpenDNS but the "fix" doesnt work for me. Plus it enables Adult sites.....cant happen at my home.
Google Maps and Gmail shortcuts work fine....

---

### Post by dondad on 2008-05-06
> **justintime32 said:**
> I think I figured it out. OpenDNS actually will briefly proxify Google if you use shortcuts (and have this feature enabled). All requests to Google first go to google.navigation.opendns.com, which they use to see if you typed in a shortcut (by default, Firefox will do a google search for anything with a space in it) and will redirect you appropriately if you did. The good news is, just disable that feature and you should be good to go ("Enable OpenDNS proxy").

I have a similar problem. I have two setups of gutsy and one of hardy. In all of them, [www.google.com](www.google.com) redirects to a japanese version. I don't believe that I am using opendns or shortcuts. If I put in the actual ip address, it works fine. Any idea how I can fix it?

---

### Post by lars-5 on 2008-05-06
if its an opendns problem, why does my windowsxp partition have no problem accessing google.com?

---

### Post by stream303 on 2008-05-07
I'm hoping that this isn't an impasse between google and opendns regarding redirects.

In any case, I just chose to use another search engine.  This may be an issue for some, but for my needs it isn't a problem.

---

### Post by darco on 2008-05-07
Ok this is strange.....I reconfigured my router DNS settings to point to 4.2.2.1 instead the OpenDNS servers. My network card dns points to my routers gateway. Rebooted, opened up FF and Opera and both opened google/igoogle w/o a problem. I then changed my router dns back to the Opendns server rebooted and again google/igoogle opened up fine. Then I typed in an adult site, and it went thru!....I logged into opendns website and my settings were turned off (makes sense). I renabled the Adult setting sites which include the Phishing site and the Proxy/Anonymizer site and bam!, google nor Igoogle will open up. Unchecked Proxy/Anonymizer but still a no go. I just renabled Proxy and unchecked Phishing...Ill see what happens...

Again in my previous post, Vista works fine....

darco

---

### Post by lars-5 on 2008-05-07
there was a thread started over at opendns... and they're working on it right now

---

### Post by darco on 2008-05-07
> **lars-5 said:**
> there was a thread started over at opendns... and they're working on it right now

ya the link above was way outdated....they are all reporting the issue w/most Linux OS's but no probs w/Windows...

[http://forums.opendns.com/comments.php?DiscussionID=1320&page=1#Item_43](http://forums.opendns.com/comments.php?DiscussionID=1320&page=1#Item_43)

---

### Post by darco on 2008-05-07
Looks like the issue is fixed... I restarted my network and google came right up!!!

darco

---

### Post by jeffimperial on 2008-05-10
I'm not using OpenDNS, and I my modem fetches my DNS automatically from my ISP. It's a dynamic service package (hence, they tell me I do not have an IP). Basically the same problem, can't load up any of Google's domains. Tracepath and traceroute reveal nothing, since I get "Too many hops" and pingback returns a Request Timed Out.

This persists in both Ubuntu and Windows. As I said, I am not behind a router, so I don't see why this would happen. Firefox is as unhelpful as Opera too.

If anyone could provide me any clue, any clue at all, as to why this should happen, I'm all eyes and ears.

---

